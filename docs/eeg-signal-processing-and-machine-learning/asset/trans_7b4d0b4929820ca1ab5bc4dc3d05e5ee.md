

# 参考文献

69. Byers, A.L., Yaffe, K., Covinsky, K.E. 等 (2010). 老年人情绪和焦虑障碍的高发病率：国家共病调查复制。 *Archives of General Psychiatry* 67 (5): 489–496. [https://doi.org/10.1001/archgenpsychiatry.2010.35](https://doi.org/10.1001/archgenpsychiatry.2010.35).

70. Oathes, D.J., Ray, W.J., Yamasaki, A.S. 等 (2008). 担忧、广泛性焦虑障碍与情绪：来自 EEG gamma 频带的证据。 *Biological Psychology* 79 (2): 165–170. [https://doi.org/10.1016/j.biopsycho.2008.04.005](https://doi.org/10.1016/j.biopsycho.2008.04.005).

71. Giannakakis, G., Grigoriadis, D., and Tsiknakis, M. (2015). 观看视频期间基于 EEG 特征的压力/焦虑状态检测。 *Proceedings of the Engineering in Medicine and Biology Conference. EMBC*.

72. Lee, S., Lee, T., Yang, T. 等 (2018). 驾驶过程中环境事件诱发焦虑的神经相关性。 *Proceedings of TENCON 2018–2018 IEEE Region 10 Conference*, Jeju, Korea (28–31 October 2018).

73. Li, Z., Wu, X., Xu, X. 等 (2019). 基于脑电图的多级焦虑识别。 *IEEE Transactions on Affective Computing*. Preprint 1–1, 12p. [https://www.doi.org/10.1109/TAFFC.2019.2936198](https://www.doi.org/10.1109/TAFFC.2019.2936198).

74. Zhang, X., Pan, J., Shen, J. 等 (2020). 基于组稀疏典型相关分析融合脑电图和眼动进行焦虑检测。 *IEEE Transactions on Affective Computing*. 2981440. [https://www.doi.org/10.1109/TAFFC.2020](https://www.doi.org/10.1109/TAFFC.2020).

75. Wang, Y., McCane, B., McNaughton, N. 等 (2019). AnxietyDecoder：一种基于 3-D 卷积神经网络的 EEG 焦虑预测器。 *International Joint Conference on Neural Networks*, 14–19. Budapest, Hungary: IJCNN.

76. Agnew, H.W., Webb, W.B., and Williams, R.L. (1966). 首夜效应：一项睡眠 EEG 研究。 *Psychophysiology* 2: 263–266.

77. Sanei, S., Jarchi, D., and Constantinides, A.G. (2020). *Body Sensor Networking, Design and Algorithms*. Wiley.

78. Angelova, M., Karmakar, C., ZHU, Y. 等 (2020). 利用多夜活动记录数据检测急性失眠的自动化方法。 *IEEE Access* 8: 74413.

79. Shahin, M., Ahmed, B., Tmar‐Ben Hamida, S. 等 (2017). 深度学习与失眠：辅助临床医生进行诊断。 *IEEE Journal of Biomedical and Health Informatics* 21 (6): 1546–1553.

80. Mulaffer, L., Shahin, M., Glos, M. 等 (2017). 临床诊断技术的两种失眠检测模型比较。 *2017 39th Annual International Conference of the IEEE Engineering in Medicine and Biology Society (EMBC)*, South Korea.

81. Holt, N.J. (2020). 类精神分裂症。见：*Encyclopedia of Creativity, 3e* (eds. M. Runco, S. Pritzker and R. Reiter‐Palmon), 452–459. Academic Press.

82. Raine, A. (1991). SPQ：一种基于 DSM‐III‐R 标准评估类精神分裂人格的量表。 *Schizophrenia Bulletin* 17: 555–564.

83. Wolff, M. (1996). 类精神分裂人格问卷 (SPQ) 德语版的心理测量学特性。硕士论文。Humboldt University, Berlin.

84. Ettinger, U., Mohr, C., Gooding, D.C. 等 (2015). 类精神分裂症中的认知与脑功能：选择性综述。 *Schizophrenia Bulletin* 41 suppl. no. 2: S417–S426.

85. Mientus, S., Gallinat, J., Wuebben, Y. 等 (2002). 通过低分辨率电磁断层扫描 (LORETA) 揭示的静息状态 EEG 中精神分裂症患者而非抑郁症患者和类精神分裂症受试者的皮层低激活。 *Psychiatry Research Neuroimaging* 116: 95–111.

# 17 利用 EEG 的脑机接口

## 17.1 简介

我们的运动意图往往能毫不费力地转化为行动，这常被视为理所当然。运动功能的丧失可能是神经系统疾病或损伤最毁灭性的后果之一。过去三十年间脑机接口 (BCI) 的发展，使得利用人类神经系统的电活动（如脑电图，EEG）与计算机和人工假体等外部设备进行通信或控制成为可能。然而，这些人工接口的性能很少能媲美自然肢体运动的速度和准确性，这使得它们的临床应用相当有限。因此，其实用性不仅取决于患者学习操作这些设备的程度，还取决于能够高效解码运动意图的实时算法（不一定复杂）的进步。在传统的 BCI 设置中，用户被指示想象不同身体部位的运动（例如右手或腿部运动），而计算机学习识别同时记录的 EEG 活动的不同模式。在大多数情况下，EEG-based BCI 系统进步的信号处理工作重点在于从 EEG 中提取更多信息量的特征，以及特征空间的细化/降维。机器学习的最新发展不仅能够识别运动，还能建模从思维到行动的神经通路。因此，机器学习已成为解决许多 BCI 问题的核心。此外，BCI 应用正越来越多地扩展到人类使用中，特别是用于康复目的。

肌电图 (EMG) 测量主要用于康复以及各种机器人和触觉工具及机器的开发。因此，EMG 仍然是连接人与机器最流行和有效的方法。EMG-based 接口的新发展源于更灵敏的表面电极阵列以及神经植入物的可用性。尽管如此，假肢要替代完全截肢的手臂或腿仍面临重大挑战。

BCI（也称为脑机接口 [BMI]）是一个具有挑战性的问题，属于更广泛的研究领域——人机交互 (HCI) 的一部分，后者将思维与行动联系起来。BCI 潜在地提供了一种无需任何物理接触即可连接大脑与物理世界的链路。在 BCI 系统中，用户的消息或指令不依赖于大脑的正常输出通道 [[1]](#c17.xhtml#c17-bib-0001)。因此，BCI 的主要目标是操控大脑神经元产生的电信号，并产生控制某些外部系统（设备、假体或人工手臂/肢体）所需的信号。最重要的应用是激活瘫痪的器官或绕过人体残疾部位。然而，当前的 BCI 系统也有助于检查人类认知系统（如记忆）的运作。相反，BCI 系统可能成为严重神经肌肉疾病患者（如脊髓损伤、肌萎缩侧索硬化症、中风和脑瘫）的唯一交流模式。

在发现大脑电活动约一百年后，Vidal [[2](#c17.xhtml#c17-bib-0002), [3](#c17.xhtml#c17-bib-0003)] 于 1973–1977 年期间首次报道了 BCI 研究。他的研究展示了如何利用脑信号构建精神假体。自 1999 年首次实验演示表明皮层神经元集合可直接控制机械臂 [[4]](#c17.xhtml#c17-bib-0004) 以来，BCI 以惊人的速度发展。从那时起，该领域已有大量研究 [[5]](#c17.xhtml#c17-bib-0005)，而在实践中，EMG 仍然更适用且商业化程度更高。

