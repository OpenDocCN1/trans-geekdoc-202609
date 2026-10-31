
51. E. Soria‐Olivas, J.D. Martin‐Guerrero, G. Camps‐Valls, A.J. Serrano‐Lopez, J. Calpe‐Maravilla, and L. Gomez‐Chova. 用于人工神经网络的低复杂度模糊激活模糊激活函数。IEEE Transactions on Neural Networks, 14(6): 1576–1579, 2003.

52. G.L. Stuber. 《移动通信原理》。Kluwer Academic Publishing, 1st Edition, 1999.

53. Y. Tan, J. Wang, and J.M. Zurada. 使用径向基函数网络的非线性盲源分离。IEEE Transactions on Neural Networks, 12(1): 124–134, 2001.

54. J. Tang, C. Deng, and G. Huang. 多层感知器的极限学习机。IEEE Transactions on Neural Networks And Learning Systems, 27(4): 809–821, 2016.

55. M. Uesugi, K. Honma, and K. Tsubaki. TDMA 数字移动无线电中的自适应均衡。In *1989 IEEE 全球电信会议和展览‘面向1990年代及以后的通信技术’*, volume 1, pages 95–101, 1989.

56. A. Uncini and F. Piazza. 通过复域自适应样条神经网络的盲信号处理。IEEE Transactions on Neural Networks, 14(2): 399–412, 2003.

57. Y. Wang, L. Yang, F. Wang, and L. Bai. 使用基于 PDF 误差函数的支持向量回归的盲均衡。In *2016 第八届智能人机系统与信息学国际会议 (IHMSC)*, volume 2, pages 212–216, 2016.

58. W.D. Weng and C.T. Yen. 用于数字通信系统的简化判决反馈 FLANN 非线性信道均衡器。IEEE Proceedings‐Communications, 151(4): 305–311, 2004.

59. Y. Xiao, Y. Dong, and Z. Li. 通过带偏置单元的递归神经网络在水声通信中的盲均衡。In *2008 第七届世界智能控制与自动化大会 (WCICA)*, pages 2407–2410, 2008.

60. N. Xie and H. Leung. 使用预测径向基函数神经网络的盲均衡。IEEE Transactions on Neural Networks, 16(3): 709–720, 2005.

61. W. Xu, Z. Zhong, Y. Be'ery, X. You, and C. Zhang. 联合神经网络均衡器和译码器。*arXiv:1807.02040v1*, 2018.

62. R. Yang, L. Yang, J. Zhang, C. Sun, W. Cong, and S. Zhu. 通过极限学习机的 QAM 信号盲均衡。In *2018 第十届先进计算智能国际会议 (ICACI)*, pages 34–39, 2018.

63. S. Yang, Y. Han, X. Wu, R. Wood, and R. Galbraith. 一种软可译的级联 LDPC 码。IEEE Transactions on Magnetics, 51(11): 1–4, 2015.

64. H. Yao, S. Zhang, and Z. Wang. 基于最小二乘支持向量回归器的盲均衡算法。In *2011 电子机械工程与信息技术国际会议*, volume 5, pages 2675–2678, 2011.

65. H. Ye and G.Y. Li. 关于深度学习用于联合信道均衡和译码的初步结果。In *2017 IEEE 第86届车载技术会议 (VTC‐Fall)*, pages 1–5, 2017.

66. H. Ye, G.Y. Li, and B. Juang. 深度学习在 OFDM 系统中信道估计和信号检测的威力。IEEE Wireless Communications Letters, 7(1): 114–117, 2018.

67. C. You and D. Hong. 使用复值多层前馈神经网络的非线性盲均衡方案。IEEE Transactions on Neural Networks, 9(6): 1442–1455, 1998.

68. X. Zhang, H. Wang, L. Zhang, and X. Zhang. 基于双线性递归神经网络的盲均衡算法。In *2004 第五届世界智能控制与自动化大会 (WCICA) 2004*, pages 1982–1984, 2004.

# 第13章
信号情报的神经网络：理论与实践

*Jithin Jagannath¹, Nicholas Polosky¹, Anu Jagannath¹, Francesco Restuccia², and Tommaso Melodia²*

¹*马可尼-罗森布拉特 AI/ML 创新实验室，ANDRO Computational Solutions LLC，纽约，美国*

²*电气与计算机工程系，东北大学，波士顿，美国*

稳健无线通信在商业和军事应用中的重要性毋庸置疑。商业部门努力在有限的频谱资源与不断增长的带宽需求之间取得平衡，后者包括具有特定服务质量（QoS）要求的<|message|> 多媒体支持。在战术场景中，在敌对、拥挤和 contested 环境中运行一直具有挑战性。这两种场景都可从高效的频谱感知和信号分类能力中受益。虽然这个问题已被研究数十年，但机器学习的近期复兴已在该领域留下显著印记。因此，本章旨在为读者全面介绍机器学习技术，特别是人工神经网络，如何应用于解决与收集信号情报相关的一些关键问题。为此，我们首先介绍人工神经网络概述。接下来，我们在信号情报的背景下讨论机器学习对物理层的影响。之后，我们讨论社区在硬件实现方面所采取的方向。最后，我们确定机器学习在物理层应用相关的关键障碍。

## 13.1 引言

根据最新的 *爱立信移动报告*，全球目前有 5.2 亿部移动宽带订阅，每月产生超过 130 艾字节的无线流量（Ericsson Incorporated, [2018](#c13.xhtml#c13-bib-0014)）。此外，预计到 2020 年，超过 50 亿台设备将被纳入互联网，形成前所未有的“物”全球网络（Cisco Systems, [2017](#c13.xhtml#c13-bib-0010)）。鉴于无线运营商可用的射频频谱带仅有少数（Federal Communications Commission \[2016\]），诸如通过波束成形进行射频（RF）频谱共享（Shokri‐Ghadikolaei et al., [2016](#c13.xhtml#c13-bib-0058); Vázquez et al., [2018](#c13.xhtml#c13-bib-0061); Lv et al., [2018](#c13.xhtml#c13-bib-0041)）、动态频谱接入（DSA）（Jin et al., [2018](#c13.xhtml#c13-bib-0032); Chiwewe and Hancke, [2017](#c13.xhtml#c13-bib-0009); Jagannath et al., [2018a](#c13.xhtml#c13-bib-0029); Federated Wireless, [2018](#c13.xhtml#c13-bib-0016); Agarwal and De, [2016](#c13.xhtml#c13-bib-0002)）和抗干扰技术（Zhang et al., [2017](#c13.xhtml#c13-bib-0070); Huang et al., [2017](#c13.xhtml#c13-bib-0026); Chang et al., [2017](#c13.xhtml#c13-bib-0007)）等技术在不久的将来将变得至关重要。

软件定义无线电被引入作为解决与僵化无线电硬件设计相关的限制的方案，该设计阻碍了可重构性和操作灵活性。为无线电配备学习和观察操作场景以做出认知决策的能力可以改善频谱共享和频谱态势感知。频谱共享将使无线电能够感知并利用未使用/未充分利用的频谱，以避免由非故意/故意干扰引起的频谱拥塞。此外，信号感知和分类可以增强无线电的频谱知识，以强化和促进态势感知。商业和战术军事运营商可以利用这种认知能力来最大化频谱利用率并提供更稳健的通信链路。
