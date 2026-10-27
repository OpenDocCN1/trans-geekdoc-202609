
我们列出辅音字母，因为它们似乎是和元音字母组分开加密的：

BCDFGHJKLMNPQRSTVWXZ（20个辅音字母）

查看最长的三组同构体时，我们得到了一些有趣的观察。

1.  

```text
LNOLLIWQAVEMZIZS
PRYPPEBTUZI QDEDW
```

从顶行任一辅音字母到其正下方的字母，在我们辅音字母表中的距离都是3。这不太可能是巧合！

2.  

```text
VXOVVIHBAGEWIKD
LNOLLIWQAVEMZIZS
```

对于这一对，距离总是12。例如，我们从V开始，向前移动经过辅音W、X和Z，然后回到字母表开头继续前进，直到到达L。同样，这不太可能是巧合！

这种攻击方式应该会让你想起卡西斯基对维吉尼亚密码的攻击（但这里使用的是同构体，而不是相同的密文段），表明基本的辅音替换字母表只是进行了移位，以产生各种加密可能性。因此，我们的替换表应大致如下：

| 类型 | 序列 |
| --- | --- |
| 明文 | BCDFGHJKLMNPQRSTVWXZ |
| 密文字母表 1 | BCDFGHJKLMNPQRSTVWXZ |
| 密文字母表 2 | CDFGHJKLMNPQRSTVWXZB |
| 密文字母表 3 | DFGHJKLMNPQRSTVWXZBC |
| 密文字母表 4 | FGHJKLMNPQRSTVWXZBCD |
| 密文字母表 5 | GHJKLMNPQRSTVWXZBCDF |
| 密文字母表 6 | HJKLMNPQRSTVWXZBCDFG |
| 密文字母表 7 | JKLMNPQRSTVWXZBCDFGH |
| 密文字母表 8 | KLMNPQRSTVWXZBCDFGHJ |
| 密文字母表 9 | LMNPQRSTVWXZBCDFGHJK |
| 密文字母表 10 | MNPQRSTVWXZBCDFGHJKL |
| 密文字母表 11 | NPQRSTVWXZBCDFGHJKLM |
| 密文字母表 12 | PQRSTVWXZBCDFGHJKLMN |
| 密文字母表 13 | QRSTVWXZBCDFGHJKLMNP |
| 密文字母表 14 | RSTVWXZBCDFGHJKLMNPQ |
| 密文字母表 15 | STVWXZBCDFGHJKLMNPQR |
| 密文字母表 16 | TVWXZBCDFGHJKLMNPQRS |
| 密文字母表 17 | VWXZBCDFGHJKLMNPQRST |
| 密文字母表 18 | WXZBCDFGHJKLMNPQRSTV |
| 密文字母表 19 | XZBCDFGHJKLMNPQRSTVW |
| 密文字母表 20 | ZBCDFGHJKLMNPQRSTVWX |

然而，我们上面的结果并未指定要从标记为“密文字母表1”的字母表开始。我们可以从该表的任意位置开始。我们可以简单地尝试第一行的20种可能的起始位置，就像用暴力方法破解凯撒移位密码一样。我们删除每五个一组的附加空格以节省空间，并在每个文本字母处逐一推进我们的20个密文字母表。

### 起始密码

