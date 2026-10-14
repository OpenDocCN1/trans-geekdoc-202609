
# Program 7.11: Program for making IBD request to peer and receiving blocks

## Payload Parsing Functions

```python
payload = {}
payload['count'] = getVarInt(payload_m)
payload['inventory'] = []

for i in range(payload['count']):
    inv = {}
    inv['type'] = int.from_bytes(payload_m.read(4), byteorder='little')
    if inv['type'] == MSG_TX:
        mempool = rpc_connection.getrawmempool(True)
        if (len(mempool_l_g) > 0):
            new_tx = set(mempool.keys()) ^ set(mempool_l_g[-1].keys())
            if len(new_tx) > 0:
                mempool_l_g.append(mempool)
                print('inserted mempool', file=flog)
            else:
                mempool_l_g.append(mempool)
                print('inserted mempool', file=flog)
    inv['hash'] = payload_m.read(32)[::-1].hex()
    payload['inventory'].append(inv)

return payload
```

```python
def parseBlockHeader(payload_m: mmap):
    hdr = {}
    hdr['version'] = int.from_bytes(payload_m.read(4), byteorder='little')
    hdr['prev_blockhash'] = payload_m.read(32)[::-1].hex()
    hdr['merkle_root'] = payload_m.read(32)[::-1].hex()
    hdr['timestamp'] = int.from_bytes(payload_m.read(4), byteorder='little')
    hdr['bits'] = payload_m.read(4)[::-1].hex()
    hdr['nonce'] = payload_m.read(4)[::-1].hex()
    return hdr
```

```python
def parseGetBlocksGetHeadersPayload(payload_m: mmap, payloadlen=0):
    payload = {}
    payload['version'] = int.from_bytes(payload_m.read(4), byteorder='little')
    payload['hash count'] = getVarInt(payload_m)
    payload['block locator hashes'] = []

    for i in range(payload['hash count']):
        h = payload_m.read(32)[::-1].hex()
        payload['block locator hashes'].append(h)

    payload['hash_stop'] = payload_m.read(32)[::-1].hex()
    return payload
```

```python
def parseHeadersPayload(payload_m: mmap, payloadlen=0):
    payload = {}
    payload['count'] = getVarInt(payload_m)
    payload['headers'] = []

    for i in range(payload['count']):
        hdr = {}
        start = payload_m.tell()
        h_b = hashlib.sha256(payload_m.read(80)).digest()
        hdr['blkhash'] = hashlib.sha256(h_b).digest()[::-1].hex()
        payload_m.seek(start)
        hdr['header'] = parseBlockHeader(payload_m)
        hdr['txn_count'] = getVarInt(payload_m)
        payload['headers'].append(hdr)

    return payload
```

```python
def parseTxPayload(payload_m: mmap, payloadlen=0):
    payload = {}
    payload['version'] = int.from_bytes(payload_m.read(4), byteorder='little')
    payload['tx_in count'] = getVarInt(payload_m)
    payload['tx_in'] = []

    for i in range(payload['tx_in count']):
        txin = {}
        txin['prev_tx_hash'] = payload_m.read(32)[::-1].hex()
        txin['prev_tx_out_index'] = int.from_bytes(payload_m.read(4), byteorder='little')
        txin['bytes_scriptsig'] = getVarInt(payload_m)
        txin['sriptsig'] = payload_m.read(txin['bytes_scriptsig']).hex()
        txin['sequence'] = payload_m.read(4)[::-1].hex()
        payload['tx_in'].append(txin)

    payload['tx_out count'] = getVarInt(payload_m)
    payload['tx_out'] = []

    for i in range(payload['tx_out count']):
        txout = {}
        txout['satoshis'] = int.from_bytes(payload_m.read(8), byteorder='little')
        txout['bytes_scriptpubkey'] = getVarInt(payload_m)
        txout['scriptpubkey'] = payload_m.read(txout['bytes_scriptpubkey']).hex()
        payload['tx_out'].append(txout)

    payload['locktime'] = int.from_bytes(payload_m.read(4), byteorder='little')
    return payload
```

```python
def parseBlockPayload(payload_m: mmap, payloadlen=0):
    payload = {}
    payload['version'] = int.from_bytes(payload_m.read(4), byteorder='little')
    payload['prev_blockhash'] = payload_m.read(32)[::-1].hex()
    payload['merkle_root'] = payload_m.read(32)[::-1].hex()
    payload['timestamp'] = int.from_bytes(payload_m.read(4), byteorder='little')
    payload['bits'] = payload_m.read(4)[::-1].hex()
    payload['nonce'] = payload_m.read(4)[::-1].hex()
    payload['txn_count'] = getVarInt(payload_m)
    payload['txns'] = []

    for i in range(payload['txn_count']):
        payload['txns'].append(parseTxPayload(payload_m))

    return payload
```

