
尽管胃电图（EGG）在临床实践很有用，但由于使用了皮肤电极，它存在一些局限性。使用这些电极记录的 EGG 信号可能会各种类型伪影的影响。例如，来自小肠和呼吸肌的电活动可以分别产生 9-13 Hz 和 12-24 Hz 的频率。心脏动作电位也会产生 60 Hz 的频率。这些伪影可能会影响 EGG 分析的准确性和可靠性，使得从其他电活动源开发合适的胃波具有挑战性。为了减少这些伪影，研究人员和临床医生应该仔细设计和开发合适的信号处理方法，并可以使用数字滤波器消除这些伪影。然而，可以放置电极以进行更详细的记录。此外，患者应处于舒适放松的位置，并且任何潜在的干扰源（如电器设备或金属物体）应远离记录区域。记录通常持续 30 分钟到几小时，取决于检查的目的。在记录期间，可能会要求患者深呼吸或吞水以刺激胃活动。记录完成后，将由医疗专业人员对数据进行分析和解释，以诊断胃活动的任何异常 [8]。

## 5 文献综述

| 序号 | 作者年份 | 样本来源 | 评估算法 | 结果 |
|---|---|---|---|---|
| [1] | Yin 等人 2013 | 综述论文 | | 这些发现表明，腹部胃活动与功能性消化不良患者的异常运动之间存在强相关性。接受治疗患者 EGG 中看到的律失常可能导致他们的恶心、胀气和饱腹等症状。胃十二肠动力可以提供有关胃和指肠运动功能的信息，并有助于识别可以指导治疗的症状。总而言，同时进行 EGG 和胃十二肠监测可以为功能性消化不良的病理学和治疗决策提供有价值的信息。 |
| [2] | Gandhi 等人 2021 | 根据作者要求提供数据 | 使用自适应共振分类网络进行特征选择分类的逻辑回归、SVM 和 KNN 算法 | 本研究中使用的 SVM 性能卓越，对于两类 EGG 信号实现了 F1 分数、召回率分别为 100 和 92%，这表明 SVM 算法在将 EGG 信号分类不同类别方面具有很高的准确性和有效性，提示其在临床实践中的潜在价值。然而，SVM 算法的性能取决于数据集的大小和质量、选择器以及用于训练的参数。因此，在应用于临床环境之前，在更大、多样化的数据集上评估 SVM 算法的性能并与其他分类算法进行比较是非常重要的。 |

| 序号 | 作者年份 | 样本来源 | 评估算法 | 结果 |
| --- | --- | --- | --- | --- |
| [3] | Saad 等人 2015 | - | - | 听到实验是在 10 个不同性别的人身上进行的以确保算法的性能，这很好。比较模拟值和结果也是验证算法性能的关键步骤。这显示出每个元素都有相似的模式，进一步验证了算法的准确性和可靠性。 |
| [4] | Strzecha 等人 2021 | 研究期间从背部肌肉收集了肌 信号样本。 | - | - |
| [5] | Brandstaeter 等人 2019 | - | - | - |
| [6] | Krishnasamy 等人 2018 | - | - | - |
| [7] | Gharibans 等人 2017 | 研究共包含八名健康学生，包括五名男性和三名女性，平均年龄为 26 ± 4 岁，参与者报告在研究期间经历了胃肠道症状或不适。 | 拉普拉斯方法、前向电生理模型、非参数自助引导法。 | 相位方向性 (PGD) 是信号中相位梯度对齐的测量。PGD 值为 1 表示相位梯度完美对齐，而值为 0 表示未对齐。所有点的 PGD 值大于 0.9 表示相位梯度几乎完美对齐。这表明，基于相位梯度对齐良好的信号，估计的 187 度方向和 5.5 m/ms 速度是可靠的。 |
| [8] | Murakami 等人 2013 | - | 快速傅里叶变换, EMD | - |
| [9] | Alagumariappan 等人 2020 | 30 名糖尿病患者 | 快速傅里叶变换、小波变换、熵 | 使用胃电图诊断 2 型糖尿病：创新特征的提取和基于遗传算法的选择。根据这些信息，振幅的相关性是显著的。 |

## 6 胃电图与肌电图的相关性

## 致谢

作者感谢班加罗尔 Ramaiah 学院研发部负责人 N S 博士的出的慷慨支持。

## 参考文献

- [1] Yin, J. & Z. "Electrogography: Methodology and Applications," Journal of Neurogenterology and Motility,19(1), 5-17.
- [2] Gandhi C, Ahmad SS, et al. "Biosensor-Assisted Method for Abdominal Syndrome Using Machine Learning," Comput Internet Neurosci.,2022:445226, 2022.
- [3] Smaili I, et al. "Electromyography (EMG) Signal Analysis for Clinical Rehabilitation," 105–110, 2015.
- [4] Strzecha K, et al. "Processing of EMG Signals with High Impact of Power Line and Cardiac Interferences," Applied Sciences, vol. 11, no. 1, p.465, 2021.
- [5] Brandstaeter, S, Fuchs, et al. "Mechanics of the Stomach: A Review of an Emerging Field of Biomechanics," GAMM - Mitteilungen, 42:e2019001, 2021.
- [6] Bellamy S, Abhell TL, et al. "Diabetic Gastroparesis: Principles and Current Trends in Management," Diabetes,60(9),doi:10.2337/db1644-2017.
- [7] Gharibans AA, Kim S, et al. "High-Resolution Gastric Ultrasound-A Novel, Noninvasive Method for Determining Gastric Slow-Wave Direction," IEEE Trans Biomed Eng. TBME.2016:2579310, 2017.
- [8] Murata H, et al. "Current Status of Multichannel Electrogography and Examples of Its Use," A Smooth Muscle Res.; 49:78-88. doi:10.1540/jsmr.49.78, 2013.
- [9] Alagumariappan P, et al. "Diagnosis of Type 2 Diabetes Using Electrogastograms: Extraction and Genetic Algorithm-Based Selection of Innovative Features," JMIR Biomed Eng, doi:10.2196/20932, 2020.
