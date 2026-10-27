
对于商用 Enigma，H = (AJPRDLZFMYSKQ) (BW) (CUGNXTE) (HOI) (V)，看起来像是随机选择的。但是，如果我们换回老式的记法，就能清楚地看到规律！

| | 输入 | 输出 |
| --- | --- | --- |
| H | ABCDEFGHIJKLMNOPQRSTUVWXYZ | JWULCMNOHPQZYXIRADKEGVBTSF |
| H⁻¹ | ABCDEFGHIJKLMNOPQRSTUVWXYZ | QWERTZUIOPASDFGHJKLYXCVBNM |

现在看起来更熟悉了吗？H⁻¹几乎与我们美式 QWERTY 键盘相符。事实上，它完全匹配 Enigma 键盘。当然，二战时期的密码分析员不需要查看不同的记法就能看出这一规律。波兰人拥有一台商用 Enigma，可以完全不使用任何记法就直接观察到，键位按顺序连接到转子系统输入端。我选择这样呈现，是为了说明记法需要适合具体情况，我们不能简单地说某种形式始终更优。

反射器（现称为 R）以及三个转子 N、M 和 L 的取值已在本章前面给出。当然，转子可以按任意顺序使用，所以我们不能简单地说 N = 转子 I，例如。波兰人起初并不了解这些置换。他们必须通过数学方法推导出来。因此，以上所有字母最初都代表未知量。

我们还需要一个置换来表示每次快转子前进一个位置时发生的改变。幸运的是，这个置换是已知的，给出为

P = (ABCDEFGHIJKLMNOPQRSTUVWXYZ).

为了加密一条消息，用户将机器设置为“日密钥”，例如 HLD，通过转动转子使这三个字母位于顶部。¹² 然后他选择另一个“会话密钥”（如果他遵守命令，则随机选择），例如 EBW。输入两次会话密钥可能会得到密文 GDOMEH。这将在消息开头发送。知道日密钥并已将 Enigma 设置为该密钥的预期接收者，输入 GDOMEH 后会得到 EBWEBW。现在回到加密者。输入两次会话密钥后，他将 Enigma 重置为会话密钥并输入消息。预期接收者在利用日密钥设置恢复会话密钥后，也将机器重置为会话密钥并输入剩余密文以恢复原始消息。显然，会话密钥不必输入两次。这种冗余是故意引入的，以确保会话密钥被正确接收。在这方面它起到了作用，但也证明是一个弱点。

一个例子将说明 Marian Rejewski 如何利用重复的会话密钥。¹³ 考虑以下使用各种会话密钥但在同一天发送的密文开头（因此前六个字母使用相同的日密钥）：¹⁴

| | | | | |
|---|---|---|---|---|
| AUQ AMN | IND JHU | PVJ FEG | SJM SPO | WTM RAO |
| BNH CHL | JWF MIC | QGA LYB | SJM SPO | WTM RAO |
| BCT CGJ | JWF MIC | QGA LYB | SJM SPO | WTM RAO |
| CIK BZT | KHB XJV | RJL WPX | SUG SMF | WKI RKK |
| DDB VDV | KHB XJV | RJL WPX | SUG SMF | XRS GNM |
| EJP IPS | LDR HDE | RJL WPX | TMN EBY | XRS GNM |
| FBR KLE | LDR HDE | RJL WPX | TMN EBY | XOI GUK |
| GPB ZSV | MAW UXP | RFC WQQ | TAA EXB | XYW GCP |
| HNO THD | MAW UXP | SYX SCW | USE NWH | YPC OSQ |
| HNO THD | NXD QTU | SYX SCW | VII PZK | YPC OSQ |
| HXV TTI | NXD QTU | SYX SCW | VII PZK | ZZY YRA |
| IKG JKF | NLU QFZ | SYX SCW | VQZ PVR | ZEF YOC |
| IKG JKF | OBU DLZ | SYX SCW | VQZ PVR | ZSJ YWG |

为了方便，我们令 A、B、C、D、E 和 F 表示产生这些消息的 Enigma 设置对所输入的第一、第二、第三、第四、第五和第六个字母施加的置换。

第一个加密的会话密钥是 AUQ AMN。现在查看第一个和第四个密文字母（它们由加密同一个明文字母得到），我们看到置换 A 和 D 都将会话密钥的第一个字母映射到密文字母 A。会话密钥的第一个字母是未知的，但我们可以用 α 表示它。我们有 A(α) = A 且 D(α) = A。因为 Enigma 是自逆的，所以我们也有 A(A) = α 且 D(A) = α。因此，如果我们形成置换的复合 AD（从左到右读——即先执行 A 再执行 D），我们看到这个新置换会将字母 A 映射到 A。

