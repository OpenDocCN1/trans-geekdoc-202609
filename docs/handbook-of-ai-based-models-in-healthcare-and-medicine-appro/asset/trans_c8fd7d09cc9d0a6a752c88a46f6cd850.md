
![](img/a2fc2296b12812e9151e817bff1de16d_171_0.png)

图 8.12 MRI 数据集的硬件实现设置。

![](img/a2fc2296b12812e9151e817bff1de16d_171_1.png)

图 8.13 超声数据集的硬件测试结果。

![](img/a2fc2296b12812e9151e817bff1de16d_172_0.png)

图 8.14 超声数据集的硬件实现设置。

![](img/a2fc2296b12812e9151e817bff1de16d_172_1.png)

图 8.15 病理学数据集的硬件测试结果。

![](img/a2fc2296b12812e9151e817bff1de16d_173_0.png)

图 8.16 病理学数据集的硬件实现设置。

![](img/a2fc2296b12812e9151e817bff1de16d_173_1.png)

图 8.17 乳房X光摄影数据集的硬件测试结果。

![](img/a2fc2296b12812e9151e817bff1de16d_174_0.png)

图 8.18 乳房X光摄影数据集的硬件实现设置。

## 参考文献

- 1. Centers for Disease Control and Prevention. (2020) Breast cancer: Things you should know. Retrieved from https://www.cdc.gov/cancer/breast/basic_info/what-is-breast-cancer.html.
- 2. https://my.clevelandclinic.org/health/diseases/3986-breast-cancer.
- 3. https://www.uicc.org/news/globocan-2020-new-global-cancer-data# Manage with L (2022) Breast cancer, 1–20.
- 4. https://www.mayoclinic.org/diseases-conditions/breast-cancer/symptoms-causes/syc-20352470.
- 5. https://www.radiologyinfo.org/en/info/screening-breast.
- 6. Sharma S, Mehra R (2020) Conventional machine learning and deep learning approach for multi-classification of breast cancer histopathology images—A comparative insight. J Digit Imaging 33(3):632–654. https://doi.org/10.1007/s10278-019-00307-y.
- 7. Qasem A, Sheikh Abdullah SNH, Sahran S, et al. (2022) An improved ensemble pruning for mammogram classification using modified Bees algorithm. Neural Comput Appl 34(12):10093–10116. https://doi.org/10.1007/s00521-022-06995-y.
- 8. Yurttakal AH, Erbay H, İkizceli T, Karaçavuş S (2020) Detection of breast cancer via deep convolution neural networks using MRI images. Multimed Tool Appl 79(21–22):15555–15573. https://doi.org/10.1007/s11042-019-7479-6.
- 9. Ma H, Tian R, Li H, et al. (2021) Fus2Net: A novel Convolutional Neural Network for classification of benign and malignant breast tumor in ultrasound images. Biomed Eng Online 20(1):1–15. https://doi.org/10.1186/s12938-021-00950-z.
- 10. Xiong S, Wu G, Fan X, et al. (2021) MRI-based brain tumor segmentation using FPGA-accelerated neural network. BMC Bioinformatics 22(1):1–15. https://doi.org/10.1186/s12859-021-04347-6.
- 11. Hassan O, Paul T, Shuvo MMH, et al. (2022) Energy efficient deep learning inference embedded on FPGA for sleep apnea detection. J Signal Process Syst 94(6):609–619. https://doi.org/10.1007/s11265-021-01722-7.
- 12. Al-Dhabyani W, Gomaa M, Khaled H, Fahmy A (2020) Dataset of breast ultrasound images. Data Brief 28:104863. https://doi.org/10.1016/j.dib.2019.104863.
- 13. Moreira IC, Amaral I, Domingues I, et al. (2012) INbreast: Toward a full-field digital mammographic database. *Acad Radiol* 19(2):236–248. https://doi.org/10.1016/j.acra.2011.09.014.
- 14. https://www.kaggle.com/code/abhinand05/histopathologic-cancer-detection-using-cnns/data.
- 15. https://www.kaggle.com/datasets/uzairkhan45/breast-cancer-patients-mris.

