
12. Sfetsos, A. 用于平均小时风速时间序列预测的一种新方法。Renew. Energy 2002, 27, 163–174. [CrossRef]
13. Başaran, Ü.; Filik, T. 基于埃斯基谢希尔多地测量的人工神经网络风速预测。Energy Procedia 2017, 107, 264–269.
14. More, A.; Deo, M.C. 用神经网络预测风。Mar. Struct. 2003, 16, 35–49. [CrossRef]
15. Li, G.; Shi, J. 关于三种人工神经网络在风速预测中的比较。Appl. Energy 2010, 87, 2313–2320. [CrossRef]
16. Zeng, J.W.; Qiao, W. 基于支持向量机的短期风电功率预测。In Proceedings of the 2011 IEEE/PES Power Systems Conference and Exposition, Phoenix, AZ, USA, 20–23 March 2011; pp. 1–8.
17. Zhou, J.Y.; Shi, J.; Li, G. 短期风速预测的支持向量机微调。Energy Convers. Manag. 2011, 52, 1990–1998. [CrossRef]
18. Fazelpour, F.; Tarashkar, N.; Rosen, M.A. 使用人工神经网络对德黑兰进行短期风速预测。Iran. Int. J. Energy Environ. Eng. 2016, 7, 377–390. [CrossRef]
19. Fortuna, L.; Guariso, G.; Nunnari, S. 统计模型对风速等级的提前一天预测。Int. J. Renew. Energy Res. 2016, 6, 1137–1145.
20. Fortuna, L.; Nunnari, S.; Guariso, G. 风速时间序列中的分形阶证据。In Proceedings of the 2014 International Conference on Fractional Differentiation and Its Applications, Catania, Italy, 23–25 June 2014; pp. 1–6.
21. Mallat, S. 多分辨率信号分解理论——小波表示。IEEE Trans. Pattern Anal. Mach. Intell. 1989, 11, 674–693. [CrossRef]
22. Amjady, N.; Keynia, F. 小波变换与神经进化算法结合的电力系统短期负荷预测。Energy 2009, 34, 46–57. [CrossRef]
23. Jang, J.S.R. ANFIS：基于自适应网络的模糊推理系统。IEEE Trans. Syst. Man Cybern. 1993, 23, 665–685. [CrossRef]
24. Graupe, P. 人工神经网络原理，第二版；World Scientific: Singapore, 2007.
25. Levenberg, K. 最小二乘法中某些非线性问题求解的一种方法。Q. J. Appl. Math. 1944, 2, 164–168. [CrossRef]
26. Michalides, C.; Loukogeorgaki, E.; Angelides, D.C. 监测连接系泊浮体模块的响应。In Proceedings of the 27th International Offshore and Polar Engineering, Anchorage, AK, USA, 30 June–5 July 2013; pp. 869–876, ISBN 978-1-880653-99-9.
27. Abdel-Aal, R.E.; Elhadidy, M.A.; Shaahid, S.M. 使用基于GMDH的溯因网络对平均小时风速时间序列进行建模和预测。Renew. Energy 2009, 34, 1686–1699. [CrossRef]
28. Kumar, G.; Malik, H. 基于广义回归神经网络的印度西部地区风速预测模型。Procedia Comput. Sci. 2016, 93, 26–32. [CrossRef]
29. Troncoso, A.; Salcedo-Sanz, S.; Casanova-Mateo, C.; Riquelme, J.C.; Prieto, L. 基于局部模型的回归树用于超短期风速预测。Renew. Energy 2015, 81, 589–598. [CrossRef]
30. Sun, G.; Chen, Y.; Wei, Z.; Li, X.; Cheung, K.W. 使用相关向量机进行日前风速预测。J. Appl. Math. 2014, 2014, 1–6. [CrossRef]
31. Botha, N.; van der Walt, C.M. 使用支持向量回归和特征选择进行风速预测。In Proceedings of the 2017 Pattern Recognition Association of South Africa and Robotics and Mechatronics, Bloemfontein, South Africa, 29 November–1 December 2017; pp. 181–186.

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_31_0.png)

© 2019 作者保留。许可方 MDPI，瑞士巴塞尔。本文是一篇开放获取文章，根据知识共享署名（CC BY）许可的条款和条件分发（http://creativecommons.org/licenses/by/4.0/）。

文章

## 多元时间卷积网络：多元时间序列预测的深度神经网络方法

Renzhuo Wan 1, Shuping Mei 1, Jun Wang 1, Min Liu 2 and Fan Yang 1,*

1 纳米光学材料与存储器件研究中心，武汉纺织大学电子电气工程学院，武汉 430200，中国

2 粉末冶金国家重点实验室，中南大学物理与电子学院，长沙 410083，中国

* 通讯作者：yangfan@wtu.edu.cn

收稿：7 July 2019；接受：5 August 2019；发表：7 August 2019

