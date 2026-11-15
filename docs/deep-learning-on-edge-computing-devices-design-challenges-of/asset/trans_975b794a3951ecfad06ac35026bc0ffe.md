

表 8.3 物体跟踪硬件实现对比。

| | 特性 | 帧率 (帧/秒) | 图像分辨率 | 时钟频率 (MHz) | 功耗效率 (nJ/pixel) |
|---|---|---|---|---|---|
| Stratix-III [8] | 方向边缘 | 150 | 640 × 480 | 60 | N/A |
| Arria-V [9] | 灰度级 LBP | 2800 | 128 × 128 | 100 | N/A |
| 28nm ASIC [15] | 光流+深度 | 30 | 1920 × 1080 | 180 | 12.22 |
| Virtex-4 [7] | LBP+HOG | 60 | 640 × 480 | 25 | N/A |
| Virtex-5 [11] | 定向能量 | 30 | 640 × 480 | 24 | N/A |
| Zynq-7045 | | 630 | 320 × 240 | | |
| (本文) | UTDCF | 253 | 640 × 480 | 100 | 15.87 |

本章介绍了一种基于简单且鲁棒的统一纹理与动态压缩特征以及椭圆匹配的低成本高速物体 VLSI 系统。该系统架构采用以存储器为中心的范式、多级流水线和并行处理电路，旨在尽可能降低硬件成本的同时提高跟踪速度。所提 VLSI 系统的 FPGA 原型机采用少量计算资源和适度的内存消耗实现。在 100-MHz 时钟频率下，它可以处理分辨率为 320 × 240 的图像，处理速度为 600 帧/秒。所提原型机的跟踪结果以及与先前工作的对比表明，我们的跟踪系统适用于高速低成本嵌入式视觉跟踪应用。

## References

- [1] W. He, J. Zhang, Y. Lin, X. Zhou, P. Li, L. Liu, N. Wu, C. Shi, 基于统一纹理与动态压缩特征的低成本高速物体跟踪 VLSI 系统, IEEE Transactions on Circuits and Systems. II, Express Briefs 68 (3) (2020) 1013–1017.
- [2] A. Yilmaz, O. Javed, M. Shah, 物体跟踪：一项综述, ACM Computing Surveys 38 (4) (2006).
- [3] H. Yang, L. Shao, F. Zheng, L. Wang, Z. Song, 视觉跟踪的最新进展与趋势：综述, Neurocomputing 74 (18) (2011) 3823–3831.
- [4] J.K. Sunkara, M. Santhosh, S.B. Cherukuri, L.G. Krishna, 物体跟踪技术与性能度量——概念性综述, 载于：International Conference on Power, Control, Signals and Instrumentation Engineering 论文集, 2017, pp. 2297–2305.
- [5] S.-A. Li, C.-C. Hsu, W.-L. Lin, J.-P. Wang, 粒子滤波器的硬件/软件协同设计及其在物体跟踪中的应用, 载于：International Conference on System Science and Engineering 论文集, 2011, pp. 87–91.
- [6] J.U. Cho, S.H. Jin, X. Dai Pham, J.W. Jeon, J.E. Byun, H. Kang, 一种基于粒子滤波器的实时物体跟踪系统, 载于：IEEE International Conference on Intelligent Robots and Systems 论文集, 2006, pp. 2822–2827.
- [7] T. Sledević, A. Serakıs, D. Plonis, 基于 LBP、HOG 和运动检测的 FPGA 选定物体跟踪, 载于：IEEE Workshop on Advances in Information, Electronic and Electrical Engineering 论文集, 2018, pp. 1–5.
- [8] P. Zhao, H. Zhu, H. Li, T. Shibata, 一种采用多候选位置生成的基于方向边缘的实时物体跟踪系统, IEEE Transactions on Circuits and Systems for Video Technology 23 (3) (2012) 503–517.
- [9] Y. Yang, J. Yang, L. Liu, N. Wu, 基于分层并行视觉处理器和灰度级 LBP 算法的高速目标跟踪系统, IEEE Transactions on Systems, Man, and Cybernetics: Systems 47 (6) (2016) 950–964.
- [10] J. Yang, C. Shi, L. Liu, N. Wu, 异构视觉芯片和基于 LBP 的高速跟踪算法, Electronics Letters 50 (6) (2014) 438–439.
- [11] E. Norouznezhad, A. Bigdeli, A. Postolà, B.C. Lovell, 基于局部定向能量特征及其硬件/软件实现的鲁棒物体跟踪, 载于：International Conference on Control, Automation, Robotics and Vision 论文集, 2010, pp. 2060–2066.
- [12] C. Shi, G. Luo, 面向智能图像传感器的流式运动放大内核, IEEE Transactions on Circuits and Systems. II, Express Briefs 65 (9) (2017) 1229–1233.
- [13] K. Zhang, L. Zhang, M.-H. Yang, 快速压缩跟踪, IEEE Transactions on Pattern Analysis and Machine Intelligence 36 (10) (2014) 2002–2015.
- [14] 视觉跟踪器基准, URL http://www.visual-tracking.net.
- [15] Z. Li, J. Wang, D. Sylvester, D. Blaauw, H.S. Kim, 一种用于统一光流和带半全局匹配的立体深度的 1920 × 1080 25 帧/秒 2.4-TOPS/W 低功耗 6-D 视觉处理器, IEEE Journal of Solid-State Circuits 54 (4) (2019) 1048–1058.
- [16] B. Chen, D. Wang, P. Li, S. Wang, H. Lu, 实时“演员-评论家”跟踪, 载于：European Conference on Computer Vision 论文集, 2018, pp. 318–334.

