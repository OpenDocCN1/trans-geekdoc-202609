
10. 支持 50%，置信度 80% 规则数量 = 7(`P[12]`, `P[12]` ← `P[15]`, `P[12]` ← `P[14]`, `P[12]` ← `P[13]`, `P[12]` ← `P[15]` `P[14]`, `P[12]` ← `P[15]` `P[13]`, `P[12]` ← `P[14]` `P[13]`)

### 6.5.1 关联规则挖掘 (ARM) 的观察

1. 这些规则显示了选择参数组合的可能性及其相关性。
2. 对于支持度小于 10% 且置信度为 80% 及以上的情況，规则数量众多且项集基数过大。这表明少数人选择相似密钥参数的可能性，以及组合太多而无法评估。
3. 当支持度大于 10% 且小于 40%，置信度为 80% 及以上时，规则数量合理但需要严格努力进行评估。然而其实用性值得怀疑，因为由于支持度高，许多参数被排除在考虑之外。
4. 当支持度大于 40%，置信度大于或等于 80% 时，虽然规则很少且参数有限，易于评估，但同时找到自然规则的机会很高。

为密码分析员配备先进工具以识别弱点并进一步改进密码系统始终是需求。在多项式时间内，密码分析员有兴趣从庞大的密文语料库中提取有用的猜测以检测原始信息。密码分析员可能已捕获包含各种密文和哈希文件的庞大数据库和语料库。当密文被插入此数据集时，它可能与由各种其他方案生成的其他密文混合在一起，包括密钥大小、协议、密文生成算法类型、与密钥空间相关的信息暴露程度，以及与明文、密文及其之间关系相关的大量其他信息。密码分析员可能会开发一种机制，根据密文类型进行分类、排序和分组。

## 6.6 结论

任何物联网应用的成功都依赖于相关信息及其测试框架的安全性。为了设计更安全、抗攻击的物联网信息系统，需要更具体的密码学方法。此外，数据检索和处理是整个基于物联网的信息系统的组成部分，需要通过高级加密进行保护。更先进的具有严格密钥的无线协议可用于物联网安全部署。其中一种方法基于 `AVK` 的使用，本章对其进行了详细分析，并探讨了支持度和置信度的变化。尽管即使使用最佳加密方案，物联网系统的设备或网络仍可能容易受到攻击。如果无法建立与物联网设备通信的数据的真实性，安全性肯定会受到损害。为了解决这个问题，`AVK` 方案可能对构建有用。所提出的模型已使用多个参数、频繁集数量以及要生成的关联规则数量进行了测试和分析。所提出的基于 `AVK` 的参数模型用户友好，但从密码挖掘角度来看更难。

## 参考文献

