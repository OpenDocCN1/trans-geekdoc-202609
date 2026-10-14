
以下是 `sendcmpct` 载荷的结构：

![](img/Figure-7.34.jpg)

**图 7.34：** `sendcmpct` 消息的结构

在 `sendcmpct` 消息中，有两个字段：

**Announce** 是一个单字节布尔值。值 `0` 表示支持低带宽中继，值 `1` 表示支持高带宽中继。

**Version** 是一个 8 字节字段；目前它可以具有以下值之一：

*   值 `1`，表示支持 `wtxid`，即隔离见证中的见证交易 ID。
*   值 `0`，表示支持具有交易 ID 的其他交易。

我们将在即将到来的章节中介绍隔离见证交易。

下一小节将介绍这些中继方法中的每一种。

## 高带宽紧凑区块通告

以下是活动图中的消息交换序列：

![](img/Figure-7.35.jpg)

**图 7.35：** 高带宽中继紧凑区块通告的序列图

## 接收和处理紧凑区块消息

收到针对隔离见证和非隔离见证交易的 `sendcmpct` 请求后，我们发送一个包含近期区块和创世区块列表的 `getheaders` 请求，并与对等节点同步我们的节点，这与我们在 **同步区块** 小节中所做的一样。

一旦对等节点知晓我们拥有其认为的最佳区块链中的所有区块，我们就可以准备好从对等节点接收新区块。请注意，我们的最佳区块链可能与对等节点的最佳区块链不同，因为我们将从多个对等节点接收区块。最佳区块链是指累积工作量证明最高的链。这可以通过将链中每个区块记录的难度相加来计算。难度调整仅在每 2016 个区块发生一次，因此累积工作量证明最高的链通常是区块更多的链。

当对等节点收到一个新区块时，它会发送一个包含该区块中所有交易的压缩或短 ID 的 `cmpctblock` 消息。为了解析和生成短 ID，我们需要安装以下 Python 包：

![Figure 7.36: pip package to generate and parse short IDs](img/Figure-7.36.jpg)

**Figure 7.36:** 用于生成和解析短 ID 的 pip 包

`cmpctblock`、`getblocktxn` 和 `blocktxn` 消息的结构如下：

![Figure 7.37: Payload structure of cmpctblock, getblocktxn and blocktxn](img/Figure-7.37.jpg)

**Figure 7.37:** `cmpctblock`、`getblocktxn` 和 `blocktxn` 的载荷结构

这些消息载荷的详细信息如下：

![Table 7.4: List of compact messages and their description](img/233.jpg)

**Table 7.4:** 紧凑消息列表及其描述

在以下代码中，连接已建立，现在我们正在发送和处理接收新区块所需的请求：

