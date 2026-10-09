

## 参考文献

9. Ozkaya, U., Ozturk, S., Barstugan, M., Coronavirus (COVID-19) Classification using Deep Features Fusion and Ranking Technique. arXiv preprint arXiv:2004.03698, 11, 1581, 2020.
10. Ong, E., Wong, M.U., Huffman, A., He, Y., COVID-19 coronavirus vaccine design using reverse vaccinology and machine learning. Front. Immunol., 11, 1581, 2020.
11. Gysi, D.M., Valle, D., Zitnik, M., Ameli, A., Gan, X., Varol, O., Barabsi, A.L., Network Medicine Framework for Identifying Drug Repurposing Opportunities for COVID-19. arXiv preprint arXiv:2004.07229, 2020.
12. Ge, Y., Tian, T., Huang, S., Wan, F., Li, J., Li, S., Cheng, L., A data-driven drug repositioning framework discovered a potential therapeutic agent targeting COVID-19. bioRxiv, 1, 1–62, 2020.
13. Batra, R., Chan, H., Kamath, G., Ramprasad, R., Cherukara, M.J., Sankaranarayanan, S., Screening of Therapeutic Agents for COVID-19 using Machine Learning and Ensemble Docking Simulations. arXiv preprint arXiv:2004.03766, 2020.
14. Bullock, J., Pham, K.H., Lam, C.S.N., Luengo-Oroz, M., Mapping the landscape of artificial intelligence applications against COVID-19. arXiv preprint arXiv:2003.11336, 2020.
15. Ardabili, S.F., Mosavi, A., Ghamisi, P., Ferdinand, F., Varkonyi-Koczy, A.R., Reuter, U., Atkinson, P.M., COVID-19 Outbreak Prediction with Machine Learning, Algorithms, 13, 10, 249, 2020.
16. Desautels, T., Zemla, A., Lau, E., Franco, M., Faissol, D., Rapid in silico design of antibodies targeting SARS-CoV-2 using machine learning and supercomputing. bioRxiv, 1, 1–14, 2020.
17. Shi, F., Wang, J., Shi, J., Wu, Z., Wang, Q., Tang, Z., Shen, D., Review of artificial intelligence techniques in imaging data acquisition, segmentation and diagnosis for COVID-19. IEEE Rev. Biomed. Eng., 14, 4–15, 2020.
18. Naudé, W., Artificial intelligence vs COVID-19: limitations, constraints and pitfalls. AI & Soc., 35, 3, 761–765, 2020.
19. Santosh, K.C., AI-driven tools for coronavirus outbreak: Need of active learning and cross-population train/test models on multitudinal/multimodal data. J. Med. Syst., 44, 5, 1–5, 2020.
20. Rahmatizadeh, S., Valizadeh-Haghi, S., Dabbagh, A., The role of Artificial Intelligence in Management of Critical COVID-19 patients. J. Cell. Mol. Anesthesia, 5, 1, 16–22, 2020.
21. Dey, L., Chakraborty, S., Mukhopadhyay, A., Machine learning techniques for sequence-based prediction of viral-host interactions between SARS-CoV-2 and human proteins. Biomed. J., 43, 5, 438–450, 2020.
22. Chakladar, D.D. and Chakraborty, S., Feature extraction and classification in brain-computer interfacing: Future research issues and challenges, in: Natural Computing for Unsupervised Learning, pp. 101–131, Springer, Cham, 2019.
23. Goswami, S., Chakraborty, S., Saha, H.N., An univariate feature elimination strategy for clustering based on metafeatures. Int. J. Intell. Syst. Appl., 9, 10, 20, 2017.
24. Goswami, S., Das, A.K., Guha, P., Tarafdár, A., Chakraborty, S., Chakrabarti, A., Chakraborty, B., An approach of feature selection using graph-theoretic heuristic and hill climbing. Pattern Anal. Appl., 22, 2, 615–631, 2019.

# 用于 COVID-19 传播动力学分析的机器学习技术实现

C. Vijayalakshmi$^{1*}$ 和 S. Bangusha Devi$^{2}$

$^{1}$印度泰米尔纳德邦中央大学统计学与应用数学系，Thiruvavur，泰米尔纳德邦，印度  
$^{2}$JP 工程学院科学与人文学系，Tenkasi，泰米尔纳德邦，印度

