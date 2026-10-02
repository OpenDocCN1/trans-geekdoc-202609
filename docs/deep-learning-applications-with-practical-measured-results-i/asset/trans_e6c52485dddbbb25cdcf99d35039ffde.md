
他最近的研究兴趣包括物联网、机器学习和深度学习、移动通信以及智能交通系统。

**Feng-Jang Hwang** 是悉尼科技大学数学与物理科学学院工业优化组的首席主要研究员，并担任高级讲师（C级，相当于北美学术体系中的副教授）。他于2011年获得国立交通大学信息管理博士学位。F.J. 两次当选为 Phi-Tau-Phi 学术学会的荣誉会员。他是2016年澳大利亚运筹学会新星奖的提名者，并获得2017年 Albert Nelson Marquis 成就奖。他的研究兴趣集中于生产建模与排程、供应链与物流优化、数据驱动优化和计算智能。F.J. 在包括《Journal of Scheduling》、《Annals of Operations Research》、《Journal of the Operational Research Society》、《Computers & Operations Research》、《Discrete Optimization》、《Engineering Optimization》、《IEEE Access》、《International Journal of Sustainable Transportation》等在内的领先期刊上发表论文。他曾担任多家国际期刊的客座编辑，包括《International Journal of Distributed Sensor Network》、《EURASIP Journal on Wireless Communications and Networking》、《Electronics》和《Agronomy》。他受邀发表了30多次研究演讲和会议报告。他的职业经历包括在台湾海军总部担任物流军官（少尉）、在中央研究院统计科学研究所担任研究助理，以及在国立清华大学、国立交通大学和华威商学院担任博士后研究员。

## Editorial
## Deep Learning Applications with Practical Measured Results in Electronics Industries

Mong-Fong Horng 1, Hsu-Yang Kung 2, Chi-Hua Chen 3,* and Feng-Jang Hwang 4

1 电子工程系，国立高雄科技大学，高雄 80778，台湾；mfhorng@nkust.edu.tw
2 管理信息系统系，国立屏东科技大学，屏东 91201，台湾；kung@mail.npust.edu.tw
3 数学与计算机科学学院，福州大学，福州 350100，中国
4 数学与物理科学学院，悉尼科技大学，Ultimo，新南威尔士州 2007，澳大利亚；Feng-Jang.Hwang@uts.edu.au
* 通讯作者：chihua0826@gmail.com；电话：+86-18359183858

收稿日期：2020年3月11日；接受日期：2020年3月12日；出版日期：2020年3月19日

摘要：本文社论介绍《Electronics》特刊“Deep Learning Applications with Practical Measured Results in Electronics Industries”。本期涵盖的主题包括四个主要部分：（I）环境信息分析与预测，（II）无人机（UAV）和目标跟踪应用，（III）测量与去噪技术，以及（IV）推荐系统和教育系统。关于环境信息分析与预测的四篇论文如下：（1）“A Data-Driven Short-Term Forecasting Model for Offshore Wind Speed Prediction Based on Computational Intelligence” by Panapakidis et al.；（2）“Multivariate Temporal Convolutional Network: A Deep Neural Networks Approach for Multivariate Time Series Forecasting” by Wan et al.；（3）“Modeling and Analysis of Adaptive Temperature Compensation for Humidity Sensors” by Xu et al.；（4）“An Image Compression Method for Video Surveillance System in Underground Mines Based on Residual Networks and Discrete Wavelet Transform” by Zhang et al. 关于无人机和目标跟踪应用的三篇论文如下：（1）“Trajectory Planning Algorithm of UAV Based on System Positioning Accuracy Constraints” by Zhou et al.；（2）“OTL-Classifier: Towards Imaging Processing for Future Unmanned Overhead Transmission Line Maintenance” by Zhang et al.；（3）“Model Update Strategies about Object Tracking: A State of the Art Review” by Wang et al. 关于测量与去噪技术的五篇论文如下：（1）“Characterization and Correction of the Geometric Errors in Using Confocal Microscope for Extended Topography Measurement. Part I: Models, Algorithms Development and Validation” by Wang et al.；（2）“Characterization and Correction of the Geometric Errors Using a Confocal Microscope for Extended Topography Measurement, Part II: Experimental Study and Uncertainty Evaluation” by Wang et al.；（3）“Deep Transfer HSI Classification Method Based on Information Measure and Optimal Neighborhood Noise Reduction” by Lin et al.；（4）“Quality Assessment of Tire Shearography Images via Ensemble Hybrid Faster Region-Based ConvNets” by Chang et al.；（5）“High-Resolution Image Inpainting Based on Multi-Scale Neural Network” by Sun et al. 关于推荐系统和教育系统的两篇论文如下：（1）“Deep Learning-Enhanced Framework for Performance Evaluation of a Recommending Interface with Varied Recommendation Position and Intensity Based on Eye-Tracking Equipment Data Processing” by Sulikowski et al. 和（2）“Generative Adversarial Network Based Neural Audio Caption Model for Oral Evaluation” by Zhang et al.

