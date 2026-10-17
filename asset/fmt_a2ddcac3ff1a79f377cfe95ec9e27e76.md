
2015 年，Ref. `[9]`进行了早期的 ML 辅助 MCI 诊断尝试。该项目结合了使用同一 306 通道 Vectorview 系统采集的多个 MEG 数据库，最终获得 102 例 MCI 和 82 例 HC 的数据。计算了各频段的互信息作为特征，包括θ（4–8 Hz）、α（8–12 Hz）、β（12–30 Hz）、γ（30–45 Hz）以及宽带（2–45 Hz）。经评估多种分类器并对参数进行优化，包括随机森林、贝叶斯网络、C4.5 决策树、k 近邻、逻辑回归和支持向量机。采用 Bootstrapping 进行交叉验证。优化后的结果为灵敏度 100%、特异度 69%、分类准确率 83%。这些使用 MEG 的首次结果相当有前景，尤其考虑到参与人数相对较多。

如前所述，EEG 用于 AD 检测已取得相当好的性能 `[7]`，而 EEG 用于 MCI 检测往往不够有效 `[8]`，可能是由于 EEG 系统的电极数量相对较少。相反，MEG 凭借更大的传感器数量可能缓解这一问题。例如，研究人员利用 148 通道 MEG 系统成功区分 MCI 和 HC，成功率达 98.4% `[10]`。参与者（18 例 MCI，19 例 HC）在数据采集时进行字母记忆任务。采用完整经验模态分解（CEEMD）进行特征提取，随后利用 permutation entropy 分析计算非线性动力学度量。增强概率神经网络（EPNN）被用于分类。得益于 CEEMD，该方法在非平稳信号（如 E/MEG）处理中表现出色，其相关变换在其他 EEG 应用中也被证明有效 `[11]`。

-   表 8.1 列出了几份具有代表性的使用 E/MEG 进行 MCI/AD 分类的报告。对于基于机器学习的系统，我们发现 SVM 和神经网络是两种最流行且表现最好的分类器。研究者倾向于在数据采集时让参与者处于休息状态。已在时间域和频率域开发了各种生物标记，以捕获信号中的有价值信息。熵相关特征表现出良好的识别性能 `[10]`，这可能与 MCI 由于脑功能减退而出现的情况有关。值得注意的是，相对不常用的数据变换，如 CMMED，表现出相当有前景的结果，其原始形式的经验模态分解（EMD）专门设计用于分析非平稳信号，如 E/MEG。

**表 8.1 传感器级别 MCI/AD 诊断的最新报告**

| **状态、模态与目的** | **方法** | **参与者** | **性能与年份** |

| --- | --- | --- | --- |

| 休息状态 & 148 通道 MEG & AD vs. HC | 分散熵（DisEn）+ `t` 检验 | 36 AD, 26 HC | HC 表现出比 AD 更不规则的 MEG。2016 `[2]` |

| --- | --- | --- | --- |

| 工作记忆任务 & 32 通道 EEG & AD vs. MCI vs. HC 分类 | 工作记忆 ERP + ICA + k-mean 聚类 + Kruskal–Wallis 统计检验 | 15 AD, 20 MCI, 26 HC | 异常组 P450 下降。2017 `[3]` |

| --- | --- | --- | --- |

| 休息、记忆和视觉空间任务 & 64 通道 EEG & MCI vs. HC | 相对功率 + ANOVA + `t` 检验 | 11 MCI, 11 HC | Theta 敏感。2017 `[4]` |

| --- | --- | --- | --- |

| 休息状态闭眼 & 19 通道 EEG & AD vs. MCI vs. HC | 相对功率、α 频率、熵、Lempel–Ziv 复杂度等 + FCBF + MLP | 37 AD, 37 MCI, 37 HC | HC 与 (MCI & AD)：灵敏度 82.35%，正预测值 84.85%。AD 与 (MCI & HC)：特异性 79.41%，负预测值 84.38%。2018 `[5]` |

| --- | --- | --- | --- |

| 超通气、清醒、困倦、清醒，以及闭眼和睁眼期间，使用 19 通道 EEG & AD vs. HC | Tsallis 熵（TsEn）、Higuchi 分形尺寸（HFD）和 Lempel–Ziv 复杂度（LZC）+ `P` 值 + SVM | 20 AD, 32 HC | 使用 LZC：灵敏度 100%，特异性 92.31%，识别准确率 95%。2018 `[6]` |

| --- | --- | --- | --- |

