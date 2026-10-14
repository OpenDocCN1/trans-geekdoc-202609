
我们遍历区块文件，使用从前面的方法获得的区块信息查找文件中的所有区块：

```python
if __name__ == '__main__':
    n_file = 138
    block_filepath = os.path.join(blocks_path_g, 'blk%05d.dat' % n_file)
    block_f = open(block_filepath, 'rb')
    blk_index = getBlockFileIndex(n_file, block_db_g)
    print(blk_index)
    for i in range(blk_index['count']):
        # moves file pointer to the end of block header
        serialized_blk = parseSerialisedBlock(block_f)
        next_blk_loc = block_f.tell() - 80 + serialized_blk['blk_size']
        block_f.seek(next_blk_loc)
        print('serialized_blk = %s' % serialized_blk)
```

以下是区块文件中前两个区块的信息：

![](images/Figure-6.22.jpg)

**图 6.22：** 显示区块文件中的前两个区块及该文件的其他信息

这种解析方法在为索引重新扫描区块时很有用。

# 使用区块索引进行区块遍历

LevelDB 索引在多方面都很有帮助。它们有助于更快地验证区块和交易。我们可以用它们来遍历区块链，这在需要解析固定数量的区块时（例如软分叉部署）非常有用。在其他情况下，使用区块文件编号和区块文件索引遍历区块链是一种更高效的方法。

下图显示了区块遍历的步骤：

![](images/Figure-6.23.jpg)

**图 6.23：** 使用 LevelDB 索引遍历区块文件的方法示意

我们需要记住一点：区块文件中的区块并不总是按顺序排列的，这意味着我们始终需要使用区块头中的前一个区块哈希来获取前一个区块的位置。

Chainstate 数据库是经过编码的，这与其他数据库不同。这是因为过去 chainstate 数据库中的字符序列曾触发杀毒软件。在这种编码方法中，每个字节都与 `obfuscate-key` 中的字节进行异或运算。`obfuscate key` 存储在 chainstate 数据库中，键为 `b'\x0e\x00'`。

以下代码将混淆键应用于所有字节并返回解码后的 chainstate 值：

```python
def getObfuscationKey(chainstate_db):
    value = chainstate_db.get(b'\x0e\x00' + b'obfuscate_key')
    print('obfuscation key = %s' % value)
    obfuscation_key = value[1:]
    return obfuscation_key

def applyObfuscationKey(data: bytes, chainstate_db):
    obfuscation_key = getObfuscationKey(chainstate_db)
    new_val = bytes(data[index] ^ obfuscation_key[index % len(obfuscation_key)] for index in range(len(data)))
    return new_val
```

**程序 6.9：** 使用混淆键解码 Chainstate LevelDB 的程序

现在，我们有足够的理解来遍历区块链。让我们看看如何做到这一点：

**步骤 1：** 从 chainstate 数据库查询最后一个区块哈希。

**步骤 2：** 在区块索引数据库中查询区块哈希以获取区块索引。

**步骤 3：** 区块索引包含区块位置的信息。利用该信息，我们读取正确的区块文件或撤销文件，并从偏移位置读取数据以获取区块数据。

**步骤 4：** 从区块数据中，我们获取前一个区块的区块哈希，然后重复步骤 2-4。

以下是从区块索引数据库获得的区块索引信息：

*   `version`：客户端的版本号（不是区块版本）。
*   `height`：区块高度。
*   `status`：指示其包含的数据类型。可能是 `BLOCK_HAVE_DATA` 或 `BLOCK_HAVE_UNDO`，指示它是正向修补还是反向修补 chainstate 数据。
*   `txcount`：区块中的交易数量。
*   `n_file`：包含该区块的区块文件编号。
*   `data_pos`：数据区块的字节位置。
*   `undo_pos`：撤销区块的字节位置。
*   `header`：区块头内容。

在上述信息中，我们遇到了通过撤销区块进行反向修补的情况。要理解这一点，我们需要知道比特币区块链中的区块可能会竞争下一个位置。这是因为矿工可能几乎在同一时间挖出一个区块，随后其中一个区块会被接受，因为竞争链中的一条会变得更长。当这种情况发生时，撤销区块被用来反向修补 chainstate 索引。

以下是使用 LevelDB 索引遍历区块链的代码：

