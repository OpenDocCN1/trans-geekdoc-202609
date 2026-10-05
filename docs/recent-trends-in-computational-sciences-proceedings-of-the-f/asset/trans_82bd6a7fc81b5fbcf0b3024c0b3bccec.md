

![](img/a35f8e852e0ee65e528c95ad0821783b_42_0.png)

(a) 腹部CT图像
(b) 分割后的肝脏图像

图5. 使用 DeepLabv3+ 模型的肝脏分割结果。

表 1. 使用机器学习方法的性能评估。

| | 直方图 | GLCM | 选取特征 |
|---|---|---|---|
| 准确率 | 69% | 74% | 76% |
| 特异性 | 63.77% | 71.43% | 68.06% |
| 敏感性 | 80.65% | 77.27% | 96.43% |

在应用特征选择后，从11个特征中仅保留了8个相关特征。如前所述，发现5个直方图特征（均值、能量、熵、方差、偏度）以及3个GLCM特征（即对比度、均匀性和角矩）对于分类至关重要。分类准确率提高了2%（达到76%）。然而，特异性降低到68.06%，敏感性增加到96.43%。因此，减少后的特征集已能够成功识别出比正常图像更多的异常图像。

使用三个深度学习网络（ResNet、ShuffleNet和EfficientNet）获得的结果所示表2。EfficientNet获得了最佳性能。

所达到的分类准确率为87%，特异性为79.37%。获得的敏感性为100%，表明所有异常病例均被正确分类。ShuffleNet也给良好的结果：准确率 = 78%，特异性 = 69.44%，敏感性 = 100%。ResNet的最低准确率为74%。

表 2. 使用深度学习方法的性能评估。

| 性能指标 | ResNet | ShuffleNet | EfficientNet |
|---|---|---|---|
| 准确率 | 74% | 78% | 87% |
| 特异性 | 70% | 69.44% | 79.37% |
| 敏感性 | 80% | 100% | 100% |

对比两种方法（表1和表2），可以看出深度学习（DL）方法提供了更好的结果。使用机器学习（ML）方法时，最高准确率为76%（使用减少后的特征集），而使用EfficientNet时准确率提高了11%。敏感性和特异性有了显著提高。EfficientNet正确预测了约80%的正常病例和100%的异常病例。此外，与机器学习方法不同，深度学习方法不需要用户识别分类所需的特征。特征提取是由卷积神经网络（CNN）自动完成的。卷积层从CT图像中提取用于区分正常和异常肝脏的有用低、高级特征。

## 5 结论

在这项研究中，对机器学习方法与深度学习方法（即ResNet、ShuffleNet和EfficientNet）进行了对比。发现EfficientNet提供了最好的结果。对于肝脏分割，使用了语义分割模型DeepLabv3+（由“deeply3 +”修正）。根据我们的实验，我们可以得出结论：深度学习在从CT图像诊断异常肝脏方面比机器学习更有效。此外，后者不需要用户执行繁琐的特征工程任务。在肝脏异常诊断中更有效且高效。我们的工作是一项初步研究，未来可以扩展到进一步将异常肝脏分类为良性性和恶性肿瘤等子类。

## 致谢

我们感谢KStePS、DST、印度卡纳塔克邦政府提供的财政援助。我们感谢Mangipal Institute of Technology, MAHE, Manipal提供研究设施，以及KMC, Manipal提供图像。

## 参考文献

- [1] Sung H. et al., “Global Cancer Statistics 2020: GLOBOCAN Estimates of Incidence and Mortality Worldwide for 36 Cancers in 185 Countries,” C.A. Cancer J. Clin., vol. 71, no. 3, p. 209–229, May 2021, doi: https://doi.org/10.3322/caac.21660.
- [2] Burite N. and Jankharia B., "Teledology: The Indian Perspective," Indian Radiol. Imaging, vol. 19, no. 1, pp. 16–18, Feb. 2009, doi:10.4103/0971-3026.45337.
- [3] Sreeja P. and Haridaran S., "Image Analysis for the Detection and Diagnosis of Hepatocellular Carcinoma from Abdomen CT Images," Lett Notes Syst., vol. 19, pp. 107–117, 2018, doi:10.1007/s10639-018-5523-2_11.
- [4] Nayaer A. et al., "Automatic Diagnosis of Cirrhosis and Hepatocellular Carcinoma Using Multiphase CT," Int. J. Comput. Assist. Radiol., vol. 14, no. 8, pp. 1341–1352, 2019, doi:10.1007/s11548-019-1991-5.
- [5] Muthuswamy S., "Classification of Liver Abnormality by SF Based Neural Network," Projects in Advanced Computing and Engineering, 2019.
- [6] Kesar A., Edwin D., and Haridaran S., "Classification of Liver Tumor Using Support Vector Machine," in IEEE Int. Conf. Intelligent Technol. ICCIT2017, pp. 1066–1070, doi:10.1109/ICCIIT2017.834276.
- [7] Li J et al., "Fully Automatic Diagnosis System for Hepatocellular Carcinoma Using Convolutional Networks," Biomed. Bio. Eng., vol. 40, no. 1, pp. 238–240, 2020, doi:10.1016/j.bjb.2019.038.
- [8] Bruno A., Carmino L., Trotta V., "Fully Automatic Diagnosis System for Hepatocellular Carcinoma Using Convolutional Networks," Biomed. Bio. Eng., vol. 40, no. 1, pp. 238–240, 2020, doi:10.1016/j.bjb.2019.038.
- [9] Sun D., Dong Y., and Li F., "Computed Tomography Predictive Value for Colorectal," Med. Imaging, 2022.
- [10] Soler L., Agnus A., and V., "Specific-Specific Database for Liver Reconstruction using Artificial Intelligence," Tech., 2010.
- [11] Chen X., Xiang Y., and Ger G., "DeepLabv3+ with Attention for Semantic Segmentation," ECCV, 2018.

