
图 2 所示的预测结果表明，使用历史主导可见度作为预测因子，不同时间长度的主导可见度平均绝对误差在 966 米至 706 米之间。最佳的预测时间为当前时间前 1 小时，平均绝对误差为 706.98 米。不同时间长度的模型预测效果各异，误差随时间长度的增加而缓慢上升。

本书版权归 Arcler 所有

![Image 1382](img/index-318_1.jpg)
![Image 1383](img/index-318_2.jpg)
![Image 1384](img/index-318_3.png)
![Image 1385](img/index-318_4.png)
![Image 1386](img/index-318_5.png)

# 深度学习算法

## 以多种气象要素作为预测因子的模型

本文尝试将预测因子扩展至主导可见度、过去的温度、露点温度、风向和风速，因为低能见度天气的发生原因众多，且能见度与温度、相对湿度等因素存在关联。本文使用该模型预测主导可见度。通过对预测结果的分析，发现使用多元预测因子的模型，不同时间长度的平均绝对误差在 799 米至 827 米之间。不同模型的平均绝对误差约为 10 米。过去 24 小时多元预测因子的模型效果最佳，其绝对误差为 798.87 米。[详情请参见图 3]。

为全面测试模型预测能见度的不同因子，本文统计了 5000 米以内的主导可见度，以预测平均绝对误差。该模型对不同量级主导可见度的预测能力进行了评估。模型在预测 1000 米以内的主导可见度时效果最佳，其平均绝对误差在 450 米至 550 米之间。该模型使用过去 72、120 小时的预测因子构建，预测效果更佳。随着主导可见度等级的提高，模型预测误差逐渐增加至约 1100 米。此处未提供详细的数据统计表。

**图 3**. 使用多种因子的主导可见度在不同时间长度下的预测效果。

本书版权归 Arcler 所有

![Image 1398](img/index-321_1.png)
![Image 1399](img/index-321_2.png)
![Image 1400](img/index-321_3.png)

# 深度学习在机场能见度预测中的应用

## 实用预测建议

基于本论文讨论的两种预测因子构建的模型预测效果，单因子构建的预测模型在能见度小于 1000 米的预测中表现更好。多因子构建的预测模型比 2000 米以上的预测效果更稳定。因此，这里同时使用这两种模型。同时考虑到能见度变化的连续性，我们选择使用过去 12 小时的预测因子来进行实际预测。

本文选择乌鲁木齐机场 2016 年 12 月 31 日的能见度数据进行预测。

机场能见度发生剧烈变化的一天，在 11 点前能见度保持在 1000 米以上，随后迅速下降，维持两小时的 100 米，然后 16:00 突然提升至 2000 米，之后又降至 100 米，如图 4 所示。低能见度过程包括持续的低能见度和能见度突然改善的过程，这对模型预测能力提出了高要求。

从模型预测结果可以看出，两种模型都能预测能见度的下降趋势和白天的转折。当实际能见度大于 1500 米时，多因子模型的预测误差相对较小。当主导能见度小于 1000 米时，单因子模型的预测效果相对更好，特别是在长期连续能见度小于 300 米时，单因子能见度的平均绝对误差为 86 米。因此，通过使用这两种预测模型，可以为预测人员提供能见度预测的量化参考。然而，从实际案例的模拟可以看出，当主导能见度良好或恶化时，深度学习模型存在一定的滞后现象，能见度大于 1500 米时错误明显增加。

# CONCLUSIONS

由于低能见度天气的高发率，系统的影响更为复杂。特别是低能见度的开始和结束时间预测更为困难。因此，如何尽可能预测低能见度天气及其消散时间，是保障乌鲁木齐机场冬季服务的关键。

![Image 1401](img/index-322_1.jpg)
![Image 1402](img/index-322_2.png)
![Image 1403](img/index-322_3.png)
![Image 1404](img/index-322_4.png)

**Figure 4**. 2016 年 12 月 31 日不同模型对主导能见度预测的影响。

本文尝试利用深度神经网络对机场能见度进行预测，使用近十年的数据进行模型预测。结果表明，乌鲁木齐机场的平均绝对误差最小可达 706 米。在能见度小于 1000 米的范围内，误差最低可达 325 米。同时，我们可以看到多因子预测模型的预测结果更为稳定。接下来，我们将尝试将该模型投入实际业务，并持续测试，以提高该方法在预测能见度方面的量化能力。

尽管该方法预测效果较好，但在对预测结果的详细分析中也发现了一些不足，例如预测能见度的转折或转差时间存在一定的滞后。结果显示，当主导能见度大于 2000 米时，平均绝对误差大于 2000 米，预测效果不佳；当主导能见度小于 1000 米时，预测效果较好。因此，我们将与其他因素合作为预测因子，以确保预测因子能更好地包含低能见度天气条件，从而提高模型的预测效果。

本书版权归 Arcler 所有

![Image 1405](img/index-323_1.png)
![Image 1406](img/index-323_2.png)
![Image 1407](img/index-323_3.png)

# REFERENCES

