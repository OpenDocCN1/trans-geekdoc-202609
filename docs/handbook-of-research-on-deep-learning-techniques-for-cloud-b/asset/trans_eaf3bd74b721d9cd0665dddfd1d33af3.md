

## 图4. *MRI图像的痴呆类别*

![](img/4a898a1f1442f24bfffba36e7ac62ad8_131_0.png)

## 图5. *训练和测试过程中准确率与损失的比较分析*

![](img/4a898a1f1442f24bfffba36e7ac62ad8_131_1.png)

我们最近的研究提出了一种有效的基于分类器的深度卷积神经网络，该网络在图4和图5所示的ADNI数据集上表现优异。ADNI-3数据集被存放在一个单一的存储库中以妥善保管。在我们的研究中，我们使用了3182张MRI轴向切片。数据集中包含大约300名AD患者和70名NC患者的MRI图像。由于这些图像来自不同的学科领域，因此检查更加可靠。本工作涉及年龄在65至90岁之间的男性和女性患者。首先，我们将每个MRI图像切割成二维切片。通过旋转预处理图像的切片，以测试它们是否能够识别这些切片，我们可以获得更大的样本量，并为我们的基于区块链的DNN模型提供更好的训练环境。

所提出的模型已与PCA、CNN、Resnet18和3DCNN等多种方法进行了比较。表1显示了准确率、精确率和召回率值，对比图如图6所示。

然而，多重验证深度学习的结果表明，需要付出额外的努力来构建模型架构并优化其超参数。由于数据量有限，且流程符合当前标准，改进特征提取和性能的唯一方法就是改变这些步骤。在数据稀少的领域中，最大化利用现有数据至关重要。领域学习可能是改善进展中的MCI识别及其向AD进展预测的一种策略。根据对当前方法的文献调研，领域学习对模型性能以及使用该方法文章的数量都产生了积极影响。除了区块链之外，训练模型权重以检测辅助性AD的特征，将提高模型在核心问题上的性能，同时也能加快收敛速度，从而减少训练时间。

基于边缘的脑部分割是另一种可能提升性能的方法。脑部分割（颞叶、顶叶、前额叶和枕叶）使并行的3D卷积层能够为这些区域提取更精确的信息，从而压缩复杂的特征空间。更紧凑的特征区域应该更容易发现有用的特征。

*表1. 准确率、精确率和召回率对比表*

| 模型 | 准确率 | 精确率 | 召回率 |
|---|---:|---:|---:|
| PCA+NN | 95 | 91 | 98 |
| 3D CNN | 93 | 93.18 | 90 |
| Resnet18 | 97.88 | 98.10 | 97.89 |
| EFFICIENTNETB0 | 78.72 | 68.96 | 58.66 |
| CNN | 92 | 91 | 93 |
| 所提出模型 | 99 | 95 | 97.5 |

*图6. 各种方法的准确率对比图*

![](img/4a898a1f1442f24bfffba36e7ac62ad8_132_0.png)

## 结论

深度神经网络中的卷积神经网络（CNN）可能有助于诊断AD。本文描述了一种基于区块链的方法，使用EfficientnetB0通过二维MRI切片区分阿尔茨海默病（AD）患者和健康个体。许多潜在的AD患者可能受益于所提出的方法，从而实现更早的疾病检测。分割采用基于边缘的分割算法完成。我们在ADNI数据库中的特征提取和分类技术在测试结果中显示出对AD的高准确率。

Li, H., Habes, M., Wolk, D. A., & Fan, Y. (2019). *一种基于海马MRI的阿尔茨海默病痴呆早期预测深度学习模型*. arXiv:1904.07282.

Lian, C., Liu, M., Zhang, J., & Shen, D. (2020). 基于结构MRI的联合萎缩定位与阿尔茨海默病诊断的层次全卷积网络. *IEEE模式分析与机器智能汇刊, 42*(4), 880–893. doi:10.1109/TPAMI.2018.2889096 PMID:30582529

López-De-Ipiña, K., Martinez-De-Lizarduy, U., Calvo, P. M., Beitia, B., García-Melero, J., Fernández, E., Ecay-Torres, M., Faundez-Zanuy, M., & Sanz, P. (2020). 面向轻度认知障碍自动检测的语音与不流畅性分析. *神经计算与应用, 32*(20), 15761–15769. doi:10.1007/s00521-018-3494-1

