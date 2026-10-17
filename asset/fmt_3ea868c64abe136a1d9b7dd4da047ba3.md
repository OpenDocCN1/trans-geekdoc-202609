
# 临床试验参与者管理与机器学习应用

临床试验参与者的管理包括患者或受影响人群的偏好、患者招募和参与者留存。遗憾的是，患者的退出和不合规通常会导致研究变得不可接受，尽管在管理参与者方面通常投入了大量的资源，包括研究协调员的时间、规划和精力。这往往超过了时间和成本，或者未能产生可用的数据。事实上，33.6% 到 52.4% 的 1-3 期临床药物在开发过程中没有进入下一阶段，而且 1 期研究药物总体有 13.8% 的概率获得批准。机器学习方法允许我们更高效、公平地识别、招募和留存参与者 [16]。

科学领域机器学习的使用可以改变事实系列和所需的评估策略。因此，机器学习策略可以帮助解决许多与缺乏事实和积累全球事实相关的问题。来自可穿戴设备和不同手机/数字设备的患者生成的健身事实在某些情况下可以补充或可能更新对访问及其相关的传统现实事实系列的观察。可穿戴设备和不同设备可能还允许使用新的、关注患者的扩展。通过借助使用手机设备的多个传感器（包括摄像头、音频录音机、加速度计和光电脉搏波记录法）收集的事实来扩展新的“虚拟生物标志物”，经常需要 `ML` 处理以获得相关的见解，因为来自这些设备的事实可能稀疏，并且在质量、易访问性和同时性方面存在差异。

通过使用极大且复杂的数据，借助可穿戴设备和不同设备进行研究的功能因此需要专门的事实系列、存储、验证和评估策略。例如，深度神经网络用于单导联电图平台，随机森林版本用于帕金森病患者的音频输出，循环神经网络用于特应性皮炎患者的加速度计事实。

# 神经影像与深度学习应用

神经影像是一种用于分析神经系统结构和功能的成像技术，包括大脑 [21]。随着神经系统疾病的发病率不断提高，对神经影像技术及后续数据分析的需求日益增长。已开发出各种成像技术和基于深度学习（`DL`）的分析方法，用于神经系统疾病的早期检测和适当的治疗策略 [22]。

近年来，`DL` 算法已应用于多个领域，包括图像分析、异常检测、疾病检测和自然语言处理。神经影像研究人员尝试使用深度结构化学习方法（如 `CNNs`）从 MRI 扫描中检测神经系统疾病。跨媒体方法（如数据融合）也被应用于各个领域，包括个性化服务和神经系统疾病诊断。在 `DL` 的各种架构中，研究人员主要基于 `CNN` 的方法来提取 MRI 数据。

这种 NLD（神经系统疾病）由深度神经网络（`DNN`）和自动编码器（`AE`）生成。此外，在 2015 年至 2019 年，发表的文献中，与 `AD` 相比，`PD` 或 `SZ` 的诊断引起了更多关注 [23]。

由于该领域的关注度日益增加，且分析 MRI 扫描的方法报告不断增多，我们总结认为已有文章可以从针对特定任务和数据集的不同视角出发，加速适用技术的筛选过程。有几篇综述文章总结了各种方法的进展。其中一个目标是将大数据和 `ML` 的应用整合到心理健康研究中 [24]。研究人员正在研究各种基于 `ML` 的任务，以提高神经系统疾病的诊断。他们还研究了 `DL` 在更更好地理解和诊断 `PD` 方面的应用。

已有关于结合多种医学图像（如神经、病理和肺部图像）分析的 `DL` 详尽综述 [25]。然而，任何现有的综述文章都没有很好地解释数据选择和预处理。为了填补这一空白，本工作重点关注提供 `DL` 在通过 MRI 扫描检测 `NLDs`（即阿尔茨海默病 `AD`、帕金森病 `PD`、精神分裂症 `SZ`）方面的应用概览，并进一步结合常用的开放数据集和预处理方法进行 [26]。

因此，本工作的主要目的是：

