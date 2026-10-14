
```
def getUnspentTransactions(tx_hash: bytes, out_index: int, chainstate_db):
    key = b'C' + tx_hash + b128_varint_encode(out_index)
    value_obf_b = chainstate_db.get(key)
    value_obf_b = applyObfuscationKey(value_obf_b, chainstate_db)
    jsonobj = {}
    code, pos = b128_varint_decode(value_obf_b)
    jsonobj['is_coinbase'] = code & 0x01
    jsonobj['block_height'] = code >> 1
    compressed_amount, pos = b128_varint_decode(value_obf_b, pos)
    jsonobj['unspent_amount'] = amount_decompress(compressed_amount)
    jsonobj['script_type'], pos = b128_varint_decode(value_obf_b, pos)
    jsonobj['scriptPubKey'] = value_obf_b[pos:].hex()
    return jsonobj
```

**程序 6.20：** 获取 UTXO 结构的程序

前面的方法 `getUnspentTransactions` 接受交易哈希、未花费的输出索引和链状态数据库。以下是调用语句的示例：

```
if __name__ == '__main__':
    tx = bytes.fromhex('a23203c053852755c97b87e354d1e9053a6d1a20d32892e8ee45dfa2c3105f94')[::-1]
    jsonobj = getUnspentTransactions(tx, 0, chainstate_db_g)
    print(jsonobj)
```

结果如下：

![](img/Figure-6.34.jpg)

**图 6.34：** 显示链状态数据库中为 UTXO 存储的信息

在前面的结果中，`scriptPubKey` 并非完整脚本；它需要脚本类型来获取完整脚本。以下代码打印脚本类型 0 的完整 `scriptPubKey`：

```
def uncompressScriptType0(script_data: bytes):
    script = bytes([
        0x76,  # OP_DUP
        0xa9,  # OP_HASH160
        20     # size
    ]) + script_data + bytes([
        0x88,  # OP_EQUALVERIFY
        0xac   # OP_CHECKSIG
    ])
    return script
```

**程序 6.21：** 使用脚本类型和脚本数据获取 scriptPubKey 的程序

我们未涵盖其他脚本，因为交易脚本将留待后续章节介绍。

以下是调用前面方法的代码：

```
if __name__ == '__main__':
    script_data = bytes.fromhex('3eba92179cd0b4caff74e3e81a14399e3c1b7ca3')
    script = uncompressScriptType0(script_data)
    print('script = %s' % script.hex())
```

这将给我们以下脚本：

![](img/Figure-6.35.jpg)

**图 6.35：** 显示通过解压脚本数据获得的 scriptPubKey

这结束了关于交易的本节内容。在本节中，我们主要关注数据库中的交易格式和交易索引。脚本内容将留待后续章节介绍。

### 挖矿

挖矿是寻找 Nonce 并创建区块的过程。我们在前面的章节和节中学到了一些知识，这些知识将有助于理解挖矿过程。

挖矿涉及以下内容：

*   消耗能量以寻找 Nonce，这是创建数值低于目标阈值的区块哈希所必需的。
*   了解区块奖励。
*   从内存池中选择交易，以在区块大小限制内最大化交易奖励。
*   使用区块奖励、交易手续费、区块高度和用于将奖励支付给自己地址的 `scriptPubKey` 创建 Coinbase 交易。
*   寻找 Merkle 根。
*   寻找下一个区块的目标阈值。
*   准备并支持软分叉。
*   创建区块头中的其他字段。

在本节中，我们将调查上述每一项。

### 挖矿盈利能力

要计算挖矿盈利能力，我们需要了解使用流行挖矿设备寻找 Nonce 所需的能量，以及每笔交易中获得的区块奖励和总交易手续费是多少。

#### 区块奖励

区块奖励是创建比特币的机制。区块奖励随时间减少。比特币网络创建时，每个区块的区块奖励为 50 ![](img/Bitcoin.jpg)。目前为 6.25 ![](img/Bitcoin.jpg)。每 210,000 个区块，区块奖励减半。这减少了新铸造比特币的供应量。

以下程序给出指定区块高度的区块奖励：

```
def getBlockReward(block_height):
    halving_count = block_height // 210000
    block_reward = 50 / (2 ** halving_count)
    return block_reward
```

**程序 6.22：** 获取给定区块高度区块奖励的程序

我们为给定的区块高度调用此方法，如下所示：

```
if __name__ == '__main__':
    block_reward = getBlockReward(645675)
    print(block_reward)
```

这给我们以下结果：

![](img/Figure-6.36.jpg)

**图 6.36：** 显示通过运行前面程序获得的区块奖励

这意味着高度为 `645675` 的区块的区块奖励为 `6.25₿`。

#### 交易手续费

我们可以通过以下公式计算交易的手续费：

*f : 交易手续费*

*i[n]: 第 n 个输入*

*o[n]: 第 n 个输出*

*f = ∑[n]i[n] - ∑[n]o[n] (1)*

