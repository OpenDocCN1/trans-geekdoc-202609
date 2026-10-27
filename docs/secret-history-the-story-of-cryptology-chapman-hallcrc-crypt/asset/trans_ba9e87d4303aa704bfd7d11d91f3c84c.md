

MD5 … SHA-1 哈希也被用于分布式修订控制系统（如 Git、Mercurial 和 Monotone）中，以标识修订版本并检测数据损坏或篡改。该算法还曾被用于任天堂 Wii 游戏机启动时的签名验证，但一个重大的实现缺陷使攻击者能够绕过该安全机制。[^14]

很少有组织能够及时更新其安全措施。

自 2013 年以来，针对 SHA-1 的惊人攻击越来越多。虽然针对 SHA-2 的攻击远没有那么引人注目，但这两组算法之间的相似性足以引起密码学家的关注。因此，NIST 举办了一场竞赛，以寻找 SHA-2 的替代方案（而非接替方案）。这个替代方案被命名为 SHA-3。在经过一场有 64 个候选方案参加的漫长竞赛后，2012 年 10 月 2 日宣布的获胜者是 Keccak，这是一种由 Guido Bertoni、Joan Daemen、Michael Peeters 和 Gilles Van Assche 设计的哈希函数。[^15] 在他们题为“The Making of KECCAK”的论文摘要中，设计者写道：

它的结构和组成部分与其前辈截然不同，乍一看似乎是对过去的彻底决裂。在这篇文章中，研究人员表明，Keccak 是一个漫长学习过程的终点，这个过程涉及许多中间设计，大部分是逐渐的变化，但也有一些方向的剧烈改变。[^16]

Daemen 评论道：“就我个人而言，我认为我最重要的成果是 Keccak，而不是 Rijndael。事实上，它的设计包含了我自 1989 年开始从事密码学研究以来所进行的所有密码学研究中最好的元素。”[^17]

当数学家们努力解决安全问题的同时，世界各国政府正在飞速前进。比尔·克林顿是美国第一位使用数字签名的总统。这些数字签名最合适地应用于 1998 年 9 月与爱尔兰签订的一项电子商务条约，以及在 2000 年一项赋予数字签名与传统签名同等法律地位的法案。

你可能已经注意到，我没有提供上述任何算法的细节。这并不是因为这些细节不重要，而仅仅是因为这是密码学中少数几个我始终无法真正兴奋起来的领域之一。我认为对我来说部分问题在于，与密码系统不同，这里没有需要揭示的消息。人们通常只是在寻找碰撞。如果你感兴趣，本章末尾的参考文献和进一步阅读列表提供了几本专门讨论哈希函数主题的书籍，以及一些重要的论文。我们现在继续讨论哈希函数如何用于保护密码，这是我发现更有趣的主题。

## 17.3.2 哈希函数与密码

哈希函数的应用不仅仅在于实现更快的数字签名。密码绝不应以明文形式存储在计算机上，但需要有一种方法来判断输入的密码是否正确。这通常是通过在输入密码后对其进行哈希处理，然后与存储的值进行比较来实现的。由于对于良好的哈希函数而言，计算任何原像都应该是困难的，因此获得哈希值访问权限的人不应该能够确定密码。

在我这本书的第一版中，我写道：“以伪装形式存储密码这一重要想法似乎并不与某个人紧密相关。必定有人是第一个想到这个主意的人，但我一直没能查到是谁。”在引用了一段明显错误的维基百科关于这一创新的描述后，我写道：“任何能够提供确切首创者信息的人，欢迎与我联系！”我很快收到了 Steven Bellovin 的来信（见第 2.12 节）。他写道：

> 在访问剑桥时（我想是我 1994 年那次访问），有几个人告诉我，这个想法是 Roger Needham 发明的。我问他为什么从未公开宣称过这一点；他说这个想法是在鹰酒吧诞生的——当时是计算机实验室下班后的聚集地——而且他和在场的其他人当时都喝了不少印度淡色艾尔啤酒，以至于他不确定这个想法有多少是他的，又有多少是别人的……¹⁸

Ross Anderson 指出：“有一段时间，Roger Needham 和 Mike Guy 都互相认为是对方发明的。”¹⁹ 无论如何，Maurice Wilkes 是第一个（在 1968 年）发表该解决方案的人，并将全部功劳归于 Needham。²⁰ Needham 在酒吧的那个美好夜晚发生在 1967 年。²¹ 十年后，他以同样的方式继续他的研究。当时还是博士生的 Sape Mullender 回忆道：

> 我第一次见到 Roger 是在七十年代末，那天下午结束时，系里的一大群人，包括 Roger，去了鹰酒吧，就是 Bene't 街上的那家。在计算机实验室搬到城市边缘之前，那里几乎是每天讨论当天事件的地方。也正是这家酒吧，Crick 和 Watson 曾在那里思考 DNA，并提出了双螺旋结构。²²

又过了十年，Mullender 再次提及：

