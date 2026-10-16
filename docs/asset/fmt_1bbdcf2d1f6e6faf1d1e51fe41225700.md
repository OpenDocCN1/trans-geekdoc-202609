
我们考虑了 SuriNet 架构用于可视化学习到的特征。图 12.20 和图 12.21 展示了从控制图像和 COVID-19 图像中提取的特征。品红表示滤波器，黄色表示学习到的特征。图 12.20 和图 12.21 表明，在 SuriNet 的第十一层会产生 256 个滤波器，以 16 × 16 网格形式输出；在第十六层（在向量化之前）会产生 128 个滤波器，以 8 × 16 网格形式输出。滤波器输出网格中包含黄色和品红的混合。部分滤波器输出显示它们在考虑图像的背景信息。例如，在图 12.20 中，第一行第七个输出显示学习到的区域（黄色）是背景，与原图相似；在图 12.20 和图 12.21 中可以看到一些类似的情况。同样，肺部 CT 扫描的关键特征被提取出来，呈现为深黄色，位于肺部区域内，如图 12.20 中第一行第四个滤波器输出所示。此类滤波器输出在 COVID-19 类中比对照类更为常见。直观上，这表明 COVID-19 的特征提取效果优于对照。这些特征的量化由 MFS 表示。

![Figure 12.20. Sample of control class visualization of SuriNet.](img/bk978-0-7503-2244-7ch12f20_online.jpg)

**Figure 12.20.** Sample of control class visualization of SuriNet.

![Figure 12.21. Sample of COVID-19 class visualization of SuriNet.](img/bk978-0-7503-2244-7ch12f21_online.jpg)

**Figure 12.21.** Sample of COVID-19 class visualization of SuriNet.

## 12.5 Discussion

### Benchmarking

我们将所提 AI 模型与现有工作进行了比较。表 12.7 展示了使用 AI 模型进行 COVID-19 研究的现有工作。第 3 列表示研究中使用的数据集，第 4 列表示使用的模型。第 5 列和第 6 列分别给出所取得的准确率和性能指标。Polsinelli *et al* \[39\] 提出了 SqueezeNet 架构，用于对 360 例肺炎和健康 CT 扫描进行分类，并实现了 0.83 的准确率和 0.85 的灵敏度。Hasan *et al* \[40\] 使用直方图阈值隔离 CT 扫描的背景，然后使用 Q-变形熵算法提取特征，并将提取的特征输入长短期记忆（LSTM）神经网络用于肺炎与健康的分类。作者实现了 99.68% 的准确率。Ahuja *et al* \[21\] 提出了基于转移学习的 ResNet18、50、101 以及 SqueezeNet 分类器，用于对分解为三层小波变换的 349 例 CT 扫描进行分类。在所有分类器中，ResNet18 实现了 0.99 的准确率。Singh *et al* \[41\] 研究了 COVID-19 对合并糖尿病的影响。作者使用了 344 例 COVID-19 受影响的 CT 扫描和 358 例非 COVID-19 受影响的 CT 扫描来提取特征，并将其输入集成学习（Bagging）与支持向量机（SVM）组合用于 COVID-19 与非 COVID-19 扫描的分类，取得了 0.957 的准确率以及 0.958 的 AUC。Purohit *et al* \[42\] 提出了一种使用多图像增强技术的 CNN 来分类 COVID-19 与非 COVID-19 CT 扫描，实现了 0.95 的准确率和 94.78% 的灵敏度。Agarwal *et al* \[31\] 提出了九种分类器（ANN、DT、RF、CNN、VGG16、Denesenet121、DenseNet169、DenseNet201、MobileNet），用于利用新型块成像技术将 CT 扫描分类为对照与 COVID-19，取得了 0.994 的准确率，分别来自深度卷积网络（DCNN）和随机森林（RF）。Saba *et al* \[30\] 提出了六种 AI 模型，用于利用 130 例肺部 CT 扫描对 COVID-19 与对照类进行分类。作者通过 bispectrum 表征 COVID-19 肺部，并使用改进的 CNN（修正 sigmoid 函数）分类器实现了 0.996 的准确率。

**Table 12.7.** Benchmarking table.

| 作者 || 数据集 || 模型 || 准确率 || 性能指标 |

| --- | --- | --- | --- | --- |

| Polsinelli *et al* (2020) \[39\] || 757 例 CT 扫描（COVID-19: 360，肺炎: 397） || SqueezeNet || 0.83 || F1 分数: 0.8333 |

| Hasan *et al* (2020) \[40\] || 321 例胸部 CT 扫描（COVID-19: 118，肺炎: 96，健康: 107） || LSTM || 1.00 || — |

