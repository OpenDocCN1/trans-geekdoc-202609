

## 6.9 使用预测阶数

显而易见，对于时间样本高度相关的信号，自回归（AR）或自回归移动平均（ARMA）模型的预测阶数较低；而对于样本间相关性较低的噪声型信号，阶数则较高。这意味着对于后一种情况，需要大量的先前样本来预测当前样本。可以采用不同的准则，如赤池信息准则（AIC），从时间序列中确定预测阶数。[图 6.4](#c06.xhtml#c6-fig-0004) 显示了为时间序列的三个部分的重叠段自动计算出的预测阶数，其中中间部分为正弦波，第一和第三部分为随机噪声信号。

![图 6.4 (a) 信号和 (b) 为信号的重叠段测量的预测阶数。](images/c06f004.gif)

[**图 6.4**](#c06.xhtml#R_c6-fig-0004) (a) 信号和 (b) 为信号的重叠段测量的预测阶数。

## 6.10 总结

大脑是一个具有非线性行为的复杂系统。通常很难准确表征和表达复杂系统的动力学特性以及由非线性系统产生的信号趋势的行为，除非该非线性已被明确定义并用数学公式化表述。为了更准确地定义系统中的混沌，往往必须估计其他参数，如最优时间延迟和吸引子维数。这些参数随时间固有地变化，因此需要更复杂的评估。如果不正确估计这些参数，上述度量仅仅是粗略的混沌估计器。相反，本章介绍的大多数度量，特别是不同的熵估计器，无法区分系统中的混沌与噪声。

本章另一个有趣的结论是，在多通道情况下，熵的集合度量对应于通道间的依赖性，因此可以代表互信息（MI）。

## 参考文献

1.  **1** Peitgen, H.‐O., Lurgens, H., and Saupe, D. (1992). Chaos and Fractals. New York: Springer‐Verlag.

2.  **2** Grassberger, P. and Procaccia, I. (1983). Characterization of strange attractors. Physical Review Letters 50: 346–349.

3.  **3** Costa, M., Goldberger, A.L., and Peng, C.‐K. (2005). Multiscale entropy analysis of biological signals. Physical Review E 71 (2): 021906.

4.  **4** Azami, H., Fernández, A., and Escudero, J. (2017). Refined multiscale fuzzy entropy based on standard deviation for biomedical signal analysis. Medical & Biological Engineering & Computing 55 (11): 2037–2052.

5.  **5** Costa, M., Goldberger, A.L., and Peng, C.‐K. (2002). Multiscale entropy analysis of complex physiologic time series. Physical Review Letters 89 (6): 068102.

