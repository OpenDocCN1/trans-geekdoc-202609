

`tx['inp_cnt'] = getVarInt(txn_m)`

`tx['is_segwit'] = False`

`if tx['inp_cnt'] == 0:`

`# check segwit flag`

`tx['is_segwit'] = (int.from_bytes(txn_m.read(1), byteorder='little') == 1)`

`if tx['is_segwit'] == True:`

`tx['inp_cnt'] = getVarInt(txn_m)`

`inp_l = []`

`for i in range(tx['inp_cnt']):`

`inp = {}`

`inp['prev_tx_hash'] = txn_m.read(32)[::-1].hex()`

`inp['prev_tx_out_index'] = txn_m.read(4)[::-1].hex()`

`inp['bytes_scriptsig'] = getVarInt(txn_m)`

`inp['scriptsig'] = txn_m.read(inp['bytes_scriptsig']).hex()`

`inp['sequence'] = txn_m.read(4)[::-1].hex()`

`inp_l.append(inp)`

`tx['inputs'] = inp_l`

`tx['out_cnt'] = getVarInt(txn_m)`

`out_l = []`

`for i in range(tx['out_cnt']):`

`out = {}`

`out['satoshis'] = int.from_bytes(txn_m.read(8), byteorder='little')`

`out['bytes_scriptpubkey'] = getVarInt(txn_m)`

`out['scriptpubkey'] = txn_m.read(out['bytes_scriptpubkey']).hex()`

`out_l.append(out)`

`tx['outs'] = out_l`

`curloc = txn_m.tell()`

`txn_m.seek(startloc)`

`txid_b = txn_m.read(curloc - startloc)`

`if tx['is_segwit'] == True:`

`# if SegWit flag is true than remove SegWit marker and flag from txhash calculation`

`txid_b = txid_b[:4] + txid_b[6:]`

`for i in range(tx['inp_cnt']):`

`tx['inputs'][i]['witness_cnt'] = getVarInt(txn_m)`

`witness_l = []`

`witness_cnt = tx['inputs'][i]['witness_cnt']`

`for j in range(witness_cnt):`

`witness = {}`

`witness['size'] = getVarInt(txn_m)`

`witness['witness'] = txn_m.read(witness['size']).hex()`

`witness_l.append(witness)`

`tx['inputs'][i]['witnesses'] = witness_l`

`locktime_b = txn_m.read(4)`

`txid_b += locktime_b`

`tx['locktime'] = int.from_bytes(locktime_b, byteorder='little')`

`tx['txid'] = hash256(txid_b)[::-1].hex()`

`curloc = txn_m.tell()`

`txn_m.seek(startloc)`

`wtxid_b = txn_m.read(curloc - startloc)`

`tx['wtxid'] = hash256(wtxid_b)[::-1].hex()`

`tx['bytes'] = len(wtxid_b)`

`tx['weight'] = (len(wtxid_b) - len(txid_b)) + (len(txid_b) * 4)`

`return tx`

**程序 12.2：** 交易解析器

前面的程序给出了给定隔离见证交易的交易信息。我们使用该程序来解析具有 `txid` 的交易：

`c6176c811328a9fd82a3a71da78e73781bc5c9a6580fdee4cf4392b165b1a072`

我们可以使用 Bitcoin Core 获取 `wtxid` 或交易哈希，如下所示：

![](images/Figure-12.8.jpg)

**图 12.8：** 从 txid 获取 wtxid 的 CLI 命令

我们按如下方式调用该方法：

```
txn_b = bytes.fromhex('02000000000102dc0f4a1601bd6bfec4241fede438bee45958773fe5d95f88ec890e2363983e0c0100000000ffffffff904d74d770c0ef5ce91190750b235d7ffb340b82b392812ba8e6ad5f0a8c4ca70000000000ffffffff02f31f0a00000000001600140c986c1d8ad520c072ee1aa0a151615c891ef71455b8180000000000160014097e656deb55afa3786c600a87d990dcab86fc2d024730440220685234e91eb14e6d1717c543193181700b1cbf5fecddbee79ed9b6b0bbf24077022033dac5cc679dca810327dcac4b84ba2b007a3a4fda6fb2cbc6099ae91c53804f01210277bed123bc0c0f9883b0bc14014f0385d39eac7ac7212d8c9928fa4121a191f4024730440220635eb52780098e3bd1e39a630a23f553ac62b97d0cd0356fa34ceb47cb0195250220599b83d8872ff173781b83b36bf159b59ed7685f73811f449fa1df814fbef15c0121022cd4d498f1ed0ee382eefe4b6e1d8c5aa678d47b693389ccdf77559b3220c5fa00000000')
txn_m = mmap.mmap(-1, len(txn_b) + 1)
txn_m.write(txn_b)
txn_m.seek(0)
tx = getTransactionInfo(txn_m)
print(json.dumps(tx))
```

我们得到以下交易信息：

![](images/Figure-12.9.jpg)

**图 12.9：** 通过执行 Python 程序获得的交易信息

在前面的程序中，`vsize` 的计算如下：