| 清醒放松状态闭眼 & 16 通道 EEG & AD vs. HC | PDI + GIC + ANOVA + SVM | 14 AD, 14 HC | 准确率 98.9%。2018 `[7]` |

| --- | --- | --- | --- |

| 词汇处理任务 & 19–32 通道 EEG & MCI 非转换者 vs. MCI 转换者 vs. 老年 HC | 试次间负相关 + SVM | 25 失忆型 MCI, 11 老年 HC | 敏感性 80%，特异性 95%。2018 `[8]` |

| --- | --- | --- | --- |

| 闭眼休息状态 & 306 通道 MEG Vectorview 系统 & MCI vs. HC | 互信息（θ、α、β、γ 和带宽）+ 多类分类器自助抽样 | 102 MCI, 82 HC | 100% 敏感度，69% 特异度，83% 分类准确率。2015 `[9]` |

| --- | --- | --- | --- |

| 记忆字母任务 & 148 通道 MEG & MCI vs. HC | CEEMD + 置换熵 + ANOVA + EPNN HC | 18 MCI, 19 | 98.4% 识别准确率。2016 `[10]` |

### 8.3 源级分析

由于源重建（SR）的复杂性和逆问题 ill-posed，与传感器级分析相比，在该领域的尝试相对较少。然而，从原则上讲，源级分析的主要吸引力在于可以确定大脑中的源点位置，这对于 MCI/AD 的早期诊断特别有用。

早期研究将 SR 与机器学习结合，使用 128 通道 EEG 系统进行 AD 诊断 `[12]`。数据采集时，有 17 位 AD 患者和 17 名健康对照者在闭眼休息状态下参与。采用标准低分辨率脑电断层成像（sLORETA）进行源空间重建。从四个传统 EEG 波段（α、β、δ、θ）中提取了 12 个皮层区域的相对对数功率谱密度值。结果表明，右颞叶在所有频段中对两组均有显著差异；在左脑半球，θ 波功率在 AD 患者中增加，而 α 波功率下降。使用 SVM 对 AD 与 HC 组进行分类，敏感度为 75.0%，特异度为 93.7%，准确率为 84.4%。

此外，还探索了多类型 MCI 检测 `[13]`。研究了两种 MCI 类型：单域失忆型 MCI（sdMCI）和多域失忆型 MCI（mdMCI）（分别 22 例 sdMCI 和 30 例 mdMCI），并与 29 名健康对照者进行比较。与许多传统研究一样，数据在休息状态下采集。使用 306 通道 MEG 系统获取传感器级信号，随后采用最小方差束形成技术构建源空间。时间域连接矩阵被用作区分 sdMCI 与 mdMCI 的指标。采用了三种流行分类器：k‑NN、LDA 和 SVM 来测试识别性能。尽管涉及三类，研究重点仍在二元分类组合：HC vs. sdMCI 86.27%，HC vs. mdMCI 81.36%，sdMCI vs. mdMCI 84.62%。鉴于 MCI 检测相较 AD 检测的明显难度，这些结果相当有前景，表明源级诊断具有巨大潜力。

2017 年，一项采用加权最小范数估计（weighted minimum norm estimate）进行源空间重建的工作被提出 `[14]`。计算了多次参与的 PSD 系数并输入 Mahalanobis 距离分类器，采用五倍交叉验证优化结果。发现所提特征与 AD 受试者的记忆障碍显著相关。随着参与者人数增加，AD 与 HC 的分类性能显著下降 `[14]`。与 2013 年的 Ref. `[12]` 相比，AD 与 HC 参与者（休息状态）均从 17 增加到 25，Ref. `[14]` 中报告的分类率从 84.4% 降至 78.4%。2017 年的 Ref. `[14]` 使用了更先进的 306 通道（Elekta Neuromag）MEG 系统，这可能暗示社区目前需要一个标准化的比较方案，以证明研究的意义。

