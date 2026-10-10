
| B | 58.79 | 73.92 | 88.18 | 55.95 | 66.33 | 34.57 | 64.99 | 22.07 |

| C | 45.91 | 85.19 | 98.16 | 50.62 | 71.45 | 20.67 | 67.5 | 10.0 |

| RES | 62.37 | 88.53 | 86.65 | 74.18 | 72.5 | 18.7 | 57.92 | 15.12 |

| SOA | 51.79 | 96.9 | 72.4 | 48.26 | 42.16 | | | |

表 2（续）。使用留一被试法（LOSO）获得的分类器准确率 H1（第 1 行）和 F1 分数（第 2 行）的实验结果。

| | WESAD | DEAP | MAHNOB-HCI | EESD |

| :--- | :--- | :--- | :--- | :--- |

| | 愉悦度 | 唤醒度 | 愉悦度 | 唤醒度 | 愉悦度 | 唤醒度 | 愉悦度 | 唤醒度 |

| ITMDER | 59.65 | 13.46 | 0.572 | 0.721 | 85.86 | 17.73 | 89.26 | 17.79 |

| H | 80.54 | 89.29 | 91.27 | 31.47 | 80.91 | 21.01 | 82.4 | 23.7 |

| E | 50.03 | 51.10 | 72.91 | 12.92 | 58.81 | 25.12 | 66.73 | 23.1 |

| F | 87.85 | 86.91 | 81.96 | 49.36 | **93.75** | 99.25 | 64.25 | 16.35 |

| B | 58.79 | 73.92 | 88.18 | 55.95 | 66.33 | 34.57 | 64.99 | 22.07 |

| C | 45.91 | 85.19 | 98.16 | 50.62 | 71.45 | 20.67 | 67.5 | 10.0 |

| RES | 62.37 | 88.53 | 86.65 | 74.18 | 72.5 | 18.7 | 57.92 | 15.12 |

| SOA | | | | | 51.79 | 96.9 | 72.4 | 48.26 | 42.16 |

表 3。在 4 折交叉验证中，针对唤醒度和愉悦度，各数据集和传感器模态所使用的分类器：K 近邻（k-NN）；决策树（DT）；随机森林（RF）；二次判别分析（QDA）。

| | WESAD | DEAP | MAHNOB-HCI | EESD |

| :--- | :--- | :--- | :--- | :--- |

| | 愉悦度 | 唤醒度 | 愉悦度 | 唤醒度 | 愉悦度 | 唤醒度 | 愉悦度 | 唤醒度 |

| ITMDER | | | | | | | | |

| 手部 EDA | | | | | | | | |

| 指部 EDA | | | | | | | | |

| 心电图 | | | | | | | | |

| 血压图 | | | | | | | | |

| 呼吸 | | | | | | | | |

### 4.4. 决策级融合与特征级融合

在本小节中，我们展示了决策级融合（DF）和特征级融合（FF）方法的实验结果。

表 6 展示了在 5 个研究数据集中，针对唤醒度和愉悦度维度的准确率和 F1 分数实验结果，并与一些最先进结果进行了对比。可以看出，我们的两种技术在愉悦度维度上表现尤为突出，均优于 ITMDER [7] 的结果。同样，在 DEAP 数据集 [8] 中，我们仅在愉悦度维度上未能取得成功，但取得了具有竞争力的结果，并在 F1 分数上实现了超越。

另一方面，在 MAHNOB-HCI 数据集 [53] 中，我们的方案未能达到文献中的结果。由于据我们所知，尚无最先进结果被应用于情绪识别（ER），因此针对 EESD 和 WESAD 数据集未呈现最先进结果。因此，我们将本论文中评估的未探索情绪维度作为对比基准；当比较 DF 与 FF 时，FF 的性能在 EESD 数据集的唤醒度和愉悦度量表上均超越了 EESD 数据集。对于其余数据集，两种技术均取得了非常有竞争力的结果。关于计算时间，FF 比 DF 更具竞争力，与 DF 相比，其平均执行时间低了两个数量级（语言：Python 3.4；内存：16 GB 2133 MHz LPDDR3；处理器：2.9 GHz Intel Core i7 四核）。

表 7 展示了在 FF 方法中，针对唤醒度和愉悦度维度，各数据集和传感器模态所使用的分类器。

实验结果显示，所选分类器为：2 个 QDA；1 个 SVM；1 个 GNB；1 个 DT（针对唤醒度量表）；以及 2 个 RF；1 个 SVM；1 个 GNB；和 1 个 QDA（针对愉悦度量表）。这些结果再次表明，对于各数据集。此外，表 8 展示了在 FF 方法中，针对唤醒度和愉悦度维度，各数据集和传感器模态所使用的特征。

结果还显示，与 SL 方法类似，大多数特征是特定于给定数据集的，在所有数据集的特征选择步骤中，通过顺序前向选择（SFS）获得的公共特征数量为零。

