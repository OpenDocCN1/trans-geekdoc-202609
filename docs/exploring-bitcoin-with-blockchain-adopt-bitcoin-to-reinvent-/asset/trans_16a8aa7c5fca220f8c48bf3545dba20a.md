
要创建确定性钱包，首先需要学习如何生成随机种子。该种子将帮助你生成私钥和公钥对。你选择的随机数决定了私钥抵抗暴力破解或基于知识攻击的安全程度。一个好的随机数是真正随机的，这意味着它不遵循攻击者可确定的模式。此外，最好是分布良好的，这意味着如果我们在有限域内持续生成，经过足够长的时间后，有限域分布非常均匀，没有大块的密集区域，也不是完全均匀的。因此，随机数需要同时防范暴力攻击和涉及推断模式的智能攻击。这需要选择正确的随机性来源，也称为**熵源**。这主要从硬件来源收集，如风扇噪音或鼠标移动。我们也可以使用背景噪音作为熵源。

我们将使用 BIP 39 实现一个生成随机种子的程序。

链接：[https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki](https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki)

该文档描述了生成种子的方法，种子由 12/18/24 个常用英语单词组成。这组单词不仅仅是纯随机序列；它还包含校验和，因此不能在不遵循 BIP 中描述的方法的情况下随机生成。