| Ahuja *et al* (2020) \[21\] || 728 例肺部 CT 扫描（COVID-19: 349，非 COVID-19: 397） || ResNet18 || 0.99 || — |

| Singh *et al* (2020) \[41\] || 702 例肺部 CT 扫描（COVID-19: 344，非 COVID-19: 358） || 集成学习与 SVM || 0.957 || AUC: 0.958，F1 分数: 95.3% |

| Purohit *et al* (2020) \[42\] || 690 例肺部 CT 扫描（COVID-19: 345，非 COVID-19: 345） || 提出的 CNN || 0.95 || 灵敏度 94.78%，特异度 95.98% |

| Agarwal *et al* (2021) \[31\] || 60 名意大利患者的肺部 CT 扫描（对照: 30，COVID-19: 30） || CNN、RF || 0.994, 0.994 || 0.991, 0.998（*p* < 0.0001） |

| Saba *et al* (2021) \[30\] || 60 名意大利患者的肺部 CT 扫描（非 COVID-19: 30，COVID-19: 100） || iCNN || 0.996 || 0.99（*p* < 0.0001） |

| **本研究** || **5600 例（2800 对照，2800 COVID-19）** || **DenseNet121** || **89.75** || **0.902 AUC（*p* < 0.0001）** |

### Strengths, weaknesses, and extensions

我们使用基于 AI 的 MFS 和基于信号处理的 bispectrum 来表征 COVID-19 组织。我们使用 DenseNet121 实现了 89.75% ± 5.85% 的最高准确率。我们比较了转移学习模型与新型深度学习架构 SuriNet 的效率。本研究的主要弱点是，高效深度学习分类器需要更大量的样本。我们的队列规模适中，因此我们进行了增强。COVID-19  extensive dataset 有助于模型更好地理解复杂模式，并高效分类 COVID-19 CT 扫描。混合深度学习模型能够更好地理解队列中的复杂模式。大数据与混合模型相结合将为从 CT 扫描中检测 COVID-19 提供更多洞察。

### Conclusion

我们成功地使用转移学习和深度学习分类器对对照与 COVID-19 CT 扫描进行分类和特征化。DenseNet121 的最高准确率为 89.75% ± 5.85%，AUC 为 0.902（*p* < 0.0001）。与该模型相比，IV3 实现了 89.54% ± 4.56% 的准确率，AUC 为 0.895（*p* < 0.0001）。基于深度学习的 SuriNet 实现了最高 85.75% ± 9.56% 的准确率。在所有 K10 组合中，SuriNet 在少数情况下实现了 98.75% 的最高准确率。bispectrum 表明 COVID-19 的平均 B 值比对照高 2.85%，而基于 AI 的 MFS 则显示出 25.09%。

## References

