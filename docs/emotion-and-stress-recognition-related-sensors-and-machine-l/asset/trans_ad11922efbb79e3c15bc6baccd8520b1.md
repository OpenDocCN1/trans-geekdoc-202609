
## 沉浸式虚拟现实中的情绪识别：从静态到情感计算

**哈维尔·马林-莫拉莱斯** (Javier Marin-Morales)，\*，**卡门·利纳雷斯** (Carmen Llinares)，**海梅·吉克拉斯** (Jaime Guiqueras) 和 **马里亚诺·阿尔卡伊** (Mariano Alcaiz)

*瓦伦西亚理工大学生物医学工程研究与创新研究所，西班牙瓦伦西亚 46022；clinear@mnp.upv.es (C.L.)；jaiguip@i3b.upv.es (J.G.)；malcaniz@i3b.upv.es (M.A)
\* 通讯作者：jamarnol@i3b.upv.es*

**收稿日期：** 2020年7月23日；**修回日期：** 2020年9月8日；**发表日期：** 2020年9月10日

**摘要：** 情绪在我们的日常生活中扮演着关键角色，因此，理解和识别情绪对于人类健康至关重要。情感计算研究大多使用非沉浸式的二维 (2D) 图片或视频来诱发情绪状态。然而，沉浸式虚拟现实允许研究人员在受控的实验室条件下模拟具有高度临场感和交互性的环境，因此在情绪研究中更为普及。它与隐性测量方法和机器学习技术的协同作用具有横向影响许多研究领域潜力，为科学界开辟了新机遇。本文对使用头戴式显示器作为诱发设备，并通过生理和行为指标进行的情绪识别研究进行了系统性回顾。研究结果强调了该领域的演变，通过聚合分析提供了清晰的视角，揭示了当前存在的问题，并为未来研究提供了指导原则。

**关键词：** 情感计算；情绪识别；情绪诱发；虚拟现实；头戴式显示器；机器学习

情绪在决策、学习以及多种影响人类生理和心理状态的其他方面起着至关重要的作用 [1]。因此，理解和识别情绪是人类行为的重要方面。为了研究人类情绪，需要在实验环境中诱发情感状态，使用诸如音频、视频以及最近的虚拟现实 (VR) 等诱发方法。近年来，VR 在科学和商业环境中的 popularity 有所增加 [2]。其应用包括培训、教育、医疗和营销。这基于新一代低成本头戴式设备的发展，促进了头戴式显示器 (HMDs) 的全球购买。尽管如此，VR 自 1990 年代以来已被用于研究 [4]。对 VR 的科学兴趣源于它提供模拟体验，营造出置身于现实世界的错觉 [5]。特别是，环境模拟是物理环境的表示，允许研究人员分析概念 [6]。当描绘无法在物理上呈现的事物时，这一点尤为重要。VR 使得在受控环境中研究这些场景成为可能 [7]。VR 允许以省时且经济高效的方式隔离和修改变量，而在真实空间中则无法做到这一点 [8]。

显示 VR 模拟的配置随着相关技术的演变，已逐渐集成到研究中。每个配置由三种客观特征的组合组成：格式、显示设备和用户界面。

格式描述了显示的沉浸结构。最常见的是二维 (2D) 多媒体和三维 (3D) 环境，它们之间的主要区别在于其交互级别 [9]。包括 360° 全景图片和视频的 2D 多媒体提供非交互式的视觉表示。这种格式的有效性已被广泛探索 [10]。此外，计算机生成图像的最新进展模拟了光线、纹理和大气条件，达到了如此程度的照片级真实感，以至于产生的虚拟图像在肉眼看来与真实世界场景的照片无法区分 [11]。这种格式允许在实验室中便宜且快速地测试静态的计算机生成环境，并带有许多变化。另一方面，3D 环境生成交互式表示，允许改变用户的视角、导航，甚至与物体和人互动 [12]。开发逼真的 3D 环境比开发 360° 计算机生成照片耗时更多，且其真实度受硬件性能限制。此外，GPU（图形处理器）的处理能力逐年增加，这将增强 3D 环境的性能容量。此外，便于执行真实任务（real-tasks）是虚拟现实应用的一个关键方面 [2]。

显示设备是用于可视化格式的技术设备。它们根据提供的沉浸级别进行分类，即它们支持的感观运动依赖关系。这与受试者在感知中执行的动作有关；例如，当他们移动头部位置，向下或向前移动以接触物体时（例如，转头，弯腰），由系统支持的一系列虚拟动作中的每一个在虚拟环境中的感知中都会带来特定的携带效果 [13]。由于沉浸是客观的，如果一个系统在一个特征上优于其他系统，而其他特征保持不变，则一个系统比另一个系统更具沉浸感。非沉浸式系统使用屏幕，如台式 PC，来显示环境 [14]。半沉浸式系统，如计算机生成的自动虚拟环境 (CAVE) 或基于运动的系统，使用大型投影在墙上显示环境，包围观看者 [15, 16]。这些显示器提供环境的立体图像，其透视投影与观察者头部的位置相关联。沉浸式设备，如 HDMDs，是全沉浸式系统，使用立体视图，并响应用户的动作。

沉浸分为三种类别：非沉浸式、半沉浸式和全沉浸式。

