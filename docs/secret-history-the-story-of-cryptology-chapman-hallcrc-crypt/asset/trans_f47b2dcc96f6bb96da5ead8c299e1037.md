
如果有人能分解模数，RSA加密就很容易被破解，但RSA的安全性并不已知等价于分解问题。可能存在其他方式破解RSA而无需揭示\(n\)的因子分解。这是一个重要的开放问题。因此，与Diffie–Hellman密钥交换一样，其安全性即便不等价于、也基于攻击者无法解决某个数学问题（对RSA是分解问题，对Diffie–Hellman是离散对数问题）。其他公钥系统则建立在其他公认的困难问题之上。后续章节还会进一步讨论。有可能明天就有人找到这些问题中某一个（或全部）的快速解法，或者已经有人找到了而我们尚不知晓！

RSA算法有一个重要的实际缺陷——它很慢。我们将快速了解一种计算幂的好方法，但与其他加密算法中使用的极快运算（如XOR）相比，它仍然十分繁琐。因此，RSA通常仅用于加密某个对称系统（如DES）的密钥。然后，加密后的密钥随同用该密钥在对称系统中加密的消息一起发送。这将在[第18章](#)中详细讨论。由于RSA仅应用于相对较短（与大多数消息相比）的密钥，延迟是可以容忍的！

即使我们只用RSA加密极少量的文本，仍然希望尽可能高效地完成。下面演示的“重复平方”技术是执行幂运算的一种好方法。以\(385^{1563} \pmod{391}\)为例。显然这个模数太小了，但相同的方法同样适用于其他数值，而较小的数字能更清晰地说明问题。自然，我们不愿重复乘以385并在过程中取模多达1,563次。相反，我们计算以下各平方：

$$385^2 = 148,225 = 36 \pmod{391}$$

对上述等式两边平方并化简得：

$$(385^2)^2 = 36^2 = 1,296 = 123 \pmod{391}$$

因此，\(385^4 = 123 \pmod{391}\)。

我们再次对两边平方得到：

$$385^8 = 123^2 = 15,129 = 271 \pmod{391}$$

继续如前，我们得到：

$$385^{16} = 271^2 = 73,441 = 324 \pmod{391}$$

$$385^{32} = 324^2 = 104,976 = 188 \pmod{391}$$

$$385^{64} = 188^2 = 35,344 = 154 \pmod{391}$$

$$385^{128} = 154^2 = 23,716 = 256 \pmod{391}$$

$$385^{256} = 256^2 = 65,536 = 239 \pmod{391}$$

$$385^{512} = 239^2 = 57,121 = 35 \pmod{391}$$

$$385^{1024} = 35^2 = 1,225 = 52 \pmod{391}$$

我们可以在此停止。我们只需计算到不超过所需幂（本例中为1,563）且最接近它的2次幂即可。

现在，为了计算\(385^{1563}\)，我们注意到1,563 = 1024 + 512 + 16 + 8 + 2 + 1，因此可以写成：

\[385^{1563}=(385^{1024})(385^{512})(385^{16})(385^8)(385^2)(385)\pmod{391}\]

代入上面得到的值：

\[385^{1563}=(52)(35)(324)(271)(36)(385)=2,214,873,460,800=63\pmod{391}\]

因此，我们的答案是63。

## 14.4 政府对密码学研究的控制

马丁·加德纳（Martin Gardner），一位多产的数学普及者，在1977年8月号的《科学美国人》的“数学游戏”专栏中描述了RSA方案。Rivest、Shamir和Adleman的正式论文原本要到1977年深秋才会在《ACM通讯》上发表；然而，加德纳专栏的读者们不必等那么久就能获得完整细节。加德纳写道：“他们的工作得到了国家科学基金会和海军研究办公室的资助，发表于‘论数字签名与公钥密码系统’（技术备忘录82，1977年4月），由麻省理工学院计算机科学实验室发布，地址为马萨诸塞州剑桥市科技广场545号，邮编02139。任何向上述地址的Rivest写信并附上一个贴有35美分邮资、9×12英寸的封口信封的人，都可免费获得该备忘录。”¹⁹

Rivest迅速收到了4,000份论文索取请求，²⁰最终Shamir的办公室里堆积了7,000份请求。²¹论文终于在1977年12月寄出。与此同时，Gus Simmons和Mike Norris在1977年10月号的《密码学》杂志上发表了一篇论文，对该系统进行了改进。²²RSA团队为何花了这么长时间才寄出论文（并使其在期刊上发表），并不只是由于请求数量众多。

1977年8月在密码学政治史上还因电气与电子工程师协会（IEEE）信息论小组收到的一封信而留下印记。该信声称，与密码学相关的出版物可能违反1954年《军火管制法》、《武器出口管制法》和《国际武器贸易条例》（ITAR）。换言之，密码学研究受到与核武器工作相同方式的限制！事实上，这封信中明确写道：“原子武器和密码学也受特别保密法约束。”^23^

写信者的挑衅似乎针对IEEE原定于1977年10月10日在纽约州伊萨卡康奈尔大学会议上举办的密码学研讨会。Hellman、Rivest等人被安排为演讲者。该信被《科学》、《纽约时报》及其他媒体广泛报道，为会议带来了大量宣传。^24^

其基本主张是，此类出版物和讲座应首先获得国家安全局（NSA）的批准。如果能实现这种自愿审查，就不必涉及合宪性问题。全文见[图14.4]。^25^

最终，一位NSA发言人透露，该信是由NSA雇员约瑟夫·A·迈耶（Joseph A. Meyer）[图14.5]（非官方地）撰写的。^26^

这并非迈耶第一次激怒公民自由支持者。保罗·迪克森（Paul Dickson）的《电子战场》（1976年）概述了迈耶1971年1月发表在《IEEE航空航天与电子系统汇刊》上的文章“犯罪威慑应答器系统”。^27^

> > 这篇由国家安全局雇佣工程师约瑟夫·迈耶撰写的文章，建议一种系统，将微型电子追踪装置（应答器）附着在那些曾触犯法律的2000万美国人身上——事实上，佩戴其中一个装置将是假释的条件。应答器通过无线电连接到一台计算机，该计算机会监控佩戴者（或用迈耶的话说，“订阅者”）的位置，并在当事人即将违反其区域或宵禁限制时发出哔声警告。此外，这些小盒子将被以某种方式附着在人身上，使得计算机不注意到该行为就无法将其移除。在迈耶的设想中，取下或篡改你的应答器将构成重罪。作为一位优秀的工程师，迈耶还想到了这些便携装置的其他一些应用，包括监控外国人和政治少数群体。作家罗伯特·巴坎（Robert Barkan）率先通过文章将迈耶的提议及其他类似想法带给更广泛的读者，他在《卫报》上对应答器系统这样评论：“‘1984’仍是虚构，但不再是*科幻*。警察国家的技术已经就绪。剩下的只是政府付诸实施。”

马丁·加德纳专栏引发的大量RSA论文索取请求来自美国境外。鉴于迈耶的信，Rivest评论道：“如果我更多疑一些，我会觉得自己被人设计了。”^28^

¹⁹ Gardner, Martin, “Mathematical Games, A New Kind of Cipher that Would Take Millions of Years to Break,” *Scientific American*, Vol. 237, No. 2, August 1977, pp. 120–124.

²⁰ Deavours, Cipher, “A Special Status Report The Ithaca Connection: Computer Cryptography in the Making,” *Cryptologia*, Vol. 1, No. 4, October 1977, pp. 312–317, p. 312 cited here.

²¹ Levy, Steven, *Crypto: How the Code Rebels Beat the Government, Saving Privacy in the Digital Age*, Viking, New York, 2001, p. 114.

²² Simmons, Gustave J. and Michael J. Norris, “Preliminary Comments on the M.I.T. Public-Key Cryptosystem,” *Cryptologia*, Vol. 1, No. 4, October 1977, pp. 406–414. The improvement consisted of showing how poor choices for the key can allow message recovery without factoring. Over the years a number of special cases that need to be avoided have been recognized. These are detailed in Section 15.1.

^23^ Levy, Steven, *Crypto: How the Code Rebels Beat the Government, Saving Privacy in the Digital Age*, Viking, New York, 2001, p. 109.

^24^ Shapley, Deborah and Gina Bari Kolata, “Cryptology: Scientists Puzzle Over Threat to Open Research, Publication,” *Science*, Vol. 197, No. 4311, September 30, 1977, pp. 1345–1349; Browne, Malcolm W., “Harassment Alleged over Code Research,” *The New York Times*, October 19, 1977, available online at https://www.nytimes.com/1977/10/19/archives/harassment-alleged-over-code-research-computer-scientists-say-us.html.

^25^ My attempt to find the full letter led to John Young, who runs www.cryptome.org. He was able to obtain it from Martin Hellman and posted it on his website in January 2010.

^26^ Foerstel, Herbert N., *Secret Science: Federal Control of American Science and Technology*, Praeger, Westport, Connecticut, 1993, p. 114.

^27^ Dickson, Paul, *The Electronic Battlefield*, Indiana University Press, Bloomington, Indiana, 1976, p. 141.

^28^ Shapley, Deborah and Gina Bari Kolata, “Cryptology: Scientists Puzzle Over Threat to Open Research, Publication,” *Science*, Vol. 197, No. 4311, September 30, 1977, pp. 1345–1349.

