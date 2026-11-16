

![](img/aa2f42c739937b682075082233e335bb_120_0.png)

**图3.12** 四个疑似发生漂移的变量的残差：MBR 1和2水位，RAS pH，以及透过液电导率。蓝色垂直虚线表示训练窗口的结束以及实时监控开始的时间。(A) mbr_1_level 的残差；(B) mbr_2_level 的残差；(C) ras_ph 的残差；(D) perm_cond 的残差。

系统的逻辑共同体。在此案例研究中，我们应用实时FD&I方法，展示先进的过程监控方法如何在系统操作员察觉之前识别系统中的故障。

2010年4月10日至16日，一周的一分钟观测数据被用作训练数据集，共包含10,045个观测。我们从4月17日开始监控，并监控系统11天（14,859个观测）。与Sect. 3.5.1中呈现的案例研究一样，我们使用一组预测变量（及其滞后值）和循环变量对观测数据进行去趋势化。数据集描述、去趋势过程的额外细节以及用于去趋势的变量可参见[42]。

我们预计在 mbr_1_level、mbr_2_level、ras_ph 和 perm_cond 中观察到漂移。四个漂移变量的残差如Fig. 3.12所示。在训练窗口期间，mbr_1_level、mbr_2_level 和 ras_ph 的残差均具有大致恒定的均值；然而，perm_cond 中仍存在一些非平稳性。mbr_1_level 和 mbr_2_level 残差的下移发生在4月22日左右，且对MBR 2水槽更为严重。ras_ph 残差的下降首先发生在4月17日，并在4月19日恢复，但又在4月23日左右开始再次下降。大约在同一时间，perm_cond 残差开始上升。

对于FD，我们通过将每个去趋势变量的滞后版本纳入监控，应用主成分分析（PCA）的动态扩展[97–100]。对于每个观测，我们保留捕获85%变异性的主成分，并计算Hotelling’s T²和Q（也称为SPE）。如果任一统计量在误报率为 alpha = 0.01 的非参数阈值下超标，则该观测被标记为失控（OC）。该方法的更多细节可见[94]和[95]，它们也将PCA的变体应用于该数据集进行FD。当观测被标记为OC时，我们应用由[55]提出并在Sect. 3.2.3.2中描述的FI方法，以识别均值的非零分量，这些分量对应于漂移变量，因为训练窗口的去趋势数据已被中心化。

![](img/aa2f42c739937b682075082233e335bb_121_0.png)

**图3.13** 监控期间的监控统计量 \( T^2 \)（顶部）和 Q 或 SPE（底部）。红色水平线（印刷版中为中灰色）表示用于将观测分类为OC的非参数阈值。(A) \( T^2 \) 监控统计量；(B) SPE 监控统计量。

Fig. 3.13 给出了监控期间的监控统计量 \( T^2 \) 和 SPE。非参数阈值是根据训练期间监控统计量的核密度估计（KDE）的百分位数确定的，以红色（印刷版中为中灰色）给出。两个统计量倾向于遵循相同的模式，即当其中一个较大时，另一个也较大，并且当Fig. 3.12中一个或多个变量发生漂移时，监控统计量倾向于较大。有三个时间段，统计量持续超过其对应的阈值：(1) 4月17日至19日期间 ras_ph 的首次下移期间；(2) 4月22日 MBR 水位故障期间；以及(3) 从大约4月24日开始至监控结束，在此期间 ras_ph 和 perm_cond 变得越来越失控。

既然FD方法已检测到系统中的故障，则应用FI方法来识别漂移变量。Fig. 3.14 绘制了监控期间每个变量被分类为漂移或未漂移的情况，其中黑色框表示该变量在给定时间点被识别为漂移，否则为白色。我们强烈怀疑已发生漂移的变量以黄色突出显示（印刷版中为浅灰色）。这种图表被称为棋盘图，有助于跟踪漂移变量随时间的变化 [15,73]，并展示故障如何随时间从一个变量传播到另一个变量，特别是在实现了反馈控制的系统中 [66]。

![](img/aa2f42c739937b682075082233e335bb_122_0.png)

图3.14 故障隔离结果的棋盘图，其中黑色框表示变量在给定时间点被识别为漂移，否则为白色。怀疑真正发生漂移的变量以黄色突出显示（印刷版中为浅灰色）。