```text
EBJHEVAWRAUPVXOVVIHBAGEWKIKDYUCJEK BPOEKYGRYLU
1 -ZGD-P-NH--BGH-CB-KC-F-SF-CT--PT-SJV--M-GQ-H-
2 -XFC-N-MG--ZFG-BZ-JB-D-RD-BS--NS-RHT--L-FP-G-
3 -WDB-M-LF--XDF-ZX-HZ-C-QC-ZR--MR-QGS--K-DN-F-
4 -VCZ-L-KD--WCD-XW-GX-B-PB-XQ--LQ-PFR--J-CM-D-
5 -TBX-K-JC--VBC-WV-FW-Z-NZ-WP--KP-NDQ--H-BL-C-
6 -SZW-J-HB--TZB-VT-DV-X-MX-VN--JN-MCP--G-ZK-B-
7 -RXV-H-GZ--SXZ-TS-CT-W-LW-TM--HM-LBN--F-XJ-Z-
8 -QWT-G-FX--RWX-SR-BS-V-KV-SL--GL-KZM--D-WH-X-
9 -PVS-F-DW--QVW-RQ-ZR-T-JT-RK--FK-JXL--C-VG-W-
10 -NTR-D-CV--PTV-QP-XQ-S-HS-QJ--DJ-HWK--B-TF-V-
11 -MSQ-C-BT--NST-PN-WP-R-GR-PH--CH-GVJ--Z-SD-T-
12 -LRP-B-ZS--MRS-NM-VN-Q-FQ-NG--BG-FTH--X-RC-S-
13 -KQN-Z-XR--LQR-ML-TM-P-DP-MF--ZF-DSG--W-QB-R-
14 -JPM-X-WQ--KPQ-LK-SL-N-CN-LD--XD-CRF--V-PZ-Q-
15 -HNL-W-VP--JNP-KJ-RK-M-BM-KC--WC-BQD--T-NX-P-
16 -GMK-V-TN--HMN-JH-QJ-L-ZL-JB--VB-ZPC--S-MW-N-
17 -FLJ-T-SM--GLM-HG-PH-K-XK-HZ--TZ-XNB--R-LV-M-
18 -DKH-S-RL--FKL-GF-NG-J-WJ-GX--SX-WMZ--Q-KT-L-
19 -CJG-R-QK--DJK-FD-MF-H-VH-FW--RW-VLX--P-JS-K-
20 -BHF-Q-PJ--CHJ-DC-LD-G-TG-DV--QV-TKW--N-HR-J-
```

现在有一个小惊喜——我们不能简单地从任意一行中读出来，如果其中一行是只缺少元音的明文，我们通常可以这样读！仔细检查后发现没有错误。第10行一开始很有希望，但随后就中断了。仔细查看第10行及附近的行，会发现单词“INTRODUCTION”（“引言”）似乎从第10行开始，但中断后在第11行继续。

```text
7 -RXV-H-GZ--SXZ-TS-CT-W-LW-TM--HM-LBN--F-XJ-Z-
8 -QWT-G-FX--RWX-SR-BS-V-KV-SL--GL-KZM--D-WH-X-
9 -PVS-F-DW--QVW-RQ-ZR-T-JT-RK--FK-JXL--C-VG-W-
10 -NTR-D-CV--PTV-QP-XQ-S-HS-QJ--DJ-HWK--B-TF-V-
11 -MSQ-C-BT--NST-PN-WP-R-GR-PH--CH-GVJ--Z-SD-T-
12 -LRP-B-ZS--MRS-NM-VN-Q-FQ-NG--BG-FTH--X-RC-S-
13 -KQN-Z-XR--LQR-ML-TM-P-DP-MF--ZF-DSG--W-QB-R-
```

稍后在从第11行到第12行又发生了另一次移位。这些移位被称为“步进动作”。稍后将详细说明的红色密码的机械结构，使这一过程更加清晰。

现在填入元音和单词分隔就很容易了：

```text
INTRODUCTION STOP NEW PARAGRAPH EACH OF THE EXERCISE(S)...
```

单词“STOP”表明该消息是电报报文风格。我们甚至能够补全最后一个单词，它比所提供的密文多需要一个字母。现在可以回头看到，元音替换是使用混合顺序字母表AOEUYI进行的，并采用了各种移位，与辅音字母表类似。

将元音加密为元音、辅音加密为辅音显然是一个劣势。日本人这样做的动机显然纯粹是经济上的，因为电报服务对可发音文本的传输收费较低。