Lu, D., Popuri, K., Ding, G. W., Balachandar, R., Beg, M. F., Weiner, M., Aisen, P., Petersen, R., Jack, C., Jagust, W., Trojanowski, J., Toga, A., Beckett, L., Green, R., Saykin, A., Morris, J., Shaw, L., Kaye, J., Quinn, J., ... Fargher, K. (2018). 使用结构MR和FDG-PET图像进行阿尔茨海默病早期诊断的多模态多尺度深度神经网络. *科学报告, 8*(1), 1–13. doi:10.1038/s41598-018-22871-z PMID:29632364

Maggipinto, T., Bellotti, R., Amoroso, N., Diacono, D., Donvito, G., Lella, E., Monaco, A., Scelsi, M., & Tangaro, S. (2017). 用于阿尔茨海默病分类的DTI测量. *医学与生物学中的物理学, 62*(6), 2361–2375. doi:10.1088/1361-6560/aa5dbe PMID:28234631

Pan, D., Zeng, A., Jia, L., Huang, Y., Frizzell, T., & Song, X. (2020). 利用磁共振成像早期检测阿尔茨海默病：一种结合卷积神经网络和集成学习的新方法. *神经科学前沿, 14*, 259. doi:10.3389/fnins.2020.00259 PMID:32477040

Parmar, H., Nutter, B., Long, R., Antani, S., & Mitra, S. (2020). 基于深度学习3D-CNN的fMRI数据时空特征提取与阿尔茨海默病分类. *医学影像杂志（华盛顿州贝灵厄姆）, 7*(5), 056001. doi:10.1117/1.JMI.7.5.056001

Pavisic, I. M., Pertzov, Y., Nicholas, J. M., O’Connor, A., Lu, K., Yong, K. X. X., Husain, M., Fox, N. C., & Crutch, S. J. (2021). 家族性阿尔茨海默病中视觉短期记忆编码受损的眼动追踪指标. *科学报告, 11*(1), 1–14. doi:10.1038/s41598-021-88001-4 PMID:33888739

Sapey-Triomphe, J.-A., Heckemann, R. A., Boublay, N., Dorey, J.-M., Hénaff, M.-A., Rouch, I., Padovan, C., Hammers, A., & Krolak-Salmon, P. (2015). 轻度阿尔茨海默病中面部表情识别的神经解剖学相关性. *PLoS One, 10*(12), e0143586. doi:10.1371/journal.pone.0143586 PMID:26673928

Sarraf, S., & Tofighi, G. (2016). *基于fMRI数据和深度学习卷积神经网络的阿尔茨海默病分类*. arXiv:1603.08631.

Tzimourta, K. D., Afrantou, T., Ioannidis, P., Karatzikou, M., Tzallas, A. T., Giannakeas, N., Astrakas, L. G., Angelidis, P., Glavas, E., Grigoriadis, N., Tsalikakis, D. G., & Tsipouras, M. G. (2019). 阿尔茨海默病脑电信号复杂度分析. *计算机与电气工程, 76*, 198–212. doi:10.1016/j.compeleceng.2019.03.018

## 基于区块链的阿尔茨海默病深度学习方法

Wang, Y., Xu, C., Park, J.-H., Lee, S., Stern, Y., Yoo, S., Kim, J. H., Kim, H. S., & Cha, J. (2019). 使用脑形态测量和白质连接组对阿尔茨海默病的诊断与预后. *神经影像.临床, 23*, 101859. doi:10.1016/j.nicl.2019.101859 PMID:31150957

Yu, S., Wang, S., Xiao, X., Cao, J., Yue, G., Liu, D., Wang, T., Xu, Y., & Lei, B. (2020). 用于早期轻度认知障碍检测的多尺度增强图卷积网络. In *医学图像计算与计算机辅助介入——MICCAI 2020* (pp. 228–237). Springer Science and Business Media LLC. doi:10.1007/978-3-030-59728-3_23

Zhang, F., Li, Z., Zhang, B., Du, H., Wang, B., & Zhang, X. (2019). 用于阿尔茨海默病辅助诊断的多模态深度学习模型. *神经计算, 361*, 185–195. doi:10.1016/j.neucom.2019.04.093

Zheng, Y., Guo, H., Zhang, L., Wu, J., Li, Q., & Lv, F. (2019). 基于机器学习的使用结构MRI特征对血管性痴呆和阿尔茨海默病进行鉴别诊断的框架. *神经病学前沿, 10*, 10. doi:10.3389/fneur.2019.01097 PMID:31708854

