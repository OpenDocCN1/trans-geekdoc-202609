
![Figure 6–14 ERA5 of Germany.](img/F000092f06-14-9780443219054.jpg)

Figure 6–14 ERA5 of Germany.

### 6.6.4 使用贝叶斯神经网络的概率海洋状态预测

对于海洋环流状态的概率预测，Clare et al. (2022) 实现了贝叶斯神经网络。最初 Sonnewald et al. (2019) 通过 `k-means` 聚类识别了海洋状态。所考虑的输入特征为风应力旋度、20 年的平均海面高度 (`SSH`)、平均 `SSH` 的梯度、海底地形，以及 Fig. 6–15 中的海底地形梯度和科里奥利力，用于预测海洋状态并构建确定性网络。在 Fig. 6–15 中，可以看出密集层更适合以网格点为单位的技术的数据形状。最后一层必须具有 `SoftMax` 激活，因为目标数据是分类的。

![Figure 6–15 Bayesian neural network (BNN) for prediction of ocean regime. Map lines delineate study areas and do not necessarily depict accepted national boundaries.](img/F000092f06-15-9780443219054.jpg)

Figure 6–15 Bayesian neural network (`BNN`) for prediction of ocean regime. Map lines delineate study areas and do not necessarily depict accepted national boundaries.

在 `BNN` 中，参数（权重和偏置）是分布而非确定性，如 Fig. 6–16 所示。从 `Tensorflow` probability，`OneHotCategorical` 层应被使用以使网络输出为分布。在确定性网络中，密集层被 `DenseVariational` 层替换为 `BNN`。

![Figure 6–16 Box-and-whisker plot of BNN predictions of ocean regimes.](img/F000092f06-16-9780443219054.jpg)

Figure 6–16 Box-and-whisker plot of `BNN` predictions of ocean regimes.

数据可以从 `ecmwf-open-data` 获取以绘制温度（Fig. 6–17）和平均海平面气压（Fig. 6–18）。该数据涵盖

1. 坐标，即 `time (datetime)`、`step (timedelta)`、`heightAboveGround`、`latitude`、`longitude`、`valid_time (time, step)`、`meanSea`；
2. 日期变量，即 `t2m (time, step, heightAboveGround, latitude, longitude)` 和 `msl (time, step, meanSea, latitude, longitude)`；
3. 属性，即 `GRIB_edition`、`GRIB_centre`、`GRIB_centreDescription` 和 `GRIB_subCentre`。

![Figure 6–17 Temperature mapped for February 17, 2023. Map lines delineate study areas and do not necessarily depict accepted national boundaries.](img/F000092f06-17-9780443219054.jpg)

Figure 6–17 Temperature mapped for February 17, 2023. Map lines delineate study areas and do not necessarily depict accepted national boundaries.

![Figure 6–18 Mean sea level pressure mapped for February 17, 2023. Map lines delineate study areas and do not necessarily depict accepted national boundaries.](img/F000092f06-18-9780443219054.jpg)

Figure 6–18 Mean sea level pressure mapped for February 17, 2023. Map lines delineate study areas and do not necessarily depict accepted national boundaries.

## 6.7 物理引导机器学习——物理信息参数化

物理引导 ML 是知识引导 ML 中的一种独特方法，其中 ML 输出被限制为由物理理解所指导的可行解。考虑预测近地表比湿和相对湿度的任务。根据定义，负预测或超过 1 的值（表示过饱和）是不可能的。以下图表（Figs. 6–19 至 6–24）外推了各种气候模型，将其与近地表比湿和相对湿度分别集成。这些模型已通过在 `Google Colab` 平台上使用 `Python` 的深度学习方法创建。

![Figure 6–19 Climate model for mean input with near-surface specific humidity. Map lines delineate study areas and do not necessarily depict accepted national boundaries.](img/F000092f06-19-9780443219054.jpg)

Figure 6–19 Climate model for mean input with near-surface specific humidity. Map lines delineate study areas and do not necessarily depict accepted national boundaries.

![Figure 6–20 Climate model for minimum input with near-surface specific humidity. Map lines delineate study areas and do not necessarily depict accepted national boundaries.](img/F000092f06-20-9780443219054.jpg)

Figure 6–20 Climate model for minimum input with near-surface specific humidity. Map lines delineate study areas and do not necessarily depict accepted national boundaries.

![Figure 6–21 Climate model for maximum input with near-surface specific humidity. Map lines delineate study areas and do not necessarily depict accepted national boundaries.](img/F000092f06-21-9780443219054.jpg)

Figure 6–21 Climate model for maximum input with near-surface specific humidity. Map lines delineate study areas and do not necessarily depict accepted national boundaries.

