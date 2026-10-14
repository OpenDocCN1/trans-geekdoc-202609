
We again got the next 2,000 block `headers`, and we repeated the process. This can be continued till we receive all the blocks. Once less than 2,000 `headers` are received, we can also send `getheaders` request to other peers. By sending `getheaders` requests to other peers, we can guess the best blockchain and keep blocks in different chains to be able to undo blocks.

The IBD method is also used to synchronize blocks if blockchain is more than 24 hours behind.

# Synchronizing blockchain

If our node is less than 24 hours behind, we must consider the possibility that there may be competing chains. In this case, we need to get blocks from different peers and keep the blocks in competing chains to undo them if the other chain becomes longer. We use the same method to get blocks as in the last subtopic, the only difference here is that we are getting blocks from multiple peers. Our node also needs to decide which chain it needs to consider best and generally, the longer chain is preferred.

# Transaction broadcasting

As we know, to spend an unspent output available as UTXO, we create a transaction and send it to the peer. We may also receive a transaction from our peers, which we may need to send to other peers. In this subtopic, we will understand how a node receives a transaction.

The following figure shows the steps involved in getting transactions:

![](images/Figure-7.23.jpg)

**Figure 7.23:** Sequence diagram showing the steps involved in transaction broadcast

When a node receives a transaction, it sends an `inv` message to its peer. The peer node checks whether it has seen the transaction earlier. If not, it sends back `getdata` requests with option `MSG_TX` and the `txid`. The node that had sent the `inv` message responds with the actual raw transaction.

`inv` has the same payload structure as `getdata`. The `tx` message has the same message structure as the Bitcoin transaction we discussed in *[Chapter 6, Blockchain, Transactions, and Mining](#c06.xhtml), [figure 6.30](#c06.xhtml#fig6_30)*.

The following code processes the `inv` message if it has the option `MSG_TX`:

```
def createGetDataTxPayload(payload: dict):
    MSG_TX = 1
    data_b = b''
    count = 0
    for i in range(payload['count']):
        # we only request data for tx
        if payload['inventory'][i]['type'] == MSG_TX:
            type_b = struct.pack('<L', payload['inventory'][i]['type'])
            hash_b = bytes.fromhex(payload['inventory'][i]['hash'])[::-1]
            data_b += type_b + hash_b
            count += 1
    count_b = setVarInt(count)
    payload_b = count_b + data_b
    return count, payload_b

def waitForInvMessage(s: socket):
    while True:
        recvmsg = recvMsg(s)
        if recvmsg['command'] == 'inv':
            break
        elif recvmsg['command'] == 'ping':
            sendPongMessage(s, recvmsg)
    print('Received INV', file=flog)
    return recvmsg

def waitForTxMsg(s: socket):
    while True:
        recvmsg = recvMsg(s)
        if recvmsg['command'] == 'tx':
            break
        elif recvmsg['command'] == 'ping':
            sendPongMessage(s, recvmsg)

def sendGetDataMessageWithTx(s: socket, recvmsg: dict):
    sndcmd = 'getdata'
    count, payload = createGetDataTxPayload(recvmsg['payload'])
    sndmsg = createMessage(sndcmd, payload)
    s.send(sndmsg)
    print('==> cmd = %s, msg = %s' % (sndcmd, sndmsg.hex()), file=flog)
    return count

def waitAndHandleInvTxnMessage(s: socket):
    recvmsg = waitForInvMessage(s)
    count = sendGetDataMessageWithTx(s, recvmsg)
    for i in range(count):
        waitForTxMsg(s)

def sendrecvHeadersData(s: socket):
    waitAndHandleInvTxnMessage(s)

def sendrecvHandler(s: socket, version: int):
    if establishConnection(s, version) == False:
        print('Establish connection failed', file=flog)
        return
    sendrecvHeadersData(s)
```

**Program 7.12:** Program for receiving and processing inv messages for transactions

The following are the communication logs showing the received `inv` message and the sent `getdata` message with a request for two transactions:

![](images/Figure-7.24.jpg)

**Figure 7.24:** The inv message received from peer and the getdata request made to the peer in response

We received two transactions as requested by our node:

![](images/Figure-7.25.jpg)

**Figure 7.25:** tx messages containing transactions received from the peer in response to the getdata request

Our node can send a received transaction to other connected nodes by first sending an `inv` message with the transaction IDs of the received transactions. This process continues till all active nodes have received the transaction.

In this subtopic, you learned how a transaction is broadcast on the Bitcoin network.

# Block broadcasting

Blocks also need to be propagated on the network as quickly as possible so that even the farthest node receives it in a reasonable time and, consequently, does not create too many or too long competing branches. Before we can receive recent blocks, we need to synchronize our node with the connected peer so that the peer is aware that our node is not lagging, and our node will be able to verify the recently received block.

Once blockchain is synchronized, we are ready for live updates from peers.

Here are the different methods to broadcast blocks:

*   A miner that has mined a new block instead just broadcasts the new block via `block` message. This is called **Unsolicited Block Push**.

*   For a normal node, there are three methods to receive new blocks. These methods are called **Direct Headers Announcements**. This is enabled either by the `sendheaders` method or the `sendcmpct` message. The `sendheaders` method is the legacy Direct headers announcement method, which is available since 70012, while the `sendcmpct` method was introduced in 70014. The following sub-points explain them:

    *   The node sends `sendheaders` immediately after the connection is established. This indicates to the peer that whenever it receives a new block, it can send `headers`. Based on `headers`, we can request `getdata`. And as a response to `getdata`, the peer sends blocks.

    *   Relay latency can be further reduced by requesting compact blocks. The `sendcmpct` message can be sent immediately after the connection is established. There are two methods:

        *   **High Bandwidth Relay:** Whenever the peer receives a block, it sends `cmpctblock`. It contains a header and a list of short IDs. We look at `mempool` for a list of transaction IDs based on short IDs and reconstruct the block. If there are missing transactions in `mempool`, we request only those missing transactions by sending `getblocktxn`. And the peer responds with a `blocktxn` message containing the transactions.

        *   **Low Bandwidth Relay:** Whenever the peer receives a block, it sends a `headers` message. We send a `getdata` message with the `MSG_CMPCT_BLOCK` type as a response. The peer responds with `cmpctblock`, and further processing is like in **high bandwidth relay**.

# Unsolicited Block Push

The following figure shows an **unsolicited block push** by the miner, which has successfully mined a block. A miner does not need to first send `headers` messages as it knows the peer will not have it. It also does not need to synchronize its node with peers as it can only mine a block if it is aware of the previous node in the chain.

![](images/Figure-7.26.jpg)

**Figure 7.26:** Illustration of miner broadcasting newly generated block to peers using Unsolicited Block Push

We can see that in the figure, a miner just pushes the newly mined block to all the connected peers. A miner does not require any other communication.

# Direct Headers Announcements

The following figure shows Direct headers announcements (Legacy):

![](images/Figure-7.27.jpg)

**Figure 7.27:** Sequence diagram of the steps involved in Direct headers announcements (Legacy)