本页故意留空

## 第 9 章

## SensCamera：一种基于学习的智能相机原型

### 9.1 模式识别之外的挑战

随着集成电路和嵌入式计算技术的进步，具有强大物体检测功能的无线智能相机已被广泛应用于不同领域 [1,2]。作为最先进的方法之一，卷积神经网络 (CNN) 在物体检测方面已被证明非常成功，激发了人们对基于卷积神经网络的智能相机在不同应用（如入侵检测 [3–5]）中实现的浓厚兴趣。

基于卷积神经网络的早期物体检测方法包含一个区域提取阶段，从目标图像中选出成千上万个区域用于物体检测，这会导致高计算开销，例如著名的区域卷积神经网络 (R-CNN) [6]。最近，提出了一组高效的物体检测卷积神经网络架构，包括 Fast R-CNN [7]、Faster R-CNN [8]、单射多框检测 (SSD) [9] 和 YOLO 模型 [10]。受这些工作的启发，基于 CNN 的物体检测的计算复杂度已大大降低，这使得使用无线嵌入式设备实现基于 CNN 的计算机视觉应用成为可能。

研究 [11] 首先使用卷积运算进行压缩感知，但仍使用随机感知矩阵以确保不相干条件。最近，一组基于学习的方法使用一组训练样本来估计确定性感知矩阵。作为早期尝试，NuMax 方法可以通过求解半定规划 (SDP) 问题来估计线性近等距感知矩阵 [12]。Baldassarre 等人 [13] 提出了一种基于学习的子采样方法，可以通过求解组合优化问题来估计感知矩阵。Blasiok 等人 [14] 将 NuMax SDP 问题放宽为特征值问题，并针对包含数千个样本的较大数据集提出了 ADAGIO 方法。

最近，一些研究人员试图使用卷积神经网络来解决压缩感知的不同问题。Mousavi 等人 [15] 提出使用卷积神经网络从随机欠采样测量中恢复原始信号。随后，Mousavi 等人 [16] 通过使用卷积神经网络来压缩和恢复信号，改进了他们的方法。Lu 等人 [17] 为图像压缩提出了类似的想法。Iliadis 等人 [18] 提出使用深度全连接网络进行视频图像恢复。Ren 等人 [19] 提出了一种遵循拉普拉斯金字塔概念的渐进式重建方法。Wu 等人 [20] 通过元学习提高了重建的性能和速度。Chen 等人 [21] 采用多层残差编码方案，以提高基于压缩感知的图像编码的率失真性能。Zhou 等人 [22] 开发了一种多通道深度网络，用于基于块的图像压缩感知，利用块间相关性。我们所提方法与这些研究的主要区别在于，压缩卷积网络 (CCN) 并非用于图像压缩或恢复的网络，而是一种网络增强方法，使物体检测网络在不降低性能的情况下获得图像压缩能力。

基于物体检测的智能相机已应用于许多物联网 (IoT) 场景，例如家庭 [23]、交通 [24]、工厂 [25] 和停车场 [4,26]，这些场景中通常会遇到大量数据。因此，只应传输那些感兴趣的帧。在此情况下，需要检测来找到那些感兴趣的帧，而图像压缩则用于数据传输。例如，在家庭监控中，大多数情况下相机不应将正常图像传输给房主，除非检测到某些事件，如入侵、人员跌倒等。此外，在工厂质量检测线上，相机被部署用于质量检测。只有在检测到不合格产品时，它们才会传输图像信息。

从系统角度来看，无线智能相机通常使用可重现现场可编程门阵列 (FPGA) 和片上系统 (SoC) 实现。近年来，已引入多个面向基于 CNN 的图像分类应用的硬件加速嵌入式系统 [27–31]。然而，与图像分类任务不同，物体检测计算量大得多且耗能更高，因为需要评估大量可能的物体候选区域。直到最近，研究人员才能够使用嵌入式系统实现轻量级基于 CNN 的物体检测算法 [32,33]。