![Figure 6–22 Climate model for mean input and relative humidity. Map lines delineate study areas and do not necessarily depict accepted national boundaries.](img/F000092f06-22-9780443219054.jpg)

Figure 6–22 Climate model for mean input and relative humidity. Map lines delineate study areas and do not necessarily depict accepted national boundaries.

![Figure 6–23 Climate model for maximum input and relative humidity. Map lines delineate study areas and do not necessarily depict accepted national boundaries.](img/F000092f06-23-9780443219054.jpg)

Figure 6–23 Climate model for maximum input and relative humidity. Map lines delineate study areas and do not necessarily depict accepted national boundaries.

![Figure 6–24 Climate model for minimum input and relative humidity. Map lines delineate study areas and do not necessarily depict accepted national boundaries.](img/F000092f06-24-9780443219054.jpg)

Figure 6–24 Climate model for minimum input and relative humidity. Map lines delineate study areas and do not necessarily depict accepted national boundaries.

## 6.8 结论

模拟气候变化是一项复杂的工作，需要理解多样的参数动态。本研究阐明了意大利和德国的特定气候模型。鉴于其他国家的数据集，类似的气候模型可以被构建。机器学习算法、数字孪生和深度学习模型等技术已证明在促进任何给定地区的日常、月度甚至十年气候预测方面具有重要作用。此类预测在全球变暖缓解工作和更广泛的保护地球目标中发挥着关键作用。

## References

* Abebe et al., 2018 Abebe Y, Kabir G, Tesfamariam S. Assessing urban areas vulnerability to pluvial flooding using GIS applications and Bayesian Belief Network model. *Journal of Cleaner Production*. 2018;174:1629–1641 ISSN 0959-6526.

* Aguilera et al., 2021 Aguilera R, Corringham T, Gershunov A, et al. Wildfire smoke impacts respiratory health more than fine particles from other sources: Observational evidence from Southern California. *Nature Communications*. 2021;12:1493.

* Ali 等, 2017 Ali Z, Hussain I, Faisal M, et al. Forecasting drought using multilayer perceptron artificial neural network model. *Advances in Meteorology.* 2017;2017:5681308.

* Al-Kahlout 等, 2020 Al-Kahlout MM, Ghaly AMA, Mudawah DZ, Abu-Naser SS. Neural network approach to predict forest fires using meteorological data. *International Journal of Academic Engineering Research (IJAER)*. 2020;4(9):68–72.

* Bae 等, 2022 Bae, C., Jeong, J., & Lee, S. (2022). Automatic flight plan creation tool with digital twin for monitoring forest fire on mountain trail through UAV. In *1st international workshop on intelligent software engineering*. Busan, South Korea.

* Baumgartner, 2019 Baumgartner RJ. Sustainable development goals and the forest sector—A complex relationship. *Forests*. 2019;10(2):152.

* Biesbroek 等, 2020 Biesbroek R, Badloe S, Athanasiadis IN. Machine learning for research on climate change adaptation policy integration: An exploratory UK case study. *Regional Environmental Change*. 2020;20:85.

* Buonocore 等, 2022 Buonocore L, Yates J, Valentini R. A proposal for a forest digital twin framework and its perspectives. *Forests*. 2022;13:498.

* Cerdà, 2019 Cerdà A. The role of fire in achieving the sustainable development goals of the United Nations. *Proceedings*. 2019;30(1):65.

* Clare 等, 2022 Clare MCA, Sonnewald M, Lguensat R, et al. Explainable artificial intelligence for Bayesian neural networks: Toward trustworthy predictions of ocean dynamics. *Journal of Advances in Modeling Earth Systems*. 2022;14 e2022MS003162.

* Cortés and Lopez-Hernandez, 2021 Cortés AJ, Lopez-Hernandez F. Harnessing crop wild diversity for climate change adaptation. *Genes*. 2021;12:783.

* Edenhofer, 2014 Edenhofer O. *IPCC: Summary for policymakers*. *Climate change 2014: Mitigation of climate change Contribution of Working Group III to the fifth assessment report of the Intergovernmental Panel on Climate Change* Cambridge University Press 2014;.

* France-Presse, 2021 France-Presse, A. (2021, Sept 23). Wildfires emitted record levels of more than 2.5 billion tonnes of CO[2] in July and August alone. Available from `https://www.firstpost.com/`.

* Goodman and Horton, 2021 Goodman, J., & Horton, J. (2021). Wildfires: How are they linked to climate change? Available from `https://www.bbc.com/news`.

* Hirschlag, 2023 Hirschlag, A. (2023). Smoke from burning forests and peat can linger in the atmosphere for weeks, travelling thousands of miles and harming the health of populations living far away. Available from `https://www.bbc.com/future/article/20200821-how-wildfire-pollution-may-be-harming-your-health`.