1.  获取 LevelDB 数据库：

    ```python
    block_db_g = plyvel.DB(os.getenv('BLOCK_INDEX_DB'), compression=None)
    chainstate_db_g = plyvel.DB(os.getenv('CHAINSTATE_DB'), compression=None)
    ```

2.  从 chainstate 数据库获取最后一个区块哈希：

    ```python
    def getRecentBlockHash(chainstate_db):
        key = b'B'
        block_hash_b = chainstate_db.get(key)
        block_hash_b = applyObfuscationKey(block_hash_b, chainstate_db)
        return block_hash_b
    ```

    **程序 6.10：** 从 Chainstate DB 获取最近区块的程序

3.  从区块索引数据库获取区块索引：

    ```python
    BLOCK_HAVE_DATA = 8
    BLOCK_HAVE_UNDO = 16

    def getBlockIndex(block_hash_b: bytes, block_db):
        key = b'b' + block_hash_b
        value = block_db.get(key)
        jsonobj = {}
        jsonobj['version'], pos = b128_varint_decode(value)
        jsonobj['height'], pos = b128_varint_decode(value, pos)
        jsonobj['status'], pos = b128_varint_decode(value, pos)
        jsonobj['tx_count'], pos = b128_varint_decode(value, pos)
        if jsonobj['status'] & (BLOCK_HAVE_DATA | BLOCK_HAVE_UNDO):
            jsonobj['n_file'], pos = b128_varint_decode(value, pos)
        if jsonobj['status'] & BLOCK_HAVE_DATA:
            jsonobj['data_pos'], pos = b128_varint_decode(value, pos)
        if jsonobj['status'] & BLOCK_HAVE_UNDO:
            jsonobj['undo_pos'], pos = b128_varint_decode(value, pos)
        jsonobj['header'] = {}
        jsonobj['header']['version'] = value[pos:pos+4][::-1].hex()
        jsonobj['header']['prevblockhash'] = value[pos+4:pos+36][::-1].hex()
        jsonobj['header']['merkleroot'] = value[pos+36:pos+68][::-1].hex()
        jsonobj['header']['time'] = value[pos+68:pos+72][::-1].hex()
        jsonobj['header']['bits'] = value[pos+72:pos+76][::-1].hex()
        jsonobj['header']['nonce'] = value[pos+76:pos+80][::-1].hex()
        return jsonobj
    ```

    **程序 6.11：** 从 Block DB 获取区块索引结构的程序

4.  以下程序解析区块字节以获取区块头信息：

    ```python
    def getTransactionCount(mptr: mmap):
        prefix = int.from_bytes(mptr.read(1), byteorder='little')
        b_cnt_m = {'fd': 2, 'fe': 4, 'ff': 8}
        if prefix < 0xFD:
            tx_cnt = prefix
        else:
            b_cnt = b_cnt_m['%x' % prefix]
            tx_cnt = int.from_bytes(mptr.read(b_cnt), byteorder='little')
        return tx_cnt

    def parseBlockHeader(mptr: mmap, start: int, height: int):
        seek = start - 8
        mptr.seek(seek)
        block_header = {}
        block_header['magic_number'] = int.from_bytes(mptr.read(4), byteorder='little')
        block_header['block_size'] = int.from_bytes(mptr.read(4), byteorder='little')
        block_header['version'] = int.from_bytes(mptr.read(4), byteorder='little')
        prev_block_header_hash = mptr.read(32)
        block_header['prev_block_hash'] = prev_block_header_hash[::-1].hex()
        block_header['merkle_tree_root'] = mptr.read(32)[::-1].hex()
        block_header['timestamp'] = int.from_bytes(mptr.read(4), byteorder='little')
        block_header['date_time'] = datetime.datetime.fromtimestamp(block_header['timestamp']).strftime('%Y-%m-%d %H:%M:%S')
        block_header['bits'] = int.from_bytes(mptr.read(4), byteorder='little')
        block_header['nonce'] = int.from_bytes(mptr.read(4), byteorder='little')
        txcount = getTransactionCount(mptr)
        return block_header, prev_block_header_hash
    ```

    **程序 6.12：** 获取区块头信息的程序

以下程序使用区块索引信息获取区块内容，然后使用其区块哈希和区块索引查找前一个区块：

```python
def traverseBlockChain():
    df = pd.DataFrame()
    prev_blockhash_bigendian_b = getRecentBlockHash(chainstate_db_g)
```
