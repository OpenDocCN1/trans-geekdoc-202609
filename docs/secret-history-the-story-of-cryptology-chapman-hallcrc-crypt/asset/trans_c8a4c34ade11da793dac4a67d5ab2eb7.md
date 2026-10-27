
其中 π ≈ 3.1415 且 e ≈ 2.71828。~ 读作“渐近趋近于”，其含义为

lim n→∞ n! / ( √(2πn) (n^n) (e^{-n}) ) = 1

因此，我们有一个简洁紧凑的公式，将阶乘的概念与数学中最重要的常数联系起来！

在古典密码学中，常常希望密钥可以被记忆，因为如果密钥被写下来，就容易被缴获。记住 A 对应 H、B 对应 Q、C 对应 R 等等全部 26 个字母会非常耗时。这就引出了关键词密码。13 例如，使用关键词 PRIVACY，我们有

A B C D E F G H I J K L M N O P Q R S T U V W X Y Z 明文
P R I V A C Y B D E F G H J K L M N O Q S T U W X Z 密文

未在关键词中使用的字母在写出密文字母表时按字母顺序跟在其后。因此，我们得到了一种优于凯撒移位的密码，但密文字母表中仍保留了一些顺序，使得密码仍然被削弱。此类密码还可通过将关键词置于字母表开头以外的位置而变得更加复杂。例如，我们可以使用双部分密钥（PRIVACY，H）进行加密：

A B C D E F G H I J K L M N O P Q R S T U V W X Y Z 明文
Q S T U W X Z P R I V A C Y B D E F G H J K L M N O 密文

此外，还可以使用长密钥短语来确定替换的顺序。如果某个字母重复出现，在写出密文字母表时只需在它再次出现时忽略它，14。密钥短语可以选为包含字母表中所有字母的短语。例如，

The quick brown fox jumps over a lazy dog.（33 个字母）

A B C D E F G H I J K L M N O P Q R S T U V W X Y Z 明文
T H E Q U I C K B R O W N F X J M P S V A L Z Y D G 密文

Richard Lederer 提供了几个使用全部 26 个字母的更短短语：15

- Pack my box with five dozen liquor jugs.（32 个字母）
- Jackdaws love my big sphinx of quartz.（31 个字母）
- How quickly daft jumping zebras vex.（30 个字母）
- Quick wafting zephyrs vex bold Jim.（29 个字母）
- Waltz, nymph, for quick jigs vex Bud.（28 个字母）
- Bawds jog, flick quartz, vex nymphs.（27 个字母）
- Mr. Jock, TV quiz Ph.D., bags few lynx.（26 个字母，最少）

13 Argentis 是第一个以这种方式使用关键词的人（1580 年代末）。参见 Kahn, David, The Codebreakers, second edition, Scribner, New York, 1996, p. 113.

14 发送给 Edgar Allan Poe 的一封加密信息因为发送者没有这样做而变得更难破解（稍后会详细介绍）。

15 Lederer, Richard, Crazy English, Pocket Books, New York, 1989, pp. 159–160.

为便于明文与密文之间的转换，已发明了一些装置。现在我们来看其中两种。

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_36_0.png)

图 1.5 Leon Battista Alberti 的密码盘。（Courtesy of the David Kahn Collection, National Cryptologic Museum, Fort Meade, Maryland.）

Leon Battista Alberti 的密码盘（图 1.5）如何用于加密和解密应该显而易见，无需解释。内层字母表位于一个单独的圆盘上，该圆盘可以相对于较大的圆盘旋转以形成其他替换。Alberti（1404–1472）于 1466 年或 1467 年发明了该圆盘。16

另一种装置是 St.-Cyr 滑尺（图 1.6）。17 这里同样，一个字母表（图中写了两次的那个）可以相对于另一个移动。该装置仅适用于使用如图所示的直线字母表并保持滑尺固定位置时执行凯撒类型移位。

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_36_1.png)

图 1.6 St.-Cyr 滑尺。

然而，即使使用完全混合的字母表，打破此类密码也是微不足道的事。MASCs 常常在小说中使用。故事的主角通常在其密码分析尝试中取得成功并解释他是如何做到的。18 其中最好的故事之一由 Edgar Allan Poe 撰写。他的密码学联系接下来将被审视。下一节将审视 Sherlock Holmes 与密码的遭遇，然后我们将以 Poe 或 Arthur Conan Doyle 的著名侦探所不知道的解决方案技术来结束对 MASCs 的论述。

16 Kahn, David, The Codebreakers, second edition, Scribner, New York, 1996, pp. 126–128.

17 该装置以法国国家军事学院命名。

18 有关小说中密码和密文的概述，请参阅 John F. Dooley 在 2005 年 10 月 Cryptologia 第 29 卷第 4 期发表的 Codes and Ciphers in Fiction: An Overview，页 290–328。该论文包含 132 条注释书目。如需更新列表，请访问 https://www.johnfdooley.com/ 并点击链接 “Crypto Fiction”。截至 2020 年 10 月 7 日，该列表包含 420 个示例。

