
*   [100] P.M. Pardalos, N. Kovoor, An algorithm for a singly constrained class of quadratic programs subject to upper and lower bounds, *Math. Program.* 1990;46:321–328.
*   [101] F. Parvaresh, H. Vikalo, S. Misra, B. Hassibi, Recovering sparse signals using sparse measurement matrices in compressed DNA microarrays, *IEEE J. Sel. Top. Signal Process.* 2008;2(3):275–285.
*   [102] S. Patterson, Y.C. Eldar, I. Keidar, Distributed compressed sensing for static and time-varying networks, [arXiv:1308.6086 [cs.IT]](http://www.arxiv.org/abs/1308.6086); 2014.
*   [103] T. Peleg, M. Elad, Performance guarantees of the thresholding algorithm for the cosparse analysis model, *IEEE Trans. Inf. Theory* 2013;59(3):1832–1845.
*   [104] M.D. Plumbley, Geometry and homotopy for `ℓ1` sparse representation, *Proceedings of the International Workshop on Signal Processing with Adaptive Sparse Structured Representations*. *SPARS, Rennes, France*. 2005.
*   [105] R.T. Rockafellar, Monotone operators and the proximal point algorithms, *SIAM J. Control Optim.* 1976;14(5):877–898.
*   [106] R. Rubinstein, R. Peleg, M. Elad, Analysis KSVD: a dictionary-learning algorithm for the analysis sparse model, *IEEE Trans. Signal Process.* 2013;61(3):661–677.
*   [107] L.I. Rudin, S. Osher, E. Fatemi, Nonlinear total variation based noise removal algorithms, *Phys. D, Nonlinear Phenom.* 1992;60(1–4):259–268.
*   [108] I.W. Selesnick, M.A.T. Figueiredo, Signal restoration with overcomplete wavelet transforms: comparison of analysis and synthesis priors, *Proceedings of SPIE*. 2009.
*   [109] K. Slavakis, Y. Kopsinis, S. Theodoridis, S. McLaughlin, Generalized thresholding and online sparsity-aware learning in a union of subspaces, *IEEE Trans. Signal Process.* 2013;61(15):3760–3773.
*   [110] P. Sprechmann, I. Ramirez, G. Sapiro, Y.C. Eldar, CHiLasso: a collaborative hierarchical sparse modeling framework, *IEEE Trans. Signal Process.* 2011;59(9):4183–4198.
*   [111] J.L. Starck, E.J. Candès, D.L. Donoho, The curvelet transform for image denoising, *IEEE Trans. Image Process.* 2002;11(6):670–684.
*   [112] J.L. Starck, J. Fadili, F. Murtagh, The undecimated wavelet decomposition and its reconstruction, *IEEE Trans. Signal Process.* 2007;16(2):297–309.
*   [113] T. Strohmer, Numerical algorithms for discrete Gabor expansions, *Gabor Analysis and Algorithms: Theory and Applications*. Boston, MA: Birkhauser; 1998:267–294.
*   [114] V.N. Temlyakov, Nonlinear methods of approximation, *Found. Comput. Math.* 2003;3(1):33–107.
*   [115] J.A. Tropp, Greed is good, *IEEE Trans. Inf. Theory* 2004;50:2231–2242.
*   [116] Y. Tsaig, *Sparse Solution of Underdetermined Linear Systems: Algorithms and Applications*. [PhD Thesis] Stanford University; 2007.
*   [117] B.A. Turlach, W.N. Venables, S.J. Wright, Simultaneous variable selection, *Technometrics* 2005;47(3):349–363.
*   [118] S. Wright, R. Nowak, M. Figueiredo, Sparse reconstruction by separable approximation, *IEEE Trans. Signal Process.* 2009;57(7):2479–2493.
*   [119] M. Yaghoobi, S. Nam, R. Gribonval, M. Davies, Constrained overcomplete analysis operator learning for cosparse signal modelling, *IEEE Trans. Signal Process.* 2013;61(9):2341–2355.
*   [120] J. Yang, Y. Zhang, W. Yin, A fast alternating direction method for TV `ℓ1` - `ℓ2` signal reconstruction from partial Fourier data, *IEEE Trans. Sel. Top. Signal Process.* 2010;4(2):288–297.
*   [121] W. Yin, S. Osher, D. Goldfarb, J. Darbon, Bregman iterative algorithms for `ℓ1`-minimization with applications to compressed sensing, *SIAM J. Imaging Sci.* 2008;1(1):143–168.
*   [122] M. Yuan, Y. Lin, Model selection and estimation in regression with grouped variables, *J. R. Stat. Soc.* 2006;68(1):49–67.
*   [123] T. Zhang, Sparse recovery with orthogonal matching pursuit under RIP, *IEEE Trans. Inf. Theory* 2011;57(9):6215–6221.
*   [124] M. Zibulevsky, M. Elad, L1-L2 optimization in signal processing, *IEEE Signal Process. Mag.* 2010;27(3):76–88.
*   [125] M. Zibulevsky, Y.Y. Zeevi, Frame analysis of the discrete Gabor scheme, *IEEE Trans. Signal Process.* 1994;42(4):942–945.
*   [126] H. Zou, T. Hastie, Regularization and variable selection via the elastic net, *J. R. Stat. Soc. B* 2005;67(2):301–320.
*   [127] H. Zou, The adaptive LASSO and its oracle properties, *J. Am. Stat. Assoc.* 2006;101:1418–1429.
*   [128] H. Zou, R. Li, One-step sparse estimates in nonconcave penalized likelihood models, *Ann. Stat.* 2008;36(4):1509–1533.

---

# 第 11 章：再生核希尔伯特空间中的学习

## 章节大纲

*   11.1  引言
*   11.2  广义线性模型
*   11.3  Volterra、Wiener 和 Hammerstein 模型
*   11.4  Cover 定理：线性二分法中的空间容量
*   11.5  再生核希尔伯特空间
    *   11.5.1  一些性质和理论亮点
    *   11.5.2  核函数示例
        *   构建核
        *   字符串核
*   11.6  表示定理
    *   11.6.1  半参数表示定理
    *   11.6.2  非参数建模：讨论
*   11.7  核岭回归
*   11.8  支持向量回归
    *   11.8.1  线性ϵ不敏感最优回归
        *   解
        *   求解优化任务
*   11.9  核岭回归再探
*   11.10  最优边界分类：支持向量机
    *   11.10.1  线性可分类别：最大边界分类器
        *   解
        *   优化任务
    *   11.10.2  非线性可分类别
        *   解

## 11.1 简介

本章的重点将放在学习非线性模型上。采用非线性模型的必要性已经在第 3 章中进行了讨论，背景涉及分类和回归任务。例如，回想一下，给定两个联合分布的随机向量（`y`，`x`）$\in \mathbb{R}^k \times \mathbb{R}^l$，我们知道在均方误差（MSE）意义上，给定 `x` = `x` 时 `y` 的最优估计是相应的条件均值，即 $\mathbb{E}[y|x]$，这通常是 `x` 的非线性函数。

处理非线性建模任务有不同的方法。本章的重点将放在一条通过所谓的**再生核希尔伯特空间**（RKHS）的路径上。该技术包含将输入变量映射到一个新空间，使得原本非线性的任务转化为线性任务。从实际角度来看，这些空间之美在于其丰富的结构允许我们以非常高效的方式执行内积运算，其复杂度与相应 RKHS 的维度无关。此外，请注意，此类空间的维度甚至可以是无限的。

我们首先回顾一些较为“传统”的技术，涉及 Volterra 级数展开，然后逐步转向探索 RKHS 概念。将讨论 Cover 定理、RKHS 的基本性质及其定义核。介绍核岭回归和支持向量机（SVM）框架。讨论涉及核函数和核矩阵的近似技术，如随机傅里叶特征（RFF）和 Nyström 方法，以及它们对 RKHS 中在线和分布式学习的影响。最后，介绍一些与稀疏性和多核表示相关的更高级概念。章节末尾给出了一个文本挖掘背景下的案例研究。

## 11.2 广义线性模型

给定 $(y, x) \in \mathbb{R} \times \mathbb{R}^l$，$y$ 的广义线性估计量 $\hat{y}$ 具有如下形式

```
ŷ = f(x) := θ_0 + ∑_{k=1}^K θ_k φ_k(x),
``` (11.1)

其中 $\varphi_1, \dots, \varphi_K$ 是*预选的*（非线性）函数。一类流行的函数是多项式函数，例如，

$$

\widehat{y} = \theta_{0} + \sum\limits_{i = 1}^{l}\theta_{i}x_{i} + \sum\limits_{i = 1}^{l - 1}\sum\limits_{m = i + 1}^{l}\theta_{im}x_{i}x_{m} + \sum\limits_{i = 1}^{l}\theta_{ii}x_{i}^{2}.

$$

![公式](img/si8.png) (11.2)

假设 $l = 2$（**x** = [$x_1$, $x_2$]^T)，通过设定 $K = 5$ 以及 $\phi_1(x) = x_1$、$\phi_2(x) = x_2$、$\phi_3(x) = x_1 x_2$、$\phi_4(x) = x_1^2$、$\phi_5(x) = x_2^2$，公式 (11.2) 可以转化为公式 (11.1) 的形式。

