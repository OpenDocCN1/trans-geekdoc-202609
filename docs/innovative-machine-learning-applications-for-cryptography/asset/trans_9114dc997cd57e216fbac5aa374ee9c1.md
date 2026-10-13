

# 参考文献

Tao, S., Zhang, X., Cai, H., Lv, Z., Hu, C., & Xie, H. (2018). Gait based biometric personal authentication by using MEMS inertial sensors. *Journal of Ambient Intelligence and Humanized Computing*, 9(5), 1705–1712. doi:[10.1007/s12652-018-0880-6](https://doi.org/10.1007/s12652-018-0880-6)

Thomas, E., Nair, P. B., John, S. N., & Dominic, M. (2014, July). Image fusion using Daubechies complex wavelet transform and lifting wavelet transform: a multiresolution approach. In *2014 Annual International Conference on Emerging Research Areas: Magnetics, Machines and Drives (AICERA/iCMMD)* (pp. 1-5). IEEE. doi:[10.1109/AICERA.2014.6908205](https://doi.org/10.1109/AICERA.2014.6908205)

Viswanathan, M., Loganathan, G. B., & Srinivasan, S. (2020, September). IKP based biometric authentication using artificial neural network. In *AIP Conference Proceedings* (Vol. 2271, No. 1). AIP Publishing. doi:[10.1063/5.0025229](https://doi.org/10.1063/5.0025229)

Yang, G., He, Y., Li, X., Liu, H., & Lan, T. (2022). Gabor-glcm-based texture feature extraction using flame image to predict the o2 content and no x. *ACS Omega*, 7(5), 3889–3899. doi:[10.1021/acsomega.1c03397](https://doi.org/10.1021/acsomega.1c03397)

Yuan, H., Lei, Z., You, X., Dong, Z., Zhang, H., Zhang, C., Zhao, Y., & Liu, J. (2023). Fault diagnosis of driving gear in rack and pinion drives based on multi-scale local binary pattern extraction and sparse representation. *Measurement Science & Technology*, 34(5), 055017. doi:[10.1088/1361-6501/acbab4](https://doi.org/10.1088/1361-6501/acbab4)

Zhang, X., Cheng, D., Jia, P., Dai, Y., & Xu, X. (2020). An efficient android-based multimodal biometric authentication system with face and voice. *IEEE Access : Practical Innovations, Open Solutions*, 8, 102757–102772. doi:[10.1109/ACCESS.2020.2999115](https://doi.org/10.1109/ACCESS.2020.2999115)

Zulfiqar, M., Syed, F., Khan, M. J., & Khurshid, K. (2019, July). Deep face recognition for biometric authentication. In *2019 international conference on electrical, communication, and computer engineering (ICECCE)* (pp. 1-6). IEEE.

Zulkurnain, N. F., Azhar, M. A., & Mallik, M. A. (2022, February). Content-Based Image Retrieval System Using Fuzzy Colour and Local Binary Pattern with Apache Lucene. In *Proceedings of Second International Conference on Advances in Computer Engineering and Communication Systems: ICACECS 2021* (pp. 13-20). Singapore: Springer Nature Singapore. doi:[10.1007/978-981-16-7389-4_2](https://doi.org/10.1007/978-981-16-7389-4_2)

# 第12章

- **S. Metilda Florence**  
  SRM Institute of Science and Technology, India
- **Akshay Raghava**  
  SRM Institute of Science and Technology, India
- **M. J. Yadhu Krishna**  
  SRM Institute of Science and Technology, India
- **Shreya Sinha**  
  SRM Institute of Science and Technology, India
- **Kavya Pasagada**  
  SRM Institute of Science and Technology, India
- **Tanuja Kharol**  
  SRM Institute of Science and Technology, India

## 摘要

加密勒索软件呈现不断增长的威胁，它加密受害者数据并索要赎金以换取解密。勒索软件攻击频率的增加凸显了对先进检测技术的需求。本文提出了一种机器学习分类模型来识别勒索软件家族。这些模型利用特定的网络流量特征，特别强调分析`用户数据报协议（UDP）`和`互联网控制消息协议（ICMP）`。重要的是，这种方法结合了特征选择以提高效率而不牺牲准确性，从而减少了内存使用并加快了处理时间。所提实验利用各种机器学习算法，包括`决策树`和`随机森林`，创建高度准确的模型以对勒索软件家族进行分类。此外，实验将网络流量分析与其他复杂方法（如行为分析和蜜罐部署）相结合，以有效扩展加密勒索软件检测。

## 1 简介

加密勒索软件是一种加密文件的恶意软件，要求以加密货币支付赎金以换取解密。它通过网络钓鱼、利用漏洞传播。攻击者青睐加密货币因其匿名性。预防涉及更新、网络安全措施、备份和用户教育。事件响应计划有助于从这些日益复杂的网络威胁中恢复。

加密勒索软件通常依赖传统通信协议，如`HTTP`或`HTTPS`（Krzysztof Cabaj, Marcin Gregorczyk, and Wojciech Mazurczyk, 2018）进行命令与控制（C2）通信，而非`UDP`或`ICMP`。然而，网络威胁在演变，攻击者可能尝试不同协议。May Almousa, Janet Osawere, and Mohd Anwar (2021) 的一项研究利用`TCP`数据包分析来检测加密勒索软件。`TCP`作为网络通信中的基础协议；然而，其在加密勒索软件检测背景下的应用存在固有局限性。一个重大挑战在于加密流量的普遍性，这是现代勒索软件变体常用的战术。加密用于保护通信安全，使得检测机制难以检查数据包内容。因此，在加密的`TCP`数据包中识别恶意行为变得越来越困难。

此外，勒索软件开发者常利用`TCP`通信的动态性。诸如端口跳跃等技术，即勒索软件在不同网络端口间快速切换，因此给基于`TCP`的检测系统带来困难。这些机制适应快速变化的通信模式和端口号的能力，成为对抗复杂勒索软件变体规避战术的关键考量。

采用强大的网络安全、监控和定期更新有助于缓解与勒索软件战术潜在变化相关的风险。攻击者可能利用`UDP`用于特定目的，如命令与控制通信或数据渗出，但其普及程度不如`TCP`。

攻击者可能因`ICMP`存在于许多网络中且可能绕过某些防火墙规则，而滥用其进行特定功能。

### 1.1 本章贡献

本章组织为若干节，旨在通过整合非常规网络协议和机器学习算法，提供对增强加密勒索软件检测所提架构的全面理解。结构化方法确保清晰度，并促进对研究方法和发现的循序渐进探索。

论文第一节阐述了所提架构的基础阶段。这涉及加密勒索软件网络流量数据的细致收集，这是构建用于分析的稳健数据集的关键步骤。所选网络协议`UDP`和`ICMP`作为特征提取和选择的焦点，旨在捕捉指示恶意活动的独特模式。通过隔离相关数据包字段，研究为有效的数据处理及其在机器学习算法中的后续利用建立了框架。

后续节深入探讨特征提取和选择的复杂性，阐述选择`UDP`和`ICMP`数据包特定字段的基本原理。该过程在从海量网络流量数据中提炼相关信息方面至关重要，有助于识别与加密勒索软件相关的独特特征。详细阐述了特征选择背后的基本原理，提供了指导这一研究关键方面的考量见解。