多音密码是 Poe 在 *Graham's* 中解决的系统之一。在这些系统中，一个字符可能对应多个字母的加密。这使得密码分析员以及预期接收者解密变得更加困难。下面给出一个例子。

Ofoiioiiaso ortsiii sov eodisoioe afduios tfoi ft iftvi
si tri oistoiv oiniafetsorit ifeov rsri inotiiiiiv ridi iot,
irio rivvio covit atro tfetsoria aioriti iitri tf oiotovin
tri aetifei ioreitit sov usttoi oioittstifo dfti afdooitior
trso iteov tri dfit oftfeov softriedi ft oistoiv
oriofiforiti suitteii viireiitifo i ft tri iarfoisiti, iiti
trir uet otiiotiiv uiftfi rid io tri eovii eci iiv rfasueostr
tf rii dft rit ftoe ei.

乍一看，我们可以断定此密文并非通过一对一替换每个字母获得；例如，第二行倒数第二个词 inotiiiiiv 中有四个相同的字母连续出现，但在英语中却没有这样的词！尽管如此，Poe 破解了此密码。他确定密钥短语（拉丁语）为 *Suaviter in modo, fortiter in re*。因此，替换被确定如下。

```
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z plaintext
S U A V I T E R I N M O D O F O R T I T E R I N R E ciphertext
```

密文中的字母 i 可能代表 E、I、S 或 W。其他字母也提供多种可能性。故意与否，加密者通过拼写错误或错字使事情变得更加困难。此外，他并没有使用简单的词汇。Poe 将解决方案表述为

> 毫无意义的短语和无意义的词语组合，正如博学的词典编纂者所承认的那样，当隐藏在密码学密码之下时，会使好奇的探究者感到困惑，并比最深刻的哲学家的最深奥的格言更完全地阻碍渗透。经院学者的深奥讨论，如果只是以其母语的未加掩饰的词汇呈现给他。

在两份期刊中，Poe 都提出了一个他后来在短篇小说《金甲虫》（1843）中重复的主张。措辞有所不同。这里以故事中出现的形式陈述。

> 然而可以断然断言，人类智慧无法构思出人类智慧无法解决的密码。

这是 Poe 关于密码学的最著名引言。它是错误的，正如我们稍后会看到的那样；存在理论上不可破解的密码。

在《金甲虫》中，Poe 终于给了读者他们渴望的东西。他揭示了他的方法。这成为他最受欢迎的短篇小说。我认为人们倾向于比非小说更被动地阅读小说。也许这是愿意搁置怀疑的结果。在大多数对《金甲虫》的引用中，一个明显的密码分析错误没有被提及。故事的主人公 Legrand 在对信息进行密码分析时注意到密文中没有词分隔，但其中一个符号可能代表空格。该符号的频率会最大——大于 e。好吧，没什么大不了的，但当 Legrand 说，

> 现在，在英语中，出现频率最高的字母是 e。随后，顺序如下：a o i d h n r s t u y c f g l m w b k p q x z。E 如此显著地占优势，以至于任何长度的句子很少见不到它成为主导字符。

我们就有一个更严重的错误。你看出来了吗？如果没有，请在继续阅读前再看一次。

在一本精彩的计算机科学教材中。²¹ William Bennett 指出了 Poe 犯的错误。²² 他将这一节命名为“Gold Bug or Humbug?”并将上述频率表的来源称为“整个短篇小说中最根本的谜团”。字母 t 应该是第二频繁的。为什么 Poe 将其放在第十位？这不是印刷错误，因为 Legrand 的破译与错误的频率表一致。根据该表，将第二频繁的密文符号（代表 t）识别为 a 会导致死胡同。因此，Legrand 放弃了该表并使用了 the 是最常见词这一事实。

Bennett 对此谜团的解决方案是，该故事最初写成西班牙语密码，在出版商要求下改为英语时，频率表被保留未改。然而，在着手寻找故事的早期手稿以证实 Bennett 的猜想之前，对密码学文献的检索揭示了一个更好的解决方案。

尽管 Bennett 并不知道，几十年前他的著作出现之前，这个谜团就已被解开。Raymond T. Bond 以编辑的身份汇编了一系列涉及密码和密文的短篇小说，并为每篇撰写了导言。²³ 在对 Poe 故事的导言中，他描述了 Abraham Rees 的 Cyclopædia or, Universal Dictionary of Arts, Sciences, and Literature（1819）中一篇关于密码的文章。该文章由 William Blair 撰写，讨论了字母频率，但将辅音和元音分开处理。Blair 根据频率将辅音分为四组，并没有尝试在每组内对字母进行排名，而是按字母顺序排列每组：

```
d h n r s t   c f g l m w   b k p   q x z
```

在描述元音时，Blair 指出 e 是最频繁的，其次是 o、a 和 i，然后指出某些辅音，如 s 和 t，比 u 和 y 更频繁。相对较新的字母 v 和 j 未被包含在内！

阅读后，Poe 在上述顺序中将 u 和 y 放在 s 和 t 之后，然后将其他元音置于开头，不小心交换了 o 和 a 的顺序，得出

```
e a o i d h n r s t u y c f g l m w b k p q x z
```