总之，本文探索了文献中尚未报道的新情绪维度和评估指标，并取得了与现有最先进水平相似或具有竞争力的结果。实验结果显示，在使用 SL 的 FF 和 DF 之间，所得结果非常相似，且表现最佳的方法在很大程度上取决于数据集。在 SL 分类器结果中，表现最佳的传感器模态尚不确定。同时，DF 方法展示了更高的计算和时间复杂度。因此，考虑到这些要点，我们选择 FF 方法作为最佳模态融合选项，因为通过单一分类器和预选特征，以较低的处理时间和计算复杂度即可达到较高的结果。

表 6。FF 和 DF 方法在 FF 方法中的实验结果。使用 LOSO 获得的结果。列中包含各数据集 MAHNO-HCI [ITMDER]、[DEAP] 的准确率（A）、F 分数（F1）和以秒为单位的时间（T）结果。最佳结果以粗体显示。

| | WESAD | DEAP | MAHNOB-HCI | EESD |

| :--- | :--- | :--- | :--- | :--- |

| | 愉悦度 | 唤醒度 | 愉悦度 | 唤醒度 | 愉悦度 | 唤醒度 | 愉悦度 | 唤醒度 | 愉悦度 | 唤醒度 | 愉悦度 | 唤醒度 |

| FF | 66.7 | 9.0 | 58.1 | 10.2 | 75.0 | 14.8 | 60.0 | 18.4 | 56.7 | 22.5 | 68.7 | 22.2 |

| A | 86.7 | 17.3 | 92.2 | 12.4 | 58.0 | 6.1 | 63.8 | 15.6 | 62.7 | 10.2 | 75.4 | 17.9 |

| F1 | | 50.9 | 23.5 | 95.0 | 12.9 | 71.8 | 7.8 | 72.9 | 14.1 | 72.5 | 24.7 |

| T | | | 1.35 | 0.0 | | | 0.6 | 0.7 | | | 0.01 | 0.0 |

表 7。在 FF 方法中，针对唤醒度和愉悦度维度，各数据集和传感器模态所使用的分类器。使用 4 折交叉验证获得的结果。

| | WESAD | DEAP | MAHNOB-HCI | EESD |

| :--- | :--- | :--- | :--- | :--- |

| | 愉悦度 | 唤醒度 | 愉悦度 | 唤醒度 | 愉悦度 | 唤醒度 | 愉悦度 | 唤醒度 | 愉悦度 | 唤醒度 | 愉悦度 | 唤醒度 |

| SVM | | | | | | | | | | | | |

| GNB | | | | | | | | | | | | |

| QDA | | | | | | | | | | | | |

| GNB | | | | | | | | | | | | |

| DT | | | | | | | | | | | | |

| RF | | | | | | | | | | | | |

| A | 86.7 | 17.3 | 92.9 | 12.0 | 57.0 | 55.2 | 56.9 | 8.2 | 62.7 | 35.9 | 68.7 | 22.6 |

| F1 | 19.4 | 34.4 | 95.9 | 10.7 | 53.8 | 23.3 | 70.7 | 6.0 | 62.5 | 16.6 | 67.5 | 22.0 |

| T | | | 0.02 | 0.0 | | | 0.07 | 0.02 | | | 0.01 | 0.03 |

#### 表 8. 在FF方法中，针对不同数据集和传感器模态所使用的特征。使用4折交叉验证在唤醒度（Arousal）和效价（Valence）维度上获得的结果。

| | WESAD | DEAP | MAHNOB-HCI | ESDD |

|---|---|---|---|---|

| **ITMDER** | EDA_H_emets_spectrum_mean BVP_medien Resp_statistic_hist64 | Resp_serene_sadit vp_phasic_rate_total_energy EDA_row_min_mandiff Resp_statistic_b625 | Resp_InhRatio_rate_maxpeaks Resp_InhRatio_rate_cross BVP_median_dist Resp_zero_cross ECG_statistic_hist43 | Resp_InhRatio_rate_min ECG Resp_onsets_mandiff EDA_onsets_spectrum_hist62 EDA_onsets_statistic_hist5 |

| **IT** | EDA_H_peaksOnVid_minAmp BVP_EDRVolRatio_total_energy EDA_F_cnets_statistic_hist112 | EDA_H_hist_dist BVP_hist_dist BVP_statistic_hist49 EDA_line_distance BVP_hr_maxAmp | Resp_statistic_hist60 Resp_inhale_dist Resp_inhale_mandiff Resp_onsets_statistic_5 | Resp_exhale_max EDA_amplitude_kurtans Resp_amplitude_mean BVP_statistic_hist35 Resp_zero_min_mandiff EDA_onsets_spectrum_statistic_hist22 |

## 5. 结论与未来工作

在过去十年中，情感计算领域得到了发展，创建了许多数据集[6–95]，然而，在以下方面缺乏整合：(1) 预期性能的范围是什么；(2) 对于情绪识别（ER），每种模态的最佳传感器模态、单个学习（SL）分类器和特征的定义是什么；(3) 处理多模态及其限制的最佳技术是什么（FF或DF）；(4) 分类模型的选择。因此，在本工作中，我们研究了在两个维度上对低情绪反应的识别：唤醒度（Arousal）和效价（Valence），涉及五个常见的公开可用数据集。为此，我们使用了易于通过普及技术测量的生理数据，即ECG、RESP和BVP数据。然后，为了处理多模态，我们使用了两种技术：FF和DF。

