
Micro-expressions (MEs), brief and uncontrollable facial movements that last only a fraction of a second, are windows into the innermost thoughts and emotions of others. In the past decade, MEs analysis techniques have evolved gradually from psychological-based to computer vision-based due to the ongoing advancement of computer technology. An essential component of MEs analysis called MEs spotting has drawn increasing attention. Recently, a few review articles on MEs have been released, however the majority of them lacked a thorough examination of MEs spotting and instead concentrated mostly on MEs recognition. Therefore, this review article aims to conduct an analysis of the methods, uses, and constraints of MEs spotting, a key aspect of non-verbal communication analysis. The review starts out by exploring the psychological and physiological bases of MEs and explaining their evolutionary significance as well as their applicability in various social circumstances. MEs spotting are used in psychology to evaluate emotional states, spot dishonesty, and guide psychotherapeutic therapies. MEs spotting improve empathy and general awareness of emotional cues in interpersonal interactions. The article, however, is not afraid to confront the major issues facing the discipline, such as the cultural and contextual heterogeneity of MEs, ethical issues, and the requirement for ongoing training to maintain spotting accuracy. In summary, this review article functions as an all-encompassing reference for individuals in the fields of research, practical application, and education who have an interest in the diverse area of identifying malicious entities. It underscores the interdisciplinary nature of this field and its potential to revolutionize human interaction analysis, decision-making processes, and emotional well-being across a spectrum of applications.

Keywords: Micro-expressions spotting, non-verbal communication, spot dishonesty, decision making, contextual heterogeneity

## Introduction

Facial expressions, which serve as outward manifestations of inner emotions, allow us to quickly determine a person’s psychological state. Only 7% of human interactions are vocal, and the remaining 38% are spoken, with facial emotions accounting for up to 55% of communication (Mehrabian, 1968). Accordingly, the facial expressions can be broadly categorized as macro-expressions and micro-expressions (MEs) (Xie, et al. 2022). The macro-expressions, can appear in any circumstance and last anywhere between 0.5 and 4 seconds. Due to the obvious facial muscle movements, they are relatively simple to spot. MEs, on the other hand, are quick and involuntary facial movements, usually exhibits only for less than half a second (Yan et al. 2013; Mandal and Awasthi, 2015). The significance of MEs comes from their potential to reveal hidden emotions that are beneficial for finding information related to law enforcement and security (O’Sullivan et al., 2009), healthcare (Endres and Laidlaw, 2009), and deciphering the intentions of business counterparts in negotiations (Chun et al., 2015; Suen et al., 2019).

