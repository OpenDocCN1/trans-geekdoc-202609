
# Bitcoin Network Messaging

Bitcoin network nodes communicate with each other for various reasons, like to learn about some other peers, to be sure that the connection is still active, to help other nodes to sync with itself, or ask for missing blocks, or to broadcast any new received block or transaction. In this topic, you will learn in detail about the messaging and its format, and program it by writing a client.

## Message Format

Messages exchanged over the network have headers and payload, and the payload is dependent on the command.

Here’s the message format:

![](images/Figure-7.6.jpg)

**Figure 7.6:** Illustration of protocol message format

The following is the explanation of each field of the message format:

*   **Magic** is the same as we learned in the block structure in ***[Chapter 6, Blockchain, Transactions, and Mining](#c06.xhtml)*** and we can look at its values in [table 6.3](#c06.xhtml#tab6_3).
*   **Command** is the command sent in ASCII padded with all zeroes i.e. `b'\0'`.
*   **Length** is the length of the payload.
*   **Checksum** is the checksum of the payload.
*   **Payload** is the parameters of the command sent.

The following is the method that creates this message:

```
def createMessage(command, payload):
    magic = 0x0709110B
    checksum = hashlib.sha256(hashlib.sha256(payload).digest()).digest()[0:4]
    magic_b = struct.pack('<L', magic)
    cmd_b = struct.pack('<12s', command.encode('ascii'))
    payload_len_b = struct.pack('<L', len(payload))
    checksum_b = struct.pack('<4s', checksum)
    msg = magic_b + cmd_b + payload_len_b + checksum + payload
    return msg
```

**Program 7.3:** A method for creating protocol message

## Establishing Connection

Bitcoin establishes a connection by first exchanging versions and then acknowledging their acceptance. Before acknowledging the version, a node needs to send its own version. So, the network handshake looks as follows:

![](images/Figure-7.7.jpg)

**Figure 7.7:** An illustration of the sequence of message transfers to establish Bitcoin connection

The following is the `version` message payload structure:

![](images/Figure-7.8.jpg)

**Figure 7.8:** Version message payload structure

The following is the explanation of each field of the `version` message:

*   `Version` is the Protocol version running on a host.
*   **Service** is the service supported by the sending node. Here’s the list of service codes:

| **Byte Code** | **Service Offered** | **Description** |
| --- | --- | --- |
| 1 | NODE_NETWORK | Full Node |
| 2 | NODE_GETUTXO | BIP 0064: Supports getutxos and utxos |
| 4 | NODE_BLOOM | BIP 0111: Supports Bloom filters |
| 8 | NODE_WITNESS | BIP 0144: Supports Segregated Witness |
| 1024 | NODE_NETWORK_LIMITED | BIP 0159: Pruned node |

**Table 7.2:** List of service codes required by Version message

*   **Timestamp** is the Unix epoch time of the payload.
*   **Addr Recv** is the address of the connection receiving node. So, the node sending the `version` payload will have the address and port of the peer it is connecting to. The Services field is normally set to zeroes.
*   **Addr from** is the address of the connection originating node. So, the node sending the `version` payload will have its own address and port. It also includes services offered by the sender.
*   **Nonce** is a random number that is useful in identifying whether we are not connected to ourselves.
*   **User Agent** is used to identify the software running at the node. It is defined in BIP-0014.
*   **Start Height** is the current block height at the node blockchain.
*   **Relay** is an optional Boolean value that is set by SPV to false to indicate that the node will not participate in relaying a message. This means it does not want peers to advertise `inv` messages with MSG_BLOCK. This protects the node from getting flooded by `inv` messages. This is defined in BIP 0037.

The following is the distribution of version of nodes at the time of writing:

![](images/Figure-7.9.jpg)

**Figure 7.9:** Chart showing the distribution of the version of nodes on the Bitcoin network

The following is the distribution of User Agents in the Bitcoin network:

![](images/Figure-7.10.jpg)

**Figure 7.10:** Bar chart showing the distribution of user agents in the Bitcoin network

The following is the program that creates `version` payload:

```
from bitcoinrpc.authproxy import AuthServiceProxy, JSONRPCException
import struct
import random

rpc_connection = AuthServiceProxy("http://%s:%s@127.0.0.1:18332" % ('test', 'test'))

def setVarInt(n: int):
    if n < 0xfd:
        n_h = '%02x' % n
    elif n > 0xfd and n < 0xffff:
        n_h = 'fd%04x' % n
    elif n > 0xffff and n < 0xFFFFFFFF:
        n_h = 'fe%08x' % n
    else:
        n_h = 'ff%016x' % n
    return bytes.fromhex(n_h)

def getLastBlockHeight():
    height = rpc_connection.getblockcount()
    return height

def createUserAgent():
    sub_version = "/MyTestAgent:0.0.1/"
    sub_version_b = sub_version.encode()
    len_b = setVarInt(len(sub_version_b))
    return len_b + sub_version_b

def createRecvIPAddress(ip, port):
    service_b = struct.pack('<Q', 1)
    ip_b = socket.inet_aton(ip)
    ipv4_to_ipv6 = bytearray.fromhex("00000000000000000000ffff") + ip_b
    ipv6addr_b = struct.pack('>16s', ipv4_to_ipv6)
    port_b = struct.pack('>H', port)
    addr_b = service_b + ipv6addr_b + port_b
    return(addr_b)

def createTransIPAddress():
    service_b = struct.pack('<Q', 1)
    ip_b = socket.inet_aton("0.0.0.0")
    ipv4_to_ipv6 = bytearray.fromhex("000000000000000000000000") + ip_b
    ipv6addr_b = struct.pack('>16s', ipv4_to_ipv6)
    port_b = struct.pack('>H', 0)
    addr_b = service_b + ipv6addr_b + port_b
    return(addr_b)

def createVersionPayload(s: socket, version: int):
    version_b = struct.pack('<L', version)
    services_b = struct.pack('<Q', 1)
    timestamp_b = struct.pack('<Q', int(time.time()))
    myip, myport = s.getsockname()
    addr_recv_b = struct.pack('<26s', createRecvIPAddress(myip, myport))
    addr_trans_b = struct.pack('<26s', createTransIPAddress())
    nonce_b = struct.pack('<Q', random.getrandbits(64))
    user_agent = createUserAgent()
    user_agent_b = struct.pack('<%ds' % len(user_agent), user_agent)
    start_height_b = struct.pack('<L', getLastBlockHeight())
    payload = version_b \
        + services_b \
        + timestamp_b \
        + addr_recv_b \
        + addr_trans_b \
        + nonce_b \
        + user_agent_b \
        + start_height_b
    return payload
```

**Program 7.4:** Program for creating Version message payload

To create the message payload, we use the Python `struct.pack`. The following are the symbols and their meanings:

| **Symbols** | **Represents** |
| --- | --- |
| `<` | Little Endian |
| `>` | Big Endian |
| `B` | 1-byte Unsigned Integer |
| `H` | 2-byte Unsigned Integer |
| `L` | 4-byte Unsigned Integer |
| `Q` | 8-byte Unsigned Integer |
| `xs` | Byte array of size x |

**Table 7.3:** List of Python struct pack symbols and their meanings

You can check out the Python docs for more details:

[https://docs.python.org/3.8/library/struct.html](https://docs.python.org/3.8/library/struct.html)

IP address and port are in big endian, while the rest of the message is in the little-endian format. When we pack an ASCII string, it converts it into a byte array and pads it with zeroes.

We call the preceding methods as follows:

```
if __name__ == '__main__':
    peers = getTestnetPeers()
    p = random.choice(peers)
    s = None
    peerinfo = {}
    print("Trying to connect to ", p)
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    err = s.connect(p)
    print('TCP Connection Established')
    payload = createVersionPayload(s, 70015)
    print('Version payload: ', payload.hex())
    s.close()
```

This creates the following payload in hex string:

![](images/Figure-7.11.jpg)

**Figure 7.11:** Shows version payload created by the CreateVersionPayload program

When we receive the `version` message, we do the following:
