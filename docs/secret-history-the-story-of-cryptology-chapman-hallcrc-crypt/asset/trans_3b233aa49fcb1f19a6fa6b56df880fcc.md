
令人沮丧时，我们可以重新开始并假设密钥长度为10。将密文字母分成十组并计算每组的IC值，可以显示这一假设是否更好或不。进行这些计算的较小的密文字母组，即使它们不完全是十个，也被称为 *抽样字母表*。

几个例子将表明卡西斯基检验和IC检验的可靠性如何。第一个在下面给出，其他的留作练习。*注意：* 有些书籍编造出此类检验完美生效的例子，造成这种方法总是如此的错误印象。

IC方程可以反过来求出密钥的长度（*L*），当密文中的字符数（*N*）和密文重合指数（*IC*）已知时：

$$L \approx \frac{0.028N}{(IC)(N-1)-0.038N+0.066}$$

虽然你不需要理解上述公式的推导过程就能使用它，但很容易证明。假设我们有一个由 *N* 个字母组成的密文，并且加密密钥的长度为 *L*。如果我们随机挑选两个字母，它们相同的概率是多少（作为 *密文*——它们所代表的明文字母不必匹配）？如果两个字母都用同一个字母表加密，那么这两个字母匹配的概率会高得多，因此我们考虑两种不同的情况并将其合并以得到最终答案。

## 案例 1：两个字母来自同一个密码字母表

哪个字母先选并不重要，但第二个字母必须来自同一个字母表，因此它必须是这种类型剩余的 (*N/L*) − 1 个字母之一（*L* 个字母表大致会将文本的 *N* 个字母分成大小为 *N/L* 的组，每个组加密方式不同）。因此，在总共剩余的 *N* − 1 个字母中，有 (*N/L*) − 1 个选择。所以概率是

$$\frac{\left(\frac{N}{L}\right)-1}{N-1}.$$

但我们也希望两个字母相同。因为我们已经在同一个字母表内，这个概率 simply 为 0.066，即一个字母表的 IC 值。我们将这两个值相乘得到

$$\frac{\left(\frac{N}{L}-1\right)(0.066)}{N-1}.$$

## 案例 2：两个字母来自不同的密码字母表

与案例1一样，哪个字母先选并不重要，但现在第二个字母必须来自不同的字母表。因为我们已经找到了第二个字母来自同一字母表的概率，所以我们可以取补集来得到它来自不同字母表的概率。我们有

$1-\left(\frac{\frac{N}{L}-1}{N-1}\right).$

现在我们有两个来自不同字母表的字母，需要乘以它们匹配的概率。这仅仅是随机文本（或等价地，大量字母表）的 IC 值，即 0.038。因此，我们案例2的概率为

$\left(1-\frac{\frac{N}{L}-1}{N-1}\right)(0.038).$

合并两种情况，我们有

$IC \approx \frac{\left(\frac{N}{L}-1\right)(0.066)}{N-1}+\left(1-\frac{\frac{N}{L}-1}{N-1}\right)(0.038).$

现在只需做代数运算求解 $L$（参见练习 23）即可得到结果。

$L \approx \frac{0.028N}{(IC)(N-1)-0.038N+0.066}$

使用这个方程，你不需要像上面给出的那样查表；然而，这个版本的方程仅适用于明文为英语的密码。对于其他语言，常数可能会有所不同。

卡西斯基检验和重合指数乍听起来可能很复杂，但它们非常容易使用。看看下面的例子，了解它们如何使维吉尼亚密码分析任务变得简单。

## 示例

```
IZPHY XLZZP SCULA TLNQV FEDEP QYOEB SMMOA AVTSZ VQATL LTZSZ
AKXHO OIZPS MBLLV PZCNE EDBTQ DLMFZ ZFTVZ LHLVP MBUMA VMMXG
FHFEP QFFVX OQTUR SRGDP IFMBU EIGMR AFVOE CBTQF VYOCM FTSCH
ROOAP GVGTS QYRCI MHQZA YHY XG LZPQB FYEOM ZFCKB LWB TQ UIHUY
LRDCD PHPVO QVVPA DBMWS ELOSM PDCMX OFBFT SDTNL VPTSG EANMP
MHKAE PIEFC WMHPO MDRVG OMPQ BTAEC CNUAJ TNOIR XODBN RAIAF
UPHTK TFIIG EOMHQ FPPAJ BAWSV ITSMI MMFYT SMFDS VHF WQ RQ
```

几个字符组重复出现。我们需要记录它们的位置以利用卡西斯基检验。

| 字符分组 | 起始位置 | 起始位置之间的差值 |
|---------------------|---------------------|----------------------------------------|
| IZP | 1 and 57 | 56 |
| HYX | 4 and 172 | 168 |
| EPQ | 24 and 104 | 80 |
| MBU | 91 and 123 | 32 |
| TSM | 327 and 335 | 8 |

考虑上表最后一列。所有值都是8的倍数。这表明密钥长度为8。密钥长度可能是4（或2），但如果是这样，很可能差值列中的一个数字是4（或2）的倍数但不是8的倍数。

计算重合指数需要更多工作。我们首先为密文字母构造一个频率表（表2.1）。

该示例的重合指数的分子然后由下式给出

## 表2.1 用于计算重合指数的频率表

| 字母 | 频率 | 字母 | 频率 |
|---|---|---|---|
| A | 18 | N | 7 |
| B | 14 | O | 18 |
| C | 12 | P | 22 |
| D | 12 | Q | 17 |
| E | 15 | R | 10 |
| F | 22 | S | 16 |
| G | 9 | T | 20 |
| H | 14 | U | 8 |
| I | 13 | V | 18 |
| J | 2 | W | 5 |
| K | 4 | X | 7 |
| L | 15 | Y | 9 |
| M | 26 | Z | 14 |

∑_{i=A}^{Z} F_i(F_i - 1) = (18)(17) + (14)(13) + (12)(11) + (12)(11) + (15)(14) + (22)(21) + (9)(8) + (14)(13) + (13)(12) + (2)(1) + (4)(3) + (15)(14) + (26)(25) + (7)(6) + (18)(17) + (22)(21) + (17)(16) + (10)(9) + (16)(15) + (20)(19) + (8)(7) + (18)(17) + (5)(4) + (7)(6) + (9)(8) + (14)(13) = 5178

重合指数为

IC = Σ_{i=A}^{Z} F_i(F_i − 1) / N(N − 1) = 5178 / (347)(346) ≈ 0.0431.

该值虽然与预期值不完全匹配，但表明使用了五或六个字母表。我们可以假设密钥长度为5，将密文字母分成本应使用同一字母表加密的组，并对每组进行IC计算。我们得到的值为0.046、0.050、0.041、0.038和0.046。这些值远低于0.066，因此它们不太可能真正来自同一字母表。我们假设密钥长度为5是错误的。基于密钥长度为6重复这些计算，得到的值为0.050、0.041、0.035、0.048、0.038和0.037。同样，似乎密钥不能是这个长度。

我们可以在IC建议的值进一步远离之前先尝试四个字母表然后七个字母表，但卡西斯基检验建议为八，所以让我们直接跳到这个值。将密文分成八个单独的组并计算每组的IC值，得到0.105、0.087、0.075、0.087、0.056、0.069、0.065和0.046。这些值是迄今为止最大的，因此我们有另一个检验支持卡西斯基检验的结果。IC计算支持卡西斯基检验结果的另一种方式在练习22中描述。

现在我们将密文重写为长度为8的块，以便同一列中的字符代表由同一字母表加密的字母。我们可以为每列构造一个频率表（表2.2）。必须这样做才能得到上面段落中给出的IC值，但我省略了工作过程，直到可以看出它会导向积极的结论。请花点时间查看表2.2及其 accompanying 文本，然后再返回此处。

对于每一列，代表E的字母有26种可能的选择。在第1列，E、A和T频率之和的最大值为21，当M代表E时得到。现在对于第2列，假设P代表E得到的和只有9。最大和为11，当Q代表E时得到。对于第3列，最大和也当Q代表E时得到。这次和为17。对于第4到第8列，这种技术表明E分别由S、V、X、E和P表示。我们看到，如果这些替换是正确的，E仅在第1、3、4和5列是最频繁的字符，而在第7列并列第一。鼓励你在练习14中研究确定每个字母表偏移量的其他技术。上述替换意味着关键字（每个字母表中代表A的字母按顺序串联起来）是IMMORTAL。由于这是一个真实的词，我们对解决方案更有信心。应用此关键字对密文进行模26减法得到：

```
IZPHY XLZZP SCULA TLNQV FEDEP QYOEB SMMOA AVTSZ VQATL LTZSZ
IMMOR TALIM MORTA LIMMO RTALI MMORT ALIMM ORTAL IMMOR TALIM
ANDTH ELORD GODSA IDBEH OLDTH EMANI SBECO NEASO NEOFU STOKN
AKXHO OIZPS MBLLV PZCNE EDBTQ DLMFZ ZFTVZ LHLVP MBUMA VMMXG
MORTA LIMMO RTALI MMORT ALIMM ORTAL IMMOR TALIM MORTA LIMMO
OWGOO DANDE VILAN DNOWL ESTHE PUTFO RTHHI SHAND ANDTA KEALS
FHFEP QFFVX OQTUR SRGDP IFMBU EIGMR AFVOE CBTQF VYOCM FTSCH
RTALI MMORT ALIMM ORTAL IMMOR TALIM MORTA LIMMO RTALI MMORT
OOFTH ETREE OFLIF EANDE ATAND LIVEF OREVE RTHER EFORE THELO
ROOAP GVGTS QYRCI MHQZA YHY XG LZPQB FYEOM ZFCKB LWB TQ UIHUY
ALIMM ORTAL IMMOR TALIM MORTA LIMMO RTALI MMORT ALIMM ORTAL
RDGOD SENTH IMF OR THFRO M THEG ARDEN OFEDE NTOTI LLTHE GROUN
LRDCD PHPVO QVVPA DBMWS ELOSM PDCMX OFBFT SDTNL VPTSG EANMP
```