共有 2048 个助记词用于生成种子，相当于 11 位。完整的助记词列表可在以下链接找到：[https://github.com/bitcoin/bips/blob/master/bip-0039/english.txt](https://github.com/bitcoin/bips/blob/master/bip-0039/english.txt)。

如果我们准备 12 个单词的助记码，需要 11\*12 位，即 132 位。

132 位由 128 位随机数和 4 位校验和组成。

我们将随机数中的位称为熵位。下图展示了获取 12 个单词助记种子的过程：

![](images/Figure-9.1.jpg)

**图 9.1：** 从熵生成助记码的示意图

使用以下公式计算所需位数：

*熵位数 = 助记词数量 \* 32 / 3*

**checksum_bit_count** 的公式如下：

*校验和位数 = 助记词数量 / 3*

以下代码用于获取 **checksum_bit_count** 和 **entropy_bit_count**：

```python
def getChecksumBitCount(mnemonic_length: int):
    if (mnemonic_length % 3) != 0:
        raise ValueError('Invalid Mnemonic code length')
    checksum_bit_count = mnemonic_length // 3
    return checksum_bit_count

def getEntropyBitCount(mnemonic_length: int):
    if (mnemonic_length % 3) != 0:
        raise ValueError('Invalid Mnemonic code length')
    entropy_bit_count = (mnemonic_length * 32) // 3
    return entropy_bit_count
```

**程序 9.1：** 从助记种子长度获取校验和位数和熵位数的程序

以下代码用于生成熵位：

```python
def getRandomNumberBits(bit_count: int):
    r = random.SystemRandom().randrange(0, 1 << 32)
    r_b = r.to_bytes((r.bit_length() + 7) // 8, 'big')
    h = hashlib.sha256()
    h.update(r_b)
    h_b = h.digest()
    byte_count = bit_count // 8
    rand_num_b = h_b[0:byte_count]
    return rand_num_b
```

**程序 9.2：** 生成随机数的程序

之后，我们将校验和位追加到随机数位。以下是生成位的代码：

```python
def getMSBChecksumBits(checksum: int, checksum_bit_count: int):
    msb_checksum = checksum >> (256 - checksum_bit_count)
    return msb_checksum

def getEntropyWithChecksum(random_number: int,
                           msb_checksum: int,
                           checksum_bit_count: int):
    shifted_random_number = random_number << checksum_bit_count
    entropy_check_i = shifted_random_number | msb_checksum
    return entropy_check_i

def convertIntToBytes(num: int, bit_count: int):
    size_bytes = math.ceil(bit_count / 8)
    num_s = ('%x' % num).zfill(size_bytes * 2)
    num_b = bytes.fromhex(num_s)
    return num_b

def getChecksum(b: bytes):
    return int.from_bytes(hashlib.sha256(b).digest(), byteorder='big')

def getEntropyCheckBits(mnemonic_length: int):
    entropy_bit_count = getEntropyBitCount(mnemonic_length)
    random_number_b = getRandomNumberBits(entropy_bit_count)
    checksum_bit_count = getChecksumBitCount(mnemonic_length)
    checksum = getChecksum(random_number_b)
    msb_checksum = getMSBChecksumBits(checksum, checksum_bit_count)
    random_number = int.from_bytes(random_number_b, byteorder='big')
    entropy_check_i = getEntropyWithChecksum(random_number, msb_checksum, checksum_bit_count)
    bit_count = entropy_bit_count + checksum_bit_count
    entropy_check_b = convertIntToBytes(entropy_check_i, bit_count)
    return entropy_check_b
```

**程序 9.3：** 获取附加校验和的熵位的程序

之后，我们需要使用这些位从 2048 个助记词列表中选择单词。这通过将 **entropy_check_bits** 分解为 11 位列表来实现。以下是实现此功能的代码：

```python
def getMnemonicWordList():
    word_list = []
    with open('mnemonic_word_list_english.txt', 'rt') as word_file:
        word_list = word_file.read().splitlines()
    return word_list

def entropyCheckBits2List(entropy_check_b: bytes, size: int):
    selector_int = int.from_bytes(entropy_check_b, byteorder='big')
    selector_list = []
    while size >= 11:
        selector_list.append(selector_int & 0x07FF)
        selector_int = selector_int >> 11
        size -= 11
    return selector_list[::-1]

def getMnemonicWordCodeString(mnemonic_length: int):
    entropy_bit_count = getEntropyBitCount(mnemonic_length)
    checksum_bit_count = getChecksumBitCount(mnemonic_length)
    entropy_check_bit_count = entropy_bit_count + checksum_bit_count
    entropy_check_b = getEntropyCheckBits(mnemonic_length)
    selector_list = entropyCheckBits2List(entropy_check_b,
                                          entropy_check_bit_count)
    mnemonic_word_list = getMnemonicWordList()
    word_key_list = []
    for selector in selector_list:
        word = mnemonic_word_list[selector]
        word_key_list.append(word)
    return word_key_list
```

**程序 9.4：** 以列表形式生成助记词代码的程序

在本小节中，你学习了如何生成助记种子。你可以用它生成 12、18 或 24 个单词的助记种子。这里存在权衡：24 个单词的种子提供更高的安全性，但比 12 个或 18 个单词的代码更难记忆。在下一节中，我们将讨论比特币使用的私钥、公钥和地址格式。

## 私钥、公钥和地址的格式与生成

在本小节中，你将了解私钥和地址的格式，并学习如何生成它们。

### 私钥

私钥可以是几乎任何 256 位的值。其范围在 `0x1` 到 `0xFFFF FFFF FFFF FFFF FFFF FFFF FFFF FFFE BAAE DCE6 AF48 A03B BFD2 5E8C D036 4140` 之间。

私钥以**钱包导入格式 (WIF)** 表示。这是一种带有前缀和校验和的 Base58 格式。

Base58 方案定义在以下文档中：

[https://tools.ietf.org/id/draft-msporny-base58-01.html](https://tools.ietf.org/id/draft-msporny-base58-01.html)

公钥可以是压缩或未压缩的。压缩和未压缩公钥会导致不同的地址，因此私钥必须携带其生成的公钥是压缩还是未压缩的信息。要生成私钥的 WIF 格式，我们需要在 WIF 格式中包含币种、网络和压缩信息，以便生成的地址属于特定网络且是确定性的。

以下是前缀信息：

![](images/296.jpg)

**表 9.1：** 私钥前缀

如前表所示，regtest 使用与 testnet 相同的私钥前缀。