公式 (11.2) 推广到 $r$ 阶多项式很容易得到，它将包含 $x_1^{p_1} x_2^{p_2} \cdots x_l^{p_l}$ 形式的乘积，其中 $p_1 + p_2 + \cdots + p_l \le r$。结果表明，$r$ 阶多项式的自由参数个数 $K$ 等于

```
K = \frac{(l + r)!}{r! l!}.
```

仅举一例，当 $l = 10$ 且 $r = 3$ 时，$K = 286$。使用多项式展开的依据是魏尔斯特拉斯定理，该定理指出：定义在紧（闭且有界）子集 $S \subset \mathbb{R}^l$ 上的每一个连续函数，都可以用一个多项式函数（例如，[95]）以任意小的误差 $\epsilon$ 进行一致逼近，且逼近程度可任意接近。当然，为了达到足够好的逼近效果，可能不得不使用较大的 $r$ 值。除了多项式函数，还可以使用其他类型的函数，例如样条函数和三角函数。

此类模型的一个共同特征是：展开式中的基函数是*预先选定*的，它们是固定的且与数据无关。此类路径的优势在于：相关模型关于未知自由参数集是线性的，并且可以通过遵循第 4–8 章中描述的线性模型的任一方法进行估计。然而，这需要付出代价。如文献[7]所示，对于涉及*K*个固定函数的展开式，平方近似误差*不能*小于$\left( \frac{1}{K} \right)^{\frac{2}{l}}$的量级。换句话说，对于高维空间，为了获得足够小的误差，必须使用较大的*K*值。这是维度灾难问题的另一种表现形式。相反，如果展开式涉及依赖于数据的函数，且这些函数针对特定数据集进行了优化，则可以消除近似误差对输入空间维度*l*的依赖。例如，第 18 章将讨论的一类神经网络就属于这种情况。在这种情况下，付出的代价是对自由参数的依赖变成了非线性的，使得关于未知参数的优化成为一项更艰巨的任务。

