

![](img/aa2f42c739937b682075082233e335bb_159_0.png)

图 4.17 (A) NLPLS-Q 统计量、(B) NLPLS-HD 和 (C) 基于去噪残差的 NLPLS-HD 在漂移故障情况下的结果。

总之，本案例研究展示了 NLPLS 模型在 FPR 过程中描述非线性的能力。此外，结果表明，与传统的 NLPLS-Q 相比，NLPLS-HD 在识别突发、间歇和渐进故障方面具有更优的检测效率。这主要归功于 HD 指标对故障自由数据残差分布与 NLPLS 生成的实际残差之间偏差的敏感性。将 NLPLS-HD 应用于过滤后的残差可提高检测能力，尤其是在处理含噪声测量值时。

## 4.6 讨论

为维持现代复杂过程的产品质量、效率和可靠性，过程监测中的异常检测变得至关重要。对过程异常进行有效且及早的检测，对于避免异常的进展和减少生产力损失至关重要；这有助于避免严重的退化或系统崩溃。因此，异常检测是一个吸引工业从业者和研究人员关注的热门话题。

线性 LVR 方法，如 PLS 和 PCA，是监测变量间存在共线性或冗余的多变量数据的常用工具。LVR 技术已被广泛用于建模和监测表现出相关/共线性变量的多变量工业数据。然而，由于它们仅从数据中提取线性信息，因此在处理过程非线性方面效果不佳，受到限制。当然，线性 LVR 方法不适用于复杂非线性过程的数据分析和监测。为解决这一问题，已经设计了各种非线性 LVR 方法，以提取非线性特征并学习过程变量之间的任何非线性关系。基于 NLVR 的监测方法通常分为两个主要步骤：离线模型构建和在线异常检测。在第一步中，根据代表过程名义行为的数据设计检验过程的经验模型，并使用 SPE 和 T² 图表计算决策阈值。然后，将设计的模型及其决策阈值用于检查新的测试测量值，以进行异常检测。基于非线性 LVR 的监测方法，如 KPCA 和非线性 PLS，由于其检测效率高且易于实现，是有效的工具。

在本章中，我们表明，基于 KPCA 的监测方法优于传统的 PCA 方法。这些方法的性能基于沙特阿拉伯 WWTP 的数据，按 FAR 和 MDR 进行评估。基于 KPCA 的 LSVM 方法能可靠地发现进水流量测量中发生的异常事件。研究了不同的核函数；当应用于 WWTP 数据时，使用 RBF 核的 KPCA-LSVM 优于所考虑的线性和非线性核。

在许多实际应用中，例如空气质量监测，会从不同的空间位置收集多个时间序列数据，并具有必要的时空依赖性，但在监测和决策中很少考虑这一点。一个改进方向是将开发的基于 LVR 的监测技术扩展到考虑数据的时空演变（即，在监测中包含空间滞后信息），并将这些改进应用于各种应用。具体来说，对于时间相关的数据矩阵 Xn×m，通过在 X 中加入滞后变量来考虑数据的动态。例如，数据矩阵 X 可以包含在时刻 t 和时刻 t − 1 观测到的 m 个变量。同样，也可以将不同位置的观测值纳入 X 中。应仔细考虑包含哪些滞后和变量。在空间统计中，通常只选择最近邻；然而，最优选择取决于变量之间的相关性以及底层时空过程中存在的依赖性。我们将研究如何将最近邻思想适应于多变量时空过程，以便在控制 X 维度的同时借用有价值的信息。

在各种实际过程中（包括环境、生物和水文过程），数据本质上是功能性的。例如，空气质量监测中的粉尘测量可以被视为时间的函数。已有研究表明，PCA 不适用于多变量观测的功能数据 [80–83]。对于功能数据，功能 PCA（FPCA）类似于 PCA，基于前几个正交功能主成分捕获数据中的大部分变化 [84,82,85]。尽管 FPCA 是功能数据分析中流行的统计方法，但它尚未用于过程监测、故障检测和诊断。挑战在于，时空数据高度相关且维度非常高；在这种情况下，现有的多变量方法往往存在局限性，需要合适的方法（例如，基于功能 PCA 的控制图方法）来处理功能数据。此外，开发功能潜在变量方法来监测功能数据将非常有益。

## 参考文献

