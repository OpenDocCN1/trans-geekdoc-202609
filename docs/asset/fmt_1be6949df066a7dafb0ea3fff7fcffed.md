
系统通过考虑多种因素来调节压力水平，如图2.2所示，这些因素包括道路状况、目标速度和油门输入程度。无级变速器（CVT）的管理是一项复杂的任务，因为必须考虑多种因素。这些因素包括速度、温度、油液粘度以及阀门的设计。这些组件之间相互作用，导致系统高度复杂。使用旨在处理复杂度较低系统的传统方法来控制无级变速箱（CVT）存在固有挑战。本章的主要目标是揭示如何简化此类变速箱的复杂性并提高相关发动机的速度。减少系统各部分之间相互作用的延迟时间可以降低负载，并有助于实现整个系统的良好性能。图2.1展示了用于获得滑轮压力的控制系统的设计。

![](img/e9de70cd491e84262133af63cb33d500_43_0.png)

**图2.1** 车辆传动系统配备无级变速箱（CVT）和湿式多片离合器。FD是终传减速比的缩写。

## 2.2 性能规格

目标是在合理的时间内（理想情况下为60到70毫秒）达到所需的压力，且不超出规定限制。目标是尽量减少大幅度超调（O.S.），因为它们有可能导致皮带过度松弛，从而从滑轮上脱开并造成系统潜在损坏。

![](img/e9de70cd491e84262133af63cb33d500_44_0.png)

**图2.2** 该示意图展示了系统的原理图，包括高级控制器。

## 2.3 无级变速器（CVT）的物理模型

Minten和Vanvuchelen开发了该系统的详细物理模型。该主题之所以复杂，是因为它全面涵盖了无级变速箱（CVT）的活动。这种方法的利用在重现现实世界现象方面被证明是有利的；然而，其冗长的执行时间使其不适合用于设计控制机制。此外，为了控制目的还设计了一个更简化的模型。该系统提供一个可控参数，即供给脉宽调制伺服阀的电压，表示为$V_{\text{in}}$。测量涵盖两个变量，即温度（$T$）和发动机转速（$N_{\text{engine}}$）。这项研究关注单一输出变量，即作用在滑轮上的压力大小。图2.3说明了非线性（$f$）与发动机转速（$N_{\text{engine}}$）之间的关系，表明前者对后者有显著依赖。