日语中表示“和”的词是“oyobi”，它具有不寻常的元音、元音、元音、辅音、元音模式；因此，在元音加密为元音、辅音加密为辅音的情况下，密码分析员可以很容易地在密文中定位这个单词，然后注意它揭示了加密过程的哪些信息。

英国人于1934年11月破解了红色密码，并于1935年8月制造了一台模拟它的机器。美国陆军密码分析员在1936年底破解了它，又花了两年时间制造了属于他们自己的模拟器。⁸ 美国人的关键洞察来自弗兰克·罗利特（Frank Rowlett），他与所罗门·库尔巴克（Solomon Kullback）合作。

在上面的示例中，我们使用了熟悉的26个字母的字母表。尽管实际的截获情报是日语的，但那些密文也是如此。由于日语的传统书写方式不适合电子传输，这些单词首先使用拉丁字母写出，⁹ 然后加密，最后发送。

要破解此类消息，人们无需知道机器实际上是如何完成加密的。事实上，用电机械方式实现红色密码加密不止一种可能方法。日本人使用两个半转子，由齿轮驱动。通常，转子单元每处理一个字母就前进一个位置，从而在字母表中推进，但有些插针可以被移除，导致转子单元在该点多前进一个位置。这就是我们在上面示例中观察到的步进动作的机制。可以移除两个相邻的插针，以造成前进三个位置。美国版的红色密码机用于恢复截获消息的明文，它使用两个转子完成此操作。¹⁰

上面分析的示例密文通过忽略红色密码的另一个组件——插线板——而被简化了。这相当于在我们的维吉尼亚表格中对明文和密文字母表都进行了单字母替换。插线板的连接每天更换。这个后来被称为“每日序列”的东西必须作为密码分析过程的一部分来恢复。与恩尼格玛密码机一样，这台机器及其使用方式在其服役期间也发生了多次更改。以上内容仅旨在传达大致概念。

## 8.3.1 橙色（Orange）

美国人使用代号“橙色（Orange）”来指代红色密码的一种变体，该变体被用作日本海军武官密码机。这台机器加密的是假名音节，而不是罗马字字母。美国人的首次破解出现在1936年2月。¹¹ 美国海军中尉杰克·S·霍尔特威克（Jack S. Holtwick, Jr.）制造了一台破解这一海军变体的机器。¹² 英国人也攻击了这个系统，而且更早取得了成果。休·福斯（Hugh Foss）和奥利弗·斯特雷奇（Oliver Strachey）于1934年11月为英国人破解了它。¹³ 该

⁸ Smith, Michael,《The Emperor's Codes: The Breaking of Japan's Secret Ciphers》（《天皇的密码：破解日本秘密密码》），Penguin Books，纽约，2002年，第46–47页。  
⁹ 日本人称之为“罗马字”（romaji）。至今仍在使用。  
¹⁰ Deavours, Cipher 和 Louis Kruh,《Machine Cryptography and Modern Cryptanalysis》（《机器密码学与现代密码分析》），Artech House, Inc.，马萨诸塞州戴德姆，1985年，美国红色密码机图片见第216–217页。  
¹¹ Smith, Michael,《The Emperor's Codes: The Breaking of Japan's Secret Ciphers》（《天皇的密码：破解日本秘密密码》），Penguin Books，纽约，2002年，第35页。  
¹² Kahn, David,《The Codebreakers》（《破译者》），第二版，Scribner，纽约，第20页和第437页。另见Deavours, Cipher 和 Louis Kruh,《Machine Cryptography and Modern Cryptanalysis》（《机器密码学与现代密码分析》），Artech House, Inc.，马萨诸塞州戴德姆，1985年，第11页。  
¹³ Smith, Michael,《The Emperor's Codes: The Breaking of Japan's Secret Ciphers》（《天皇的密码：破解日本秘密密码》），Penguin Books，纽约，2002年，第34–35页。

