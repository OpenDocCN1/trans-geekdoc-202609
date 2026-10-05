

## 12.3 DES 的安全性

## 表 12.9
商用 DES 芯片

| 制造商 | 芯片 | 年份 | 时钟频率 | 数据速率 | 可性 |
|---|---|---|---|---|---|
| AMD | Am9518 | 1981 | 3 MHz | 1.3 Mbyte/s | N |
| AMD | Am9568 | ? | 4 MHz | 1.5 Mbyte/s | N |
| AMD | AmZ8068 | 1982 | 4 MHz | 1.7 Mbyte/s | N |
| AT&T | T7000A | 1985 | ? | 1.9 Mbyte/s | N |
| CE-Infosys | SuperCrypt CE99C003 | 1992 | 20 MHz | 12.5 Mbyte/s | N |
| CE-Infosys | SuperCrypt CE99C003A | 1994 | 30 MHz | 20.0 Mbyte/s | Y |
| Cryptch | Cry12C102 | 1989 | | 2.8 Mbyte/s | Y |
| Newbridge | CA20C03A | 1991 | 25 MHz | 3.85 Mbyte/s | Y |
| Newbridge | CA20C03CW | 1992 | 8 MHz | 0.64 Mbyte/s | |
| Newbridge | CA95C68/18/09 | 1993 | 33 MHz | 14.6 Mbyte/s | Y |
| Pijenburg | PCC100 | ? | | 2.5 Mbyte/s | |
| Semaphore | Roadrummer284 | ? | 40 MHz | 35.5 Mbyte/s | Y |
| Communications | VM0007 | 1993 | 32 MHz | 200.0 Mbyte/s | Y |
| VLSI Technology | VM0009 | 1993 | 33 MHz | 14.0 Mbyte/s | Y |
| VLSI Technology | 6888 | 1995 | 32 MHz | 64.0 Mbyte/s | Y |
| Western Digital | WD2001/2002 | 1984 | 3 MHz | 0.23 Mbyte/s | N |

## 表 12.10
不同微处理器和计算机上的 DES 规格

| 处理器 | 速度 (MHz) | DES 块数 [每秒] |
|---|---|--|
| 8088 | 4.7 | 370 |
| 68000 | 7.6 | 900 |
| 80286 | 6 | 1,100 |
| 68020 | | 3,500 |
| 68030 | 16 | 3,900 |
| 80386 | 25 | 5,000 |
| 68030 | 50 | 10,000 |
| 68040 | 25 | 16,000 |
| 68040 | 40 | 23,000 |
| 80486 | 66 | 43,000 |
| Sun ELC HyperSparc RS6000-350 | | 26,000 |
| Sparc 10/52 | | 32,000 |
| DEC Alpha 4000/610 | | 53,000 |
| HP 9000/887 | 125 | 84,000 |

第 12 章 数据加密标准 (DES)

根据国家安全局 (NSA) 请求提出的标准……Tuchman 解释道：“NSA 告诉我们，我们本能地重新发明了一些深度秘密，以制造他们自己的算法。”

在文章后半部分，引用了 Tuchman 的：“我们完全在 IBM 内部使用 IBM 员工开发了 DES 算法。NSA 并没有规定过任何一根导线的细节！”Tuchman 在 1992 年国家计算机安全会议上谈到 DES 历史时再次重申了这一点。

另一方面，Copersham 写道 [373, 374]：“国家安全局 [NSA] 为 IBM 提供了技术建议。”Konheim 也曾被引用说：“我们把 S 盒发送到了华盛顿。它们送回来时已经全变样了。我们运行了测试并通过了。”人们指出，这是 NSA 在 DES 中留有**后门**的证据。

在在被问及关于 DES 的任何拟议弱点时，NSA 回答道 [363]：

“关于数据加密标准 [DES]，我们认为 1978 年参院情报委员会对 NSA 在 DES 开发中角色的调查公开记录已经回答了你们的问题。委员会报告指出，NSA 未以任何方式篡改算法设计，且 DES 提供的安全性对于其旨在用于非密数据来说，至少在 5 到 10 年范围内是足够的。NSA 没有对 DES 施加或试图施加任何弱点。”

那么，他们为什么要修改 S 盒呢？也许是为了确保 IBM 没有理由不信任 IBM 的研究人员。

*(注：原文后续部分存在大量重复和断句，此处已按核心逻辑整合翻译)*

