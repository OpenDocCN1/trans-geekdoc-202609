
常见的情况是拥有 20 个值。这是 *分段密码* 的一个例子，之所以如此称呼，是因为原始消息字母被替换为在换位步骤中会被拆分的配对。

## 5.3 ADFGX 的密码分析

法军得益于乔治·潘文（图 5.3）的拯救，他在近三个月里付出了巨大的努力，首先破解了使用 5×5 波利比乌斯方阵的 ADFGX，然后破解 ADFGVX，期间体重减轻了 33 磅（15 公斤），但最终获得了揭示下一次攻击将发生地点的解。¹⁴ 前美国外交官 J. Rives Childs 观察到，¹⁵

> 他对德国密码的精湛破解使他被称为“胜利的工匠”，如果不是潘文获知德国的意图——他们将在何处发动攻击，巴黎本可能陷落。

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_194_0.png)

图 5.3 法国密码分析员乔治·潘文。（摘自国家密码博物馆大卫·卡恩收藏。）

¹⁴ Kahn, David, *密码破译者*, 第二版, Scribner, 纽约, 1996, 第 347 页。
¹⁵ Childs, J. Rives, “我对 G.2 A.6 的回忆”，*Cryptologia*, 第 2 卷, 第 3 期, 1978 年 7 月, 第 201–214 页, 第 206 页 引自此处。

潘文的解法并不能读取所有 ADFGVX 密码，但确实破解了一些特殊情况。通用的解法只是在战争结束后才找到。我们下面考察一个特殊情况，但其中的一些评论可以更广泛地应用。如果以下段落过于抽象，请随意跳到示例。

要攻击 ADFGVX 密码，我们唯一需要担心的是如何解开换位部分。一旦完成，我们剩下的是一个非常容易破解的波利比乌斯密码。解开换位部分的第一个步骤是确定使用了多少列。我们假设截获的消息没有“短列”。也就是说，消息形成一个完美的矩形。这会使事情变得稍微容易一些。作为第一步，我们确定列数是偶数还是奇数。这可以通过比较两组频率来完成。为此，请考虑下面的通用示例。

将代表每个消息字母的密文字母对表示为 BE（B 代表“开头”，E 代表“结尾”），在换位之前，我们的矩形将根据列数是偶数还是奇数而采取两种形式之一。

```
Even # of Columns                         Odd # of Columns
B E B E B E ... B E                    B E B E B E ... B E B
B E B E B E ... B E                    E B E B E B ... E B E
B E B E B E ... B E                    B E B E B E ... B E B
B E B E B E ... B E                    E B E B E B ... E B E
:                                  :       : :
B E B E B E ... B E                    (form of last row depends on number of rows)
```

对于偶数情况，换位列后，每列仍将全部是 B 或全部是 E。对于奇数情况，换位列后，每列仍将交替出现 B 和 E。

除非在波利比乌斯方阵中字母的放置经过精心安排以避免这种情况，否则密文字母对中作为开头字符和结尾字符的单个字母 A、D、F、G、V 和 X 的频率会有所不同。这使得密码分析员能够利用上述模式确定列数是偶数还是奇数。其具体做法现说明如下。

给定一个包含 _n_ 个字符的消息，我们将其除以我们认为的列数上限 _c_。结果 _n/c_ 将是行数的下界。例如，假设 _n/c_ 为 18，那么密文中的前 18 个字母都来自同一列。它可能是一列全是 Bs、全是 Es，或一半一半。取奇数位置的字符并构建频率分布。这些字符 **必须** 全部是同一类型（全部是 Bs 或全部是 Es），无论列数是偶数还是奇数。现在取偶数位置的字符并构建频率分布。

同样，这些字符 **必须** 全部是同一类型，B 或 E。现在比较两个频率分布。如果它们看起来相似，那么该列中的所有字符都是同一类型，因此列数必须是偶数。如果它们看起来不相似，则必须使用了奇数列。

