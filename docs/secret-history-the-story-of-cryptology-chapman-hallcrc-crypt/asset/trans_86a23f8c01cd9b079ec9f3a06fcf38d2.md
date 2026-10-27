
有意义的消息。在这种差异中，我们期望相同的字母对约 6.6% 的时间对齐（以英语为例）。因此，差异中约有 6.6% 应为 A = 0。如果 C₁ 和 C₂ 并非源自同一一次性密码本密钥，则 C₁ − C₂ 的差值本质上是随机的，对于此类文本，A = 0 的期望概率仅约为 3.8%。但在苏联密码的情况下，底层代码使配对和破译过程变得更加困难。尽管有这一额外障碍，仍最终破译了超过 2,900 条消息的部分内容。³⁸ 1953 年底，经过多年的努力，人们发现一份于 1945 年 4 月发现的部分烧毁的代码本副本³⁹ 已用于 1942 年和 1943 年大部分时间的信息。⁴⁰ 然而，到那时，主要的突破已经以艰难的方式取得。⁴¹

从这些材料中获得的情报最初代号为 Jade，后来改为 Bride、Drug，最后为 Venona，这是历史学家今天所称的名称。许多破译结果直到 1960 年代和 1970 年代才被发现。⁴² 包含这些消息明文的解密文件于 1995 年 7 月开始发布。

因为所有的安全性都在于保持密钥保密，所以它必须易于隐藏，并且在特工被渗透时易于销毁；否则，我们就有了系统失效的另一种方式。

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_123_0.png)

图 2.21 一个一次性密码本，非常类似于冷战间谍所使用的那种。（版权 Dirk Rijmenants，2009；https://users.telenet.be/d.rijmenants/en/onetimepad.htm。）

如图 2.21 所示的一个一次性密码本，被在 1961 年于英国被捕的苏联间谍 Helen 和 Peter Kroger 持有。两人都是美国人，其真实姓名为 Morris 和 Lona Cohen。他们曾在美国从事间谍工作，但在 Julius Rosenberg 被捕后逃离了该国。被捕后，他们被判处 20 年监禁，但 8 年后被交换给苏联。一家苏联报纸称，“多亏了 Cohen，苏联原子弹的设计者直接从洛斯阿拉莫斯的秘密实验室获得了成堆的技术文件。”43

³⁸ Benson, Robert Louis 和 Michael Warner 编辑，《Venona: Soviet Espionage and the American Response, 1939-1957》，NSA/CIA，华盛顿特区，1996 年，第 viii 页。

³⁹ 它最初由芬兰部队发现，他们在 1941 年占领了芬兰的苏联领事馆。德国人随后从芬兰人手中获得了该书，最后在 1945 年 5 月，美国人在德国萨克森州的一处德国信号情报档案馆中发现了一份副本。参见 Haynes, John Earl 和 Harvey Klehr，《Venona: Decoding Soviet Espionage in America》，Yale University Press，康涅狄格州纽黑文，1999 年，第 33 页。

⁴⁰ Haynes, John Earl 和 Harvey Klehr，《Venona: Decoding Soviet Espionage in America》，Yale University Press，康涅狄格州纽黑文，1999 年，第 33 页。

⁴¹ Benson, Robert L.，《The Venona Story》，Center for Cryptologic History，National Security Agency，马里兰州 Fort George G. Meade，2001 年，可在线获取 https://www.nsa.gov/Portals/70/documents/about/cryptologic-heritage/historical-figures-publications/publications/coldwar/venona_story.pdf。

⁴² Benson, Robert Louis 和 Michael Warner 编辑，《Venona: Soviet Espionage and the American Response, 1939-1957》，NSA/CIA，华盛顿特区，1996 年，第 xxx 页。

我们最初的例子使用字母作为密钥，但上面描绘的密码本使用的是数字。假设我们使用随机数生成器得到一个值串，每个值介于 0 和 9 之间。然后我们一次一个地用数字偏移消息的每个字母。以下是一个例子：

```
IS THIS SECURE?      message
74 9201 658937        key
PW CUIT YJKDUL        ciphertext
```