`vsize = weight / 4`

前面的程序还给出了 `wtxid`。为了确保包含见证数据的整个交易的完整性，我们计算承诺哈希。该承诺哈希是使用隔离见证——默克尔根派生的，后者是通过区块中所有交易的 `wtxid` 计算得出的。当矿工将承诺哈希添加到币基交易时，他们无法知道币基交易的 `wtxid`。这就是我们不计算币基交易的 `wtxid` 的原因。相反，我们给它一个由全零组成的 32 字节值。此外，我们还需要见证保留值，即第一个输入的第一个见证。

在以下程序中，我们计算承诺哈希：

```
def getWitnessReservedValue(cb_tx: dict):
    return cb_tx['inputs'][0]['witnesses'][0]['witness']

def getRootHashes(txn_m):
    txcount = getVarInt(txn_m)
    wtxid_l = []
    txid_l = []
    cb_tx = getCoinbaseTransactionInfo(txn_m)
    txid_l.append(cb_tx['txid'])
    wtxid_l.append(bytes(32).hex())
    for txindex in range(txcount - 1):
        tx = getTransactionInfo(txn_m)
        wtxid_l.append(tx['wtxid'])
        txid_l.append(tx['txid'])
    witness_merkle_root_h = buildMerkleRoot(wtxid_l)
    merkle_root_h = buildMerkleRoot(txid_l)
    return merkle_root_h, witness_merkle_root_h, cb_tx

def calculateCommitmentHash(blkhash_b: bytes, block_db):
    jsonobj = getBlockIndex(blkhash_b, block_db)
    if 'data_pos' in jsonobj:
        txn_filepath = os.path.join(blocks_path_g, 'blk%05d.dat' % jsonobj['n_file'])
        start = jsonobj['data_pos']
    elif 'undo_pos' in jsonobj:
        txn_filepath = os.path.join(blocks_path_g, 'rev%05d.dat' % jsonobj['n_file'])
        start = jsonobj['undo_pos']
    # load file to memory
    with open(txn_filepath, 'rb') as txn_file:
        #File is open read-only
        with mmap.mmap(txn_file.fileno(), 0, prot=mmap.PROT_READ, flags=mmap.MAP_PRIVATE) as txn_m:
            txn_m.seek(start)
            blkhdr = getBlockHeader(txn_m.read(80))
            merkle_root_h, witness_merkle_root_h, cb_tx = getRootHashes(txn_m)
            print('Calculated Witness Merkle Root Hash\t = %s' % witness_merkle_root_h)
            print('Calculated Merkle Root Hash\t = %s' % merkle_root_h)
            witness_reserved_value = getWitnessReservedValue(cb_tx)
            print('witness_reserved_value = ', witness_reserved_value)
            # calculate commitment hash
            commitment_hb = hashOfJoinedStr(witness_merkle_root_h, witness_reserved_value)
            commitment_h = commitment_hb.hex()
            print('calculated commitment hash = ', commitment_h)
            return commitment_h, cb_tx
```

**程序 12.3：** 计算承诺哈希

为了验证计算出的交易哈希是否正确，我们使用 scriptPubKey 以 `'6a24aa21a9ed'` 开头的输出索引：

```
def getCommitmentHashInCbTx(cb_tx: dict):
    for output in cb_tx['outs']:
        if output['scriptpubkey'][:12] == '6a24aa21a9ed':
            commitment_h = output['scriptpubkey'][12:]
            print('Actual commitment hash = ', commitment_h)
            return commitment_h

def verifyCommitmentHash(cb_tx: dict, commitment_h: str):
    if getCommitmentHashInCbTx(cb_tx) == commitment_h:
        print('Commitment hash matches')
    else:
        print('Invalid commitment hash')
```

**程序 12.4：** 验证承诺哈希

我们按如下方式调用前面的程序来计算承诺哈希并验证其正确性：

```
if __name__ == '__main__':
    blk_hb = bytes.fromhex('00000000000000000000f608724d1e152a875384e5ed06ae4a889c5a6c19c2f1')[::-1]
    commitment_h, cb_tx = calculateCommitmentHash(blk_hb, block_db_g)
    verifyCommitmentHash(cb_tx, commitment_h)
```

这给我们以下结果：

![](images/Figure-12.10.jpg)

**图 12.10：** 通过执行 Python 程序获得的承诺哈希

## 交易费计算

Bitcoin Core 根据每笔交易收取的交易费（位于内存池中）、内存池大小和内存池清理等因素，为我们提供费用估算。

以下 Bitcoin Core CLI 命令给出了费用估算：

![](images/Figure-12.11.jpg)

**图 12.11：** 获取推荐交易费率的 CLI 命令

这表明，要在接下来的六个区块内让交易被打包，我们需要支付每千 vbytes 0.00075062。这里的 vbytes 与我们在 Bitcoin Core CLI 输出中获得的 `vsize` 相同。

以下程序计算使交易获得确认所需的**预估最低费用**：

```
def calculateTransactionFee(vsize: int, feerate: float):
```