如果我们确定频率分布匹配，则列数是偶数。然后我们可以将密文填入代表每种可能列数的矩形中，2、4、6、…22、24、26、28、…（两端不太可能）。对于每种情况，我们可以计算每列的频率分布。对于正确的情况，分布应分为两个不同的组，每组包含相同数量的列。当已知列数为奇数时，采用类似的方法来确定列数（见练习 7）。

一旦列数已知，密文可以写在适当大小的矩形中。为了撤销换位，我们首先使用不同的频率分布将每列标记为 B 或 E（在奇数情况下，此标签仅表示该列开始的字符类型）。此时无法知道哪个是哪个，但这不是问题！我们只需将任意一列标记为 B，然后将具有相似频率分布的其他列标记为 Bs，最后将剩余列标记为 Es。

如果我们标记的第一列标记正确，一切都好。如果它实际上是 E 列也没关系，因为唯一的变化是按列和行而不是按行和列来索引波利比乌斯方阵中的条目。

然后我们可以将 B 列与 E 列配对，使得 resulting 密文字母的频率分布类似于疑似明文字段。一旦通过将 Bs 与 Es 连接重新创建字母，我们应该能够挑出一些高频明文字母，如 E 和 T。这将有助于我们正确排序配对的列，特别是如果我们有一个 crib 或可以找到常见单词如 THE 和 AND 的出现。当所有列都正确排序后，其余部分就很简单——只是一个没有词间距的单字母替换密码。下面的示例应使这种攻击更加清晰。

### 示例 1

我们将攻击一条使用原始版本 ADFGX 加密的消息，这样在解开换位后我们就不必担心各种数字的频率。我们假设消息为英文，并且 I 和 J 由同一对加密，因为 5×5 网格只能容纳 25 个明文字母。我们的密文是

```
AXDXD XDDDX DXXDD DXXDD DXXDG DXGXX XDFGA AGGAF FGGFA AAFFA
ADGGF GFFAD FAFAD FGGAF DFDXD XDFFX AXDXG FGFGX DXGXX DXFAD
XGFDA AFADF FFGGA DFGDF FADFA GAAFF GAAGG XFFDF GGDFG FDFFF
GAFDA FAF AF FGAGA FAF AF? GAF? DDDGX DFFF GXD? XDFXX DXX? 
FDXFX FGADD GGDDA AXXXX FFGXX FDXDD FXFGD DFFFD DXDDA DXDDD
GXAFD DXXXX DGGDF XXXXF XXDDD AGGDA FAAGF GGGFA GFGAG FFXAG
FFFGF FXXFX AFXDG DXXXD XXXXD XAADF FXDDF GXGDX XFXXX AGGXD
AFFAA FGFA X? XXXAD FDFDF DFDXD XFFXX XDXDA GDGFX XGDFA FGXFG
DDXXX XXGFX FFXFX A?G?X? A?X?G? XFD?D? AX?DD X?X?D X?G?A
GAAAA FGAGA AGAAA FDGAF DAGAA GGDFF FGGGG GGAGG AF GAA GFFFG
FG AFF DFAFA GGAGA FGAAD AGGGF GFGFG FFAGA GGAAF AAAGD GGXGF
GGAFF AGAFG AAAAF GDAAG D GFGF FGGXX DDXFD FXXXG GAXXX GGDDG
FFGXD XGDGX FFXGA AGAFG ADAGG FXFGG GAAGA FFGFD DAAAA DGAFF
AFGDA ADFGD FAAGG AFAAG FGGGG FFGDG
```

我们有 680 个字符，我们假设使用的列数不超过 30，因此每列至少有 22 个字符（680/30 = 22.67）。我们取前 22 个字符，AXDXD XDDDX DXXDD DXXDD DX，并找到奇数位置字符的频率分布：

- A = 1, D = 8, F = 0, G = 0, X = 2

和在偶数位置：

- A = 0, D = 4, F = 0, G = 0, X = 7

经验有助于我们判断这两个分布是相似还是不相似。X 频率的明显差异可能使我们倾向于后者，但 F 和 G 的频率相同，且 A 尽可能接近而不相同。五种字母中有三种如此接近，我们得出结论分布是相同的。