> 我在 1987/1988 年间在剑桥度过了一个学术休假，每天去鹰酒吧仍然是文化的重要组成部分。Roger 每周肯定会去好几次。在那段时间里，鹰酒吧经过翻修，失去了一些破旧的魅力，因此也会去更远的地方。The Bath 和 The Mill 成了常去的地方。我认为这些地方之所以如此具有启发性，是因为 (1) 学生们在那里很放松，这是产生灵感的必要条件；(2) 不同群体之间会有交流，这为一些问题的解决带来了新想法的机会。²³

18 Bellovin, Steven，给作者的电子邮件，2013 年 8 月 5 日。
19 Ross Anderson 给作者的电子邮件，2020 年 5 月 20 日。Anderson 在他即将出版的著作中同时归功于两人：Anderson, Ross, *Security Engineering*，第三版，Wiley，印第安纳波利斯，印第安纳州，见第 3 章，第 108 页，在线可访问 https://www.cl.cam.ac.uk/~rja14/book.html。
20 Wilkes, Maurice V., *Time-Sharing Computer Systems*, American Elsevier, New York, 1968, pp. 91–92。
21 Schofield, Jack, “Roger Needham,” *The Guardian*, 2003 年 3 月 10 日，在线可访问 https://www.theguardian.com/news/2003/mar/10/guardianobituaries.microsoft。
22 Sape Mullender 给作者的电子邮件，2020 年 5 月 20 日。
23 Sape Mullender 给作者的电子邮件，2020 年 5 月 20 日。

Cipher Deavours 或许并不知道 Needham 在这个故事中的角色，他写道：“这类函数的非保密工作可以追溯到 20 世纪 70 年代初。”[^24] 人们可以推测，政府在此之前就已经研究过这个问题。Deavours 继续引用了 Peter J. Downey 1977 年的一篇论文，该论文描述了一个 1972 年投入使用的系统。[^25] 该系统的第一步被含糊地描述为“对[密码]长度进行一些初步缩减”。但在那之后，下一步就非常清晰了。密码 *p* 被加密为

$$C = (2^{16})(p) \pmod{10^{19}-1}.$$

Downey 破解了这个系统，从加密值中恢复了密码。这只需要计算 $2^{16} \pmod{10^{19}-1}$ 的乘法逆元。真奇怪居然有人会认为这能保证安全！

以这种方式使用的哈希并不一定要减小被“哈希”数据的规模，但它们必须具有难以计算原像的性质。有时这类哈希被称为单向函数；然而，目前还没有数学证明单向函数是存在的！下面列出了一些 20 世纪 70 年代初关于密码保护的其他参考文献：

- Bartek, Douglas J., “Encryption for Data Security,” *Honeywell Computer Journal*, Vol. 8, No. 2, September 1974, pp. 86–89.
- Evans, Jr., Arthur, William Kantrowitz and Edwin Weiss, “A User Authentication Scheme not Requiring Secrecy in the Computer,” *Communications of the ACM*, Vol. 17, No. 8, August 1974, pp. 437–442.
- Purdy, George B., “A High Security Log-in Procedure,” *Communications of the ACM*, Vol. 17, No. 8, August 1974, pp. 442–445.
- Wilkes, Maurice V., *Time-Sharing Computer Systems*, American Elsevier, New York, 1972. 这是首次提出 Needham 想法的著作的第二版。

贝尔实验室的 Robert Morris 和 Ken Thompson 在 1979 年发表的一篇论文值得更详细地研究。[^26] 该论文讲述了 UNIX 分时系统上密码安全的历史。起初，密码是通过软件模拟美国在二战期间使用的一种密码机（即 M-209）来加密的（见[第 9.1 节](#)的末尾）。然而，事实证明，这台机器在这方面的表现并不比它在战争期间长期保守秘密的表现更好。

事实证明，M-209 程序是可用的，但使用给定的密钥，该程序产生的密文很容易被逆推。而要在给定明文输入和程序加密输出的情况下找到密钥，则要困难得多。因此，密码不是作为要加密的文本，而是作为密钥，使用该密钥对一个常量进行加密。加密后的结果被输入密码文件。[^27]

[^24]: Deavours, Cipher, “The Ithica Connection: Computer Cryptography in the Making, A Special Status Report,” *Cryptologia*, Vol. 1, No. 4, October 1977, pp. 312–316, 此处引用第 313 页。

[^25]: Downey, Peter J., *Multics Security Evaluation: Password and File Encryption Techniques*, ESD-TR-74-193, Vol. III, Electronic Systems Division, Hanscom Air Force Base, Massachusetts, June 1977.

[^26]: Morris, Robert and Ken Thompson, “Password Security: A Case History,” *Communications of the ACM*, Vol. 22, No. 11, November 1979, pp. 594–597.

[^27]: Morris, Robert and Ken Thompson, “Password Security: A Case History,” *Communications of the ACM*, Vol. 22, No. 11, November 1979, pp. 594–597, 引文取自在线版本 https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.128.1635。