关键词：深度学习；机器学习；监督学习；无监督学习；强化学习；优化技术

## 1. Introduction

机器学习和深度学习技术已成为电子工业应用开发中进行特征提取和事件估计的关键工具 [1–8]。一些技术已在嵌入式系统中实现并应用于工业4.0应用、工业电子应用、消费电子应用和其他电子应用。例如，监督学习技术，包括神经网络（NN）[9–19]、卷积神经网络（CNN）[20–26]和循环神经网络（RNN）[27–32]，可用于电子工业中的预测应用和分类应用。无监督学习技术，包括受限玻尔兹曼机（RBM）[33,34]、深度信念网络（DBN）[35]、深度玻尔兹曼机（DBM）[36]、自动编码器（AE）[37,38]和去噪自动编码器（DAE）[39]，可用于去噪和泛化。此外，强化学习技术，包括生成对抗网络（GANs）[40,41]和深度Q网络（DQNs）[42]，可用于在零和博弈框架下获得生成网络和判别网络以进行竞争和优化。这些技术可以为电子应用提供精确的预测和分类。因此，本特刊的目的是向读者介绍电子工业中具有实际测量结果的深度学习应用的最新研究工作。

本特刊共收到45篇投稿，仅有14篇被接受。本期从评审过程中获得的68.89%的高拒稿率是为了确保具有重要成果的高质量论文被选出并发表。特刊的统计数据如下所示。

- 提交（45）；
- 发表（14）；
- 拒稿（31）；
- 文章类型：研究论文（13）；综述论文（1）。

本期涵盖的主题包括以下四个主要部分：（I）环境信息分析与预测，（II）无人机（UAV）和目标跟踪应用，（III）测量与去噪技术，以及（IV）推荐系统和教育系统。下面简要介绍四个被接受论文的主题。

## 2. Environmental Information Analyses and Predictions

关于环境信息分析与预测的四篇论文如下：（1）"A Data-Driven Short-Term Forecasting Model for Offshore Wind Speed Prediction Based on Computational Intelligence" by Panapakidis et al. [43]；（2）"Multivariate Temporal Convolutional Network: A Deep Neural Networks Approach for Multivariate Time Series Forecasting" by Wan et al. [44]；（3）"Modeling and Analysis of Adaptive Temperature Compensation for Humidity Sensors" by Xu et al. [45]；（4）"An Image Compression Method for Video Surveillance System in Underground Mines Based on Residual Networks and Discrete Wavelet Transform" by Zhang et al. [46]。

Panapakidis 等人来自希腊和塞浦路斯，在"A Data-Driven Short-Term Forecasting Model for Offshore Wind Speed Prediction Based on Computational Intelligence" 中认为风速时间序列数据具有高度非线性和波动性特征。因此，构建了自适应神经模糊推理系统（ANFIS）和前馈神经网络（FFNN）来分析风速的非线性和波动性以进行短期风速预测。在他们的实验中，选择了五种情况来预测1分钟前和10分钟前的风速，以评估所提出的方法。结果表明，所提出方法下每个案例的平均绝对范围归一化误差（MARNEs）均低于其他方法（例如回归神经网络、回归树、支持向量回归等）下每个案例的 MARNEs [43]。
