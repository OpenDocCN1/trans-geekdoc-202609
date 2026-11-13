
46.  [Singh, A. P., Pradhan, N. R., Luhach, A. K., Agnihotri, S., Jhanjhi, N. Z., Verma, S.](#ch4.xhtml#R_ref4_46), … & Roy, D. S. (2020). 一种面向区块链医疗应用的新型以患者为中心的架构框架。IEEE Transactions on Industrial Informatics, *17*(8), 5779–5789. [https://ieeexplore.ieee.org/abstract/document/9259231](https://ieeexplore.ieee.org/abstract/document/9259231)

47.  [Kumar, M. S., Vimal, S., Jhanjhi, N. Z., Dhanabalan, S. S., & Alhumyani, H. A.](#ch4.xhtml#R_ref4_47) (2021). 基于区块链的自主无人机操作中的点对点通信。Energy Reports, *7*, 7925–7939. [https://expert.taylors.edu.my/file/rems/publication/109566_6018_1.pdf](https://expert.taylors.edu.my)

48.  [Kumar, M. S., Vimal, S., Jhanjhi, N. Z., Dhanabalan, S. S., & Alhumyani, H. A.](#ch4.xhtml#R_ref4_48) (2021). 基于区块链的自主无人机操作中的点对点通信。Energy Reports, *7*, 7925–7939. [https://www.sciencedirect.com/science/article/pii/S2352484721006752](https://www.sciencedirect.com)

49.  [Rajmohan, R., Kumar, T. A., Pavithra, M., Sandhya, S. G., Julie, E. G., Nayahi, J. J. V., & Jhanjhi, N. Z.](#ch4.xhtml#R_ref4_49) (2020). Blockchain: Industry 4.0 的下一代技术。Blockchain Technology, 177–198. [https://www.researchgate.net/profile/T-Ananth-Kumar/publication/346792929_Blockchain_Technology/links/601a0281a6fdcc37a8fc1ef5/Blockchain-Technology.pdf](https://www.researchgate.net)

# 5 用于在智能医疗领域实现分类脑电图（EEG）信号的安全物联网协议

S. Saravanan

SASTRA (Deemed to be University), Kumbakonam, India

M. Lavanya

SASTRA (Deemed to be University), Thanjavur, India

Chandra Mouli Venkata Srinivas

BVC Engineering College, Odalarevu, India

M. Arunadevi

Cambridge Institute of Technology, Bangalore, India

N. Arulkumar

CHRIST (Deemed to be University), Bangalore, India

DOI: [10.1201/9781003203087-5](https://dx.doi.org/10.1201/9781003203087-5)

## 5.1 引言

当今技术聚焦于工业4.0革命，在智能自动化、可信信息存储、海量数据处理、大规模生产处理和安全医疗等领域寄予厚望。特别是在医疗保健领域，工业4.0革命侧重于大规模数据处理、数字化、诊断、监测、安全数据传输以及患者与护理人员之间的可信通信。该工业4.0集成了多种技术，如物联网（IoT）、人工智能（AI）、机器对机器（M2M）通信、云计算和存储、数据分析以及安全数据传输 \[[1](#ch5.xhtml#ref5_1)\]。该框架有助于开发更好的医疗保健系统，了解患者的问题和康复方法。

本章聚焦于脑电图（EEG）信号，其涉及生物医学、生物工程、神经科学和脑科学等多个研究领域。它通过各种电极测量膜电位和神经元强度。这些信号有助于分析癫痫发作检测、肌肉无力、身体昏迷状态、脑死亡、无创性、中风和睡眠障碍。EEG信号通过头皮上的各种电极接收以测量脑活动。头皮上电极的位置遵循国际10–20标准系统。所有EEG信号均处于模拟域，需要由ADC（模数转换器）进行采样。接收到的EEG信号被分为delta、theta、alpha、beta和gamma频率。根据低频到高频的范围，它指示患者状况从放松模式（睡眠）到严重模式（脑死亡）。EEG信号的主要优势是支持高时间分辨率以及低成本设备。

EEG信号是生物信息的重要组成部分，在远程医疗系统中发挥着至关重要的作用。患者数量增加而临床设施不足的需要使远程医疗成为不可避免的技术。远程医疗承诺以较低成本提供改善的医疗质量。该技术更舒适且可适应物联网，为健康信息提供合适的解决方案。

物联网的基本结构在于将互联网扩展到嵌入式系统和智能移动设备之外。预计到2025年，超过700亿个物（设备）将连接到互联网连接，产生79.4泽字节（ZB）的信息。基于物联网的技术通过为健康监测服务提供兼容支持，改变了远程医疗的领域。在当前情况下，基于物联网的远程医疗技术具有很多偏好，被认为是新兴技术之一。该技术有助于通过各种生物传感器接收人体信号以进行观察、监测和诊断。它集成了各种设备，如传感器、执行器和通信协议以及互联网连接，以支持与医疗保健相关的问题。有了这项技术，患者无需为了解自己的健康问题而去医院进行体检。他们可以通过远程物联网环境从医生那里获得所有医疗支持和治疗。这种方法有助于更高效的流程和更好的舒适度，并为健康信息提供合适的解决方案。该系统还具有隐私保障、成本效益、易于访问和改善医疗质量等各种优势。

研究人员和开发人员提出了各种物联网架构以满足应用需求。基本物联网架构被认为是三层 \[[2](#ch5.xhtml#ref5_2),[3](#ch5.xhtml#ref5_3)\]。它们是感知层（底层）、网络层（中间层）和应用层（顶层）。在底层，所有实时生物信号在各种传感器的帮助下收集。在中间层，它将传感器数据与各种网关设备和通信协议连接。该中间层还以低功耗提高了生物信号的效率。在顶层，个性化生物信号与用户应用程序和安全参数集成。

中间物联网架构包含四层结构，在三层物联网架构中加入了支持层。第四层有助于安全和身份验证目的。它主要用于确认安全数据以及可信用户和受保护的连接。该层还检查拒绝服务（DoS）攻击和恶意攻击 \[[4](#ch5.xhtml#ref5_4)\]。高级物联网架构包含五层，加入了处理层和业务层。在处理层，它支持消除不必要数据或额外数据。该层还影响耗尽和恶意软件攻击。在业务层，它充当整体应用程序的管理者，并负责控制和管理特定应用程序。它也容易受到业务逻辑攻击 \[[5](#ch5.xhtml#ref5_5)\]和零日攻击。

基于物联网的环境接收实时EEG信号并通过基于机器学习的分类算法进行处理。它有助于更好地过滤不需要的生物信息并提供所需信息。数据过滤过程有各种分类算法。本章聚焦于支持向量机（SVM）分类算法。该算法基本上以学习统计理论和为两类线性方法提供更好解决方案而闻名。EEG信号与头痛、无力、瘫痪、眼动不良和癫痫等症状监测密切相关。
