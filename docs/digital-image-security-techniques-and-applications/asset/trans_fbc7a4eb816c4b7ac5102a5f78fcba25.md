
[29] Zhou, T. & Yang, B. (2022). 利用 prenyltransferase iacE 生产 prenylated resveratrol 的新策略及神经保护机制评价. Biochemical and Biophysical Research Communications, 609, 127–133.

[30] Sengupta, S., Chowdhary, A., Sabur, A., Alshamrani, A., Huang, D., & Kambhampati, S. (2020). 网络安全移动目标防御综述. IEEE Communications Surveys & Tutorials, 22(3), 1909–1941.

[31] Sengupta, S., Chowdhary, A., Huang, D., & Kambhampati, S. (2019). 云网络中利用移动目标防御进行高级持续性威胁战略检测的一般和马尔可夫博弈. In Decision and Game Theory for Security: 10th International Conference, GameSec, Stockholm, Sweden, October 30–November 1, 2019, 492–512.

[32] Gao, Y., Li, X., Peng, H., Fang, B., & Philip, S. Y. (2020). Hinacti: 基于异构信息网络的网络威胁情报建模与识别系统. IEEE Transactions on Knowledge and Data Engineering, 34, 708–722.

[33] Zhao, H., Yao, Q., Li, J., Song, Y., & Lee, D. L. (2017). 异构信息网络上的基于元图的推荐融合. In Proceedings of the 23rd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, New York, NY, United States, 13–17 August 2017, 635–644.

[34] Li, J., Ranka, S., & Sahni, S. (2011). GPU 上的 Strassen 矩阵乘法. In 2011 IEEE 17th International Conference on Parallel and Distributed Systems, Tainan, Taiwan, 7–9 December 2011, 157–164.

[35] Mavroeidis, V., & Bromander, S. (2017). 网络威胁情报模型：网络威胁情报中分类法、共享标准和本体论的评估. In 2017 European Intelligence and Security Informatics Conference (EISIC), 11–13 September 2017, Athens, Greece, 91–98.

[36] Mittal, S., Das, P. K., Mulwad, V., Joshi, A., & Finin, T. (2016). Cyberwitter：利用 Twitter 生成网络安全威胁和漏洞警报. In 2016 IEEE/ACM International Conference on Advances in Social Networks Analysis and Mining (ASONAM), Davis, California, 18–21 August 2016, 860–867.

[37] Andrian, J., Kamhoua, C., Kiat, K., & Njilla, L. (2017). 网络威胁信息共享：范畴论方法. In 2017 Third International Conference on Mobile and Secure Services (MobiSecServ), Miami Beach, USA, United States, 17–18 February 2017, 1–5.

[38] Sánchez-Zas, C., Villagrà, V. A., Vega-Barbas, M., Larriva-Novo, X., Moreno, J. I., & Berrocal, J. (2023). 基于本体的实时风险管理与网络态势感知方法. Future Generation Computer Systems, 141, 462–472.

[39] Dog, S. E., Tweed, A., Rouse, L., Chu, B., Qi, D., Hu, Y., ... & Al-Shaer, E. (2016). 战略性网络威胁情报共享：IDS 日志案例研究. In 2016 25th International Conference on Computer Communication and Networks (ICCCN), Hawaii, USA, 1–4 August 2016, 1–6.

[40] Dondio, P., & Longo, L. (2014). 将信任计算作为一种推定推理形式. In 2014 IEEE/WIC/ACM International Joint Conferences on Web Intelligence (WI) and Intelligent Agent Technologies (IAT), 26–29 October 2014, Venice, Italy, 274–281.

## 利用区块链进行水印
### 综述

Om Prakash Singh
印度信息技术学院 Bhagalpur 分校，印度

Kedar Nath Singh
Jaypee Institute of Information Technology, Noida UP, India

Amit Kumar Singh
NIT Patna, Patna, India

Amrit Kumar Agrawal
Sharda University, Greater Noida, India

## 10.1 INTRODUCTION