要编写计算交易手续费的程序，我们需要在 txindex 中查找上一笔交易。节点总是根据存储在链状态数据库中或内存池中的先前未花费交易输出来验证交易。区块中的所有交易都已经过验证。节点只需根据区块中包含的交易列表验证区块头和 Merkle 根哈希。由于我们试图查找已验证并确认的交易的先前交易输出，因此我们需要 txindex 来查找交易。

以下方法返回交易输出中锁定的比特币价值：

```
def getTransactionOutAmount(tx_hash: bytes, out_index: int, txindex_db):
    tx = findTransaction(tx_hash, txindex_db)
    return tx['outs'][out_index]['satoshis']
```

**程序 6.23：** 从 txindex 获取 UTXO 金额的程序

该方法调用 *程序 6.17* 中定义的 `findTransaction`。

以下方法使用前面方法中的交易输入锁定值，并返回与该交易关联的交易手续费：

```
def getTransactionFee(tx: dict):
    inp_val = 0
    for inp in tx['inputs']:
        prev_tx_hash = bytes.fromhex(inp['prev_tx_hash'])[::-1]
        inp_val += getTransactionOutAmount(prev_tx_hash, inp['prev_tx_out_index'], txindex_db_g)
    out_val = 0
    for out in tx['outs']:
        out_val += out['satoshis']
    tx_fee = inp_val - out_val
    return tx_fee
```

**程序 6.24：** 获取矿工从给定交易中收取的交易手续费的程序

现在，我们可以将区块中交易列表收集的所有交易手续费相加。以下是计算区块矿工收取的手续费奖励的程序：

```
def getBlockFeeReward(block_hash: bytes, block_db):
    block_index = getBlockIndex(block_hash, block_db)
    if 'data_pos' in block_index:
        block_filepath = os.path.join(blocks_path_g, 'blk%05d.dat' % block_index['n_file'])
        start = block_index['data_pos']
    elif 'undo_pos' in block_index:
        block_filepath = os.path.join(blocks_path_g, 'rev%05d.dat' % block_index['n_file'])
        start = block_index['undo_pos']
    with open(block_filepath, 'r+b') as block_f:
        blk_m = mmap.mmap(block_f.fileno(), 0)
        blk_m.seek(start + BLOCK_HEADER_SIZE)
        tx_cnt = getVarInt(blk_m)
        print(tx_cnt)
        coinbase_tx = getCoinbaseTransactionInfo(blk_m)
        print(coinbase_tx)
        fee_reward = 0
        for i in range(1, tx_cnt):
            print(i)
            start = blk_m.tell()
            tx = getTransactionInfo(blk_m)
            end = blk_m.tell()
            tx_fee = getTransactionFee(tx)
            print(tx_fee)
            fee_reward += tx_fee
    return fee_reward
```

**程序 6.25：** 用于计算矿工挖掘区块所收集交易费用的程序

在前面的代码中，`getCoinbaseTransactionInfo` 和 `getTransactionInfo` 分别定义在 *程序 6.14* 和 *程序 6.15* 中。

我们通过执行以下代码来调用该方法：

```
if __name__ == '__main__':
    block_hash_b = bytes.fromhex('000000000000000004ec466ce4732fe6f1ed1cddc2ed4b328fff5224276e3f6f')[::-1]
    total_tx_fee = getBlockFeeReward(block_hash_b, block_db_g)
    print('Fee Reward = %d' % total_tx_fee)
```

运行代码后，我们得到以下结果：

![](img/Figure-6.37.jpg)

**图 6.37：** 显示矿工挖掘给定区块所收集的交易费用

我们使用的区块哈希是高度为 `400000` 的区块，其挖矿奖励为 `2500000000` 聪。

##### Coinbase 交易金额验证

利用区块奖励和交易费用之和，我们可以验证矿工收集的比特币总额是否正确，以及他们是否没有多付给自己。Coinbase 交易输出的聪数之和告诉我们矿工付给自己的金额。以下是矿工付给自己的总奖励：

![](img/Figure-6.38.jpg)

**图 6.38：** 显示支付给矿工的 Coinbase 交易输出价值

我们可以看到，矿工付给自己 `2533349423 聪`，这等于我们计算出的区块奖励和费用奖励之和。

##### 挖矿成本

矿工通过不断尝试新值来寻找 Nonce，这需要大量的 CPU 处理，因此也消耗大量能源。挖矿设备还会产生大量噪音和热量，矿工需要对其进行管理。高能耗设备还需要足够的电力负载、消防安全和维护。此外，随着历史上对挖矿的兴趣增加和更好的挖矿设备生产出来，挖矿盈利能力已经下降。根据设备消耗的电费和挖出的比特币，旧设备有可能开始亏损，因此升级设备可能成为一种必要。

因此，任何进入挖矿领域的人都必须确保电费低廉，并且除了在维护和安全方面的支出外，还应将利润的很大一部分用于挖矿设备的升级和扩展。

