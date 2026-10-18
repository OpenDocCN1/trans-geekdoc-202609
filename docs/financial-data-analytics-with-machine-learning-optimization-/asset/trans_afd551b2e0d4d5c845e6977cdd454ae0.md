

13. Nualart, D., and Nualart, E. (2018). Introduction to Malliavin Calculus. Cambridge University Press.

14. Oosterlee, C.W., and Grzelak, L.A. (2020). Mathematical Modeling and Computation in Finance: With Exercises and Python and Matlab Computer Codes. World Scientific.

15. Robert, C.P., and Casella, G. (1999). Monte Carlo Statistical Methods. Springer.

16. Ross, M.R. (2022). Simulation (6th ed.). Academic Press.

17. Shreve, S.E. (2004). Stochastic Calculus for Finance II: Continuous-Time Models. Springer.

18. Steele, J.M. (2001). Stochastic Calculus and Financial Applications. Springer.

19. Walters, P. (2000). An Introduction to Ergodic Theory. Springer Science & Business Media.

20. Wilmott, P., Howison, S., and Dewynne, J. (1995). The Mathematics of Financial Derivatives: A Student Introduction. Cambridge University Press.

## NOTES

1. [1](#c05.xhtml#R_c05-note-0001) `σ_C_T^2` 的显式形式可能相当复杂。对于大多数实际考虑，可以直接使用自助样本方差作为估计值。

2. [2](#c05.xhtml#R_c05-note-0002) 这条曲线描绘了金融期权的行权价与隐含波动率，之所以得名，是因为它通常是凸的，且看起来像是一张朝向我们的微笑。

# CHAPTER 6  

模型推断的近似

拟合模型的过程通常通过最小化平方和（如回归分析）或最小化交叉熵（如分类方法）来完成。这些都是 `maximum likelihood approach` 拟合的示例。本章全面解释了最大似然法，并介绍了用于模型推断的几种近似方法。

本章提供的示例突出了即将介绍的算法的实际应用和重要性。例如，通过在数值算法中利用最大似然法进行拟合，可以实现手写数字识别系统，准确识别支票和许多业务表格中常见的手写数字。使用数值方法估计分位数对于风险评估和投资组合管理至关重要，例如 `Value-at-Risk` 校准（将在 [第 8 章](#c08.xhtml) 中介绍）。在提供 `Markov Chain theory` 的全面且自包含的介绍之后，我们还通过一个示例介绍了非常有用的 `Markov Chain Monte Carlo` (MCMC) 方法，用于从复杂概率分布中进行采样。

## 6.1 EM ALGORITHM

`Expectation–Maximization Algorithm`（简称 `EM Algorithm`）是一种参数学习方法，最初在 `[5](#c06.xhtml#c06-bib-0005)` 中引入，用于处理参数估计，特别是涉及不可观测变量的情况。EM 算法不是寻找显式解析解，而是通过一个现代计算机可以轻松执行的迭代过程来找到对数似然函数的最大点。关于 EM 算法一般理论及其各种扩展的深入论述见经典教材 `[22](#c06.xhtml#c06-bib-0022)`。