4月17日至19日期间，ras_ph 持续被识别为漂移。mbr_2_level 的漂移也被清晰识别，但 mbr_1_level 的漂移未被识别；这可能是因为漂移幅度小得多，并可能被训练期间的一些极端值掩盖。4月23日结束时，ras_ph 中识别出另一个漂移，并持续被标记为漂移直到监控结束。然而，perm_cond 未被识别为漂移，这可能是由于残差中存在非平稳性。在 bio_1_temp、bio_2_temp 和 ras_temp 等变量中识别出的其他漂移也可能是由数据中的非平稳性或噪声引起的，在缺乏变量发生漂移的持续证据的情况下可以忽略。

操作员直到4月24日上午10:00才收到故障警报，一旦确定了根本问题，系统花了两个月时间才完全恢复并实现正常运行条件。使用本案例研究中提出的FD&I方法本可更早检测到故障，并会向操作员指出负责故障的一些关键变量，从而使他们能够更快地解决问题。在拥有众多复杂相关变量的系统中，FD通常是不够的，因为操作员可能难以识别漂移变量，尤其是在随时间变得更严重的漂移故障的情况下。因此，FI是在整个系统受影响之前诊断故障的重要步骤。

## 3.6 进一步阅读

已发表了一些包含进一步阅读参考文献的优秀综述论文。Capizzi [101] 总结了一些基于VS的第二阶段控制图，并指出了一些开放的研究领域，例如开发无分布法、用于自相关数据的方法以及用于第一阶段分析的VS方法。Peres 和 Foglia [102] 提供了对整合到多元统计过程监控中的30种VS方法的广泛近期综述。列出了每篇论文解决的现有方法局限性及其各自的目标。他们将方法分为以下几类：(i) 在过程监控前通过执行VS对变量进行预处理；(ii) 在过程监控后通过执行VS对变量进行后处理；或(iii) 在VS和过程监控之间进行迭代。他们以自己的未来研究主题列表结束，其中一些与[101]重叠。其他独特问题包括对批处理过程和故障诊断方法的更多工作，Reis 和 Gins [66] 也将其引用为未来工作的重要领域。事实上，Reis 和 Gins [66] 对工业过程监控的发展和未来需求提供了非常好的高级概述，其中包括基于VS的监控以及隔离和分类方法。他们观察到，故障检测速度相对于诊断故障所需的时间较低，因此主张研究人员专注于故障预后，后者旨在预判故障并在故障发生前干预系统以进行维护或修理。最后，Qin [103] 提供了一篇更侧重技术的综述，重点介绍了PCA和PLS，以及在受控系统背景下使用重建图进行故障隔离。

## 参考文献

- [1] M. Turkoz, S. Kim, Y.-S. Jeong, K.N. Al-Khalifa, A.M. Hamouda, Distribution-free adaptive step-down procedure for fault identification: non-parametric fault identification approach, Quality and Reliability Engineering International 32 (8) (2016) 2701–2716.
- [2] K. Wang, W. Jiang, High-dimensional process monitoring and fault isolation via variable selection, Journal of Quality Technology 41 (2009) 247–258.
- [3] C. Zou, W. Jiang, F. Tsung, A LASSO-based diagnostic framework for multivariate statistical process control, Technometrics 53 (3) (2011) 297–309.
- [4] C. Zhao, W. Wang, Efficient faulty variable selection and parsimonious reconstruction modelling for fault isolation, Journal of Process Control 38 (2016) 31–41.
- [5] N. Shinozaki, T. Iida, A variable selection method for detecting abnormality based on the T² test, Communications in Statistics. Theory and Methods 46 (2017) 8603–8617.
- [6] W. Jiang, K. Wang, F. Tsung, A variable-selection-based multivariate EWMA chart for process monitoring and diagnosis, Journal of Quality Technology 44 (2012) 209–230.
- [7] K. Paynabar, C. Zou, P. Qiu, A change-point approach for phase-I analysis in multivariate profile monitoring and diagnosis, Technometrics 58 (2) (2016) 191–204.
- [8] G. Capizzi, G. Masarotto, Phase I distribution-free analysis of multivariate data, Technometrics 59 (2017) 484–495.
- [9] M. Hubert, T. Reynkens, E. Schmitt, T. Verdonck, Sparse PCA for high-dimensional data with outliers, Technometrics 58 (4) (2016) 424–434.
- [10] D. Dong, T.J. McAvoy, Batch tracking via nonlinear principal component analysis, AIChE Journal 42 (1996) 2199–2208.
- [11] F. Baggiani, S. Marsi-Libelli, Real-time fault detection and isolation in biological wastewater treatment plants, Water Science and Technology: a Journal of the International Association on Water Pollution Research 60 (2009) 2949–2961.
- [12] D.S. Lee, P.A. Vanrolleghem, Adaptive consensus principal component analysis for on-line batch process monitoring, Environmental Monitoring and Assessment 92 (2004) 119–135.

