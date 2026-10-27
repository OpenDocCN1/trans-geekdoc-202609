

在它的下方，密钥 GAUSS 垂直写在左侧，提供五个密码字母表的首字母。这些密码字母表中的每一个都从其首字母开始，按照与初始混合字母表相同的顺序延续。现在进行加密时，五个字母表按顺序使用，视需要重复，直到消息结束。我们得到：

```
MATHEMATICS IS THE QUEEN OF THE SCIENCES plaintext
GAUSSGAUSSG AU SSG AUSSG AU SSG AUSSG AUS key
OHZQLOHZUIN VR DQX RJLLS FA DQX GTULSJSF ciphertext
```

这种密码被美国密码协会（ACA）成员（如 James J. Gillogly）称为 Quagmire III。Kryptos 的完整明文尚未被恢复，但 Gillogly 使用自己设计的计算机程序，在 1999 年破译了其中的大部分。有几个因素使他的工作更加困难：

- 1. 没有明显迹象表明左侧包含四个密码而不是只有一个。
- 2. 字母表的混合使用了关键字，但不是右侧线索中的 KRYPTOS。
- 3. Sanborn 故意在密码中引入了一些错误。
- 4. 只有前两个密码是 Quagmire III。密码 3 和 4 源自其他系统。

确定正确的密钥并恢复前两条消息的任务留给读者作为挑战。解决方案很容易在网上找到。你能运用本章详述的技术来迎接这一挑战吗？第二部分应该比第一部分容易，因为有更多密文可供使用。

第三个密码使用了换位（见第 3 章），也由 Gillogly 破解。只剩下三行多一点密文时，Gillogly 卡住了。他无法破解第四个也是最后一个密码。

在 Gillogly 取得成功后，中央情报局（CIA）透露，其一名员工 David Stein 早在 1998 年就已破译了 Gillogly 恢复的那些部分。Stein 的结果出现在一份机密出版物中，James 无缘看到。为了不被 CIA 超越，国家安全局（NSA）透露他们的一些员工在 1992 年已解决此问题，但起初 NSA 不愿提供他们的名字！2005 年，有信息公布说这实际上是 NSA 的一个团队（Ken Miller、Dennis McDaniels，以及另外两名身份至今仍未公开的人）。17 尽管备受关注，但 Kryptos 的最后一部分仍然无法破译，至少就公众所知是这样！“人们称我为撒旦的代理人，”艺术家 Sanborn 说，“因为我不愿透露我的秘密。”18

至少，Sanborn（图 2.14）透露了有价值的线索。2010 年 11 月 20 日，他表示未破译部分第 64 位开始的字母，即 NYPVTT，破译为 BERLIN。19 令人惊讶的是，这没有帮助！没有解决方案出现！整整四年后的 2014 年 11 月 20 日，Sanborn 发布了另一条线索。它是对先前线索的扩展。他说 NYPVTTMZFPK 破译为 BERLIN CLOCK。仍然没有解决方案出现，

17 http://cn.wikipedia.org/wiki/Kryptos.
18 Levy, Steven, “Mission Impossible: The Code Even the CIA Can’t Crack,” Wired, Vol. 17, No. 5, April 20, 2009.
19 Scryer, “Kryptos Clue,” The Cryptogram, Vol. 77, No. 1, January–February 2011, p. 11. Scryer 是 James J. Gillogly 使用的美国密码协会（ACA）笔名。

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_105_0.png)

