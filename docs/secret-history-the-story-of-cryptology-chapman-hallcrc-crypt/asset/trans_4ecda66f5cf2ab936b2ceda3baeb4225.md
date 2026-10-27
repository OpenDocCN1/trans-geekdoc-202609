
![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_326_0.png)

## 图 9.11 整个加密过程。

警告称该设备“应以每分钟 45 至 50 个词的最大速度操作……如果超过此速度，字符可能无法打印。”18

对于这个时代的许多密码机，预期的接收者必须弄清楚在哪里插入词间空格才能使恢复的消息可读。与此类机器不同，SIGABA 的实现方式是在传递消息的同时传递间距。因为每个密码转子只有 26 根导线，似乎这是不可能的，但第 27 个符号其实并不需要。保留空格的方法如下：

- 在加密之前，SIGABA 将每个 Z 转换为 X。真正的 X 保持不变。基本上，Z 和 X 合并为一个用 X 表示的字符。
- 空格被转换为（现在可用的！）Z。

18 Mucklow, Timothy J., SIGABA/ECM II: A Beautiful Idea, Center for Cryptologic History, National Security Agency, Fort George G. Meade, Maryland, 2015, p. 33.

## 示例¹⁹

ZERO ONE TWO THREE FOUR FIVE SIX

被 SIGABA 转换为

```
XEROZONEZTWOZTHREEZFOURZFIVEZSIX
```

使用特定密钥，其加密为

```
IEQDEMOKGJEYGOKWBXAIPKRHWARZODWG
```

然后解密为

```
XERO ONE TWO THREE FOUR FIVE SIX
```

解密者需要自行识别第一个 X 应被视为 Z，而最后一个 X 是 X。因为 Z 是英语字母表中出现最少的字母，所以需要改为 Z 的 X 不会很多。无论如何，上下文应能让它们很容易被识别。

## 9.4 SIGABA 生产

虽然发现女性比男性更高效地生产 SIGABA 转子，但机器的生产涉及男女双方。图 9.12 显示了一些正在工作的男性，以及一名女性（最左边）。

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_327_0.png)

图 9.12 SIGABA 工厂的一部分。（由国家密码学博物馆提供，马里兰州 Fort Meade。）

> 19 引自 Stamp, Mark 和 Wing On Chan，“SIGABA: Cryptanalysis of the Full Keyspace”，Cryptologia，第 31 卷，第 3 期，2007 年 7 月，第 201–222 页。

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_328_0.png)

图 9.13 SIGABA。（来自 CryptoMuseum，cryptomuseum.com，许可号 CM500576。）

一台完工的机器，重约 100 磅，显示在图 9.13 中。

SIGABA 并非简单地 24-7 放在办公桌上。它们必须安全存放。由于安全柜（即保险箱）重达 800 磅，被保护的机器必须通过“战术通信车辆”运输。作为进一步的预防措施，热剂紧急销毁装置通常会随行。这些装置可在仅 97 秒内将 SIGABA 的绝密部件还原为熔融金属。由于可能引发比预期更大的火灾，这种保护在船上被放弃了。²⁰

密码学的历史跨越数千年，因此在一卷书中涵盖它意味着许多故事无法像我所希望的那样详细讲述。就 SIGABA 而言，更仔细的观察显示，在 Rowlett 的伟大初始洞见与帮助赢得第二次世界大战的机器之间存在许多版本。一系列原型机从 1936 年底制造到 1941 年 1 月，逐渐变得更小、更轻、更快，并且更不易因热量、湿度、振动而失效。²¹

## 9.5 密钥空间与现代密码分析

关于任何密码，一个重要问题是“密钥空间是什么？”与 Enigma 一样，针对 SIGABA 也可以提出几种答案来回应这个问题。

²⁰ 参见 Mucklow, Timothy J., SIGABA/ECM II: A Beautiful Idea, Center for Cryptologic History, National Security Agency, Fort George G. Meade, Maryland, 2015, p. 39, 其中引用了 Safford, Captain Laurance, History of Invention and Development of the Mark II ECM, SRH-360, United States Navy OP-20-S-5, Office of the Chief of Naval Operations, Washington, DC, October 30, 1943, p. 61。 该历史可查阅 NARA（国家档案和记录管理局）RG 457, Box 1124, College Park, Maryland。 注：SRH 代表 Special Research Histories。

