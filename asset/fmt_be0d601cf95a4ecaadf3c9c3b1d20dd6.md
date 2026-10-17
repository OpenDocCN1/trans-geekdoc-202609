
| Mamta and Gupta [[25]](#05chap_05.xhtml#ref5_25) | `3*E + 1*H` | `(ξ+6)*E + (k+1)*H` | `7*E + 1*P + 1*H` | `(ξ+2)*E + 6*P` |
| Miao et al. [[26]](#05chap_05.xhtml#ref5_26) | `(3*ξ+8)*E` | `(4*N+3)*E + 2*E[T] + P` | `(2*ξ+2)*E` | `2*P` |
| Mamta and Gupta [[27]](#05chap_05.xhtml#ref5_27) | `2*E` | `(2*N+1)*E + 2*E[T] + 1*H + 1*P` | `(ξ+3)*E + 1*H` | `4*P + 1*E[T]` |
| Mamta et al. [[28]](#05chap_05.xhtml#ref5_28) | `2*E` | `(T+1)*E + 1*H + 2*E[T]` | `2*E + 1*H` | `(T+1)*P + 1*E[T]` |

根据表 5.3 和表 5.4 可观察到，与其他方案相比，方案 [[25]](#05chap_05.xhtml#ref5_25)、[[27]](#05chap_05.xhtml#ref5_27) 和 [[28]](#05chap_05.xhtml#ref5_28) 的密钥生成算法在涉及属性数量方面具有恒定的存储成本和时间复杂度。对于加密算法，除 [[27]](#05chap_05.xhtml#ref5_27) 存储成本恒定外，其余给定方案均具有可变的存储和计算成本。对于陷门生成算法，[[25]](#05chap_05.xhtml#ref5_25)、[[27]](#05chap_05.xhtml#ref5_27) 和 [[28]](#05chap_05.xhtml#ref5_28) 的存储成本恒定，而 [[25]](#05chap_05.xhtml#ref5_25) 和 [[28]](#05chap_05.xhtml#ref5_28) 使计算成本不随属性数量变化。在 `Search` 算法中，[[26]](#05chap_05.xhtml#ref5_26) 和 [[27]](#05chap_05.xhtml#ref5_27) 实现了恒定数量的配对操作，从而实现了快速搜索。

## 5.3 章节总结

在多用户云环境中，公钥设置是开发可搜索加密方案的首选，因为对称密钥方案面临着秘密密钥共享的复杂过程。本章详细解释了公钥设置下可搜索加密的概念。它提供了非对称密钥设置下可搜索加密方案的通用结构。此外，本章主要讨论了基于 IBE 和 ABE 开发的可搜索加密技术。二者之中，我们认为 ABE 是合适的选择，因为它提供了细粒度访问控制能力，使其成为能够真正以高效方式处理多用户的适当方案。此外，我们还在此设置下对文献中的现有方案进行了比较分析。

# 参考文献

1. Z. Wang, J. Ye, and J. Wang, “An efficient traceable data sharing scheme in cloud computing for mobile devices,” Int. J. High Perform. Comput. Netw, vol. 12, no. 2, pp. 156–165, 2018.
2. S.-H. Heng, and K. Kurosawa, “k-resilient identity-based encryption in the standard model,” in *Cryptographers' Track at the RSA Conference*, 2004, pp. 67–80.
3. J. Wang, and C. Wang, “Full secure identity-based encryption scheme over lattices for wireless sensor networks in the standard model,” Int. J. High Perform. Comput. Netw, vol. 12, no. 2, pp. 111–117, 2018.
4. Y. Lu, G. Wang, J. Li, and J. Shen, “Efficient designated server identity-based encryption with conjunctive keyword search,” Ann. Telecommun, vol. 72, no. 5–6, pp. 359–370, 2017.
5. Y. Miao, J. Ma, F. Wei, K. Zhang, and Z. Liu, “VKSE-DO: Verifiable keyword search over encrypted data for dynamic data-owner,” Int. J. High Perform. Comput. Netw, vol. 12, no. 1, pp. 39–48, 2018.
6. J. Zhang, and H. Gao, “A compact construction for non-monotonic key-policy attribute-based encryption,” Int. J. High Perform. Comput. Netw, vol. 13, no. 3, pp. 321–330, 2019.
7. S. Zhu, and Y. Han, “Secure data outsourcing scheme in cloud computing with attribute-based encryption,” Int. J. High Perform. Comput. Netw, vol. 12, no. 2, pp. 128–136, 2018.
8. D. Boneh, G. Di Crescenzo, R. Ostrovsky, and G. Persiano, “Public key encryption with keyword search,” in *International Conference on the Theory and Applications of Cryptographic Techniques*, 2004, pp. 506–522.
9. D. Khader, “Public key encryption with keyword search based on k-resilient IBE,” in *International Conference on Computational Science and Its Applications*, 2007, pp. 1086–1095.
10. M. Abdalla *et al.*, “Searchable encryption revisited: Consistency properties, relation to anonymous IBE, and extensions,” J. Cryptol., vol. 21, no. 3, pp. 350–391, 2008.
11. P. Xu, H. Jin, Q. Wu, and W. Wang, “Public-key encryption with fuzzy keyword search: A provably secure scheme under keyword guessing attack,” IEEE Trans. Comput, vol. 62, no. 11, pp. 2266–2277, 2012.
12. D. Boneh, and M. Franklin, “Identity-based encryption from the Weil pairing,” in *Annual International Cryptology Conference*, 2001, pp. 213–229.
13. Mamta, B. B. Gupta, and S. T. Ali, “ISEkFT: An IBE-based searchable encryption scheme with k-keyword fuzzy search trapdoor,” J. Inf. Technol. Res, vol. 12, no. 3, pp. 133–153, 2019.
14. M. Sookhak, F. R. Yu, M. K. Khan, Y. Xiang, and R. Buyya, “Attribute-based data access control in mobile cloud computing: Taxonomy and open issues,” Futur. Gener. Comput. Syst, vol. 72, pp. 273–287, 2017.
15. J. Bethencourt, A. Sahai, and B. Waters, “Ciphertext-policy attribute-based encryption,” in 2007 IEEE Symposium on Security and Privacy (SP'07), 2007, pp. 321–334.
16. X. Yang, and W. Ding, “Researches on data encryption scheme based on CP-ASBE of cloud storage,” Int. J. High Perform. Comput. Netw, vol. 14, no. 2, pp. 219–228, 2019.
17. V. Goyal, O. Pandey, A. Sahai, and B. Waters, “Attribute-based encryption for fine-grained access control of encrypted data,” in *Proceedings of the 13th ACM Conference on Computer and Communications Security*, 2006, pp. 89–98.
18. L. Ibraimi, Q. Tang, P. Hartel, and W. Jonker, “Efficient and Provable Secure Ciphertext-Policy Attribute-Based Encryption Schemes,” in *International Conference on Information Security Practice and Experience*, 2009, pp. 1–12.

# 第 6 章：设计与开发工具及跨域应用

可搜索加密方案的**设计与开发**本质上需要数学知识，但一旦开发完成并证明安全，我们就需要实现它以检验其实用性。在本章中，我们将讨论实现这些方案的语言选择、可用的库，以及可用于测试的不同数据集。此外，我们还将讨论可搜索加密在密码学以外的其他几个领域的应用。

## 6.1 语言与库选项

可搜索加密方案是一组协同工作以实现搜索加密数据这一共同目标的不同算法的集合。因此，用户熟悉的任何语言都可用于实现。在公钥设置中，需要执行配对运算，因此必须使用配对库。因此，建议使用与配对库相同的语言以获得更好的兼容性。

### 6.1.1 对称可搜索加密方案的工具包

对于对称密钥设置下的可搜索加密方案，有以下工具包可用于评估可搜索加密。

**OpenSSE 密码学工具包：** 该工具包拥有一个密码学层，提供伪随机函数、哈希函数和加密方案等特性的接口与实现，典型的可搜索加密方案依赖于这些特性。该工具包包含用 C 和 C++ 实现的单关键词搜索方案。它提供了所需的抽象层级，可轻松实现可搜索加密方案。著名的密码学库（如 `OpenSSL`）不提供可搜索加密方案构建模块的接口。然而，它仍是一个研究项目，建议**不要**用于敏感信息。

**Clusion 库：** 如果我们谈论对称可搜索加密（SSE），`Clusion` 是另一个值得一提的软件库。它不仅提供了近期 SSE 方案的模块化实现，而且在考虑最坏情况下，所有实现均具有亚线性渐近搜索复杂度。此外，它还提供支持多关键词搜索中析取、合取运算的构造，同时也支持简单的单关键词搜索。

### 6.1.2 公钥设置下可搜索加密的配对库

公钥设置下的可搜索加密方案主要利用基于身份的加密、基于属性的加密和谓词加密等进行开发，这些高级加密方案通常在其构造中使用配对概念。有多种配对库可用，其中一些流行的库描述如下：

**PBC（基于配对的密码学）库：** 这是一个用于执行配对运算的免费 C 库。它基于 `GMP` 库开发，后者执行数学运算。`PBC` 库是基于配对的密码系统的组成部分 [[1]](#06chap_06.xhtml#ref6_1)。因为它在底层使用 `GMP` 库，尽管是用 C 编写的，但配对时间非常短。因此，速度和可移植性是其主要特性。此外，椭圆曲线算术和配对计算等基本功能可轻松执行。Boneh-Lynn-Shacham 短签名 [[2]](#06chap_06.xhtml#ref6_2)、Hess 基于身份的签名 [[3]](#06chap_06.xhtml#ref6_3) 和 Paterson 基于身份的签名 [[4]](#06chap_06.xhtml#ref6_4) 是一些使用该库测试的密码系统示例。

**JPBC（Java 基于配对的密码学）库：** 顾名思义，Java 基于配对的密码学库基于 Java 语言 [[5]](#06chap_06.xhtml#ref6_5)。它是 Lynn 提供的 `PBC` 库的扩展 [[1]](#06chap_06.xhtml#ref6_1)。基于 `JPBC` 的实现支持多线程，并采用内存映射文件来优化主内存使用。`JPBC` 使用包装器将配对计算委托给 `PBC` 库。除了双线性映射，`JPBC` 还提供对多重线性映射的支持。多个函数加密方案和签名方案已成功使用 `JPBC` 库进行测试。

**Charm：** `Charm` 是一个基于 Python 的库。利用 `Charm` 框架 [[6]](#06chap_06.xhtml#ref6_6)，高级密码系统的原型可快速且无缝地创建。代码复用、可读性和简洁性是 `Charm` 的显著特点。它为各种数学设置提供支持，包括整数环/域、双线性和非双线性椭圆曲线群。它拥有一个基础加密库，包含对称加密方案、哈希函数和伪随机数生成器。

此外，`Charm` 提供标准应用程序编程接口以构建数字签名和加密方案。而且，它提供了一个“协议引擎”以简化多方协议的实现过程。`Charm` 框架还提供了一个用于交互式和非交互式零知识证明的集成编译器。因此，就其提供的功能而言，它是最全面的框架。

## 6.2 数据集

有不同的数据集可用于进行模拟并评估可搜索加密方案中所涉及算法的时间复杂度。

### Enron 电子邮件数据集

Enron 电子邮件数据集包含 Enron 组织员工生成的约 500,000 封电子邮件 [10]。联邦能源监管委员会在其对 Enron 倒闭的调查过程中获取了该数据集。该数据集是在“会学习和组织的认知助手”（CALO）项目下收集和整理的。它包含约 150 位用户的统计数据，在大多数情况下为 Enron 的高级管理人员。数据被组织到文件夹中。联邦能源监管委员会在其研究过程中将这些记录公开并发布到了互联网上。后来，该数据集被麻省理工学院的 Leslie Kaelbling 购买，她发现了一些完整性问题并进行了修正，随后将该数据集提供给研究项目使用。无效的电子邮件地址被转换为通用形式，如 `user@enron.com`（当指定了收件人时）或 `no_address@enron.com`（当未指定收件人时）。

### 互联网征求意见稿（RFC）

该数据集包含 6,870 个纯文本文件，总大小约为 349MB [11]。为了从每个 RFC 文件中提取关键词，通常使用密闭式词频计数器 [12]。

## 6.3 跨域应用

可搜索加密不仅限于密码学领域，还可以应用于不同平台并与之结合。除了在云平台上应用可搜索加密外，文献中还出现了其他应用场景。研究人员已将这一概念应用并测试于不同平台，如物联网、无线传感器网络（WSN）、雾计算及其组合 [13, 14, 15]。最近，区块链技术被用于构建更稳健的可搜索加密方案。这方面的大多数进展见于 2017 年以后。

### 云辅助无线传感器网络（CWSN）

可搜索加密应用出现的一个新领域是云辅助无线传感器网络（CWSN）。Xu [16] 为 CWSN 提出了一种轻量级可搜索加密方案，降低了生成密文和执行搜索的成本。传感器网络所有者生成公钥和私钥对，并将公共组件存储在所有传感器节点上。传感器节点收集并将加密数据存储在云服务器上。为了检索数据，数据所有者为关键词生成陷门并将其发送给云服务器以执行搜索。

### 基于云的物联网

物联网设备贡献了当今数字世界中的大部分数据，收集的数据存储在云服务器中。收集的数据可能是敏感的；因此，可搜索加密可用于基于云的物联网。Wu 等人 [17] 为此提出了一种可搜索加密方案。其系统的工作原理与公钥设置下的标准可搜索加密相同。除了基本功能外，他们专注于开发抗 KGA（关键词猜测攻击）的方案。

### 雾计算

Miao 等人 [18] 将细粒度联合关键词搜索应用于雾计算。它基本上是云计算的一种扩展，其中雾节点被放置在终端用户和云之间。他们的方案是轻量级的，因为大多数计算密集型任务被委托给雾节点。终端用户仅执行部分计算；最终密文甚至最终陷门由雾节点生成并发送给云服务器。雾节点接收云服务器返回的搜索结果并执行部分解密，以进一步减轻终端用户的负担。云服务器像往常一样扮演搜索者的角色，但它不再将搜索结果返回给终端用户，而是返回给执行所有必要计算的中间雾节点。他们还考虑了访问策略中属性更新的过程，因此支持动态策略。来自终端用户的数据由这些用户使用的物联网设备（可穿戴或移动设备）收集。

### 区块链技术