该过程通过利用静态非线性函数（表示为$f(V_{\text{in}}, N_{\text{engine}}$））以及具有可变参数的动态线性系统$G(s)$来表示。图2.4提供了变量$f$与发动机转速之间的相关性。图表是针对不同的发动机转速绘制的。

![](img/e9de70cd491e84262133af63cb33d500_45_0.png)

![](img/e9de70cd491e84262133af63cb33d500_45_1.png)

在保持温度恒定的情况下，考察静态非线性$f$在各种发动机转速（$N_{engine}$）值下的表现。模糊推理系统（FIS）[3–5]决定了参数$P$和$T_i$是如何生成的。

## 2.4 控制器设计

控制器构建的第一阶段是使用非线性$f(V_{in}, N_{engine})$的反函数$\hat{f}^{-1}(V_{in}, N_{engine})$对其进行补偿。由于函数$f(., .)$的单调性，可以观察到这种技术是适用的。在获得$T$和$N_{engine}$的各种数值下的局部线性模型以及函数$\hat{f}^{-1}(., .)$之后，采用一种优化方法来计算给定工作点的次优比例积分（PI）控制器（图2.5）。优化的代价函数规定为

$$J(K_p, T_i) = \lambda M_p + (1 - \lambda) \int_0^{\infty} t (e^2(t) dt)^{1/2} \quad (2.1)$$

其中$K_p$和$T_i$分别代表PI控制器的比例增益和积分时间。$\lambda$的值等于0.5，用于量化代价函数中O.S.的重要性。

![](img/e9de70cd491e84262133af63cb33d500_46_0.png)

**图2.5** 生成的参数$P$和$T_i$。

跟踪误差表示为

$$e(t)=P_{\mathrm{ref}}(t)-P_{\mathrm{sec}}(t) \tag{2.2}$$

代表了时间$t$时理想值与次级值之间的差异。O.S.，$M_p$，表征输出$y(t)$的最大偏差。在数学上，$M_p$定义为

$$M_p=\max\{\max\{y(t)-1\}, 0\}. \tag{2.3}$$

展示了使用准牛顿法进行无约束多变量优化的过程。包含一系列局部PI控制器的PI控制器在连续时间中可以数学表达为

$$C(s)=K_{p}\left(T,N_{\text {engine }}\right)\left(1+\frac{1}{T_{i}\left(T,N_{\text {engine }}\right)s}\right). \tag{2.4}$$

在离散时间的背景下，表达式可以写为

$$C(z)=K_{p}\left(T,N_{\text {engine }}\right)\left(1+\frac{1}{T_{i}\left(T,N_{\text {engine }}\right)\left(1-z^{-1}\right)}\right). \tag{2.5}$$

通过采用这种方法，考虑了所有量化效应，从而提高了控制器的精度。$K_p(T,N_{\text{engine}})$、$T_i(T,N_{\text{engine}})$和$\hat{f}^{-1}(V_{\text {in }}^{r}, N_{\text {engine }})$的值被限制在某些工作点。需要一种插值方法来促进不同运行位置之间的平滑过渡。必须利用插值方法。已确定，一种有效的方法将涉及利用FIS [6–9]来近似查找表。该FIS [10–13]的主要属性包括高斯隶属函数，采用重心法。控制器如图2.6所示。

## 2.5 稳定性分析

变速箱在多个交互组件的稳定性方面已经实现了稳定。变速箱的轴有时在稳定动作方面会出现一些问题，但通过模糊逻辑系统[14–17]可以使整体组件及其相互作用得到稳定。不同的基于模糊逻辑的模型[18–22]已在许多已报告的工作中用于评估稳定性。我们可以利用“Takagi–Sugo模糊模型”来描绘闭环系统，假设标记为$f(.,.)$的非线性已被完全消除。为了说明这一点，考虑一条规则，Rule$_i$，其中$\mu_i$代表温度，$\mu_j$代表发动机。在此上下文中，变量$x$的变化率方程可以表示为

$$\dot{x} = A_{i}\tilde{x} + B_{i}\tilde{u}. \quad (2.6)$$

![](img/e9de70cd491e84262133af63cb33d500_48_0.png)

**图2.6** 模糊控制器与线性规划控制器的比较。

在此上下文中，当存在一个满足以下不等式的共享正定矩阵$P$时，稳定性要求得以满足：

$$P > 0 \quad (2.7)$$

$$A_{i}^{T} P + P A_{i} < 0 \quad (2.8)$$

$$\forall i \in \{1, ..., N_{\text{rules}}\} \quad (2.9)$$

$P$矩阵的确定可以通过解决可行性线性矩阵不等式（LMI）问题来实现。已为该问题找到一个可行解，确保了稳定性。图2.6提供了模糊控制器与线性规划控制器的模型[23–27]。

本研究考察了实施模糊控制器[28–30]与线性规划控制器相比所取得的改进。需要注意的是，不仅性能有所提升，而且由于规则库解释提供了更多信息，设计修改的实施也变得更容易。

## 2.6 结论

本节阐明了设计无级传动控制系统的过程。控制系统采用模糊推理方法来

根据对扰动的测量，动态修改控制器的参数。采取了以下措施。

1. 通过优化过程计算了适用于各种场景的线性控制器。
2. 开发了非线性补偿器，以适应不同的发动机转速值 ($N_{\text{engine}}$)。
3. 为了建立稳定性，成功解决了一个名为 LMI 的数学问题。
4. 所构建的控制器还提供了对调度机制的全面阐述，从而促进了工业环境中系统优化的过程。控制系统的评估以对比形式展示在图 2.7 中。

![](img/e9de70cd491e84262133af63cb33d500_49_0.png)

**图 2.7** 控制系统的对比评估。

该图表描绘了一条代表参考值的实线，一条代表具有前馈作用的线性控制器的虚线，以及一条代表模糊控制器的点线。显而易见，模糊控制器有效地减少了系统的超调量（O.S.）和调节时间。

## 关键词

- 模糊逻辑
- 无级变速箱
- 模糊控制器
- 模糊推理系统
- 非线性补偿器

## 参考文献

1. Grace. (1992). Optimization Toolbox—For use with MATLAB. Mathworks, Inc.
2. Isidori. (1989). Nonlinear Control Systems—An Introduction, 2nd edn. Springer-Verlag.
3. Peña Reyes, C. A. (2002). Cooevolutionary fuzzy modeling. PhD thesis, Ecole Polytechnique Fédérale de Lausanne.
4. von Alstroek. (1995). Fuzzy logic applications in Europe. Industrial Applications of Fuzzy Logic and Intelligent System, IEEE Press.
5. Broadbent. (1975). The magic number seven after fifteen years. Studies in Long Term Memory, Addison Wesley: USA.
6. Clarke, D., Mohtadi, C., & Tuffs, P. (1987). Generalized predictive control-parts i–ii. Automatica, 23, 137–160.
7. Drankov, D., Hellendoorn, H., & Reinfrank, M. (1993). An Introduction to Fuzzy Control. Springer-Verlag.
8. Goldberg, D. E. (1989). Genetic Algorithms in Search, Optimization and Machine Learning, Addison Wesley: USA.
9. Camacho, C. B. (1995). Model Predictive Control in the Process Industry. Springer-Verlag: London.
10. Gustafson, E., & Kessel, W. (1979). Fuzzy clustering with fuzzy covariance matrix. In: Proc. IEEE Control Decision Conference, pp. 761–766.
11. Ecole Nationale Supérieure de Techniques Avancées (ENSTA), Optimization and Control Group: (1998), LMITOOL-2.0 package.
12. Allgöwer, T. B., Qin, J., Rawlings, J., & Wright, S. (1999). Nonlinear predictive control and moving horizon estimation– an introductory overview. Advances in Control—Highlights of ECC’99. Springer-Verlag.
13. Box, G. J. (1970). Time Series Analysis, Forecasting and Control. Holden Day: San Francisco, CA.
14. Goodwin, G., & Sin, K. (1984). Adaptive Filtering Prediction and Control. Prentice Hall: Englewood Cliffs, NJ.
15. Lightbody, G., & Irwin, G. (1997). Nonlinear control structures based on embedded neural system models. *IEEE Transactions on Neural Networks and Learning Systems*, 8, 553–567.
16. Akaïke. (1974). A new look at the statistical model identification. *IEEE Transactions on Automatic Control*, 19, 716–723.
17. Ying, H. (1998). The Takagi–sugeno fuzzy controllers using the simplified linear control rules are the nonlinear variable gain controller. *Automatica*, 34(2), 157–167.
18. Abonyi, H. A., Nagy, L., & Széifert, F. Inverse fuzzy-process-model based direct adaptive control. URL citeeear.nj.nec.com/abonyi99inverse.html.
19. Bezdek. (1976). A physical interpretation of fuzzy data. *IEEE Transactions on Systems, Man, and Cybernetics 6*(5), 387–389.
20. Espinosa, J., & Vandewalle, J. (1998). Fuzzy modeling and identification, using afreli and fuzion algorithms. In: *Proceedings of the 5th. International Conference on Soft Computing IIZUKA-98 Iizuka, Japan*, pp. 535–540.
21. Espinosa, J., & Vandewalle, J. (1998). Fuzzy modeling with linguistic integrity. In: *Proceedings of the International Workshop on Advanced Black Box Techniques for Nonlinear Modeling Leuven, Belgium*, pp. 197–202.
22. Espinosa, J., & Vandewalle, J. (1998). Predictive control using fuzzy models applied to a steam generating unit. In: Ruan, D., Abderrahim, H. A., D’hondt, P., & Kerre, E. (Eds.), *Fuzzy Logic and Intelligent Technologies for Nuclear Science and Industry*. World Scientific: Singapore.
23. Espinosa, J., & Vandewalle, J. (1999). Constrained predictive control using fuzzy models. In: *Proceedings of the Eight International Fuzzy Systems Association World Congress (IFSA-99) Taiwan*, pp. 649–654.
24. Espinosa, J., & Vandewalle, J. (1999). Predictive control using fuzzy models. In: Roy, R., Furuhashi, T., & Chawdhry, P. (Eds.), *Advances in Soft Computing Engineering Design and Manufacturing*. Springer-Verlag: London.
25. Espinosa, J., & Vandewalle, J. (2000). Constructing fuzzy models with linguistic integrity-afredl algorithm. *IEEE Transactions on Fuzzy Systems*, 8(5), 591–600.
26. Espinosa, J., & Vandevvalle, J. (2003). Extracting linguistic fuzzy models from numerical data-afreli algorithm. In: Cassillas, J., Cordon, O., Herrera, F., & Magdalena, L. (Eds.), *Interpretable Issues in Fuzzy Modeling*. Springer-Verlag: London.
27. Espinosa, J., Hadjili, M., Wertz, V., & Vandewalle, J. (1999). Predictive control using fuzzy models-comparative study. *Proceedings of the European Control Conference-99*.