²¹ Mucklow, Timothy J., SIGABA/ECM II: A Beautiful Idea, Center for Cryptologic History, National Security Agency, Fort George G. Meade, Maryland, 2015, p. 16。

如果敌人不知道 SIGABA 转子的任何内部接线方式，则每个 10 个大型转子有 26! 种选择，每个较小的索引转子有 10! 种选择。因此，似乎总共有约 (26!)^10(10!)^5 ≈ 7.2 × 10^298 种可能性。对于现代加密算法，密钥大小通常以位为单位表示。因为 7.2 × 10^298 ≈ 2^992.8，我们看到密钥空间约为 993 位。我写“约”是因为很容易挑剔这个数字，指出系统不太可能使用两个具有完全相同接线的转子或接线为恒等式的转子（尽管军事 Enigma 的插线板到转子组件的内部接线是恒等式！）。更严重的挑剔在于索引转子是静止的。因此，5 个转子的集合等同于某种不同接线的单个转子。因此，应将上述计算中的因子 (10!)^5 替换为 10!。^22 这将密钥空间减少到 ≈ 4.13 × 10^272 ≈ 2^905.6

如果敌人能够通过间谍、双重间谍、勒索、秘密潜入等手段了解 SIGABA 所有转子的接线方式，那么需要考虑的可能密钥就少得多，但数量仍然巨大。为计算它，我们首先注意到 10 个大型转子可以以 10! 种不同顺序放置在机器中。然而，每个转子都可以正放或倒放放置在给定位置！这些方向被称为“正向”或“反向”。因此，我们还有一个 2^10 的因子。一旦每个转子以某种方向放置在机器中，有 26 种选择来决定其旋转的起始位置。当考虑全部 10 个大型转子时，这给出另一个 26^10 的因子。因此，大型转子可以以 (10!)(2^10)(26^10) 种方式设置。同样，5 个小型索引转子可以以 5! 种方式排序，以正常或反向位置插入^23（一个 2^5 的因子）并各自设置为 10 个初始位置中的任意一个（一个 10^5 的因子）。总计为 (10!)(2^10)(26^10)(5!)(2^5)(10^5) ≈ 2.0 × 10^32。这大约是 2^107.3，所以如果已知所有转子的接线，SIGABA 可以说具有约 107 位的密钥。

上述计算显示了在仅受可用转子接线限制的情况下的潜在密钥数量。然而，实际使用机器的程序也施加了其他限制。例如，SIGABA 手册指示将控制转子的设置以明文（！）形式作为消息指示符发送，并随加密消息一起发送。这显然减少了知道消息指示符含义的敌人所面对的密钥空间。另一方面，罗斯福与丘吉尔之间的通信并非以这种方式进行。对于所有用户，索引转子输出的捆绑效应使得索引转子的不同排序可能产生相同的结果，从而降低了有效密钥空间。^24

Mark Stamp 和 Wing On Chan 计算出罗斯福和丘吉尔可用的密钥空间约为 2^95.6，而按照手册关于消息指示符的做法所达到的约为 2^48.4。他们指出，虽然在他们撰写时（2007 年）这个较小的密钥空间可以被暴力破解，但“在 1940 年代的技术下，如果没有捷径攻击，是不可攻破的。”他们攻击了更令人印象深刻的 2^95.6 密钥空间，假设有 100 个字符的已知明文，发现他们有 82% 的成功率，总工作量仅为 2^84.5。虽然他们承认这“远非实用”，但任何优于暴力破解的方法都是

22 这在 Stamp, Mark 和 Wing On Chan，“SIGABA: Cryptanalysis of the Full Keyspace”，Cryptologia，第 31 卷，第 3 期，2007 年 7 月，第 201–222 页中指出。

23 尽管索引转子可以使用反向位置，但在第二次世界大战期间实际上从未使用过（参见 Mucklow, Timothy J., SIGABA/ECM II: A Beautiful Idea, Center for Cryptologic History, National Security Agency, Fort George G. Meade, Maryland, 2015, p. 29），因此在计算密钥空间时合理地消除 2^2 的因子。

24 Stamp, Mark 和 Wing On Chan，“SIGABA: Cryptanalysis of the Full Keyspace”，Cryptologia，第 31 卷，第 3 期，2007 年 7 月，第 201–222 页。