用户界面，这是 3D 环境独有的允许此级别交互的功能，是用户与 VR 环境之间的功能连接，允许他或她与物体交互并进行导航 [20]。关于与物体的交互，任务包括：选择（即识别一个物体或物体子集）、定位（即改变用户的 3D 位置）、旋转（即物体的 3D 朝向）。在 3D 环境中导航方法方面，虚拟移动（virtual locomotion）已被分析 [22]，并可归类为物理或人工。关于物理方法，有基于房间的方法，如真实步行，允许用户在有限的物理空间内自由行走。这些通常与 HDMDs 一起使用，位置和方向由用户头部的位置确定。然而，这些方法中最自然的一种受到有限区域的限制 [23]。此外，还有一种在伪自然主义隐喻中步行的方式，其中用户通过执行虚拟移动来导航，例如，像行走一样移动手/手臂，或执行类似步足的动作，同时保持静止。重定向行走（Redirected walking）是一种技术，用户感知自己在自由行走，但实际上是无意识地被虚拟环境操纵。

### 参考文献

1.  Udovičić, G.; Derek, J.; Russo, M.; Sikora, M. Wearable Emotion Recognition System on GSR and PPG. In Proceedings of the 21st International Workshop on Multimedia for Personal Health and Health Care, Mountain View, CA, USA, 23–27 October 2017; pp. 53–59. [CrossRef]
2.  Liu, M.; Fan, D.; Zhang, G.; Xu, H. Emotion Recognition Based on Galvanic Skin Response Feature Selection and SVM. In Proceedings of the 2016 International Conference on Smart City and Systems Engineering, Wuhan, China, 25–26 November 2016: 157–160. [CrossRef]
3.  Wei, J.; Jia, Q.; Yong, F.; Chen, G. Emotion Recognition Based on Weighted Fusion of Physiological Signals. Comput. Sens. Neurosci. 2018, 1–9. [CrossRef][PubMed]
4.  Chen, J.; Hu, B.; Ma, L.; Moore, P.; Yi. Feature-level fusion of multimodal physiological signals for emotion recognition. In Proceedings of the International Conference on Bioinformatics and Biomedicine (BIBM), Washington, DC, USA, November 9–12, 2011: pp. 395–399. [CrossRef]
5.  Canento, F.; Berg, F.; Silva, A.; Silva, M.; Gao, H.; Lorenzo, Y. Multimodal biosensor fusion for emotion recognition. In Proceedings of the 2011 IEEE Sensors Conference, Limerick, Ireland, 28–31 October 2011: pp. 47–52. [CrossRef]
6.  Xu, J.; Xu, X. WT Based Emotion Recognition from Multi-channel Physiological Signals with Decision Fusion. In Proceedings of the IEEE Conference on Affective Computing and Intelligent Intelligence, Beijing, China, May 2018: pp.20–22.
7.  Subramanian, R.; Wache, J.; Abdi, M.; Viktor, R.L.; Winkler, S.; Sebe, N. ASCERTAIN: Emotion and Personality Recognition Using Convolution. IEEE Trans. Affect. Comput. 2018, 9, 147–160. [CrossRef]
8.  Aguelta, A. A.; Brena, R.F.; Mayor, O.; Moreno-Rero, E.; Trejo, L.A. Multi-Sensor Fusion for Activity Recognition—A Survey. Sensors 2019, 19, 3880. [PubMed]
9.  Egger, E. M.; Lage, H.; Chen, P.; Nichele, S. Emotion Recognition from Physiological Signals: A Review. Electron Notes. Comput. Sci. 2019, 43, 35–55. [CrossRef]
10. Duma, V.; Pirosz, J. A comprehensive analysis of machine learning methods for emotion recognition using EEG and physiological signals. Data, 2020, 7, 188.
11. Dzieidzic, A.; Kalaskiewicz, J.; Vman, M. Human Emotion Recognition: Review of Sensors and Methods. Sensors 2020, 20, 592. [CrossRef]
12. Marechak, C.; Majtkowski, D.; Turek, K.; Prokopowicz, P.; Bouguerau, L.; Ancient, C.; Wegzyn-Walski, M. High-Performance Modeling and Simulation for Big Data Applications: Selected Results of the COST Action 2140 chip;Springer International Publishing: Cham, Switzerland, 2019; pp. 307–324. [CrossRef]
13. Zhang, J.; Yin, Z.; Chen, P.; Nicole. Emotion recognition using multi-modal data and machine learning techniques: A tutorial and review. Inf. Fusion. 2020, 39, 103–126. [CrossRef]
14. Pedosa, F.; Varoquaux, G.; Gramfort, A.; Michel, V.; Theron, B.; Grisel, O.; Prettenhofer, P.; Weiss, R.; Daubour, V.; et al. Scikit-learn: Machine learning in Python. J. Mach. Learn. 2011, 12, 2825–2830.
15. Da Silva, H.P.; Ferreira, F.A.; Martins, R.. Emotion Recognition. IEEE Predictive Comput. 2014, 13, 64–71. [CrossRef]
16. Alves, A.P.; da Silva, H.; Lorenzo, A.; Ferreira, B.A. Binal Acquisition System on Arduino. In Proceedings of the International Conference on Biomedical Engineering and Devices (BIOMEDVICES), Barcelona, Spain, 11–14 February 2013.
17. Soleymani, M.; Lichtenauer, J.; Pant, T.; Tantic, I. A Multimodal Database for Affect Recognition and Implicit Tagging. IEEE Trans. Affect. Comput. 2012, 3, 42–55. [CrossRef]
18. Wiem, M.; Lachni, Z. Emotion Classification in Arousal Valence Model using MAHNOB-HCI Database. Int. J. Adv. Comput. Sci. 2017, 8. [CrossRef]

![](img/601340ca744b738277eef45ff127492a_473_0.png)

![](img/601340ca744b738277eef45ff127492a_475_0.png)

![](img/601340ca744b738277eef45ff127492a_475_1.png)