```python
def parseShortIds(payload_m: mmap, shortids_len: int):
    shortids = []
    for i in range(shortids_len):
        shortids.append(payload_m.read(6).hex())
    return shortids

def parsePrefilledTxn(payload_m: mmap, prefilledtxn_len: int):
    prefilledtxn_l = []
    for i in range(prefilledtxn_len):
        prefilledtxn = {}
        prefilledtxn['index'] = getVarInt(payload_m)
        prefilledtxn['tx'] = parseTxPayload(payload_m)
        prefilledtxn_l.append(prefilledtxn)
    return prefilledtxn_l

def parseCmpctBlockPayload(payload_m: mmap, payloadlen = 0):
    payload = {}
    pos = payload_m.tell()
    payload['hdr_nonce'] = payload_m.read(88).hex()
    payload_m.seek(pos)
    payload['header'] = parseBlockHeader(payload_m)
    payload['nonce'] = payload_m.read(8)[::-1].hex()
    payload['shortids_length'] = getVarInt(payload_m)
    payload['shortids'] = parseShortIds(payload_m, payload['shortids_length'])
    payload['prefilledtxn_length'] = getVarInt(payload_m)
    payload['prefilledtxn'] = parsePrefilledTxn(payload_m, payload['prefilledtxn_length'])
    return payload

def parseBlockTxnPayload(payload_m: mmap, payloadlen = 0):
    payload = {}
    payload['blkhash'] = payload_m.read(32)[::-1].hex()
    payload['txn_len'] = getVarInt(payload_m)
    payload['txn'] = []
    for i in range(payload['txn_len']):
        txn = parseTxPayload(payload_m)
        payload['txn'].append(txn)
    return payload

def createSendCompactPayload(announce: int, version: int):
    announce_b = struct.pack('<B', announce)
    version_b = struct.pack('<Q', version)
    payload = announce_b + version_b
    return payload

def createHeadersPayloadNoHeaders():
    cnt_b = setVarInt(0)
    headers_b = b''
    payload = cnt_b + headers_b
    return payload

def createGetBlockTxnPayload(payload: dict, shortIDs_index_l: list):
    hdr_b = bytes.fromhex(payload['hdr_nonce'])[0:80] #header
    blkhash_b = hashlib.sha256(hashlib.sha256(hdr_b).digest()).digest()
    print('blkhash = %s' % blkhash_b[::-1].hex())
    indexes_len_b = setVarInt(len(shortIDs_index_l))
    indexes_b = b''
    for shortIDs_index in shortIDs_index_l:
        indexes_b += setVarInt(shortIDs_index)
    payload = blkhash_b + indexes_len_b + indexes_b
    return payload

def sendSendCompactMessage(s: socket):
    # send sendcmpct message for Segwit
    sndcmd = 'sendcmpct'
    payload = createSendCompactPayload(1, 2)
    sndmsg = createMessage(sndcmd, payload)
    s.send(sndmsg)
    print('==> cmd = %s, msg = %s' % (sndcmd, sndmsg.hex()), file=flog)
    # send sendcmpct message for others
    sndcmd = 'sendcmpct'
    payload = createSendCompactPayload(1, 1)
    sndmsg = createMessage(sndcmd, payload)
    s.send(sndmsg)
    print('==> cmd = %s, msg = %s' % (sndcmd, sndmsg.hex()), file=flog)

def sendHeadersMessage(s: socket):
    # send header message
    sndcmd = 'headers'
    payload = createHeadersPayloadNoHeaders()
    sndmsg = createMessage(sndcmd, payload)
    s.send(sndmsg)
    print('==> cmd = %s, msg = %s' % (sndcmd, sndmsg.hex()), file=flog)

def convertTxIDs2ShortIDs(payload: dict, txid_l: list):
    hdr_nonce_b = bytes.fromhex(payload['hdr_nonce'])
    shortids_l = []
    for txid in txid_l:
        txid_b = bytes.fromhex(txid)[::-1]
        h_b = hashlib.sha256(hdr_nonce_b).digest()[0:16]
        sip = siphash.SipHash_2_4(h_b, txid_b)
        siphash_b = sip.digest()
        shortid = siphash_b[:-2].hex()
        shortid_l = siphash_b[2:].hex()
        shortids_l.append(shortid)
    return shortids_l

def findMissingShortIDs(payload: dict):
    for i in range(len(mempool_l_g)):
        stored_mempool = mempool_l_g[-1-i]
        txid_l = []
        for k, v in stored_mempool.items():
            if 'wtxid' in v:
                txid_l.append(v['wtxid'])
            else:
                txid_l.append(k)
        shortIDs = convertTxIDs2ShortIDs(payload, txid_l)
        shortIDs_index_l = []
        for recvd_shortID in payload['shortids']:
            if recvd_shortID not in shortIDs:
                shortIDs_index_l.append(payload['shortids'].index(recvd_shortID) + 1)
        if len(shortIDs_index_l) > 0:
            break
    return shortIDs_index_l

def waitForCmpctBlock(s: socket):
    while True:
        recvmsg = recvMsg(s)
        if recvmsg['command'] == 'cmpctblock':
            return recvmsg
        elif recvmsg['command'] == 'ping':
            sendPongMessage(s, recvmsg)
            return recvmsg

def sendGetBlockTxn(s: socket, recvmsg: dict, shortIDs_index_l):
    sndcmd = 'getblocktxn'
    payload = createGetBlockTxnPayload(recvmsg['payload'], shortIDs_index_l)
    sndmsg = createMessage(sndcmd, payload)
    s.send(sndmsg)
    print('==> cmd = %s, msg = %s' % (sndcmd, sndmsg.hex()), file=flog)

def waitForBlockTxn(s: socket):
    while True:
        recvmsg = recvMsg(s)
        if recvmsg['command'] == 'blocktxn':
            return recvmsg
        elif recvmsg['command'] == 'ping':
            sendPongMessage(s, recvmsg)

def waitAndHandleHeaderResponse(s: socket):
    recvmsg = waitForCmpctBlock(s)
    shortIDs_index_l = findMissingShortIDs(recvmsg['payload'])
    if len(shortIDs_index_l) > 0:
        sendGetBlockTxn(s, recvmsg, shortIDs_index_l)
        waitForBlockTxn(s)

def sendrecvHeadersData(s: socket, version: int):
    sendSendHeadersMessage(s)
    sendSendCompactMessage(s)
    blkhash_l = getBlockHashListFromCoreClient()
    sendAndHandleGetHeaders(s, blkhash_l, version)
    waitAndHandleHeaderResponse(s)

def sendrecvHandler(s: socket, version: int):
    if establishConnection(s, version) == False:
        print('Establish connection failed', file=flog)
        return
    sendrecvHeadersData(s, version)
```

**Program 7.14:** 用于接收和处理高带宽中继紧凑消息的程序

我们执行了上述代码并获得了以下通信消息。我忽略了其他消息，例如 `ping`、`addr` 或 `inv`。

首先，我们发送了用于隔离见证的 `sendheaders` 和 `sendcpmct` 以及用于非隔离见证的 `sendcmpct`：

![Figure 7.38: Messages sent to peer that our node accepts compact messages for both segwit and non-segwit payload](img/Figure-7.38.jpg)

**Figure 7.38:** 发送给对等节点的消息，表明我们的节点接受隔离见证和非隔离见证载荷的紧凑消息

然后，我们发送了一个 `getheaders` 消息并收到了 **headers** 消息。以下是截断的 `getheaders` 消息和接收到的 `headers` 消息：

![Figure 7.39: Truncated getheaders request sent to peer with a list of block hashes](img/Figure-7.39.jpg)

**Figure 7.39:** 发送给对等节点的截断 `getheaders` 请求，包含区块哈希列表

我们在以下传入消息中收到了一个空的头部列表作为响应：

![Figure 7.40](img/Figure-7.40.jpg)

**图 7.40：** 对等节点响应最近的区块头列表，而非 `getheaders` 请求中的内容

对等节点响应了 `headers` 消息，且不包含计数为零的任何 `headers`。

接下来，我们等待对等节点发送 `cmpctblock` 消息。与此同时，我们收到了包含交易的 `inv` 消息。以下是我们收到的截断后的 `cmpctblock` 消息：

![](img/Figure-7.41.jpg)

**图 7.41：** 对等节点在收到新区块时发送 `cmpctblock` 消息
