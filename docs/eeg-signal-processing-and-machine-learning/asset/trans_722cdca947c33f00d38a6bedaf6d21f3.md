

# 参考文献

54. Greenspan, H., Ruf, A., and Goldberger, J. (2006). Constrained Gaussian mixture model framework for automatic segmentation of mr brain images. *IEEE Transactions on Medical Imaging* **25** (9): 1233–1245.

55. Rio, M., Hutt, A., and Loria, B.G. (2010). Partial amplitude synchronization detection in brain signals using Bayesian Gaussian mixture models. *Cinquième conférence plénière française de Neurosciences Computationnelles, “Neurocomp'10”, Lyon, France (October 2010)*, 109–113.

56. Malmivuo, J. and Plonsey, R. (1995). *Bioelectromagnetism: Principles and Applications of Bioelectric and Biomagnetic Fields*. Oxford University Press.

57. Lewis, E.R. (1964). An electronic model of the neuron based on the dynamics of potassium and sodium ion fluxes. In: *Proceedings of the 1962 Ojai Symposium on Neural Theory and Modelling* (eds. R.F. Reiss, H.J. Hamilton, L.D. Harmon, et al.), 427. Stanford: Stanford University Press.

58. Roy, G. (1972). “A simple electronic analog of the squid axon membrane,” *The Neurofet*. *IEEE Transactions on Biomedical Engineering* **19** (1): 60–63.

59. Eccles, J.C. (1964). *The Physiology of Synapses*. Berlin: Springer‐Verlag.

60. Harmon, L.D. (1961). Studies with artificial neurons, I: properties and functions of an artificial neuron. *Kybernetik Heft* **3** (Dez.):: 89–101.

61. Mahowald, M.A., Douglas, R.J., LeMoncheck, J.E., and Mead, C.A. (1992). An introduction to silicon neural analogs. *Seminars in Neuroscience* **4**: 83–92.

62. Prange, S. (1990). Emulation of biology‐oriented neural networks. In: *Proceedings of the International Conference on Parallel Processing in Neural Systems and Computers (ICNC)* (ed. M. Eckmiller). Düsseldorf.

63. Mahowald, M.A. and Douglas, R.J. (1991). A silicon neuron. *Nature* **354**: 515–518.

64. Lu, U., Roach, S.M., Song, D., and Berger, T.W. (2012). Nonlinear dynamic modelling of neuron action potential threshold during synaptically driven broadband intercellular activity. *IEEE Transactions on Biomedical Engineering* **59** (3): 706–716.

65. Azouz, R. and Gray, C.M. (1999). Cellular mechanisms contributing to response variability of cortical neurons *in Vivo*. *Journal of Neuroscience* **19** (6): 2209–2223.

66. Henze, D.A. and Buzsáki, G. (2001). Action potential threshold of hippocampal pyramidal cells in vivo is increased by recent spiking activity. *Neuroscience* **105** (1): 121–130.

67. Chacron, M.J., Lindner, B., and Longtin, A. (2007). Threshold fatigue and information transfer. *Journal of Computational Neuroscience* **23** (3): 301–311.

# 4 EEG 信号处理基础

## 4.1 简介

脑电图（EEG）信号是神经活动的特征，通常是不同时刻、不同脑区神经元群发出的、具有不同潜伏期的动作电位的积分。它们由多电极脑电仪采集，电极位置可以在脑内、颅骨下的皮层表面，或者在绝大多数应用中，位于头皮的特定位置。不同录制设备的 EEG 文件格式各异，但如今它们可以通过常规软件轻松读取或转换。信号通常在时域呈现，然而，许多新型脑电仪能够应用简单的信号处理工具（如傅里叶变换）进行频率分析，并配备成像工具以可视化 EEG 地形图（空间域中的脑活动图谱）。

迄今为止，已开发出许多用于处理 EEG 信号的算法。操作包括但不限于时域分析、频域分析、空域分析和多路处理。此外，还开发了若干算法，仅从重建的 EEG 图像（即地形图）中可视化脑活动。从多传感器 EEG 中分离期望源信号是另一个研究领域。这进而可导致癫痫等脑异常的检测，以及与各种生理和心理活动相关源的定位。在本书的[第 17 章](#c17.xhtml)中，我们还将看到，近年来脑机接口（BCI）[[1]](#c04.xhtml#c4-bib-0001)的研究重点在于先进信号处理的发展，以及协同网络和深度学习工具与算法的巨大进步。

神经活动的建模可能比任何其他器官功能的建模都更困难。然而，已有人提出了一些用于生成 EEG 信号的简单模型。其中一些模型也已扩展以包含异常 EEG 信号的生成。

脑信号源定位是另一个非常重要的研究领域[[2]](#c04.xhtml#c4-bib-0002)。为了提供一种在脑内定位源的可靠算法，需要具备关于电磁波传播的充分知识，以及如何利用测量信号中的信息来分离和定位脑内源。源可以被视为磁偶极子，从而求解著名的反问题；也可以被视为分布电流源。

病人监护和睡眠监测需要对长达数天的长 EEG 序列进行实时处理。EEG 提供了关于睡眠大脑的重要且独特的信息。睡眠期间的主要脑活动可通过开发的算法捕获，例如本章后面讨论的匹配追踪（MP）法[[3]](#c04.xhtml#c4-bib-0003)。

癫痫监测、检测和预测也吸引了众多研究者。时间序列的动力学分析结合信号源的盲分离应用，已实现从头皮 EEG 预测局灶性癫痫。反之，时频（TF）域分析在新生儿癫痫发作检测中的应用，为该领域的进一步研究铺平了道路。癫痫领域的一项重要近期贡献是如何建模颅内癫痫样放电（主要在发作间期）与头皮电极之间的传导路径。该领域的最新进展通过引入多视角方法和字典学习[[4]](#c04.xhtml#c4-bib-0004)–[[6]](#c04.xhtml#c4-bib-0006)以及深度神经网络结构[[7]](#c04.xhtml#c4-bib-0007)、[[8]](#c04.xhtml#c4-bib-0008)，实现了从头皮捕获相当比例的所谓发作间期癫痫样放电（IED）。本书[第 7 章](#c07.xhtml)和[第 11 章](#c11.xhtml)将描述该技术。

在以下章节中，将解释上述目标的大多数工具和算法，并讨论其数学基础。然而，这些算法在正常和异常 EEG 分析中的应用将在本书后续章节中介绍。读者还应了解从线性代数中借用的所需概念和定义。详情可参阅[[9]](#c04.xhtml#c4-bib-0009)。在本章及本书其余部分中，连续时间用“*t*”表示，离散时间用“*n*”表示（归一化采样周期 *T* = 1）。但在某些图示中会给出以秒为单位的实际时间。

## 4.2 介质的非线性

