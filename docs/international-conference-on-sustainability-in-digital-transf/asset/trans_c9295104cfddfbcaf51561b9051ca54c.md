
Multi-SVM（支持向量机）和 K-means 聚类被选为论文中作物选择模块的两种技术（表 59.1）。所建议的方法使用 K-means 聚类和 multi-SVM 根据土壤检测结果进行作物选择。K-means 和 multi-SVM 算法基于数据集的分类创建聚类。在论文中，提出了 multi-SVM 与 K-means 算法之间的联系。Multi-SVM 的实现比 K-means 稍微具有挑战性，但提供了更好的准确性。Multi-SVM 的准确率为 80%，而 K-means 聚类的准确率为 62%。使用 multi-SVM 算法时，更大的数据库比微小的数据库表现更好。

## References
1.  [Arnal Barbedo, J. G.](#ch58.xhtml#R_ref58_1) (2019). 利用深度学习从单个病变和斑点进行植物病害识别。Biosystems Engineering, 180(2016), 96–107.
2.  [Chaturvedi, R., Islam, A., Singh, P. K., and Saraswat, M.](#ch58.xhtml#R_ref58_2) (202). 纳米技术用于先进能源系统：纳米燃料的合成与性能表征。In AIP Conference Proceedings (Vol. 2721, No. 1). AIP Publishing.
3.  [Ashqar, B., and Abu-Naser, S.](#ch58.xhtml#R_ref58_3) (2018). 基于图像的番茄叶片病害检测使用深度学习。International Journal of Advanced Engineering Research (IJAER), 2(12), 10–16.
4.  [Kumar, P., Singh, P. K., Nagar, S., Sharma, K., and Saraswat, M.](#ch58.xhtml#R_ref58_4) (2021). 功能化石墨烯不同浓度对热能存储系统充电时间减少的影响。Materials Today: Proceedings, 44, 146–152.
5.  [Agrawal, R.](#ch58.xhtml#R_ref58_5), (2022). 低功耗 SRAM 存储器架构用于物联网系统。In Recent Advances in Manufacturing, Automation, Design and Energy Technologies, (pp. 505–512). Singapore: Springer.
6.  [Bansal, S., and Tomar, V. K.](#ch58.xhtml#R_ref58_6) (2022). 物联网中的挑战与安全威胁及解决方案架构。In 2022 2nd International Conference on Power Electronics & IoT Applications in Renewable Energy and its Control (PARC). IEEE, 2022.
7.  [Chaturvedi, R., Sharma, A., Sharma, K., and Saraswat, M.](#ch58.xhtml#R_ref58_7) (2022). 多壁碳纳米管增强 AA 7075 纳米复合材料的摩擦学行为。Advances in Materials and Processing Technologies, 8(4), 4743–4755.
8.  [Periyannan, S., Milne, R. J., Figueroa, M., Lagudah, E. S., and Dodds, P. N.](#ch58.xhtml#R_ref58_8) (2017). 遗传锈病抗性的概述：从广谱到特异性机制。PLoS Pathogens, 13, e1006380.
9.  [Azadbakht, M., Ashourloo, D., Aghighi, H., Radiom, S., and Alimohammadi, A.](#ch58.xhtml#R_ref58_9) (2019). 小麦叶锈病在不同 LAI 水平下的冠层尺度检测使用机器学习技术。Computers and Electronics in Agriculture, 156(September 2018), 119–128.
10.  [Sharma, A., Chaturvedi, R., Sharma, K., and Saraswat, M.](#ch58.xhtml#R_ref58_10) (2022). 基于响应面法的铝毛刺复合材料铣削中的力评估和加工参数优化。Advances in Materials and Processing Technologies, 8(4), 4073–4094.
11.  [Dodds, P. N., and Lagudah, E. S.](#ch58.xhtml#R_ref58_11) (2016). 饿死敌人。Science, 354, 1377–1378.
12.  [Bashir, K., Rehman, M., and Bari, M.](#ch58.xhtml#R_ref58_12) (2019). 水稻病害的检测与分类：一种使用纹理特征的自动化方法。Mehran University Research Journal Science and Technology, 38(1), 239–250.
13.  [Bai, X., Li, X., Fu, Z., Lv, X., and Zhang, L.](#ch58.xhtml#R_ref58_13) (2017). 一种基于邻域灰度信息的模糊聚类分割方法用于定义黄瓜叶斑病图像。Computers and Electronics in Agriculture, 136, 157–165.
14.  [Ali, S., Gladieux, P., Leconte, M., Gautier, A., Justesen, A. F., Hovmøller, M. S., et al.](#ch58.xhtml#R_ref58_14) (2014). 小麦黄锈病病原菌 Puccinia striiformis f. sp. tritici 的起源、迁移路线和全球种群遗传结构。PLoS Pathogens, 10, e1003903.

# 59 物联网在智能灌溉系统 (SIS) 中的利用

Saloni Bansal^([^(58)](#fn58))

DOI: [10.1201/9781003534136-59](https://dx.doi.org/10.1201/9781003534136-59)

## Abstract
自动化目前在人类生活中发挥着重要作用。它不仅使你更舒适，而且还能节省时间和精力。现在工业使用昂贵的自动化和控制设备，这些设备不适合在农田中使用。因此，这里还设计了一种印度农民负担得起且有用的智能灌溉系统。整个系统的核心大脑是 Raspberry Pi。为了最大化农业作物灌溉水的利用率，创建了一个自动灌溉系统。得益于自动化，我们可以自动控制电器。本研究的目标是水电机的自主管理、通过网络摄像头监控植物生长以及在 Android 移动设备上实时直播农场。我们的研究旨在以两种方式减少农民的人力劳动：1) 通过防止不可预见的用水，从而防止大量水浪费。2) 农民可以通过在土壤不够湿润时仅使用灌溉来节省大量时间。阈值决定了泵何时应打开或关闭。

**关键词:** Android, 连接农场, 灌溉, raberry pi, wifi

## Introduction
印度的经济在很大程度上基于农业，该国在农产品产量方面全球排名第二。截至 2018 年，印度 17% 至 18% 的 GDP 来自农业，农业雇用了 50% 的劳动力。在印度，大多数灌溉系统是手动操作的。随着水资源变得更加稀缺，我们的国家有能力节约每一滴水 [[1](#ch59.xhtml#ref59_1) 和 [2](#ch59.xhtml#ref59_2)]。水是灌溉系统非常重要的一部分，因此新的灌溉技术应以比过时技术使用更少水的方式实施。智能灌溉意味着除了使用更少的水外，还能按需供水。这带来了农业生产率的提高和风险降低的潜力。使用无线传感器，该系统远程监测天气条件、植物土壤条件和水库水位。虽然传统方法产生 20% 至 70% 的水浪费，但智能灌溉解决方案可将其减少高达 95%。在我们传统的耕作方法中，需要额外的劳动力来给植物浇水。最大限度地减少农民参与并将此程序转变为 an 许多传感器，例如土壤湿度传感器、温度传感器等，被用于自动化系统中，并且这些传感器的输出连接到微控制器。典型的灌溉系统的主要缺陷是在水库注水期间的水损失，过量浇水植物是另一个因素。这是出现水资源短缺的最可能情况 [[3](#ch59.xhtml#ref59_3) 和 [4](#ch59.xhtml#ref59_4)]。植物土壤湿度这一关键组成部分正被智能浇水系统监测。根据此情况，可以确定植物是否获得足够的生长用水。许多人在日常事务中忽视给植物浇水，使得保持植物的健康和生命变得困难。为了避免这些问题并创建自动灌溉系统以促进植物生长。因此，我们项目的目标是提供智能灌溉系统用于浇灌植物，同时通过消息通知客户。用户还将从本项目关于水箱水位和土壤湿度含量的信息中受益。这项研究还有助于确定环境的湿度和温度。

## Methodology