-   [最近的一项研究](https://wiki.example.org/feynmans_learning_method)指出了基于机器学习（ML）辅助诊断系统当前研究中的一个重要问题。该研究采用了五倍交叉验证，报告了 98%的高分类率，而当使用留一出交叉验证（leave-one-out cross-validation）对系统进行评估时，相同的生物标记仅实现了约 70%的准确率。具体而言，从 24 名轻度认知障碍（MCI）患者和 30 名健康对照（HC）受试者采集了 MEG 数据，使用 306 通道 Elektra Vectorview 系统，受试者保持休息状态 4 分钟。采用线性受限最小方差（LCMV）束 former 进行源重建；计算了三种连接估计器：相位锁定值（PLV）、相位锁定值的虚部（iPLV）以及包络相关性（CorrEnv），并将其作为神经标记。分类结果使用带核的支持向量机（SVM）生成。相关讨论将在下一节中呈现。

-   最近的一项研究表明，数据量的增加会显著影响类内差异。该研究在 Ref. `[16]`中涉及 75 名 MCI 患者和 75 名 HC 受试者，报告了 73%的灵敏度、64%的特异度以及 68.5%的准确率。与同年发表的 Ref. `[15]`相比，这些结果显著下降。参与者人数增加 2~3 倍，观察到分类性能出现显著下降。在 Ref. `[16]`的研究中，仅使用 19 通道 EEG 系统收集数据，随后采用 eLORETA 和基于 FFT 的功率谱分析进行源分析和特征提取，采用 SVM 和 ANOVA 进行分类和评估。

Table 8.2 provides some reports on the source-level MCI/AD detections. Similar to Table 8.1, it is found the SVM is one of the most popular classifiers. Compared to the sensor-level approaches, source space analysis for the MCI/AD classification appears to be slightly worse. This is not too surprising: the source reconstruction algorithms are designed for the points localization; additional research needs to be done to better facilitate both the classification and localization.

TABLE 8.2 Recent Reports on MCI/AD Diagnosis in the Source Level

| **State, Modality & Purpose** || **Method** || **Participants** || **Performance & Year** |

| --- | --- | --- | --- |

| Resting state with eyes closed & 128-channel EEG & AD vs. HC || sLORETA + Band PSDs + SVM || 17 AD, 17 HC || Sensitivity 75.0%, specificity of 93.7%, and accuracy of 84.4%. 2013 `[12]` |

| --- | --- | --- | --- |

| Resting state & 306-channel MEG system & HC vs. sdMCIs; HC vs. mdMCIs; mdMCIs vs. sdMCIs || Minimum variance beamformer + time-domain connectivity matrix + k-NN, LDA, SVM || 22 sdMCIs, 30 mdMCIs and 29 HC || HC vs. sdMCI 86.27%, HC vs. mdMCI 81.36% and sdMCI vs. mdMCI 84.62%. 2014 `[13]` |

| --- | --- | --- | --- |

| Resting-state with eyes-closed & 306-channel Elekta Neuromag MEG system & AD vs. HC || Weighted minimum norm estimate + multi-participation PSD features + Mahalanobis distance classifier || 25 AD, 25 HC || Specificity = 65.68%, sensitivity = 91.11%, the best classification accuracy 78.39%. 2017 `[14]` |

| --- | --- | --- | --- |

| Four minutes of resting state & 306- channel Elekta Vectorview system & MCI vs. HC || LCMV beamformer + PLV + iPLV + CorrEnv + intra and cross-frequency estimators + SVM with RBF kernel || 24 MCI, 30 HC || Five-fold cross-validation: 98% accuracy; leave-one-out cross-validation: 70% accuracy. 2018 `[15]` |

| --- | --- | --- | --- |

| Resting-state & 19-channel EEG & MCI vs. HC || eLORETA + FFT-based power spectral analysis + SVM + ANOVA || 75 MCI, 75 HC || Sensitivity of 73% and specificity of 64%, an accuracy of 68.5%. 2018 `[16]` |

## 8.4 Discussion and Conclusion

In this chapter, we discussed a few recent researches on ML-aided MCI/AD diagnosis. It is noted that with the development of ML techniques in other fields, the integration of ML into clinical practice has become increasingly popular. However, it is admitted that currently there is no practically available ML-aided diagnosing system officially used in the actual clinical cases. This is not just an academic matter, but also an issue of trust: patients usually would not risk to solely put their faith on a machine. This is one big obstacle that prevents academic achievements from implementing in the real-world clinical practices.

Traditionally, the computer-aided MCI/AD diagnosis was mainly focusing on the statistical analysis of data; the current new trend aims to combine the statistical analysis with ML algorithms. This completes the pipeline of a typical expert system and makes such diagnosis systems truly automated. With the inclusion of ML modules, it also establishes a standardized framework from a statistical perspective (as opposed to the visual inspection of the plotted performance); within such framework, the evaluation of the systems becomes more objective: the well-recognized metrics in the ML field, such as sensitivity, specificity and recognition accuracy, provide a clearer reflection of the diagnosis performance than the conventional computer-aided systems in the clinical community.

In spite of the promising results for ML-aided MCI/AD diagnosis in recent years, a few issues are noticed in designing the detection systems and need to be carefully addressed for improvement in the future. These important factors are listed as follows:
