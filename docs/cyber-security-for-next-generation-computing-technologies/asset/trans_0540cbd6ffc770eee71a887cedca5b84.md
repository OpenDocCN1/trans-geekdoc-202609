

# 下一代计算技术的网络安全

NSL-KDD 和 NOT-IoT 可用于 SVM 来检测如中间人攻击、DoS、DDoS、篡改等攻击 [72]。

## 8.6 针对物联网的基于深度学习的特征入侵检测系统（Signature-IDS）解决方案

在处理大型数据集集时，我们采用深度学习（DL）技术，而不是机器学习解决方案。这些方法被广泛应用于入侵检测系统（IDS）中。深度学习是机器学习（ML）的一个领域，由神经网络组成，通过层层修改来帮助识别数据的高层特征 [73]。在入侵检测系统中，神经网络的隐藏层有助于识别用于模式选择的最佳特征。它包含一个输入层、一个或多个层隐藏层和一个输出层。网络的每个输入都关联着特定的权重，这些权重通过反向传播方法进行调整以获得最佳输出 [74]。深度学习技术主要分为三类：监督学习、无监督学习技术和混合方法 [75]。

一些著名的技术如深度神经网络（DNN）、卷积神经网络（CNN）等等被包含在监督学习方法中。这些方法提供了高准确率。深度神经网络（DNN）包含许多隐藏层，有助于特征提取。Tang 等人 [76] 设计了一个执行基于流检测的简单 DNN。卷积神经网络（CNN）执行池化以及与数据集输入的全连接。CNN 涉及的预处理较少。Kolosnici 等人 [77] 设计了一个使用带有递归网络层的 CNN 来检测恶意软件的模型。循环神经网络（RNN）由一个存储以前数据的内存函数组成。它能高效地处理时间序列信息。Yin 等人 [78] 使用二分类和多分类分类评估了 RNN。

无监督学习技术包括生成对抗网络（GANs）、自动编码器（AE）、深度置信网络（DBN）等。由于从标记数据中获取的知识不足，这些方法的性能较低。其在 KDCup 数据集上获得了最佳性能。生成对抗网络（GAN）是一种无监督学习类型，有助于处理、审查和捕获数据。它由一个生成器和一个判别器组成，有助于从伪数据中识别真实特征。Erpek 等人 [80] 设计了一种基于发射器、接收器、干扰器的生成对抗网络攻击检测模型。自动编码是一种用于减少维度和检测异常值的数据压缩算法。它使用特征空间来压缩输入，Zhang 等人 [81] 提出了使用扩张自动编码器（DCAEEs）从原始网络流量中提取特征。混合方法具有高性能和较少的训练样本，但由于结构复杂，计算时间较高。Li 等人 [82] 使用实现了自动编码器和深度神经网络的混合深度学习技术进行异常检测。![](img/6cda7de08ea4ec22ad1540507165_0.png)

**图 8.5** 基于特征的 IDS 威胁检测。

## 8.7 基于特征的入侵检测系统架构

研究人员根据网络框架使用了各种类型的 IDS 以满足需求。Sourour 等人 [83] 建议使用双层 IDS 来解决与地址转换（NAT）的安全问题。第 1 层监控实体，第 2 层使用告警聚合、告警分类和告警关联三个模块来减少报警。Zhang 等人 [84] 引入了使用多层架构进行攻击分类和选择（CSC）的离散类型 IDS。深度学习（MDL）模型也被建议部署在 IDS 中，它受人类大脑启发，但这一概念仍处于新生阶段 [85]。应用层容易受到各种攻击的影响，因此对于云安全，基于特征的 IDS 是一种有效的方法，从而保护了应用层 [86, 87]。基于特征的 IDS 威胁检测现象如图 8.5 所示。

## 8.8 基于特征的 IDS 的局限性