**图 2.14**  James Sanborn（1945–）（[http://www.pbs.org/wgbh/nova/sciencenow/3411/images/ate-bio-03.jpg](http://www.pbs.org/wgbh/nova/sciencenow/3411/images/ate-bio-03.jpg)）

现在我们又遇到了一个小谜团——为什么两条线索都在 11 月 20 日发布？这个日期对 Sanborn 或 *Kryptos* 有某种特殊意义吗？2020 年，Sanborn 提供了第三条线索：第 26 到 34 位的字母破译为 NORTHEAST。这条线索打破了以往日期的规律，是在 1 月 29 日给出的。[^20]

尽管矩阵加密要到[第 6 章]才介绍，但我现在应该指出，一些研究人员认为，*Kryptos* 仍未破解的部分使用了某种矩阵加密形式。Greg Link、Dante Molle 和我研究了这种可能性，但无法提供任何一方面的确切证据。[^21] 矩阵可用于加密文本的方式有很多，我们只能利用 Sanborn 的线索排除一些较简单的方法。

## 2.5 自动密钥

现在我们已经考察了基本维吉尼亚密码的密码学、密码分析学以及历史用途，接下来让我们看看布莱斯·德·维吉尼亚（Blaise de Vigenère）对这个已存在的系统所做的真正贡献，正如我们回忆的那样，这个系统已经存在。

[^20] Schwartz, John, and Jonathan Corum, “This Sculpture Holds a Decades-Old Mystery. And Now, Another Clue,” *The New York Times*, January 29, 2020, available online at [https://www.nytimes.com/interactive/2020/01/29/climate/kryptos-sculpture-final-clue.html](https://www.nytimes.com/interactive/2020/01/29/climate/kryptos-sculpture-final-clue.html).

[^21] Our investigation appeared as Bauer, Craig, Gregory Link, and Dante Molle, “James Sanborn’s *Kryptos* and the Matrix Encryption Conjecture,” *Cryptologia*, Vol. 40, No. 6, 2016, pp. 541–552. The results were later summarized in a broader survey of *Kryptos* as part of chapter 9 (pp. 386–407) of Bauer, Craig P., *Unsolved! The History and Mystery of the World’s Greatest Ciphers from Ancient Egypt to Online Secret Societies*, Princeton University Press, Princeton, New Jersey, 2017.

回忆一下，维吉尼亚的自动密钥只使用给定的密钥（如下例中的 COMET）一次。在那一次使用之后，原始消息（或生成的密文）用作消息其余部分的密钥。

```
S E N D S U P P L I E S ...    message
C O M E T S E N D S U P ...    key
U S Z H L M T C O A Y H ...    ciphertext
```

使用密文作为“密钥”：

```
S E N D S U P P L I E S ...    message
C O M E T U S Z H L O H ...    key
U S Z H L O H O S T S Z ...    ciphertext
```

这个具体例子由克劳德·香农在其经典论文《保密系统的通信理论》中提出。22

由于每个字母的加密依赖于先前的消息或密文字母，我们在这里使用了一种链式结构。这一思想在矩阵加密被发现时再次得到应用，并且至今仍用于现代分组密码。本书第 14.6 节将更详细地讨论它，该节涵盖各种加密模式。使用密文作为密钥，虽然听起来复杂，却产生了一种容易被攻破的密码！

各种自动密钥方法的一个风险是，单个位置的错误可能会传播到密文的其余部分。观察我们之前的例子，如果第三个字符被错误地加密为 N 而不是 Z，会发生什么。下面重现一个无错误的加密以作比较。

```
S E N D S U P P L I E S ...    message
C O M E T U S N H L O H ...    key
U S N H L O H C S T S Z ...    ciphertext obtained
U S Z H L O H O S T S Z ...    ciphertext desired
```

继续下去我们会发现，在最初错误之后的每个第五个密文字符也是错误的。

本章介绍了维吉尼亚密码，然后攻破了它，我们接下来将对其进行修补，创建一个更强的系统。然而，应该指出，维吉尼亚密码在现实世界中并没有这么快被淘汰。它曾有过极为成功的运行。我们可能再也见不到一个能在被发现有效攻击之前幸存数百年的系统了。

## 2.6 滚动密钥密码及其密码分析

由于维吉尼亚密码的主要弱点在于密钥按固定间隔重复，使上述攻击成为可能，一个自然的改进是以类似方式加密，但使用不重复的密钥。一种方法是用一本书的文本作为密钥。这种方法通常称为滚动密钥（维吉尼亚）密码。下面给出一个例子。

```
BEGIN THE ATTACK AT DAWN    plaintext
IT WAS THE BEST OF TIMES I    key
JXCIF MOI BXKTQP TB PEOV    ciphertext
```