* [\[1\] Chakrabarti P., Bhuyan B., Chowdhuri A., and Bhunia C., 一种实现最优数据传输和密码学中自动可变密钥（AVK）的新方法。 IJCSNS. 8, 241, 2008.](#Ch06.xhtml#bck_ref6_1)
* [\[2\] Chakrabarti, P., Bhuyan, B., Chowdhuri, A., and Bhunia, C. T., “在 RSA 中应用自动可变密钥（AVK）,” in Int’l J HIT Transactions on ECCN, 2, 304–311, 2007.](#Ch06.xhtml#bck_ref6_2)
* [\[3\] Chakrabarti, P., Mondal, G. H., Bhunia, C. T., and Chowdhuri, A., 用于选择性加密（DES、RSA 和 AES）的 AVK 各种新方法和改进方法及其比较研究。 Int. J. Trans. ECCN, 1(4), 236–244, 2008.](#Ch06.xhtml#bck_ref6_3)
* [\[4\] Bhunia, C. T., AVK 和选择性加密在提高量子密码学和网络性能中的应用, United Nations Educational Scientific and Cultural Organization and International Atomic Energy Agency, 10, 200–210, 2006.](#Ch06.xhtml#bck_ref6_4)
* [\[5\] Dutta, M. P., Banerjee, S., and Bhunia, C., “生成自动可变密钥（AVK）的两种新方案以实现不安全通信信道中的完美安全性,” in Proceedings of the 2015 International Conference on Advanced Research in Computer Science Engineering and Technology (ICARCSET 2015), 1–4, 2015.](#Ch06.xhtml#bck_ref6_5)
* [\[6\] Bhunia, C. T., Chakrabarti, P., Chowdhuri, A., and Chandan, T., 使用混沌理论实现自动可变密钥及其研究, J. IUP Comp. Sci. 5, 22–32, 2011.](#Ch06.xhtml#bck_ref6_6)
* [\[7\] Bhunia, C. T., Mondal, G., and Samaddar, S., “RSA 中时变密钥的理论与应用以及 AES 中选择性加密的应用,” in Proc. EAIT, Elsevier Publications, Calcutta CSI-06, 219–221, 2006.](#Ch06.xhtml#bck_ref6_7)
* [ \[8\] Bhunia, C. T., Chakrabarti, P., Goswami, R., “实现完美安全性的自动可变密钥新技术（CSAVK）,” 100th Indian Science Congress Association, 2013.](#Ch06.xhtml#bck_ref6_8)
* [\[9\] Bhunia, C. T., 针对 AES 错误传播效应的选择性 AES 新方法。 Asia. J. Inform. Technol. 5, 1017–1022, 2006.](#Ch06.xhtml#bck_ref6_9)
* [\[10\] Han, J., Kamber, M., and Pei, J., 数据挖掘：概念与技术, 2nd edn, Morgan Kaufmann, 2006.](#Ch06.xhtml#bck_ref6_10)
* [\[11\] Prajapat, S., and Thakur, R. S., 密码挖掘：基于参数化自动可变密钥对称密码系统的 Apriori 分析。 Int. J. Comp. Sci. Inform. Secur. 14, 233–246, 2016.](#Ch06.xhtml#bck_ref6_11)
* [\[12\] Prajapat, S., Rajput, D., and Thakur, R. S., “面向对称密钥的时变方法,” in Proceedings of IEEE Science and Information Conference (SAI), London 2013, 398–405, 2013.](#Ch06.xhtml#bck_ref6_12)
* \[13\] Prajapat, S., and Thakur, R. S.. “对称密钥加密的 AVK 最优密钥大小,” In Covenant Journal of Information and Communication Technology, 3(2), 71–81, 2015.
* [\[14\] Prajapat, S., Thakur, R. S., 密码分析的各种方法。 Int. J. Comp. Appl. 127(14), 15–24, 2015.](#Ch06.xhtml#bck_ref6_14)
* [\[15\] Prajapat, S., Thakur, R. S., 基于自动可变密钥的密码系统的密码挖掘。 Elsevier Procedia Comp. Sci. 78(78C), 199–209, 2016.](#Ch06.xhtml#bck_ref6_15)
* \[16\] Prajapat, S., Thakur, R. S., 使用基于 Fibo-Q 的对称密码系统实现信息交换。 Int. J. Comp. Sci. Inform. Secur. 14(2), 216–223, 2016.
* \[17\] Prajapat, S., Thakur, A., Maheshwari, K., and Thakur, R. S., 在人工智能视角下的密码挖掘。 IJACSA 6(8), 62–69, 2015.

# 索引

### A
* 亚马逊 Spark [47](#Ch03.xhtml#p47_65)
* 攻击面 [55](#Ch04.xhtml#p55_65), [73](#Ch04.xhtml#p73_65)
* 身份验证 [3](#Ch01.xhtml#p3_65), [58](#Ch04.xhtml#p58_65), [83](#Ch04.xhtml#p83_65), [105](#Ch06.xhtml#p105_65)

### B
* 大数据 [6](#Ch01.xhtml#p6_65), [41](#Ch03.xhtml#p41_65), [47](#Ch03.xhtml#p47_66)
* 比特币 [93](#Ch05.xhtml#p93_66), [95](#Ch05.xhtml#p95_66)
* 区块链 [50](#Ch03.xhtml#p50_66), [87](#Ch05.xhtml#p87_66), [89](#Ch05.xhtml#p89_66)
* 区块 [90](#Ch05.xhtml#p90_66), [96](#Ch05.xhtml#p96_66)

### C
* Cisco [42](#Ch03.xhtml#p42_66), [95](#Ch05.xhtml#p95_67)
* Cisco JASPER [95](#Ch05.xhtml#p95_68), [96](#Ch05.xhtml#p96_68)
* 云 [3](#Ch01.xhtml#p3_68), [40](#Ch03.xhtml#p40_68), [58](#Ch04.xhtml#p58_68), [102](#Ch06.xhtml#p102_68)
* 云计算 [6](#Ch01.xhtml#p6_68), [40](#Ch03.xhtml#p40_69), [48](#Ch03.xhtml#p48_69)
* 云节点 [42](#Ch03.xhtml#p42_69), [49](#Ch03.xhtml#p49_69)