## Message Creation Functions

```python
def createGetHeadersPayload(hdr_info_l: list, version: int):
    version_b = struct.pack('<L', version)
    blk_locator_hashes_b = b''
    count = 0

    for i in range(len(hdr_info_l) - 1, len(hdr_info_l) - 32, -1):
        if i < 1:  # assuming first block is genesis
            break
        blk_locator_hashes_b += bytes.fromhex(hdr_info_l[i]['blkhash'])[::-1]
        count += 1

    blk_locator_hashes_b += bytes.fromhex(getGenesisBlockHash())[::-1]
    count += 1

    hash_count_b = setVarInt(count)
    stop_hash_b = bytes(32)

    payload = version_b \
        + hash_count_b \
        + blk_locator_hashes_b \
        + stop_hash_b

    return payload
```

## Network Communication Functions

```python
def waitForBlock(s: socket):
    while True:
        recvmsg = recvMsg(s)
        if recvmsg['command'] == 'block':
            break
        elif recvmsg['command'] == 'ping':
            sendPongMessage(s, recvmsg)
    return recvmsg
```

```python
def sendGetHeadersMessage(s: socket, hdr_info_l: list, version: int):
    sndcmd = 'getheaders'
    payload = createGetHeadersPayload(hdr_info_l, version)
    sndmsg = createMessage(sndcmd, payload)
    s.send(sndmsg)
    print('==> cmd = %s, msg = %s' % (sndcmd, sndmsg.hex()), file=flog)
```

```python
def waitForHeaders(s: socket):
    while True:
        recvmsg = recvMsg(s)
        if recvmsg['command'] == 'headers':
            break
        elif recvmsg['command'] == 'ping':
            sendPongMessage(s, recvmsg)
    return recvmsg
```

```python
def createGetDataPayload(count: int, hash_l: list):
    MSG_BLOCK = 2
    hash_count_b = setVarInt(count)
    hashes_b = b''

    for i in range(count):
        type_b = struct.pack('<L', MSG_BLOCK)
        hashes_b += type_b + bytes.fromhex(hash_l[i]['blkhash'])[::-1]

    payload_b = hash_count_b + hashes_b
    return payload_b
```

```python
def sendGetDataMessage(s: socket, count: int, hash_l: list):
    sndcmd = 'getdata'
    payload = createGetDataPayload(count, hash_l)
    sndmsg = createMessage(sndcmd, payload)
    s.send(sndmsg)
    print('==> cmd = %s, msg = %s' % (sndcmd, sndmsg.hex()), file=flog)
```

```python
def sendAndHandleGetHeaders(s: socket, hdr_info_l: list, version: int):
    sendGetHeadersMessage(s, hdr_info_l, version)
    recvmsg = waitForHeaders(s)
    count = recvmsg['payload']['count']

    for i in range(0, count, 16):
        lindex = i + 16 if i + 16 < count else count
        print(i, lindex)
        blk_l = recvmsg['payload']['headers'][i:lindex]
        sendGetDataMessage(s, lindex - i, blk_l)

        for j in range(i, lindex):
            waitForBlock(s)

    return recvmsg
```

```python
def sendrecvHeadersData(s: socket, version: int):
    recvmsg = sendAndHandleGetHeaders(s, [], version)
    sendAndHandleGetHeaders(s, recvmsg['payload']['headers'], version)
```

```python
def sendrecvHandler(s: socket, version: int):
    if establishConnection(s, version) == False:
        print('Establish connection failed', file=flog)
        return
    sendrecvHeadersData(s, version)
```

## Output Analysis

This gives the following output. First, we send the `getheaders` request with genesis block hash and no hash stop:

![Figure 7.18: getheaders request sent to the peer](images/Figure-7.18.jpg)

The following is the truncated `headers` response containing 2,000 headers:

![Figure 7.19: Received headers response from the peer](images/Figure-7.19.jpg)

We responded with `getdata` requesting 16 blocks. Here's the request:

![Figure 7.20: Sent getdata request to the peer](images/Figure-7.20.jpg)

We got 16 blocks, and the following is one of them:

![Figure 7.21: Received block in response from the peer](images/Figure-7.21.jpg)

After 16 blocks are received, we requested the next 16 blocks and again got 16 blocks. This continued till all 2,000 blocks are received. A node also needs to verify each block according to the consensus rules. Some of these consensus rules were covered in [Chapter 6, Blockchain, Transactions, and Mining](#c06.xhtml).

After receiving 2,000 blocks, we again send `getheaders` requests with a list of the last 31 block hashes and the genesis block hash, making it 32 hashes. The following is the part of the request:

![Figure 7.22: Truncated getheaders request made to the peer](images/Figure-7.22.jpg)
