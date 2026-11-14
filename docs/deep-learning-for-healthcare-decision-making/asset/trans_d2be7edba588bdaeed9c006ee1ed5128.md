
## 参考文献

46. [T. Mikolov, G. Corrado, K. Chen, and J. Dean](#ch6.xhtml#R_ref6_46), “向量空间中词表示的高效估计,” 见 Proc. Int. Conf. Learn. Representations, 2013, 页 1–12.

47. [Y. Cheng, F. Wang, P. Zhang, H. Xu, and J. Hu](#ch6.xhtml#R_ref6_47), “基于电子健康记录的风险预测：一种深度学习方法,” 见 Proc. SIAM Int. Conf. Data Mining, 2015, 页 432–440.

48. [Z. C. Lipton, D. C. Kale, C. Elkan, and R. Wetzell](#ch6.xhtml#R_ref6_48), “利用LSTM循环神经网络进行诊断学习,” arXiv:1511.03677, 2016.

49. [P. Nickerson, P. Tighe, B. Shickel, and P. Rashidi](#ch6.xhtml#R_ref6_49), “用于预测镇痛反应的深度神经网络架构,” 见 Proc. 2016 IEEE 38th Annu. Int. Conf. Eng. Med. Biol. Soc., 2016, 页 2966–2969.

50. [A. Esteban, O. Staeck, Y. Yang, and V. Tresp](#ch6.xhtml#R_ref6_50), “利用循环神经网络结合静态和动态信息预测临床事件,” 见 Healthcare Info. (ICHI), 2016 IEEE Int. Conf., 2016年10月, 页 93–101.

51. [R. Poplin, A. V. Varadarajan, K. Blumer, Y. Liu, M. V. McConnell, G. S. Corrado, L. Peng, and D. R. Webster](#ch6.xhtml#R_ref6_51), 利用深度学习从视网膜眼底照片预测心血管风险因素, arXiv preprint arXiv: 1708.09843, 2017.

52. [H. Li, X. Y. Li, M. Ramanathan, and A. D. Zhang](#ch6.xhtml#R_ref6_52), 骨病的预测与信息性风险因素选择, IEEE/ACM Transactions on Computational Biology and Bioinformatics, 卷 12, 第 1 期, 页 79–91, 2015.

53. [F. Dernoncourt, J. Y. Lee, O. Uzuner, and P. Szolovits](#ch6.xhtml#R_ref6_53), “利用循环神经网络对患者笔记进行去标识化,” J. American Medical Informat. Assoc., 卷 24, 第 3 期, 页 596–606, 2017.

54. [A. E. Shweta, S. Saha, and P. Bhattacharyya](#ch6.xhtml#R_ref6_54), “临床记录中患者数据去标识化的深度学习架构,” 见 Proc. Clin. Natural Lang. Process. Workshop, 2016, 页 32–41.

55. [R. Miotto, L. Li, B.A. Kidd, and J.T. Dudley](#ch6.xhtml#R_ref6_55), “DeepPatient：一种从电子健康记录预测患者未来的无监督表示,” Sci. Rep., 卷 6, 第 4 月, 2016, 文章编号 26094.

56. L. Nie, M. Wang, L. Zhang, S. Yan, B. Zhang, and T.-S. Chua, “通过稀疏连接深度学习从健康相关问题推断疾病,” IEEE Trans. Knowl. Data Eng., 卷 27, 第 8 期, 页 2107–2119, 2015年8月.

57. [H.I. Sukand, D. Shen](#ch6.xhtml#R_ref6_57), “基于深度学习的特征表示用于AD/MCI分类,” 见 Proc. 16th Int. Conf. Med. Image Comput. Comput. Assisted Intervention, 2013, 卷 8150, 页 583–590.

58. [Z. Che, D. Kale, W. Li, M. Taha Bahadori, and Y. Liu](#ch6.xhtml#R_ref6_58), “深度计算表型分型,” 见 Proc. 21st ACM SIGKDD Int. Conf. Knowl. Discovery Data Mining, 2015, 页 507–516.

59. [G. J. Kuperman 等](#ch6.xhtml#R_ref6_59), “计算机化医嘱录入系统中与药物相关的临床决策支持：综述,” J. Amer. Med. Informat. Assoc., 卷 14, 第 1 期, 页 29–40, 2007.

60. [K.P. Murphy](#ch6.xhtml#R_ref6_60), 机器学习：概率视角. Cambridge, MA, USA: MIT Press, 2012.

# 7 利用AI的基于远程医疗的M-Health信息学发展

Jagjit Singh Dhatterwal^()

## 摘要

M-Health的主要问题之一是如何有效利用现在几乎普遍可用的移动电信能力。本文旨在演示一个基于通用分组无线服务（GPRS）并具有蓝牙连接的多通道M-Health系统。目标是创建一个系统，利用商用GPRS网络上的智能手机将患者的生物信号即时发送至医院。为观察和处理健康信息，该系统与客户端计算机应用程序相结合。远程医疗会话由应用服务器处理，该服务器还控制来自远程患者的客户端请求消息。远程医疗会话期间传输的所有诊断信息，连同患者身份识别和远程医疗会话详细信息，均保存在数据库中以供后续分析。临床医生可根据需要使用浏览器应用程序查询存储库以获取这些数据。

## 7.1 引言

传统的远程医疗技术传递方法是利用“固定电话”通信技术（如公共交换电话网（PSTN）和综合业务数字网（ISDN））将患者的生物信号发送给临床医生。在放射学、心脏病学、病理学和外科领域，已在低带宽下传输编码心电图（ECG）、高血压、体温和血氧水平等参数，在高可用带宽下传输X光片和超声成像 [[1](#ch7.xhtml#ref7_1)]。由于向远程患者提供临床记录和医院服务提供者的概念，远程医疗已成为一个快速发展的研究课题。远程医疗在城乡以及工业化和发展中经济体中，均有显著潜力提高医院设施的质量和可用性，因为它意味着允许医护人员以真正远程的方式受到监督，可能是在移动中，且几乎来自全球任何地方。传统远程医疗的局限性显而易见，因为操作局限于固定站点之间的对话，常使用Windows软件。因此，将移动蜂窝连接与远程医疗应用相结合，被视为提供更移动、更具成本效益的医疗服务的下一关键步骤。技术人员与医生之间的互动开始显示，这种结合对医疗服务交付既切实可行又有益。远程医疗极大地受益于无线通信技术的进步，范围从固定技术平台到移动通信能力。此外，普适、高度先进和可穿戴系统的同步进步催生了M-Health概念，这是21世纪远程医疗的总括性概念。M-Health可广泛描述为“用于全民医疗的移动计算、医疗传感器和电信技术”。尽管医患面对面交流永远不应被取代，但有些医疗问题利用M-Health技术可治疗得更有效。远程常规检查、灾难响应场景和运动科学中的生理测量皆为可能的软件应用。医疗服务现可提供给全球移动通信系统（GSM）等无线网络通信范围内的任何地点。在住院期间高效、持续地监测个体，有显著潜力减轻国家医疗资源的压力。农村地区的个体可通过手机接受常规检查，而无需按固定时间表频繁前往医院。频繁的检查和监测可在个体居家、途中、工作或娱乐时进行，腾出医院人员处理更复杂的患者。这可节省医生和患者的精力和金钱，特别是消除了个人长途跋涉、在长时间等待后进行短暂预约的需求 [[2](#ch7.xhtml#ref7_2)]。

## 7.2 本章目标

本研究旨在创建一个集成的蓝牙M-Health系统，用于通过一个或多个无线通信系统传输多通道传感器数据。研究目标如下：