要计算电费，我们需要了解寻找所需 Nonce 所需的网络算力。寻找 Nonce 所需的网络算力是寻找 Nonce 难度的结果，因此它取决于区块哈希低于目标阈值的概率。由于哈希生成随机的 256 位代码，因此有 $2^{256}$ 种可能的结果。

Nonce 小于 1 的可能值只有 0，所以找到它的概率是 $1/2^{256}$。

Nonce 小于 2 的可能值是 0 和 1，所以找到它们的概率是 $2/2^{256}$。

这给我们得出：

*p：找到 Nonce 的概率*

*T：目标阈值*

*p = T / 2^{256}* (1)

挖矿设备以极快的速度尝试寻找哈希值。

1 TH/s 的算率是每秒 $10^{12}$ 次哈希。以下计算得出比特币网络的算率：

*t[b]：出块时间（秒）*

*H[network]：网络算率*

由 *(1)* 式 $\Rightarrow$ *所需尝试次数 = H[network] \times t[b] = 2^{256} / T*

$\Rightarrow$ *H[network] = 2^{256} / (T \times t[b])*

使用前面的公式，我们可以找到当前的网络算率：

高度为 `645675` 的区块的目标阈值为

`T = 0x1007ea0000000000000000000000000000000000000000`

`H[network] = 2^{256} / (600 \times T) = 125,686,927,612,715,270,144`

正如我们所见，该值为每秒 125 亿亿次哈希 (exa-hashes per second)。这随时间呈指数级增长。下图显示了网络算率随时间上升的图表：

![](img/Figure-6.39.jpg)

**图 6.39：** 多年来比特币网络算率的变化

尽管网络算率呈指数级增长，但也有过短暂的算率下降时期。这发生在矿工开始亏损并被迫停止挖矿的时候。这是比特币挖矿与商品开采之间的一个关键区别。比特币的挖矿成本具有相当大的弹性，并根据挖矿盈利能力进行调整，而在常规开采中，利润下降不会导致开采成本下降。此外，商品矿工需要持续开采，因为关闭矿山并重新开采成本高昂，有时甚至很困难。因此，常规商品开采始终面临这样的风险：如果找不到更便宜的储备，则必须放弃开采或价格必须上涨。因此，价格上涨会导致供应增加。相比之下，在比特币中，通胀由算法固定，因此挖矿盈利能力和网络算率不会导致比特币产量发生变化。这使得比特币通胀免受禁令或限制等外部影响。

挖矿设备成本高达数千美元。算力最高的设备已超过 100 万亿次哈希每秒 (TH/s)。对于使用 100 TH/s 设备的矿工来说，要挖出一个区块，他们将需要：

![](img/c06eq-1.jpg)

正如我们所见，即使是 100 TH/s 也不足以单独挖出一个区块。出于这个原因，挖矿几乎从不单独进行。要将挖矿作为一项业务进行，矿工需要加入矿池。矿池通过集体尝试寻找 Nonce 来运作。每个参与者贡献他们的 CPU 算力给矿池以寻找 Nonce。矿池中谁成功找到 Nonce 并不重要。矿池使用该 Nonce 打包区块，然后根据参与者贡献的挖矿算力比例与所有参与者分享利润。这是一个非常民主的制度，但它使挖矿更加中心化。由于只有找到 Nonce 时才会分享利润，每个矿工都倾向于加入累积算力最高的矿池，因为这增加了找到 Nonce 的概率和更频繁地分享利润。因此，比特币网络上有一些大型矿池，如果它们联手主导共识规则，那么开发者和其他利益相关者可能会失去话语权，网络将被少数玩家接管。

在本书撰写时，以下是几个主要的矿池：

*   Foundry USA
*   AntPool
*   F2Pool
*   Poolin
*   Binance Pool
*   VIABLE
*   BTC.com
*   SlushPool

比特币挖矿使用 ASIC 矿机，专门设计用于以极快的速度执行 SHA256 运算。选择合适的矿机取决于多个因素，如投入成本、功耗、产生的热量和噪音量、效率、电力来源以及回本时间。

新矿机可能能效更高，但可能花费巨资，这会推迟回本时间。廉价或免费的电力来源可以使低效设备更具经济性。

此外，可以使用以下两种流行的矿池挖矿协议进行挖矿：

*   Stratum
*   Stratum V2

#### Stratum V2

顾名思义，Stratum V2 是 Stratum 协议的更新版本。这些是开放协议，广泛用于矿池挖矿。Stratum V2 的效率比版本 1 高两到三倍。版本 2 还赋予了单个矿工更好的控制权，体现在区块模板的定制化方面，这可以允许矿工单独决定他们打算支持或不支持的增强功能。

##### 常用矿池挖矿软件

*   Nice Hash
*   Better Hash
*   Cuddle Miner

上述每款软件都有优缺点，选择取决于个人需求。

##### 矿池签名