1. Zhu, L. and Zhu, G.D. (2012) Analysis of Low Visibility Weather Characteristics of Urumqi Airport in Recent 30 Years. Journal of Civil Aviation Flight Administration of China, 23, 27-30.
2. Zhu, L. and Zhu. G.D. (2010) Application of Support Vector Machine Method in Visual Field Forecast of Airport Runway. Journal of Stroke, 29, 171-175.
3. Li, P., Wang, S.G., Shang, K.H., et al. (2012) Beijing Area Visibility +# + Model ing. Journal of Lanzhou University (Natural Science Edition), 48, 52-57. (In Chinese)
4. Wang, K., Zhao, H., Liu, A.X., et al. (2009) Prediction of Atmospheric Visibility Based on Risk Neural Network. China Environmental Science, 29, 1029-1033.
5. Chen, H.Z., Hao, L.P., Xie, N., et al. (2009) Digitalization of Information ? { 151-156.
6. Zhu, G.D. (2011) Multi-Element Prediction of Urumqi International Airport based on `SVM` Method. Development and Oasis Meteorology, 5, 40-43.
7. <¯° Network in Urban Short-term Forecast of Visibility. Proceedings of the 6th Annual Conference of Chinese Society for Particles and Cross-Strait Particle Technology Symposium, 606-609.
8. Shao, Z.P. (2014) Zhengzhou Airport Visibility Changes and the Causes of Fog Analysis. Meteorological and Environmental Science, 37, 75-82.
9. He, H. and Luo, H. (2009) Fark Forecasting Method Based on Support Vector Machine Pattern Recognition. Meteorological Science and Technology, 37, 149-151.
10. Cao, Z.J., Wu, D., Wu, X.J., et al. (2008) Climate Characteristics of Fog in China from 1961 to 2005. Meteorological Science and Technology, 36, 556-560.
11. ½ ¨ ¸ \`| Analysis of Fog in the Capital Airport. Meteorological Science and Technology, 36, 717-723.

本书版权归 Arcler 所有

![Image 1408](img/index-324_1.png)
![Image 1409](img/index-324_2.png)
![Image 1410](img/index-324_3.png)

12. Bengio, Y. (2009) Learning Deep Architectures for AI. Foundations and Trends in Machine Learning, 2, 1-127. `https://doi.org/10.1561/2200000006`
13. Hinton, G., Osindero, S. and Teh, Y. (2006) A Fast Learning Algorithm for Deep Belief Nets. Neural Computation, 18, 1527-1554. `https://doi.org/10.1162/neco.2006.18.7.1527`
14. Liu, J.W., Liu, Y., Luo, X.L., et al. (2014) Progress in the Study of Depth. Application Research of Computers, 31, 1921-1930, 1942.

本书版权归 Arcler 所有

![Image 1411](img/index-325_1.png)
![Image 1412](img/index-325_2.png)
![Image 1413](img/index-325_3.png)

# CHAPTER 15

## HIERARCHICAL REPRESENTATIONS FEATURE DEEP LEARNING FOR FACE RECOGNITION

Haijun Zhang1,2 and Yinghui Chen1,3

1Guangdong Provincial Key Laboratory of Conservation and Precision Utilization of Characteristic Agricultural Resources in Mountainous Areas, Meizhou, China

2School of Computing, Jiaying University, Meizhou, China
3School of Mathematics, Jiaying University, Meizhou, China

## ABSTRACT

Most modern face recognition and classification systems mainly rely on hand-crafted image feature descriptors. In this paper, we propose a novel deep learning algorithm combining unsupervised and supervised learning named deep belief network embedded with `Softmax regress` (`DBNESR`) as a natural source for obtaining additional, complementary hierarchical representations, which helps to relieve us from the complicated hand-crafted **Citation**: Zhang, H. and Chen, Y. (2020), Hierarchical Representations Feature Deep Learning for Face Recognition. Journal of Data Analysis and Information Processing, 8, 195-227. doi: 10.4236/jdaip.2020.83012.

**Copyright** È# #<- censed under the Creative Commons Attribution International License (CC BY). `http://creativecommons.org/licenses/by/4.0`

本书版权归 Arcler 所有

![Image 1414](img/index-326_1.png)
![Image 1415](img/index-326_2.png)
![Image 1416](img/index-326_3.png)

feature-design step. `DBNESR` first learns hierarchical representations of feature by greedy layer-wise unsupervised learning in a feed-forward (bottom-up) and back-forward (top-down) manner and then makes more efficient recognition with `Softmax regress` by supervised learning. As a comparison with the algorithms only based on supervised learning, we again propose and design many kinds of classifiers: `BP`, `HBPNNs`, `RBF`, `HRBFNNs`, `SVM` and multiple classification decision fusion classifier

`~?|Ç# ¯+¯?+¶~ <`

experiments validate: Firstly, the proposed `DBNESR` is optimal for face recognition with the highest and most stable recognition rates; second, the algorithm combining unsupervised and supervised learning has better effect than all supervised learning algorithms; third, hybrid neural networks have better effect than single model neural network; fourth, the average recognition rate and variance of these algorithms in order of the largest to the smallest are respectively shown as `DBNESR`, `MCDFC`, `SVM`, `HRBFNNs`, `RBF`, `HBPNNs`, `BP` and `BP`, `RBF`, `HBPNNs`, `HRBFNNs`, `SVM`, `MCDFC`, `DBNESR`; at last, it reflects hierarchical representations of feature by `DBNESR` in terms of its capability of modeling hard artificial intelligent tasks.

Keywords: Face Recognition, Unsupervised, Hierarchical Representations, Hybrid

## INTRODUCTION

Face recognition (FR) is one of the main areas of investigation in biometrics and computer vision. It has a wide range of applications, including access control, information security, law enforcement and surveillance systems. FR has caught the great attention from large numbers of research groups and has also achieved a great development in the past few decades \[1\] \[2\] \[3\].