**Abstract:** 多变量时间序列预测已在电力能源、空气学、气象学、金融、交通运输等领域得到广泛研究。传统建模方法模式复杂，且难以捕捉数据长期多元依赖关系以获得期望的预测精度。为解决这些问题，提出了基于循环神经网络（RNN）和卷积神经网络（CNN）方法的各种深度学习模型。为提高预测精度并最小化非周期数据多元时间序列数据的依赖性，本文采用一种新颖的多元时间卷积网络（M-TCN）模型对北京PM2.5和ISO-NE数据集进行分析。在该模型中，多变量时间序列预测被构建为非周期数据集的序列到序列场景。基于深度卷积神经网络提出了并行的多通道非对称结构残差块。结果与长短期记忆（LSTM）、卷积LSTM（ConvLSTM）、时间卷积网络（TCN）和多元注意力LSTM-FCN（MALSTM-FCN）等丰富的竞争算法进行了比较，表明我们的模型在预测精度、鲁棒性和泛化能力方面有显著提升。

**Keywords:** 深度学习；多元时间序列预测；多元时间卷积网络

### 1. 引言

随着物联网（IoT）应用和大数据的爆炸性增长，多元时间序列在许多领域变得无处不在，例如空气学 [1]、气象学 [2]、环境 [3]、多媒体 [4]、电力能源 [5]、金融 [6] 和交通运输 [7]。基于历史动态数据的精确趋势预测以及潜在危险事件预测是一个主要挑战，尤其对于非周期多元时间序列。一个关键原因是变量之间的非周期性和非线性，模型难以捕捉并自适应复杂的数据特征。传统方法如自回归（AR）[8]模型和高斯过程（GP）[9]可能失效。作为人工智能领域的重要组成部分，深度神经网络（DNNs）在许多任务上提供了最先进的精度 [10]，并在自然语言处理（NLP）、计算机视觉（CV）、时间序列分类和时间序列预测方面得到了深入发展。

受NLP中使用的算法（即序列到序列 [11,12] 和注意力机制）以及CV中使用的算法（即空洞卷积网络 [13] 和残差结构 [14]）启发，本文提出了M-TCN模型用于非周期多元时间序列预测，该模型将非周期数据构建为序列到序列并采用一种新颖的多通道和非对称残差块网络。该模型通过丰富的现有竞争模型对非周期时间序列数据集进行了交叉验证。本文其余部分组织如下：第2节回顾背景工作。第3节介绍所提模型的 methodology。第4节对实验进行分析和讨论。最后，第5节得出结论并展望。

### 2. 背景

多元时间序列预测的主要挑战之一是数据来源于短期和长期动态行为的非线性和非周期性。基于经典统计方法或机器学习算法建立了各种模型。

突出的经典单变量时间序列模型是具有经典统计算法的自回归（AR）及其后继。AR方法适用于平稳时间序列。改进的模型，如自回归积分滑动平均（ARIMA）[15]、自回归滑动平均（ARMA）[16] 和向量自回归（VAR）[17]，通过纳入灵活的指数平滑技术而发展。然而，对于长期时间模式，这些模型不可避免地容易过拟合且计算成本高，尤其对于高维输入。

另一种方法是将时间序列预测问题视为具有时变参数的一般回归问题，由机器学习模型应用，例如线性支持向量回归（SVR）[18]、随机森林 [19]、岭回归 [20] 和LASSO [21] 模型。这些模型由于机器学习社区中高质量的现成解决方案而在实践中更高效。尽管如此，基于机器学习的模型可能无法包含多元大数据集的复杂非线性依赖关系。

同时，卷积神经网络（CNNs）和循环神经网络（RNNs）构建的完善深度神经网络已被广泛应用于时间序列预测，这归功于开源深度学习框架，如Keras（Keras，可在网上获取：https://keras.io）、TensorFlow（TensorFlow，可在网上获取：https://tensorflow.org）和PyTorch（PyTorch，可在网上获取：https://pytorch.org），包括灵活而复杂的数学库。一些代表性模型是长短期记忆（LSTM）[22]及其继承者、卷积LSTM（ConvLSTM）[23]和多元注意力LSTM-FCN（MALSTM-FCN）[24]，它们克服了为混合长短期时域训练循环神经网络所涉及的挑战。然而，这些模型耗时且对非周期数据预测不稳健。

另一种用于时间序列预测的新方法是一种混合多尺度方法，如经验模态分解（EMD）[25]、集合EMD（EEMD）[26]、多级小波分解网络（mWDN）[27]和变分模态分解（VMD）[28]。这些方法用于将数据分解为不同频率分量以促进预测。然而，预设分解K值是训练模型输入的必要前提，这对于复杂的多元时间序列预测并不通用。

最近，提出了一种用于序列建模任务的预测序列模型的通用架构，即时间卷积网络（TCN）[29]，其由卷积和循环架构组成。TCN的突出特征是卷积架构设计和序列长度的因果性。此外，通过残差网络和扩展卷积的组合，很方便地构建非常深且宽的网络。在此背景下，我们的模型基于TCN设计，并对PM2.5和电力预测进行了测试。

为比较，表1对比了多元时间序列预测的一些常见方法的优势和挑战。