## 11.3 Volterra、Wiener 和 Hammerstein 模型

让我们从非线性系统建模的情况入手，其中涉及的输入-输出实体是时间序列/离散时间信号，分别记为（`u[n]`、`d[n]`）。公式(11.2)中多项式建模的对应形式现在称为 Volterra 级数展开。

本书将不再深入探讨这类模型，此处简要讨论它们是为了从更一般的背景和历史原因来阐述非线性建模任务。*因此，初次阅读时可跳过本节*。

Vito Volterra（1860–1940）是一位意大利数学家，他在数学、物理学和生物学方面做出了重大贡献。他的里程碑式理论之一是 Volterra 级数的发展，用于求解积分和积分-微分方程。他是拒绝向墨索里尼法西斯政权宣誓效忠的意大利教授之一，因此被迫辞去大学职位。

图 11.1 展示了一个未知的非线性系统/滤波器及其相应的输入-输出信号。离散时间 Volterra 模型的输出可以写为

```
d_n = \sum\limits_{k = 1}^{r}\sum\limits_{i_1 = 0}^{M}\sum\limits_{i_2 = 0}^{M}\cdots\sum\limits_{i_k = 0}^{M}w_k(i_1,i_2,\ldots,i_k)\prod\limits_{j = 1}^{k}u_{n - i_j},
```

其中 `w_k(·,…,·)` 表示第 *k* 阶 *Volterra 核*；通常情况下，*r* 可以是无限的。例如，当 `r = 2` 且 `M = 1` 时，输入-输出关系涉及以下项的线性组合