*   内容描述了用于分析 MRI 扫描以检测神经系统疾病（`NLDs`）的 `DL` 方法的几个方面。它包含引言，引用了用于从 MRI 扫描中识别异常的各种 `DL` 架构和预处理技术。该引言目的是帮助初学者理解框架并为未来提供参考。
*   内容还包括对现有研究的详细综述，这些研究在 MRI 中 `DL` 对三种主要 `NLD` 变体（`AD`、`PD` 和 `SZ`）进行诊断和分类。综述试图验证适用于这三种疾病的基于 `DL` 的分类方法。
*   此外，内容回顾了热门的开放数据集，并提供了有关受体的信息，包括年龄、性别和 MRI 扫描模态。这有助于使用开放基准数据集对新方法进行验证和比较。
*   最后，内容对当前面临的研究问题和可以帮助学者有效开发的未来研究想法进行了重点讨论。它简要描述了目前用于分析 MRI 扫描以检测 `AD`、`PD` 和 `SZ` 的不同 `DL` 架构。该部分还描述了常见的预处理技术，并提供了对这 `NLDs` 检测的详细报告。

本节提供了可供探索的现有开放数据集。该节包含对综述技术的性能评估。它在几秒钟提供了完成工作的挑战和未来展望。

## 6.7 结论

`DL` 的主要目标是通过每份数据进行增强。这包括调整其底层结构以准确评估数据的能力。一旦使用测试数据完全构建，该网络将通过客户分析实现更易于使用。

类似于流媒体服务推荐你应该看的内容，你观看过的节目数据会被处理，并做出决策以推荐你可能感兴趣的内容。`DL` 模型侧重于认知计算和模拟人类的思维结构。

作为 `ML` 的一部分，`DL` 与神经网络一起工作，模拟大脑对输入做出反应并做出决策。神经网络的节点从输入连接到网络的隐藏层，然后连接到输出。`DL` 尝试增强决策过程；模型运行得越久，就越精确、越有表现。后来，`AI` 采用 `DL` 来增强其分析过程。因此，随着突破，`AI` 在准确性和速度方面变得智能。随着 `DL` 驱动我们的未来，大数据已使这种模型变得直观。

# References

