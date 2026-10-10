

# 参考文献

*   Swiss Quantum Initiative. n.d. 访问日期：2024年10月28日。[https://qc.ethz.ch/community-and-initiatives/network/swiss-quantum-initiative.html](https://qc.ethz.ch/community-and-initiatives/network/swiss-quantum-initiative.html)。

*   von Burg, Vera, Guang Hao Low, Thomas Häner, Damian S. Steiger, Markus Reiher, Martin Roetteler, and Matthias Troyer. 2021. "Quantum computing enhanced computational catalysis." *Physical Review Research* 3, no. 3: 033055。

*   Wehner, Stephanie, David Elkouss, and Ronald Hanson. 2018. "Quantum internet: A vision for the road ahead." *Science* 362, no. 6412: eaam9288。

*   Wineland, David J. 2013. "Nobel Lecture: Superposition, entanglement, and raising Schrödinger's cat." *Reviews of Modern Physics* 85, no. 3: 1103–1114。

*   Xu, Feihu, Xiongfeng Ma, Qiang Zhang, Hoi-Kwong Lo, and Jian-Wei Pan. 2020. "Secure quantum key distribution with realistic devices." *Reviews of Modern Physics* 92, no. 2: 025002。

*   Yin, Juan, Yuan Cao, Yu-Huai Li, Sheng-Kai Liao, Liang Zhang, Ji-Gang Ren, Wen-Qi Cai et al. 2017. "Satellite-based entanglement distribution over 1200 kilometers." *Science* 356, no. 6343: 1140–1144。

*   Zhang, Qiang, Feihu Xu, Yu-Ao Chen, Cheng-Zhi Peng, and Jian-Wei Pan. 2018. "Large scale quantum key distribution: challenges and solutions." *Optics Express* 26, no. 18: 24260–24273。

*   Zhang, Yichen, Yiming Bian, Zhengyu Li, Song Yu, and Hong Guo. 2024. "Continuous-variable quantum key distribution system: Past, present, and future." *Applied Physics Reviews* 11, no. 1: 011318. [https://doi.org/10.1063/5.0179566](https://doi.org/10.1063/5.0179566)。

# 第3章：基于遗传算法的医学图像增强优化框架

Kirti Aggarwal and Meenal Jain

DOI: [10.1201/9781003569619-3](http://doi.org/10.1201/9781003569619-3)

## 3.1 引言

增强医学图像增强的临床能力对于图像分析至关重要。本研究的目标是应用遗传算法（`GA`s）来生成增强后的图像。基本思路是将初始图像输入`GA`s以生成清晰、高质量的重现图像，然后进一步增强。本研究旨在利用一种考虑所有限制条件以产生更好结果的前沿算法，创建一个生成最佳可能图像的框架。为实现准确高效的图像增强，它采用了`GA`。我们从读取图像和准备适应度函数开始。这种随机生成的图像通过交叉和变异，在许多代中利用`GA`持续进化，直到找到最优解。具有双峰强度分布，这可以增强图像数据中感兴趣区域（`ROI`）的视觉效果。

在处理之前，图像增强可提高原始数据的质量和信息含量。传统技术包括对比度增强、空间滤波和密度分层。在对比度增强或拉伸中，应用线性变换来扩展灰度级的范围。空间滤波改善自然发生的线性特征，如断层。密度分层将连续的灰度范围分割成一系列密度区间，每个区间用特定的颜色或符号表示。

近年来，为了协助临床医生做出准确诊断，对医学图像改进的需求不断扩大；因此，医学图像处理为提升医学图像以实现疾病的正确诊断提供了帮助 [[1]](#ch13.xhtml#r080)。改善图像质量始终是医学图像处理的主要目标之一。图像增强提高了图像供人眼观看的清晰度。

增强技术包括去除图像中的模糊和噪声、增加对比度以及显示细节 [[2]](#ch13.xhtml#r081)。在捕获图像时，部分信息会丢失，导致图像模糊或信息量减少，并不总是清晰可见。医学图像光照不足，图像的许多关键部分不可见，导致视觉模糊和难以察觉的对比度。

医学研究数据包含大量信息，在某些情况下，无法使用传统统计方法简单地检查，甚至根本无法检查。本可从算法中受益以解决困难医学问题的医生却不知其存在。因此，我们希望利用`GA`及其医学应用。`GA`在放射学等多个医学专业中的应用具有引人入胜的意义。本文介绍了`GA`在疾病筛查、诊断、治疗规划、药物警戒、预后和医疗管理中的用途，并让医生设想如何在自己的实践中应用这种元启发式方法。**[图 3.1](#ch13.xhtml#f4)** 表示 `GA` 的流程循环。算法在 **[第 3.3 节](#ch13.xhtml#h1-014)** 中有详细定义。

![图 3.1 遗传算法的流程循环。](html/images/9781032942346_C003_001.jpg)

**图 3.1** 遗传算法的流程循环。

在本研究工作中，我们将深入研究 `GA` 的工作原理以及如何将其用于优化图像增强过程。我们渴望为医疗保健领域开辟一条新路径，使解决方案能够通过 `GA` 实现。图像增强问题可以由多个因素表征，这使得参数选择问题变得困难。

本章提出了一个框架，该框架在连接认知网络的背景下应用 `GA`，以优化跨各个领域的图像增强。通过利用计算智能的力量，该框架将跨学科知识——从人工智能到图像处理——连接成一个旨在提高图像质量的集成系统。`GA` 作为计算智能的核心组件，被用于解决图像增强中涉及的复杂优化挑战，提供适应性强且可扩展的解决方案。本章重点介绍了这些算法如何模拟进化过程以迭代改进图像质量，反映了连接认知网络链接多样化认知过程和专业知识的自适应本质。这种方法通过展示如何利用连接认知来开发用于图像增强的创新解决方案，促进了计算智能的进步，最终改善了不同应用中的视觉结果。

## 3.2 文献综述

现有的大多数图像增强方法都是与特定类型图像相关的经验或启发式方法，旨在增强在采集过程中退化的图像的对比度水平。优化问题在于确定能够增强每个不同输入图像的理想灰度级。一些方法采用群体智能技术。粒子群优化（`PSO`）被用于多目标直方图均衡化，以在保持亮度的同时提高对比度。一些工作利用人工蜂群（`ABC`）算法，在优化框架内使用相似的候选解编码和直方图映射策略。