因此，置换 AD 以 (A) 开始。继续用第二个和第四个加密会话密钥 BNH CHL 和 CIK BZT 进行同样的论证，我们看到置换 AD 将 B 映射到 C，也将 C 映射到 B，因此现在我们有 AD = (A) (BC)...

检查更多会话密钥后，我们接下来得到更长的循环，(DVPFKXGZYO) 和 (EIJMUNQLHT)。最后，我们用 (RW) 和 (S) 结束该置换。把它们全部放在一起，按循环长度递减的顺序排列，我们有

```
AD = (DVPFKXGZYO) (EIJMUNQLHT) (BC) (RW) (A) (S)
```

对第二和第五个字母重复此方法，然后对第三和第六个字母再重复一次，我们得到另外两个置换。

```
BE = (BLFQVEOUM) (HJPSWIZRN) (AXT) (CGY) (D) (K)
CF = (ABVIKTJGFCQNY) (DUZREHLXWPSMO)
```

注意构成 AD 的循环长度为 10、10、2、2、1 和 1。对于 BE，循环长度为 9、9、3、3、1 和 1。而对于 CF，我们有 13 和 13。循环长度的确切结果取决于日密钥，但如果出现某一长度的循环，则同等长度的另一个循环也会出现。15 Rejewski 将循环长度的模式称为特征结构，或更简称为给定日的特征。

相比上述乘积，更有用的是知道 A、B、C、D、E 和 F，但我们无法轻易得到它们。事实上，我们需要通过分解更容易获得的乘积置换 AD、BE 和 CF 来确定 A、B、C、D、E 和 F。幸运的是，有一个很好的公式可以做到这一点。也就是说，知道乘积 AD 我们就能快速找到 A 和 D，BE 和 CF 也是如此。然而，与把整数分解为素数乘积不同，这里的分解不会是唯一的。这种分解的非唯一性给密码分析员带来了额外的工作！例如，如果 XY = (AB)(CD)，则分解为

```
X = (AD)(BC) and Y = (BD)(AC)
```

and

```
X = (AC)(BD) and Y = (BC)(AD).
```

对于更大的循环对，可能的分解更多。一般来说，16 如果 XY = (x1 x3 x5… x2n-1) (y2n… y6 y4 y2)，则我们可以将其分解为

```
X = (x1 y2)(x3 y4)(x5 y6)…(x2n-1 y2n) and Y = (y2 x3)(y4 x5)(y6 x7)…(y2n x1).
```

将循环 (x1 x3 x5… x2n-1) 表示为 (x3 x5… x2n-1 x1) 并遵循同一规则会得到不同的分解。因为长度为 n 的循环可以用 n 种不同方式表示，我们会得到 n 个不同的分解。我们可以独立分解长度相同的互不相交循环对，然后将所有这些结果拼凑起来得到“整体”分解。这将在下面进行。当 Rejewski 解释他的工作时，他通过写下以下内容跳过了以下大部分内容

> 我们假设凭借对换乘积定理，加上对加密者习惯的了解，我们分别知道置换 A 到 F。

希望与 Rejewski 的解释相比，以下页面在简洁性上的损失能以清晰度得到弥补。

我们从分解 AD = (DVPFKXGZYO) (EIJMUNQLHT) (BC) (RW) (A) (S) 开始，通过对每个等长循环对反复使用我们的分解规则，并以示例为指导。

AD 包含 1-循环 (A) 和 (S) ⇒

```
(AS) is part of A and (SA) is part of D.
```

AD 包含 2-循环 (BC) 和 (RW) ⇒

```
(BR)(CW) is part of A and (RC)(WB) is part of D
or
(BW)(CR) is part of A and (WC)(RB) is part of D.
```

AD 包含 10-循环 (DVPFKXGZYO) 和 (EIJMUNQLHT) ⇒

```
(DT)(VH)(PL)(FQ)(KN)(XU)(GM)(ZJ)(YI)(OE) is part of A and
(TV)(HP)(LF)(QK)(NX)(UG)(MZ)(JY)(IO)(ED) is part of D
or
(DE)(VT)(PH)(FL)(KQ)(XN)(GU)(ZM)(YJ)(OI) is part of A and
(EV)(TP)(HF)(LK)(QX)(NG)(UZ)(MY)(JO)(ID) is part of D.
```

15. 这是 Enigma 自逆的后果。因此置换 A、B、C、D、E 和 F 都必须是自逆的，因而由互不相交的 2-循环组成。由互不相交的 2-循环组成的置换的任意乘积，其循环结构中所有长度都成对出现。

16. 应当指出，本章中使用的该结果和其他抽象代数定理在密码分析需要它们之前就已存在。波兰人不需要发明或发现数学；他们只需要知道它并加以应用。
