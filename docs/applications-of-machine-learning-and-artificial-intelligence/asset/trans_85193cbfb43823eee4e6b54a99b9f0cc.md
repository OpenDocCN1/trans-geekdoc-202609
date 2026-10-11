

# 参考文献

Vadakkepat, P., Lim, P., De Silva, L. C., Jing, L., & Ling, L. L. (2008). Multimodal approach to human-face detection and tracking. *IEEE Transactions on Industrial Electronics*, 55(3), 1385–1393. doi:10.1109/TIE.2007.903993

Vezhnevets, V., Sazonov, V., & Andreeva, A. (2003, September). A survey on pixel-based skin color detection techniques. *Proc Graphicon*, 3, 85–92.

Yang, M.-H., & Ahuja, N. (1998). Gaussian mixture model for human skin color and its applications in image and video databases. In *Storage and retrieval for image and video databases vii* (Vol. 3656, pp. 458–467). doi:10.1117/12.333865

Zarit, B. D., Super, B. J., & Quek, F. K. (1999). Comparison of five color models in skin pixel classification. In *Proceedings international workshop on recognition, analysis, and tracking of faces and gestures in real-time systems. in conjunction with iccv'99* (cat. no. pr00378) (pp. 58–63). 10.1109/RATFG.1999.799224

Zuo, H., Fan, H., Blasch, E., & Ling, H. (2017). Combining convolutional and recurrent neural networks for human skin detection. *IEEE Signal Processing Letters*, 24(3), 289–293. doi:10.1109/LSP.2017.2654803

# 关键术语与定义

**计算机视觉**：计算机科学的一个研究领域，处理图像和视频。其目标是从图像和视频中提取重要信息。

**人体皮肤检测**：从图像或视频中检测人体皮肤的过程。它在计算机视觉中有各种应用。

**机器学习**：人工智能领域的一部分。它由各种算法组成，可用于分析数据并从数据中获取洞察。

**监督学习**：机器学习算法的一种技术。它使用已知数据，通过统计模型对未知数据进行预测。

**测试数据**：不带已知标签/信息的数据集。计算机模型使用该数据进行实际应用。

**训练数据**：带有已知标签的数据集。此类数据用于训练计算机模型以实现预期应用。

**无监督学习**：一种机器学习技术。它不需要任何已知数据。它通过自身发现各种数据信息。

# 第3章

**Ladly Patel**  
斯里克里希纳理工学院，印度

## 摘要

人类通过面部表情进行交流和表达情绪。面部表情是表达情绪的重要组成部分。面部特征可视为眼睛、嘴巴和鼻子。在本章中，作者考虑了这些面部特征用于情绪检测，并使用 `convolutional neural network (CNN)` 对其进行处理。主要有六种基本情绪类型：恐惧、厌恶、愤怒、悲伤、快乐和惊讶。这些情绪可分为两类：积极情绪和消极情绪。积极情绪是指没有消极性的感觉，如快乐、中性。消极情绪是指抑郁、沮丧的感觉，包括愤怒、悲伤、恐惧。本章描述了在 `CNN` 中处理图像并给出输出的分步方法。`CNN` 对不同情绪进行分类。进一步将情绪分为消极和积极，当检测到消极情绪时，播放音乐以改变一个人的情绪。

## 介绍

`convolutional neural network (CNN)` 是一种神经网络，由一个或多个卷积层组成，用于图像处理、物体或图像分类、分割。它主要用于处理大量数据，且仅一个 `CNN` 算法即可提取特征、对物体或图像进行分类并给出期望的快速结果。`CNN` 处理速度更快。`CNN` 由三层组成，分别是第一层卷积层、第二层池化层和最后的全连接层。`CNN` 有许多应用，但主要用于图像相关应用。`CNN` 的一些应用包括图像分类、图像分割、图像中的物体检测、天气预报等。研究工作包含关于图像处理和分类的信息，通过分析面部特征来检测情绪，以及处理图像并对其进行分类以获得期望输出的算法及其代码片段。还展示了图像如何在卷积层的不同层中逐步处理并输出。本章展示了 `CNN` 所有层的各种方程。在本章中，`CNN` 检测人的情绪，然后将情绪分类为积极和消极情绪，在后期阶段针对消极情绪给予音乐疗法，使人的情绪从消极转为积极。此处仅考虑两种积极情绪，即快乐和中性，而仅考虑两种消极情绪，即悲伤和愤怒。已提取并绘制了从消极到积极情绪的面部表情变形。此处通过序列图展示了架构中的整体流程。本章还展示了不同情绪的数据集和示例数据集。为所有情绪绘制了直方图。还展示了 `CNN` 混淆矩阵，并在表格中展示了人工预测和神经网络预测。

## 背景

`Convolutional neural networks`（卷积神经网络）一词最早由 Yann LeCun 于 1980 年提出。`Convolutional neural network (CNN)` 是一类深度学习神经网络。卷积网络的灵感来源于对动物视觉皮层神经元间模式的观察。`convolutional neural network` 是一种用于图像识别和处理的人工神经网络，旨在处理像素数据。`CNN` 由输入层、隐藏层和输出层组成。`CNN` 从图像中提取特征。`CNN` 中的输入层是灰度图像。输出层由多类标签组成。隐藏层由卷积层、`ReLu` 层、池化层和全连接神经网络组成。为了训练 `CNN`，每个输入图像都需要通过多个卷积层系列（带有核）、`ReLu` 层、池化层，最后到达全连接层，以便以 0 到 1 之间的概率值对物体或图像进行分类。为本章进行了一些调查，以证明 `CNN` 最适合处理和分类图像。部分调查列举如下：

*   在一篇 2012 年由 Deng J 发表的论文中，作者描述了一个用于检测情绪的分层框架，它包含两层：第一层是外部层，显示初步和表层情绪；第二层是内在层，显示心理和共鸣情绪。基于这两层，构建了一个名为 `Resonance Arousal Valence model`（共鸣唤醒效价模型）的音乐情绪模型。该模型在三维连续空间中显示情绪。基于强度、音高、和声等特征，音乐将被传递给该模型。为了高效地用多个情绪标签说明音乐，实现了使用 `KNN` 方法的监督多类标签。

*   在一篇 2015 年由 H.Jing 发表的论文中，作者为监测老年人设计了机器人内部的认知情绪模型。通过结合 `Gabor filter`（Gabor 滤波器）、`k-Nearest neighbour algorithm`（k-最近邻算法）和 `Local Binary Pattern algorithm`（局部二值模式算法），提取并识别面部特征。面部特征影响机器人的情绪状态，称为 `AVS emotion space`（AVS 情绪空间）。随后，使用 `simulated annealing algorithm`（模拟退火算法）分析智能家居环境对认知情绪模型的优化。最后，使用 `cognitive reappraisal strategy`（认知重评策略）和 `Euclidean distance`（欧氏距离）获得不同情绪状态间的转换概率。仿真和实验已进行测试以减少消极情绪。