消息提出的问题的答案是否定的！如果每个字母只有十种可能的偏移量，那么每个密文字符只有十种可能的破译。例如，初始密文字母 P 不可能代表明文 A，因为这需要密钥的第一个数字为 15。

为了安全地实现数值一次性密码本，消息必须首先转换为数字。使用俄罗斯间谍所做的那种数值代码是可以的，就像先应用 Polybius 密码一样，比如 Ché Guevara。

即使该领域随着机器加密不断进步，这类密码在冷战期间仍在间谍中流行。有很多原因。其中主要的是它们可以用铅笔和纸创建；间谍不必携带密码机，这往往会招致怀疑！

## 2.9 伪造随机性

随机性对一次性密码本至关重要，但生成随机性相当困难，因此除了生成所需大量密钥的困难外，我们还有生成其中任何一部分的困难！太阳辐射和其他自然现象已被用于生成密钥，另外还有人工来源；然而，人工来源不能真正随机。我们称它们为伪随机数生成器。如果我们使用其中一种，通常更方便，我们就有了所谓的流密码。这些系统在第 19 章中讨论。

如前所述，这里介绍的一次性密码本的实现方式并不是 Vernam 的实现方式。他的故事始于 1917 年，当时他设计了一台利用磁带进行加密的机器。他机械解决方案的后一个版本如图 2.22 所示。

Vernam 的实现用于通过有线或无线电报发送的消息，因此它不作用于我们的 26 个字母表或数字，而是涉及将消息字符逐个打孔到长纸带上。这使用现有的五单元印刷电报码完成（图 2.23），其中每个符号由打孔在纸上的孔的排列表示。

每个符号最多有五个孔，可以表示 2^5 = 32 个不同的字符。其中只有 26 个可能性用于字母。剩下的六个表示空格、回车、换行、图形转换、字母转换和空白或空闲信号。

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_125_0.png)

图 2.22 密码印刷电报机。（摘自 Vernam, Gilbert S.，“Cipher printing telegraph systems: For secret wire and radio telegraphic communications”，《Journal of the American Institute of Electrical Engineers》，第 45 卷，第 2 期，1926 年 2 月，第 109-115 页，第 109 页，此处引用。）

密钥带看起来像消息带，只是所代表的字符序列是随机的。Vernam 建议提前通过“随机操作键盘”生成。机器通过将每对消息和密钥字符组合来产生密文字符。这使用类似于 Vigenère 表的方法，但使用 32 个移位字母表，而不是 26 个。在接收端，密文带与密钥带的副本组合以恢复原始消息，然后自动以字母形式打印出来。

Vernam  intended  磁带以环形使用，但这种重复使其等同于 Vigenère 密码。一位工程师 Lyman F. Morehouse 提出了使用两卷磁带的想法，其中一卷比另一卷长一个字符。由每卷磁带字符对组合产生的字符将用作密钥。虽然他知道这样的序列不能真正随机，但他获得的密钥段比单独使用每卷磁带时要长得多（两卷长度的乘积），而不是两卷长度之和。44

Mauborgne 的贡献是在 1918 年，随着 Vernam 密码的演变，他认识到如果密钥是随机的且永不重复，系统将完全不可破译。多年后，Vernam 在一篇论文中通过描述手动实现这种不可破译密码的不切实际性来推广他的设备：45

如果手动执行，该方法缓慢、费力且容易出错。如果出现错误，例如遗漏一个或多个字母，接收者就难以破译消息。准备、复制和保护长随机密钥也会涉及某些困难。该系统的困难足以使其不适合一般使用，除非使用机械方法。

44 他还建议两个长度可以相差其他数量，只要该数量不是任一磁带长度的因子。如果这听起来不太对，你做得很好！如果我们想要获得较长的周期，有一种更好的方法来限制两卷磁带的长度。

45 Vernam, Gilbert S.，“Cipher Printing Telegraph Systems: For Secret Wire and Radio Telegraphic Communications”，《Journal of the American Institute of Electrical Engineers》，第 45 卷，第 2 期，1926 年 2 月，第 109–115 页，第 113 页，此处引用。