1. Jiménez J., Skalic M., Martinez-Rosell G., De Fabritiis G. K deep: Protein-ligand absolute binding affinity prediction via 3d-convolutional neural networks. J ChemInf Model. 2018; 58(2): 287–296.
2. Jha A., Gazzara M. R., Barash Y. Integrative deep models for alternative splicing. Bioinformatics. 2017; 33(14): i274–i282.
3. Jung E., Kim J., Kim M., Jung D., Rhee H., Shin J-M, Kang K, Yun C. Artificial network models for intestinal permeability of oligopeptides.
4. Zhang J., Chen K., Wang D., Gao F., Zheng Y., Yang M. Editorial: Advances of neuroimaging and data analysis. Front Neurol. 2020; 11: 257. doi: `4.3389/fneur.2020` (https://doi.org/10.3389/fneur.2020)
5. Jeon J., Lemke N., Datti A., Wrana J., Sidhu S., Moffat J. A systematic approach to identify cancer targets using machine learning. Genome Med. 2014; 6(7).
6. Kadurin A., Aliper A., Kazennov A., Mamosina P., Vanhaelen Q., Khrabrov K., Zhavoronkov A. The cornucopia of meaningful leads: Applying deep adversarial autoencoders for new molecule development. Oncotarget. 2017; 8(7): 10883.
7. Kandoi G., Acencio M. L., Lemke N. Prediction of druggable proteins using machine learning and systems biology: a mini-review. Front Physiol. 2015; 6: 366.
8. Kearnes S., Goldman B., Pande V. Modeling industrial ADMET data with multitask networks. arXiv: Machine Learning: 20161606.0879
9. Finnegan A., Song J. S. Maximum entropy methods for extracting the learned features of deep neural networks. PLoS Comput Biol. 2017; 13(10): e1005836
10. Free S. M., Wilson J. W. A mathematical contribution to structure-activity studies. J Med Chem. 1964; 7(4): 395–399.
11. Kapoor R., Hagan M., Paltab J., Ghosha P. Artificial intelligence methods in computer-aided diagnostic tools and decision support analytics for clinical informatics. ArtifIntPrec Health FromConcAppl. 2020; 31: 31–59.
12. Etzold T., Ulyanov A., Argos P. SRS: Information retrieval system for molecular biology data banks. Methods Enzymol. 1996; 266: 114–128.
13. Falchi F., Caporuscio F., Recanatini M. 基于结构的小分子蛋白质-蛋白质相互作用调节剂的设计：目前进展。Future Med Chem. 2014; 6(3): 343–357.
14. Zsoldos Z., Reid D., Simon A., Sadjad S. B., Johnson A. P. eHiTS: 一种新的快速、详尽柔性配体对接系统。J Mol Graph Model. 2007; 26(1): 198–212.
15. Esposito E. X., Hopfinger A. J., Madura J. D. 应用定量结构-活性关系范式的方法。In Chemoinformatics. Springer, 2004, pp. 131–213.
16. Ferrero E., Dunham I., Sanseau P. 利用基因-疾病关联数据预测新型治疗靶点。J Transl Med. 2017; 15(1): 182.
17. Friedman J., Hastie T., Tibshirani R. 统计学习的要素，第 1 卷。1. 纽约：Springer Series in Statistics; 2001.
18. Friesner R. A., Banks J. L., Murphy R. B., Halgren T. A., Klicic J. J., Mainz D. T., Repasky M. P., Knoll E. H., Shelley M., Perry J. K., 等人. Glide: 一种快速、准确对接和评分的新方法。1. 方法与对接准确性的评估。J Med Chem. 2004; 47(7): 1739–1749.
19. Asher M. 制药师的星系指南。Nature News. 2017; 549(7673): 445.
20. Bai F., Morcos F., Cheng R. R., Jiang H., Onuchic J. N. 利用碎片对接和共进化分析阐明蛋白质-蛋白质相互作用的可成药界面。Proc Natl Acad Sci. 2016; 113(50): E8051–E8058.
21. Bakheet T. M., Doig A. J. 人类蛋白质药物靶点的性质与鉴别。Bioinformatics. 2009; 25(4): 451–457.
22. Bengio Y., Lamblin P., Popovici D., Larochelle H. 神经处理系统中深度网络的贪心逐层训练。Cambridge, MA: MIT Press; 2007.
23. Boyiadzis M. M., Kirkwood J. M., Marshall J. L., Pritchard C. C., Azad N. S., Gulley J. L. FDA 批准用于生物标志物定义的帕博利珠单抗的意义与影响。J Immunother Cancer. 2018; 6(1): 1–7.
24. Beck A. H., Sangoi A. R., Marinelli R. 利用基因-疾病关联数据预测新型治疗靶点。J Transl Med. 2017; 15(1): 182.
25. Sathiya V. 深度架构。Now Publishers; 2009.

# 7 引言

物联网（IoT）的发展改变了几乎所有领域，包括教育、交通和医疗领域，通过连接设备进行通信、共享和存储。物联网对医疗领域产生了重大影响，并通过智能网络提供了更可靠的结果[1][2]。

医疗物联网（IoMT）是指通过安全网络进行数据传输，并对疾病进行即时监测的医疗设备[3][4]。

基于人体植入式功能，由于需要定期充电或更换电池，传统的远程监测系统[5][6][7]对患者来说是不舒适的。医疗物联网（IoMT）通过创建微型物联网设备和优化的通信通道解决了上述问题[8]。

在家里或救护车内的患者观察区域是远程医疗系统的重要组成部分[9][10][11]。患有慢性疾病的患者可以根据物联网进行监测，在紧急情况下可以提供及时的诊断。在医疗物联网中，传感器通过无线通信支持数据交换，并获取处理大量数据，为医疗专业人士提供见解[12][13][14]。

根据调查结果，一些老年人的依赖程度正在不断增加。独自居住的老人的孤独感大多归因于现代生活方式。在某些情况下，他们被忽视且无法获得及时的护理，这可能对他们的健康有害。现在，对抑郁、血压、睡眠、心脏功能和疼痛的监测通过各种基于计算机的患者监测技术进行[15][16][17]。

在患者监测系统的硬件方面，使用了传感器和专用硬件来 `get` 患者行为监测、姿态监测 [25]以及疼痛检测；而在软件端，则采用了机器学习和计算机视觉算法。为了监测健康状况，患者对在身上连接传感器并没有表现出任何兴趣。因此，面部表情被用作疼痛检测的方法。然而，只有当患者正对着摄像头时才能捕捉到面部情绪 [26,27]。与此类似，基于姿态的监测策略侧重于使用多个摄像头。

所提出的基于 `AX-YOLOV5`（任意极大你只看一次第 5 版）算法的非侵入性不适检测 [28,29,30]可以克服这些缺点。所提模型不需要不同的传感器和视线设备。为了在视频输入中定位患者，应用 `AX-YOLOV5` 算法。此外，使用 `AlphaPose` 库检测人体的 17 个关键位置 [31,32]，并使用 `IP camera` 持续记录患者的动作。为了在实时照片中确定人体的位置，使用了 `AX-YOLOV5` 算法。通过关联挖掘规则，将关键点与人体五个最关键的关键点坐标相关联。利用这些区分特征来判断患者是坐着还是躺在床上。在时间阈值技术的帮助下，通过跟踪身体主要部位坐标随时间变化的频率，可以识别医疗健康问题。最后，根据重要位置之间的距离和时间阈值对患者身体的疾病进行分类。此外，可以获取关键点的坐标，以精确确定人体内的正确病变。

本章涵盖的研究安排如下：第 7.2 节 提供了详尽的文献综述回顾；患者的不适检测过程见第 7.3 节；机器学习训练过程的数据集和系统配置摘要见第 7.4 节；患者不适检测算法的实现描述在第 7.5 节；`AX-YOLOV5` 模型训练阶段讨论在第 7.6 节；各种性能指标的计算表示在第 7.7 节；基于神经网络的各种性能指标的比较结果见第 7.8 节；研究论文的结论讨论在第 7.9 节。参考文献位于最后。

## 7.2 相关工作

在医疗控制领域，近期已付出巨大努力。包括计算机视觉、机器学习和深度学习在内的多个领域已取得进展。本部分将简述最近开发的系统和方法。对于涉及患者监测的应用，研究人员提出了各种跌倒检测和监控系统 [33]。这也被认为是一项重要程序，因为它是许多致命伤口的关键阶段，特别是在追踪老年人方面。脑电图 [34]用于评估患者行走时的损伤，而支持向量机使用径向基函数核来分析数据。在这里，使用了一种非侵入性设备在患者移动时追踪其疼痛水平。该研究的主要目标是早期识别疼痛强度，以减轻疼痛带来的抑郁。提出支持向量机（`SVM`）通过患者疼痛的面部指标对疼痛与无疼痛表情进行分类 [35,36]。使用活跃外观模型对数字化面部图像的参数和形状进行解耦 [37]。

睡眠追踪认为是患者健康的重要标志。在典型的睡眠监测系统中，会记录睡眠习惯，包括醒/睡时间、身体部位活动习惯、心率和呼吸频率的波动以及睡眠姿态。深度分析方法的开发 [38,39]允许在用户睡眠期间对其呼吸率、睡眠姿态和身体活动进行非接触监测。实验中要求八名志愿者每 15 次呼吸在床上切换仰卧和侧卧睡眠姿态。结果表明，所提技术可能成功检测处于各种睡眠位置和体型的头部和躯干。为了持续识别睡眠状态（包括床上活动、下床和呼吸阶段），`Sleep Sense` [40]通过监测运动声音声音有效追踪睡眠状态，并根据多普勒效应捕捉睡眠运动和噪声，这包含了 `Sleep Sense` 的三个部分。对于睡眠识别框架，这项工作发布了许多 TD 和 FD 属性。对于医疗治疗、健康保健和健身行业，能够追踪关键体征之一呼吸率至关重要。提出使用一种新颖可靠的方法进行呼吸监测 [41]，该方法可以准确提取出心脏跳动次数和体温等极具动态性的属性，同时也考虑了氧摄入和持续身体运动，有助于有效保护患者健康。通过在高度热动力学环境中受控呼吸运动期间评估，确立了系统监测鼻部区域的卓越耐用性，并记录呼吸频率。