## 摘要

本文主要涉及用于分析 COVID-19 传播动力学的机器学习模型设计。由于冠状病毒，全球都受到了影响。依赖呼吸机的患者、重症急性呼吸衰竭患者以及隔离护理重症监护病房（ICU）患者，由于呼吸系统疾病、语言障碍或插管等原因，经常在其最基本的人际互动，即沟通方面面临困难。ICU 患者在身体和心理层面因沟通问题而受到严重影响。研究人员开发了不同类型的服务，如言语语言病理学家，以便为所有医疗专业人员 and 护理人员提供增强型替代沟通辅助。设计了一个概率模型来分析新病例和死亡病例。使用机器学习方法设计了回归模型，并展示了未来的预测。讨论了模型的充分性，并给出了新病例和死亡病例的残差。获得了 PCF 和 APCAF。本文主要涉及一个概率模型，用于分析和预测 COVID-19 的新病例和死亡病例。执行了新的平稳性分析变换，并基于此执行预测。

**关键词：** 统计模型，COVID-19，全球，大流行病，ARIMA，回归分析

## 14.1 引言

COVID-19 目前是困扰全球各国的致命性疾病，具有不同的症状。该疾病的流程图如图 14.1 所示。

![](img/bb4a43d3cc1537c84f048d14c493ee68_329_0.png)

**图 14.1** 流程图——COVID-19 的症状和预测措施。

## 14.2 数据分析

数据从世界卫生组织（WHO）收集，并使用统计技术进行了分析。数据已通过现有的统计技术进行预处理和归一化。

## 14.3 方法论

### 14.3.1 线性回归模型

**(i) 模型识别**

首先，使用预测变量和自变量的散点图来识别它们之间的关系。这在二维几何中可视化。绘制数据点，线性回归模型定义为

$$Y = b_0 + b_1X + \varepsilon$$

其中 Y 是响应变量，$b_{0}$ 是截距，$b_{1}$ 是回归系数，X 是预测变量，$\varepsilon$ 是误差项 [10, 13]。为了实现对响应变量和预测变量的识别，可以通过获得未知参数或回归系数的估计值来确定模型。可以使用最小二乘法估计回归系数，前提是满足以下假设：

- i. 响应变量 Y 与自变量 X 之间的关系近似为线性。
- ii. 误差项具有零均值和常数方差
- iii. 误差项正态分布，且
- iv. 误差不相关。

**(ii) 参数估计**

使用最小二乘法估计 $\beta_{0}$ 和 $\beta_{1}$。为了估计模型参数，首先计算以下项，

$$S_{xx}=\sum_{i=1}^{n}x_{i}^{2}-\left(\frac{\sum_{i=1}^{n}x_{i}}{n}\right)^{2}$$

![](img/bb4a43d3cc1537c84f048d14c493ee68_331_0.png)

**图 14.2** 线性回归模型。

$$S_{xy} = \sum_{i=1}^n x_i y_i - \frac{\left(\sum_{i=1}^n y_i\right)\left(\sum_{i=1}^n x_i\right)}{n}$$

$$\hat{\beta}_1 = \frac{S_{xy}}{S_{xx}} \text{ 且 } \hat{\beta}_0 = \bar{y} - \hat{\beta}_1 \bar{x}$$

数学上，第 $i$ 个残差为

$$e_i = y_i - \hat{y}_i = y_i - (\hat{\beta}_0 + \hat{\beta}_1 x_i), i = 1, 2, ..., n.$$

上述图 14.2 展示了沿独立变量和因变量的回归线的数据点。正在进行平方和计算及残差分析。

**(iii) 模型充分性研究**

使用残差估计值来分析拟合回归模型的充分性。正态性假设可通过正态 P–P 图进行验证。残差非相关性的假设可通过应用 Durbin–Watson 检验进行测试。这也被称为自相关检验。自相关术语指的是随机变量的连续取值之间的关系。回归模型的充分性如图 14.3 所示。如果 $\rho$ 表示自相关系数，则检验假设，且检验统计量如下：

$$d = \frac{\sum_{i=2}^{n}(e_t - e_{t-1})^2}{\sum_{i=1}^{n}e_t^2}$$