随着计算机和通信技术的快速发展，可以通过公共网络共享多媒体数据用于医疗诊断、研究与开发、国防、商业分析等[1]。图像比其他媒体数据提供更关键的信息，使其成为首选的内容格式。不幸的是，图像隐私信息泄露和版权侵权已成为一个根本性问题[2]。因此，我们迫切需要找到保护多媒体数据，特别是图像形式的解决方案。数字水印是实现图像数据安全的一种很有前景的方法。水印以显著的不可见性和鲁棒性将特定消息——即水印——嵌入到载体媒体中[3]。通过从标记媒体中提取嵌入的消息，我们可以验证媒体的所有权。在这种情况下，标记媒体在消息恢复前可能受到攻击；水印系统应能抵抗攻击以实现可靠的所有权验证。嵌入和提取过程的基本概念概述在图 10.1 中。

鲁棒性、不可见性和容量是水印系统的基本要求。然而，同时在任何通用水印系统的基本要求上获得令人满意的性能并不容易。虽然安全性和复杂性同样重要，但在水印系统的三个基本要求之外实现它们具有挑战性[4]。水印要求权衡图示于图 10.2。

![](img/6e4271af21d9a195003ab8711aa79d27_213_0.png)

图 10.1 通用水印概念。

![](img/6e4271af21d9a195003ab8711aa79d27_213_1.png)

图 10.2 水印系统权衡属性。

水印系统的所有三个属性相互矛盾，因此保持平衡是一项具有挑战性的任务。

利用区块链（BC）概念最近被用作媒体文档额外安全性和隐私性的一个层面，具有各种应用[5]。BC 技术的优势包括去中心化、可追溯性、防篡改状态、透明度、可扩展性和不可变性，可解决媒体数据的 f安全挑战[6–7]。每个记录包含存储在 BC 环境中的哈希值，有助于增强媒体应用方面的更好安全性。当前一代 BC 系统已广泛应用于工业 4.0、加密货币、物联网（IoT）、信息安全、数据溯源、5G 无线网络、医疗保健和金融行业等各种应用[8–10]。根据市场分析报告，BC 技术全球市场价值在 2022 年为 100.2 亿美元。预计 BC 技术将从 2023 年到 2030 年以 87.7% 的年增长率超过 2022 年[11]。2022 年，全球市场报告[12]强调 BC 技术显著改善了制药行业。新兴 BC 技术的初始阶段及其发展如图 10.3 所示。

这一第一代 BC 技术为公共渠道设计和开发，被称为 Blockchain 1.0。在 BC 技术的初始阶段，比特币和加密货币是确保交易安全的两种最受欢迎的加密货币[13]。2013 年，引入了 BC 系统的第二阶段（Blockchain 2.0），采用智能合约来解决参与者之间的相互信任和用户身份问题[13]。然后在 BC 系统中采用了 Hyperledger 概念。它与智能合约相关联，以将交易访问限制为授权参与者[14]。

因此，利用 BC 进行水印是实现实际应用中图像安全的一种很有前景的方法。

利用 BC 技术的 watermarking 概念概述在图 10.4 中。首先，采用嵌入过程将机密信息隐藏在视觉质量可接受的多媒体对象内部。创建一个新交易以存储并上传标记图像及其哈希值到 BC 框架，以增强额外的安全性和真实性。

![](img/6e4271af21d9a195003ab8711aa79d27_214_0.png)

图 10.3 BC 系统的发展阶段。

![](img/6e4271af21d9a195003ab8711aa79d27_215_0.png)

图 10.4 传统水印方案与新型 BC 技术的概念。

![](img/6e4271af21d9a195003ab8711aa79d27_216_0.png)

图 10.5 BC 系统三大主要属性之间的关系。

最后，采用一种过程来提取机密信息用于医疗诊断。

图 10.5 显示了 BC 系统关键属性之间的关系。BC 系统的所有三个属性相互矛盾。因此，在 BC 开发过程中，可扩展性、安全性和去中心化特性之间应存在最佳权衡[15]。

## 10.2 OUR CONTRIBUTION

考虑到水印与 BC 的结合是一个相对较新的研究领域，目前关于水印的综述主要集中在传统算法上。基于数字图像水印的现有综述很多。然而，关于数字水印与 BC 的全面综述仍然缺乏。本研究是首个利用水印与 BC 检验图像安全的综述，包括近期工作的广泛范围。本章的贡献总结如下：

- 1. 介绍水印和 BC 的背景，包括最近的应用和基本特征。
- 2. 讨论最新发展并回顾基于数字图像的水印与 BC 的现有技术。
- 3. 总结并比较文献中最新的贡献，突出重大的挑战以及未来研究方向的建议。