检测和识别是分析表情运动（MEs）的两个关键过程。检测旨在识别特定视频中 MEs 的存在，并精确定位其出现的瞬间。而识别后的 MEs 则会被分类到喜悦、悲伤、愤怒、恐惧、惊讶、厌恶或轻蔑等情绪状态中。尽管检测和识别都至关重要，但检测通常是 MEs 分析中更为困难的环节，且在近期研究中相对较少受到关注。因此，从视频序列中检测出 MEs 的时间段称为 MEs 检测，而找出短视频中强度最高的帧（即高潮帧）是 MEs 检测的主要目标。视频的开始和结束分别对应每个 ME 的起始和终止时长。在此，起始帧、高潮帧和终止帧分别代表肌肉运动开始增长、面部表情达到高峰以及肌肉恢复到中性状态，([Valtar and Pantic, 2012)。已有若干最近的报告 (`Li et al., 2018`; `Oh et al., 2018`; `Takalkar et al., 2018`; `Goh et al., 2020`; `Xie et al., 2020`; `Pan et al., 2021`; `Zhou et al., 2021`; `Ben et al., 2022`; `Esmaeili et al., 2022`; `Gong et al., 2022`; `Li et al., 2022`; `Verma et al., 2023`) 就 MEs 分析发表了论文，如 `Table 77.1` 所示。根据 `Table 77.1`，几乎所有出版物都评估了 MEs 识别方法，只有少数研究涉及 MEs 区间和高潮检测。在识别面部恶意实体时，典型的预处理步骤包括检测和跟踪面部关键点、注册和面部面罩、以及检索面部区域。

根据现有研究，面部表情（ME）分析应分别对面部的上下部分进行单独处理，而不是对整个面部进行，最初的面部图像被划分为三个区域（`Porter and ten Brinke, 2008`；`Shreve et al., 2009`）。随后，在现代方法中，面部图像被分割为对应所需的表情动作单元（AUs）的感兴趣区域（ROIs）（`Davison et al., 2018`；`Liong et al., 2015`；`Li et al., 2018`）。

## 微表情检测

面部微表情检测属性是通过自动检测微表情在视频序列中的时间或时间间隔，即“时刻”来实现的。 “顶点和间隔”检测是当前用于检测面部微运动的两种方法，它们可能传达人的真实情绪。近年来用于检测面部微表情的现有技术总结如下 `Table 77.3`。

Table 77.3 Few of the existing techniques employed for spotting a facial Es

| 年份/参考文献 | 目的 | 使用的特征 | 运动（M）/顶点（A） | 检测技术 | 使用的数据集 | 结论 | 挑战和未来方向 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 2009/`Polikovsky et al., 2009`[¹] | 利用高速摄像机和三维梯度描述符识别面部恶意实体 | 三维梯度直方图 |  | K-均值聚类 | `Polikovsky` | 该方法可被视为动作单元，用于精确分析 | 该方法无法直接测量表情持续时间 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 2008/`Porter and ten Brinke, 2008`[²] | 将连续且变化的表情从面部视频中分割出来，基于应力模式 | 光学应力 | M | 阈值技术 | USF, BU | 该方法能够自动检测宏表情和微表情，并在 USF 和 BU 数据集中实现 100% 的准确率 | 在 USF 数据集中，微表情检测表现不佳，眼动跟踪算法可能有助于精确划分面部区域，同时计算时间可降低并提高鲁棒性 |
| 2011/`Shreve et al., 2011`[³] | 自动检测长视频中的面部表情，包括微表情和宏表情，通过时间分割逐帧分析视频 | 光学应力 |  | 阈值技术 | USF-HD | 宏表情检测最高达 85% 的准确率，所有微表情的检测准确率为 74% |  |
| 2013/`Wang et al., 2017`[⁴] | 利用 FACS 检测并描述高速视频中的面部微表情 | 三维梯度直方图 |  | K-均值聚类 | `Polikovsky` | 该方法提供了更精细的微表情时序特征描述 | 该方法仅用于评估假装的面部恶意实体，实验以分类任务进行，不适用于实时检测 |
| 2014/`Polikovsky et al., 2013`[⁵] | 通过外观特征差异分析自动检测视频中的快速面部运动 | LBP | M | 阈值技术 | CASME-A CASME-B SMIC-VIS-E | 通过阈值化中心帧的 LBP 卡方距离以及首尾帧的平均值，检测出自发微表情，并提供面部区域中运动的空间位置信息 | 可采用仿射变换进行图像注册以校正姿态，提高长视频的鲁棒性；需要更自适应的阈值计算 |
| 2015/`Davison et al., 2015`[⁶] | 利用梯度方向直方图（HOG）作为特征描述符，识别细微面部运动 | HOG | M | 阈值技术 | 院内数据集 | 实现了 0.8429 的召回率和 0.7672 的 F 测度 | 可结合空间和时间维度的特征变化，以及使用正弦距离指标和归一化直方图的地球移动距离，该方法适用于多种特征描述符和额外数据集 |
| 2015/`Patel et al., 2015`[⁷] | 通过预定义算法确定恶意实体的起始和结束帧，并找到峰值 | 空间时态集成的 OF 向量 | M | 阈值技术 | SMIC-VIS-E | 实现了 95% 的 AUC，平均起始误差为 1.14（标准差 3.68），平均结束误差为 -0.55（标准差 3.52） | 结合识别与检测的方法可用于检测 AU 并降低假阳率 |
| 2016/`Xia et al., 2016`[⁸] | 通过几何变形建模实现自发微表情的检测 | 几何运动、变形 | M | 随机游走模型 | CASME, SMIC | 该框架使用的特征可以通过局部化方法进一步改进 |  |
| 2018/`Li et al., 2018`[⁹] | 分析自发微表情检测和识别方法 | HOOF, LBP |  | 阈值技术 | CASME II SMIC-E-HS SMIC-E-VIS SMIC-E-NIR | 开发了基于特征差异对比和峰值检测的自动微表情分析系统（MESR） | 检测每个微表情的峰值时间点及结束帧可用于进一步分析；结合 AU 检测与 FD 过程可帮助识别非微表情运动 |
| 2018/`Davison et al., 2018`[¹⁰] | 利用 3D 梯度方向直方图（3D HOG）时间差分法检测微运动 | 3DHOG, LBP, OF |  | 阈值技术 | SAMM, CASME II | 在 SAMM 和 CASME II 上分别获得 0.7512 和 0.7261 的 AUC | 需要提高特征提取和预处理的速度，并实现实时分析 |
| 2019/`Li et al., 2019`[¹¹] | 利用局部时间模式（LTP）和局部二值模式（LBP）检测长视频序列中的微表情 | LBP-χ2 |  | 阈值技术 | SAMM, CASMEII | LTP-ML 在 SAMM 和 CAS(ME)² 上的 F1 得分分别为 0.0316 和 0.0179 | 强调仅在增强区分微表情与其他面部运动的能力，以减少与深度学习相关的面部点数 |
| 2020/`Ying [He et al., 2020]`[¹²] | 采用主方向最大差分分析（MDMD）检测长视频序列中的宏表情和微表情区间 | MDMD |  |  | SAMM, CAS(ME)² | 在 CAS(ME)² 上得到宏表情和微表情的 F1 得分分别为 0.1196 和 0.0082；在 SAMM 长视频上得到 0.0629 和 0.0364 | CAS(ME)² 上的假阳子数量非常高，需要降低假阳子率 |

[¹]: `Polikovsky et al., 2009`
[²]: `Porter and ten Brinke, 2008`
[³]: `Shreve et al., 2011`
[⁴]: `Wang et al., 2017`
[⁵]: `Polikovsky et al., 2013`
[⁶]: `Davison et al., 2015`
[⁷]: `Patel et al., 2015`
[⁸]: `Xia et al., 2016`
[⁹]: `Li et al., 2018`
[¹⁰]: `Davison et al., 2018`
[¹¹]: `Li et al., 2019`
[¹²]: `He et al., 2020`

| 2021/Yap et al., 2022 || 通过使用浅层光流三流 CNN 来检测长视频中的宏观和 MEs || SOFTNet ||  ||  || SAMM, CAS(ME)² || 本研究提出了一种新的回归策略，在 CAS(ME)²和 SAMM 数据集上分别实现了总体 F1 分数 0.2022 和 0.1881 || 为了检测宏观和 MEs，需要进行创新的建模以处理局部面部过渡和强健的峰值检测 |
| 2021/Gupta, 2023 || 利用创新的卷积神经网络（CNN）在长视频中检测多尺度自发 ME 间隔 || MESNet ||  ||  || SAMM, CAS(ME)² || MESNet 的 CPN 和 CRN 在 CAS(ME)²和 SAMM 数据集上分别实现了最高 F1 分数 0.028、0.036 和 0.077、0.088，并发现大多数 MEs |
| 2022/Yap et al., 2022 || 利用带有时间定位帧跳的 3D-CNN 在长视频序列中检测宏观和 MEs || 局部对比度归一化（LCN） ||  ||  || SAMM-LV, CAS(ME)² || 该技术在高帧率（200 fps）长视频序列（SAMM-LV）上实现了 0.105 的 F1 分数，并被认为在与低帧率（30 fps）数据集（CAS(ME)²）相比具有竞争力 || 该技术包括人脸关键点检测算法的降级。此外，为实时 ME 分析分配更多计算资源，简化的检测算法需要被分配 |

### Challenges and future directions

#### Challenges in availability of MEs dataset

The rationale for the scarcity of datasets includes spontaneous MEs (Takalkar et al., 2018; Zhou et al., 2021).