基于特征的 IDS 技术是一种广泛使用的方法，因为它通常具有低报警率和高效的结果。但这种技术具有需要解决的局限性。基于特征的 IDS 只能识别已保存的威胁；无法检测缺失 [88, 90]，且零日漏洞未被处理 [89]。基于特征方法的每个数据包都需要匹配，在大规模网络流量异常的情况下，这种情况会导致数据丢弃，使系统面临丢失潜在威胁 [92]。因此这些局限性被称为设计或实现缺陷 [93]。

## 8.9 讨论与未来方向

技术和物联网的进步导致数据安全出现巨大漏洞 [94, 95]。由于特征的检测能力是商业领域广泛安装的 IDS，这些系统每天都在改进以适应新变体的复杂度。本章讨论了基于特征的 IDS 详细综述以及各种实现技术。未来的工作可以通过实施具有特定威胁倾向技术的 IDS 来完成。如 SNORT、WINPCAP 等软件可以关注实时检测和效率 [96]。

## 8.10 结论

安全不再是 IT 基础设施中的一个选项；它是一个紧迫的问题。物联网设备的爆炸式增长给物联网环境带来了安全挑战。基于特征的 IDS 是应对安全威胁的一种极方法。不同的研究人员使用不同的方法提出了许多基于特征检测的解决方案。模式匹配方法具有这种类型的识别，但它存在一些导致假阴性和潜在危险的局限性。机器学习和深度学习算法通过在各种数据集上进行训练，应对基于特征检测的局限性，降低了误报率并提高了准确性。这项工作提供了各种基于特征的 IDS 及其部署技术的详细综述。

## 参考文献

- [1] Algahtani B, Alnajrani B (2020) 互联网协议和通信研究。ICCIS，页 1–6, doi:10.1109/ICCIS49240.2020.927652.
- [2] Soumayatha R, Hegde SG (2016) IoT 研究：理解 IoT 架构、应用和挑战。ICCKIN，CSE, International Journal of Networking & Applications, vol 478.
- [3] Abdawal N, Sajun A, Kaddoura Y, Zulkerman IA, Aloul F (2022) 用于 IoT 数据集的网络攻击检测生成深度学习。IEEE Access 10: 6430–6441, doi:10.1109/ACCESS.2023.3140015.
- [4] Mann P, Tyagi N, Gautam S, Rana A (2020) IoT 环境中各种攻击的分类。2020 第12 届计算智能与通信国际会议 (CICN), IEEE, Bhimtal, India.
- [5] Cisco 年度互联网报告–Cisco 年度互联网报告 (2018–2023)。白皮书。访问：2021年5月31日。https://www.cisco.com/en/us/executive/perspectives/annual-internet-report.
- [6] Ashraf J, Bakshi AD, Moustafa N, Khurshid K, Mihova A, Voznak M (2021) 用于基于类的无线传感网络的异常检测深度学习自动编码器。Wireless Personal Communication, 85(1): 207.
- [7] Archana MB, Harshitha BN, Prakaj M (2017) 防止基于类的无线传感网络的 Sybil 攻击技术。International Journal of Recent Trends in Engineering and Research, 3(4):370–373, doi:10.23883/ijiter.js.
- [8] Wang W, He S, Sun L, Zhang Q (2019) 异构物联网的交叉技术。IEEE Transactions on Wireless Communications, 18(2): 796–806, doi:10.1109/twc.2018.28834.
- [9] Kumar V (2012) 使用 SNORT 的特征网络入侵检测系统。International Journal of Computer Applications & Information Technology, I(7).
- [10] Bhuyan MH, Bhattacharjya DK, Kalita JK (2014) 网络异常检测：方法、系统和工具。IEEE Surveys & Tutorials, 16(1): 303–336.
- [11] Tang Y, Chen J (2007) 跨多态蠕虫的自动特征方法。IEEE Transactions on Parallel and Distributed Systems, 18(7): 879–892, doi:10.1109/TPDS.2007.1050.
- [12] Snehi J, Bhandari A, Gautam V, Beni M (2020) 采用的多种特征 IDS 方案。International Journal of Recent Technology and Engineering, 9(2): 44–49.

