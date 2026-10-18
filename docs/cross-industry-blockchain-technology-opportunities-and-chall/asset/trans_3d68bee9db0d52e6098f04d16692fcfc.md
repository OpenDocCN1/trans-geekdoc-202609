

| \[10\] || Huh S., Cho S., Kim S.. Managing IoT devices using blockchain platformInt. Conf. Adv. Commun. Technol. ICACT464467.201710.23919/ICACT.2017.7890132 |

| \[11\] || Lone A.H., Naaz R.. Applicability of Blockchain smart contracts in securing Internet and IoT: A systematic literature review.Comput. Sci. Rev.20213910036010.1016/j.cosrev.2020.100360 |

| \[12\] || Tange K., De Donno M., Fafoutis X., Dragoni N.. A Systematic Survey of Industrial Internet of Things Security: Requirements and Fog Computing Opportunities.IEEE Commun. Surv. Tutor.20202242489252010.1109/COMST.2020.3011208 |

| \[13\] || Xiao L., Wan X., Lu X., Zhang Y., Wu D.. IoT Security Techniques Based on Machine Learning: How Do IoT Devices Use AI to Enhance Security?IEEE Signal Process. Mag.2018355414910.1109/MSP.2018.2825478 |

| \[14\] || Hussain F., Hussain R., Hassan S.A., Hossain E.. Machine Learning in IoT Security: Current Solutions and Future Challenges.IEEE Commun. Surv. Tutor.20202231686172110.1109/COMST.2020.2986444 |

| \[15\] || Wang T., Zhang G., Liu A., Bhuiyan M.Z.A., Jin Q.. A secure IoT service architecture with an efficient balance dynamics based on cloud and edge computing.IEEE Internet Things J.2019634831484310.1109/JIOT.2018.2870288 |

| \[16\] || Sha K., Yang T.A., Wei W., Davari S.. A survey of edge computing-based designs for IoT security.Digital Communications and Networks20206219520210.1016/j.dcan.2019.08.006 |

| \[17\] || Bhardwaj K., Miranda J. C., Gavrilovska A.. Towards IoT-DDoS prevention using edge computingUSENIX Work. Hot Top. Edge Comput. Hot Edge, co-located with USENIX ATC2018 |

| \[18\] || Sridhar S., Smys S.. Intelligent Security Framework for IoT Devices.Int. Conf. Inven. Syst. Control Intell.201715 IEEE.. |

| \[19\] || Khari M., Garg A.K., Gandomi A.H., Gupta R., Patan R., Balusamy B.. Securing Data in Internet of Things (IoT) Using Cryptography and Steganography Techniques.IEEE Trans. Syst. Man Cybern. Syst.2020501738010.1109/TSMC.2019.2903785 |

| \[20\] || Summary E.. Empowering the edge.201418 |

| \[21\] || Corporation I.B.M.. Empowering the edge - Practical insights on a decentralized Internet of Things IBM Institute for Business Value2015 [`https://www-01.ibm.com/common/ssi/cgi-bin/ssialias? subtype=XB&infotype=PM&htmlfid=GBE03662USEN&attachment=GBE03662USEN.PDF`](https://www-01.ibm.com/common/ssi/cgi-bin/ssialias?subtype=XB&infotype=PM&htmlfid=GBE03662USEN&attachment=GBE03662USEN.PDF) |

| \[22\] || Dorri A., Kanhere S.S., Jurdak R., Gauravaram P.. Blockchain for IoT security and privacy: The case study of a smart home.IEEE Int. Conf. Pervasive Comput. Commun. Work. PerCom Work.201761862310.1109/PERCOMW.2017.7917634 |

# 分布式账本技术及其潜在应用——金融领域

**Sachin Sharma**^([1](#9789815051452-C2.html#aff1), [\*](#9789815051452-C2.html#cor1))****,** **Kamal Kumar**^([2](#9789815051452-C2.html#aff2))**

¹ Computer Science and Engineering, Maharishi Markandeshwar (Deemed to be) University, Mullana, Ambala, India

² Computer Science and Engineering, National Institute of Technology Uttarakhand, Srinagar, Garhwal, India

## 摘要

区块链的概念在过去十年中展现出了巨大的潜力和增长。区块链和分布式账本技术等术语被混用。许多研究工作致力于解释和利用分布式账本技术在金融领域的优势。数字货币或加密货币是一种基于区块链概念的技术货币。

**关键词：**`Bitcoin`, `Blockchain`, `Digital Currencies`, `Digital Ledger Technology`, `Financial Inclusion`, `Financial Sector`, `Smart Contracts`。

* * *

^(\*) **通讯作者 `Sachin Sharma`：**Computer Science and Engineering, Maharishi Markandeshwar (Deemed to be) University, Mullana, Ambala, India; E-mail: [`er.sachinsharma@gmail.com`](mailto:er.sachinsharma@gmail.com)

## 引言

DLT 利用现有的对等技术，例如互联网电话、电子邮件、文件共享和互联网。匿名人士“中本聪”于 2008 年撰写的一篇基准论文《比特币：一种点对点电子现金系统》，介绍了一种名为“比特币”的 P2P 技术的资金转移独特方法。中本聪论文中描述的技术被称为区块链，它解释了一种存储和组织信息及交易的新方式。其他形式的信息传输和交易技术被设计出来，“分布式账本技术”这一术语被创造出来。DLT 在账本（多个数据存储）之间记录和共享数据，每个账本由分布式计算设备控制和管理，并拥有相同的数据记录副本。这些计算设备被称为节点。DTL 可以理解为一种具有独特属性的分布式数据库。区块链是一种特殊的 DLT，它利用算法和密码学技术生成和验证仅追加的增长数据结构。该数据结构以交易块（链）的形式充当账本，被称为区块链。其中一个节点创建一个新的数据块，该块包含多个交易记录。

其中一个节点发起数据库添加，进而生成一个包含多个交易记录的新数据“块”。此新块信息（以加密格式）分布到整个网络以维护数据隐私。此块的有效性由每个网络参与者使用共识机制（算法验证方法）来确定。验证后，新块被添加到所有参与者的各自账本中。使用此方法，账本的每次更改都会导致整个网络中的账本复制，整个相同的账本随时可供每个网络成员使用。该技术可用于任何数字交易记录。参见 Fig. [(**1**)](#9789815051452-C2.html#f1)（“迪拜旨在成为基于区块链建造的城市”。作者：Nikhil Lokhade，2017 年 4 月 24 日，《华尔街日报》 [`https://www.wsj.com/articles/dubai-aims-to-be-a-city-built-on-blockchain-1493086080`](https://www.wsj.com/articles/dubai-aims-to-be-a-city-built-on-blockchain-1493086080)）。

![](Images/9789815051452-C2-F1.jpg)**Fig. (1))**

基于区块链的 DTL 工作原理。

1\. 基于区块链的 DLT 系统构成一个仅追加的数据块链。其中一个节点发起数据库的新添加，并创建一个包含多个交易记录的新数据块。

2\. 关于新数据块的信息在整个网络中共享。交易详情包含加密数据。

3\. 所有网络参与者使用“共识机制”来确定块的有效性。验证后，每个参与者将新数据块添加到各自的账本中，以便整个账本的完整相同副本在整个网络中复制。

基于 DLT 的解决方案的两个特征是：

1. 它消除了集中式记录保存、存储、记录和分发数字信息的需求，这些操作在自管理的交易对手之间进行。

2. 它还消除了双重支付，这意味着同一个代币不能分发给多个交易对手。

## DLT 的近期工作