[1] WHO 2020 *Coronavirus Disease (COVID-19) Situation Reports* [`who.int/emergencies/diseases/novel-coronavirus-2019/situation-reports`](https://www.who.int/emergencies/diseases/novel-coronavirus-2019/situation-reports)

[2] Gabutti G 等 2020 关于当前 COVID-19 疫情的更新 *Infect. Dis. Ther.* [9 241–53](http://dx.doi.org/10.1007/s40121-020-00295-5)

[3] Wang H-Y 等 2020 COVID-19 的潜在神经症状 *Therap. Adv. Neurol. Disorders* [13 10.1177/1756286420917830](http://dx.doi.org/10.1177/1756286420917830)

[4] Cascella M 等 2022 冠状病毒（COVID-19）的特征、评估和治疗 *StatPearls*

[5] Pan C 等 2020 COVID-19 相关急性呼吸窘迫综合征中的肺可扩展性：单中心观察研究 *Am. J. Respir. Crit. Care Med.* [201 1294–7](http://dx.doi.org/10.1164/rccm.202003-0527LE)

[6] Meng L 等 2020 疫情期间的插管和通气：武汉的经验 *Anesthesiology* [132 1317–32](http://dx.doi.org/10.1097/ALN.0000000000003296)

[7] Huang C 等 2020 2019 冠状病毒病患者在武汉，中国的临床特征 *Lancet* [395 497–506](http://dx.doi.org/10.1016/S0140-6736\(20\)30183-5)

[8] Devaux C A, Rolain J-M and Raoult D 2020 ACE2 受体多态性：易感 SARS-CoV-2、高血压、多器官衰竭以及 COVID-19 疾病结局 *J. Microbiol., Immunol. Infect.* [53 425–35](http://dx.doi.org/10.1016/j.jmii.2020.04.015)

[9] Zaim S 等 2020 COVID-19 与多器官反应 *Curr. Prob. Cardiol.* [45 100618](http://dx.doi.org/10.1016/j.cpcardiol.2020.100618)

[10] Saba L and Suri J S 2013 *Multi-Detector CT Imaging: Principles, Head, Neck, and Vascular Systems* vol 1 (Boca Raton, FL: CRC Press)

[11] El-Baz A and Suri J 2019 *Lung Imaging and CADx* (Boca Raton, FL: CRC Press)

[12] El-Baz A and Suri J S 2011 *Lung Imaging and Computer Aided Diagnosis* (Boca Raton, FL: CRC Press)

[13] World Health Organization 2020 *Use of Chest Imaging in COVID-19: A Rapid Advice Guide* (Portland, OR: Pacific Northwest Evidence-Based Practice Center, Oregon Health and Science University)

[14] Hatamabadi H 等 2020 冠状病毒相关肺炎患者的肺超声表现与胸部 CT 扫描的比较：一项试点研究 *Adv. J. Emerg. Med.* [5 e19](http://dx.doi.org/10.18502/fem.v5i2.5612)

[15] Revel M-P 等 2020 COVID-19 患者与放射科——来自欧洲放射学会（ESR）和欧洲胸部成像学会（ESTI）的建议 *Eur. Radiol.* [30 4903–9](http://dx.doi.org/10.1007/s00330-020-06865-y)

[16] Yan C 等 2020 肺超声与胸片在疑似肺炎儿童中的对比研究：回顾性队列研究 *Exp. Therap. Med.* [19 1363–9](http://dx.doi.org/10.3892/etm.2019.8333)

[17] Hu S 等 2020 基于 CT 图像的 COVID-19 感染检测和分类的弱监督深度学习 *IEEE Access* [8 118869–83](http://dx.doi.org/10.1109/ACCESS.2020.3005510)

[18] Li Z 等 2020 从社区获得性肺炎到 COVID-19：基于厚片 CT 扫描的深度学习定量分析方法 *Eur. Radiol.* [30 6828–37](http://dx.doi.org/10.1007/s00330-020-07042-x)

[19] Chen J 等 2020 基于高分辨率 CT 图像的 2019 冠状病毒肺炎检测深度学习模型 *Sci. Rep.* [10 1–11](http://dx.doi.org/10.1038/s41598-020-76282-0)

[20] Chaganti S 等 2020 胸部 CT 与 COVID-19 相关的放射学模式定量 *arXiv:* [2004.01279](http://arxiv.org/abs/2004.01279)

[21] Ahuja S 等 2021 基于肺部 CT 切片的深度迁移学习自动检测 COVID-19 *Appl. Intell.* [51 571–85](http://dx.doi.org/10.1007/s10489-020-01826-w)

[22] Maghdid H S 等 2020 使用深度学习和迁移学习算法从 X 光和 CT 图像诊断 COVID-19 肺炎，arXiv: [2004.00038](http://arxiv.org/abs/2004.00038)

[23] Jaiswal A 等 2020 使用 DenseNet201 深度迁移学习对 COVID-19 感染患者进行分类 *J. Biomol. Struct. Dyn.* [39 5682–9](http://dx.doi.org/10.1080/07391102.2020.1788642)

[24] Caldwell M and Griffin L D 2019 从照片图像数据向 X 光威胁检测迁移学习的局限性 *J. X-Ray Sci. Technol.* [27 1007–20](http://dx.doi.org/10.3233/XST-190545)

[25] Saba L, Sangala S S, Gupta S K, Koppula V K, Johri A M, Sharma A M, Kolluri R, Bhatt D L, Nicolaides A and Suri J S 2021 基于超级计算机的深度学习范式，对颈动脉斑块的超声特征进行特征化，用于心血管疾病/中风风险评估系统 *Int. J. Cardiovasc. Imaging.* [37 1511–28](http://dx.doi.org/10.1007/s10554-020-02124-9)

[26] Saba L 等 2021 多中心研究：使用六种深度人工智能模型对颈动脉斑块组织特征和分类进行研究，用于中风应用 *IEEE Trans. Instrum. Meas.* [70 1–12](http://dx.doi.org/10.1109/TIM.2021.3052577)

[27] Sanagala S S 等 2019 快速轻量深度卷积神经网络模型，用于人类肺部癌症病识别 *18th IEEE Int. Conf. On Machine Learning And Applications* (Piscataway, NJ: IEEE)

[28] Skandha S S 等 2020 3-D 优化分类和特征人工智能范式，用于基于颈动脉超声斑块的动脉粥样病风险分层：Atheromatic™ 2.0 *Comput. Biol. Med.* [125 103958](http://dx.doi.org/10.1016/j.compbiomed.2020.103958)

[29] Nolf E X 等 2003 开源医学图像转换工具包 *Eur. J. Nucl. Med.* 30 S246