## 9 利用卷积神经网络和视觉变换器集成框架实现阿尔茨海默病的稳健诊断

*Poonguzhali Elangovan and Malaya Kumar Nath*

### 9.1 引言

大脑是人体最复杂的器官。它负责大多数身体活动，例如处理、整合和协调来自各种感觉器官的感官信息。因此，大脑的正常和活跃功能对于实现日常活动至关重要。一些疾病，如阿尔茨海默病（AD）、精神分裂症（SZ）、帕金森病（PD）、痴呆和脑肿瘤，会损害大脑功能。在发达国家，AD 的患病率估计影响 65 岁以上人群的 5%，以及令人震惊的 85 岁以上人群的 30% [1]。到 2050 年，预计将有 0.64 亿人受到这种疾病的影响 [2]。AD 主要影响负责记忆的大脑部分。它会导致脑细胞退化，因此 AD 患者在早期阶段会出现记忆丧失。随着疾病的进展，AD 患者会失去对周围环境的反应能力。他们经常弄错时间，并可能将家庭成员误认为是陌生人。因此，他们可能会变得具有攻击性或容易走出家门。在晚期，AD 最终会导致死亡，因为它破坏了负责呼吸和心脏功能的脑部区域。因此，及时筛查 AD 至关重要。此外，早期诊断可以使患者免受不必要的药物治疗及其副作用。阿尔茨海默病是一种灾难性的神经功能障碍，会损害记忆和认知能力。AD 的临床表现是过度产生 β-淀粉样蛋白 [1]。随着海马体缩小，细胞丢失和损伤发生 [3]。由于此原因，神经元无法通过突触做出反应。这会影响记忆和思维能力 [1]。由于 AD 尚无治愈方法，减缓认知衰退的唯一方法是从大脑中清除淀粉样蛋白 [3]。然而，由于 AD 进展缓慢，早期诊断相当具有挑战性。AD 的筛查很麻烦，因为症状出现在最后阶段。因此，有效诊断 AD 至关重要。需要进行身体和神经生物学检查以及患者的详细病史来正确评估 AD。此外，成像在 AD 诊断中起主导作用。神经科医生已使用磁共振成像（MRI）来可视化大脑的结构和功能。他们确定 AD 迹象并进行各种检查以诊断 AD。通过这些检查可以实现准确的诊断。可以根据 AD 的阶段（例如中度、轻度和非常轻度）推荐适当的药物。AD 相关的病理可以在 MRI 图像中检测到。这使 MRI 模式成为 AD 诊断中显著的模式。

AD 的临床诊断需要训练有素的专家，并且由于涉及众多控制参数，可能容易出现术者间/术者内误差。此外，所使用的成像仪器昂贵且笨重。虽然病理特征在 MRI 图像中很明显，但临床检查是一个繁琐的过程。因此，利用计算机辅助检测（CAD）技术进行 AD 诊断是必要的。随着技术的进步，机器学习（ML）和深度学习（DL）正逐步部署以从脑成像数据中提取相关特征。本研究旨在利用深度学习技术提高 AD 分类结果。以下为本工作的主要目标：

- 调查 EfficientNet-B0 和视觉变换器对 MRI 图像中 AD 阶段分类的性能。
- 说明 KNN、softmax、Bi-LSTM 和 SVM 等分类器对 AD 分类任务的有效性。
- 探索小波变换和主成分分析（PCA）等特征选择技术的有效性。
- 提出一种基于堆叠技术的新型集成模型以提高整体性能。

论文的后续部分结构如下。第 9.2 节提供了现有工作的快速概述。数据库和建议的方法在第 9.3 节中解释。第 9.4 节和第 9.5 节分别讨论结果和结论。

### 9.2 相关工作

深度 CNN 以分层方式学习有效属性。因此，这些网络是图像分类任务的绝佳选择，例如青光眼分类 [4, 5]、疟疾寄生虫检测 [6]、乳腺癌检测 [7] 和皮肤癌检测 [8]。近年来已开发出多种算法用于