我们在以下方面扩展了现有技术：(1) 系统地对SL、FF和DF的情绪识别分类性能进行基准测试；(2) 总结准确率和F1分数；(3) 对每种模态的SL分类器和扩展特征进行系统分析。我们能够为所选数据集获得文献中尚属新颖的重要结果。实验结果表明，FF是最具竞争力的技术。

对于未来工作，我们确定了以下方向：(1) 获取数据以开发基于受试者的模型，因为情绪具有高度的受试者依赖性，根据文献[11]，这将导致更高的分类性能；(2) 在FF中通过集群对用户进行分组，并在考虑情绪检测时予以考量；(3) 如第4.3节所述，我们使用了SFS方法来选择在所有测试技术中使用的最佳特征集，然而，这并不是最优的，因此应测试使用额外特征选择技术的分类结果；(4) 最后，我们的工作高度依赖于深度学习技术，该方法关注特征工程和数据表示学习方法的探索与比较，侧重于性能和可解释性方面。

**作者贡献：** 概念化，A.F.；概念化，C.W.；资金获取，C.W.；验证，P.B.；撰写–初稿，P.B.；撰写–审阅与编辑，H.S.；监督，H.S. 所有作者已阅读并同意发表该手稿的最终版本。

**资助：** 本工作部分由新华网未来媒体融合研究院在S-0003-LX-19项目下资助，由西班牙教育与竞争力部与欧洲区域发展基金（ERDF）共同资助（PhysComp项目）在TIN2017-85409-P项目下资助，并通过FCT/MCTES的国家资金以及当适用时的欧盟共同资金在UIDB/EEA/5000项目下资助。

**利益冲突：** 作者声明没有利益冲突。资助方在研究设计、数据收集、分析或解释、手稿撰写或发表结果的决定中均未发挥作用。

## 附录 A

![](img/601340ca744b738277eef45ff127492a_471_0.png)

**图 A1.** 在所有数据集中，针对唤醒度（Arousal）和效价（Valence）轴，SL（监督学习）方法中使用的特征比较（a, b）。有关特征的更多信息，请参阅作者提供的参考([https://github.com/PIA-Group/BioSPPy])。

## 参考文献

- Greenberg, L.S.; Safran, J. Emotion, Cognition, and Attention. In *Theoretical Foundations of Behavior Therapy*; Springer: Boston, MA, USA, 1987; pp. 295–311. [Ref]

- Shu, L.; Ji, J.; Yang, M; Li, Z.; Liao, D.; Xu, X.; Yang, A. A Review of Emotion Recognition using Physiological Signals. *Sensors* 2015, 18, 44 [PubMed]

- Paul, E. Anger for argument basis. *Cogen. Genet.* 1992, 6, 169–200. New York, NY, USA, 1994.

- Damasio, A.R. *Error of Error: Emotion, Reason, and the Human Brain*; New York, NY, USA, 1994.

- Lang, J. The emotion process: Studies of motivation and attention. *Psychol.* 1995, 50, 372–385 [Ref]

- Schmid, P.; Risse, A.; Duerchen, R.; Martinez, G.; Van Laervo, K. Introducing Multimodal Data for Wearable Stress and Detection. In *International Conference on Multimodal Interaction*, BOLD, CO, USA, October 2018; pp. 400–408. [Ref]

- Pinto, J. Physiological Multimodality for Emotion Assessment. *Master’s Thesis, Instituto Superior Técnico*, Porto, Lisbon, Portugal, 2019.

- Koestra, S.; Wang, C.; Soleymany, M.; Lee, J.; Yazadani, A.; Ebrahimi, T.; Punj, N.; I DEAP: A Database for Emotion Analysis using Physiological Signals. *IEEE Trans. Affect. Comput.* 2012, 3, 18–31 [Ref]

- Schmidt, P.; Weiss, A.; Duerchen, R.; Laerven, K. Variable affect and stress recognition: A review. *arXiv* 2018, arXiv:1811.08855.

- Bota, J.; Wang, C.; Fred, A/L; Silva da, H. Current Trends, Challenges and Possibilities on Emotion Recognition using Machine Learning and Physiological Signals. *IEEE Access* 2019, 7, 140910–140120. [Ref]

- Liu, C.; Rani, P.; Park, S. An empirical study of machine learning techniques for affect human-robot interaction. In *International Conference on Intelligent Robots and Systems*, Edmonton, AB, Canada, 2–6 August 2005; pp. 2662–2667. [Ref]

- Kim, S.M.; Valutti, A.; Calvo, R.A. Evaluation of Unsupervised Emotion Models to Textual Recognition. In *Proceedings of the NAACL HLT Workshop on Computational Approaches to Analysis and Generation of Emotion in Text*, Los Angeles, CA, USA, June 2010; pp. 62–70.