- [1] B.R. Kowalski, M.B. Seasholtz, 多元校准的最新进展, Journal of Chemometrics 5 (1991) 129–145.
- [2] I. Frank, J. Friedman, 一些化学计量回归工具的统计视角, Technometrics 35 (2) (1993) 109–148.
- [3] M. Stone, R.J. Brooks, 连续回归：采用交叉验证顺序构建的预测，涵盖普通最小二乘法、偏最小二乘法和主成分回归, Journal of the Royal Statistical Society, Series B 52 (2) (1990) 237.
- [4] S. Wold, 软建模：基本设计及一些扩展, Systems Under Indirect Observations, Elsevier, Amsterdam, 1982.
- [5] E. Malthouse, A. Tamhane, R. Mah, 非线性偏最小二乘法, Computers & Chemical Engineering 21 (8) (1997) 875–890.
- [6] H. Hotelling, 两组变量之间的关系, Biometrika 28 (1936) 321–377.
- [7] F.R. Bach, M.I. Jordan, 核独立成分分析, Journal of Machine Learning Research 3 (1) (2003).
- [8] S.S.D.R. Hardoon, J. Shawe-taylor, 典型相关分析：学习方法应用概述, Neural Computation 16 (12) (2004) 2639–2664.
- [9] M. Borga, T. Landelius, H. Knutsson, PCA、PLS、MLR 和 CCA 的统一方法, Technical Report, Linköping University, 1997.
- [10] A. Maalud, D. Wang, J. Romagnoli, 多变量统计过程监测的多尺度正交非线性策略, Journal of Process Control 16 (7) (2006) 671–683.
- [11] H. Peng, R. Wang, L. Hai, 使用核 PCA 及其快速数据重建进行传感器故障检测与识别, in: Control and Decision Conference, 2010, pp. 3857–3862.
- [12] S. Mika, B. Schölkopf, A.J. Smola, K.-R. Müller, M. Scholz, G. Rätsch, 特征空间中的核 PCA 与去噪, in: Advances in Neural Information Processing Systems, 1999, pp. 536–542.
- [13] B. Schölkopf, A. Smola, K.-R. Müller, 作为核特征值问题的非线性成分分析, Neural Computation 10 (5) (1998) 1299–1319.
- [14] D. Dong, T.J. McAvoy, 基于主曲线和神经网络的非线性主成分分析, Computers & Chemical Engineering 20 (1) (1996) 65–78.
- [15] A.H. Monahan, 通过神经网络进行非线性主成分分析：理论与洛伦兹系统的应用, Journal of Climate 13 (4) (2000) 821–835.
- [16] R. Rosipal, L.J. Trejo, 再生核希尔伯特空间中的核偏最小二乘回归, Journal of Machine Learning Research 2 (2001) 97–123.
- [17] S. Wold, 非线性偏最小二乘建模 II。样条内部关系, Chemometrics and Intelligent Laboratory Systems 14 (1–3) (1992) 71–84.
- [18] S. Wold, N.K. Wold, B. Skagerberg, 非线性 PLS 建模, Chemometrics and Intelligent Laboratory Systems 7 (1989) 53–65.
- [19] S.J. Qin, T.J. McAvoy, 使用神经网络的非线性 PLS 建模, Computers & Chemical Engineering 16 (4) (1992) 379–391.
- [20] D. Lee, M. Lee, S. Woo, Y. Kim, J. Park, 全规模生物废水处理厂的非线性动态偏最小二乘建模, Process Biochemistry 41 (1992) 2050–2057.
- [21] Y.H. Bang, C.K. Yoo, I.-B. Lee, 使用模糊推理系统的非线性 PLS 建模, Chemometrics and Intelligent Laboratory Systems 64 (2) (2003) 137–155.
- [22] I. Araby Abdel-Rahman, G.J. Lim, 使用二次模糊系统的非线性偏最小二乘算法, Journal of Chemometrics 23 (2009) 530–537.
- [23] I.E. Frank, 非线性 PLS 模型, Chemometrics and Intelligent Laboratory Systems 8 (2) (1990) 109–119.
- [24] I. Frank, NNPPSS：基于平滑器和样条非线化的 PCR 和 PLS 组件神经网络, in: INCINC94 Chemometrics Conference, 1994.
- [25] I. Frank, 非线性 PLS 模型, Chemometrics and Intelligent Laboratory Systems 8 (1990) 109–119.

