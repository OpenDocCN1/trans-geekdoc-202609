

结合上述结果，(4.220) 以及 (4.221) 证明了

$$
\begin{aligned}
\mathcal{P}\left(\mathbf{F}_{\varepsilon}\right) & \leq \left[\frac{9}{8}\left(3dL(b-a)\right)^{2d}\varepsilon^{-2d} + (d+22)\left(3dL(b-a)\right)^d\varepsilon^{-d} + d + 11\right] \\
& \leq \left[\frac{9}{8}\left(3dL(b-a)\right)^{2d} + (d+22)\left(3dL(b-a)\right)^d + d + 11\right]\varepsilon^{-2d} = \mathfrak{C}_{\varepsilon}\varepsilon^{-2d}. \tag{4.232}
\end{aligned}
$$

将此结果与 (4.224) 和 (4.227) 结合，便确立了 (4.217)、(4.218) 和 (4.219)。至此，引理 4.4.13 的证明已经完成。$\Box$

### 注 4.4.14（高维 ANN 近似结果）

上述引理 4.4.13 是一个多维 ANN 近似结果，其意义在于：我们旨在近似的目标函数 $f$ 的定义域 $[a, b]^d$ 的输入维度 $d \in \mathbb{N}$ 可以是任意自然数。然而，我们注意到，当维度 $d$ 较大时（例如 $d \geq 5$），引理 4.4.13 并没有提供有用的贡献，因为该引理并未提供关于 (4.219) 中常数 $\mathfrak{C}$ 如何随 $d$ 增长的信息，且维度 $d$ 出现在 (4.219) 中 ANN 参数数量界里指定近似精度 $\varepsilon$ 的倒数 $\varepsilon^{-1}$ 的指数中。

在文献中，还有许多合适的高维 ANN 近似结果，这些结果保证参数界中的常数至多以维度 $d$ 的多项式速度增长，并且保证 ANN 参数界中指定近似精度 $\varepsilon$ 的倒数 $\varepsilon^{-1}$ 的指数完全独立于维度 $d$。当维度 $d$ 较大时，此类结果确实有潜力提供关于 ANN 近似的有用实用结论。例如，对于一般目标函数类背景下的高维 ANN 近似结果，我们参见 [14, 15, 28, 70, 121, 160] 及其中的参考文献；对于目标函数为偏微分方程（PDE）解的高维 ANN 近似结果，我们参见 [3, 29, 35, 123, 128, 161–163, 177, 179, 205, 209, 228, 259, 353] 及其中的参考文献（另见下文第 18.4 节）。

### 注 4.4.15（无限维 ANN 近似结果）

在文献中，现在也存在一些结果，其中我们要近似的目标函数定义在无限维向量空间上，因此目标函数的定义域维度即为无穷大（参见例如 [32, 68, 69, 202, 255, 363] 及其中的参考文献）。这一观点似乎非常合理，因为在许多应用中，应通过目标函数处理的输入数据（如图像和视频），用无限维空间中的元素表示比用有限维空间中的元素表示更为自然。

## 第三部分
### 优化

## 第 5 章
### 通过梯度流（GF）轨迹进行优化

在下文的第 6 章和第 7 章中，我们将研究文献中确定的和随机的 GD 型优化方法。此类方法在机器学习问题中被广泛用于近似最小化合适的目标函数。第 7 章中的 SGD 型优化方法可以被视为第 6 章中确定的 GD 型优化方法的合适蒙特卡洛近似，而第 6 章中确定的 GD 型优化方法粗略来看可以被视为合适的 GF 常微分方程（ODE）解的时间离散近似。为了建立对 GD 型优化方法以及我们用于分析此类方法的一些工具的理解，我们将在本章研究此类 GF 常微分方程。特别是，我们将在本章展示如何利用此类 GF 常微分方程来近似求解适当的优化问题。

例如，可以在 [2, 44, 126, 216, 224, 225, 258] 及其中的参考文献中找到关于通过 GF 常微分方程进行优化的进一步研究。

### 5.1 ANN 训练的初步注释

深度监督学习算法的关键组成部分通常是深度 ANN 以及合适的基于梯度的优化方法。在第一部分和第二部分中，我们介绍并研究了不同类型的 ANN，而在第三部分中，我们介绍并研究基于梯度的优化方法。在本节中，我们简要概述了基于梯度的优化方法背后的主要思想，并勾勒了此类基于梯度的优化方法如何在深度监督学习算法中产生。为此，我们现在回顾引言中的深度监督学习框架。

具体而言，设 $d, M \in \mathbb{N}$，$\mathcal{E} \in C(\mathbb{R}^d, \mathbb{R})$，$\pmb{x}_1, \pmb{x}_2, \dots, \pmb{x}_{M+1} \in \mathbb{R}^d$，$\pmb{y}_1, \pmb{y}_2, \dots, \pmb{y}_M \in \mathbb{R}$ 满足对于所有 $m \in \{1, 2, \dots, M\}$ 有

$$y_m = \mathcal{E}(\pmb{x}_m) \qquad \qquad \qquad \qquad \qquad \qquad \qquad (5.1)$$

并且设 $\pmb{\mathfrak{L}}: C(\mathbb{R}^d, \mathbb{R}) \to [0, \infty)$ 满足对于所有 $\phi \in C(\mathbb{R}^d, \mathbb{R})$ 有

$$\pmb{\mathfrak{L}}(\phi) = \frac{1}{M} \left[ \sum_{m=1}^{M} |\phi(\pmb{x}_m) - \pmb{y}_m|^2 \right]. \quad (5.2)$$

如同在**引言**中一样，我们将 $M \in \mathbb{N}$ 视为可用的已知输入-输出数据对的数量，将 $d \in \mathbb{N}$ 视为输入数据的维度，将 $\mathcal{E}: \mathbb{R}^d \to \mathbb{R}$ 视为通过**(5.1)** 关联输入数据和输出数据的未知函数，将 $\pmb{x}_1, \pmb{x}_2, \dots, \pmb{x}_{M+1} \in \mathbb{R}^d$ 视为可用的已知输入数据，将 $\pmb{y}_1, \pmb{y}_2, \dots, \pmb{y}_M \in \mathbb{R}$ 视为可用的已知输出数据，并且 (5.2) 中的函数 $\pmb{\mathfrak{L}}: C(\mathbb{R}^d, \mathbb{R}) \to [0, \infty)$ 是与所考虑的学习问题相关的优化问题中的目标函数（即我们要最小化的函数）（参见**引言**中的**(3)**）。特别地，请注意

$$\pmb{\mathfrak{L}}(\pmb{\mathcal{E}}) = 0$$

我们试图通过计算函数 $\pmb{\mathfrak{L}}: C(\mathbb{R}^d, \mathbb{R}) \to [0, \infty)$ 的近似最小化器来近似函数 $\pmb{\mathcal{E}}$。为了使该优化问题适合数值计算，我们通过采用 **ANN** 的参数化（参见**引言**中的**(7)**）来考虑与 **(5.2)** 相关的优化问题的空间离散化版本。

更正式地，设 $a: \mathbb{R} \to \mathbb{R}$ 可微，设 $h \in \mathbb{N}$，$l_1, l_2, \dots, l_h, \mathfrak{d} \in \mathbb{N}$ 满足 $\mathfrak{d} = l_1(d+1) + \sum_{k=2}^h l_k(l_{k-1}+1) + l_h + 1$，并考虑参数化函数

$$\mathbb{R}^{\mathfrak{d}} \ni \theta \mapsto \mathcal{N}^{\pmb{a}, d}_{\pmb{m}_{a,l_1}, \pmb{m}_{a,l_2}, \dots, \pmb{m}_{a,l_h}, \mathrm{id}_{\mathbb{R}}} \in C(\mathbb{R}^d, \mathbb{R}) \quad (5.4)$$

（参见定义 **1.1.3** 和 **1.2.1**）。请注意，$h$ 是 **(5.4)** 中 **ANN** 的隐藏层数量；请注意，对于每个 $i \in \{1, 2, \dots, h\}$，$l_i \in \mathbb{N}$ 是 **(5.4)** 中 **ANN** 第 $i$ 个隐藏层的神经元数量；并且请注意，$\mathfrak{d}$ 是描述 **(5.4)** 中 **ANN** 所使用的实参数数量。我们观察到，对于每个 $\theta \in \mathbb{R}^{\mathfrak{d}}$，函数

$$\mathbb{R}^d \ni \pmb{x} \mapsto \mathcal{N}^{\pmb{a}, d}_{\pmb{m}_{a,l_1}, \pmb{m}_{a,l_2}, \dots, \pmb{m}_{a,l_h}, \mathrm{id}_{\mathbb{R}}}(\pmb{x}) \in \mathbb{R}$$

在 **(5.4)** 中不过是与一个 *全连接前馈 ANN* 相关联的实现函数，其中在每个隐藏层之前都应用激活函数 $a: \mathbb{R} \to \mathbb{R}$ 的多维版本。在本节中，我们将自己限制在可微的激活函数上，因为这种可微性允许我们考虑梯度（详见下文 **(5.7)**、**(5.8)** 以及第 **5.3.2** 节）。

我们现在将 **(5.2)** 中的优化问题离散化为计算函数 $\mathcal{L}: \mathbb{R}^{\mathfrak{d}} \to [0, \infty)$ 的近似最小化器的问题，该函数满足对于所有 $\theta \in \mathbb{R}^{\mathfrak{d}}$ 有

$$\mathcal{L}(\theta) = \frac{1}{M} \left[ \sum_{m=1}^{M} \left| \left( \mathcal{N}^{\pmb{a}, d}_{\pmb{m}_{a,l_1}, \pmb{m}_{a,l_2}, \dots, \pmb{m}_{a,l_h}, \mathrm{id}_{\mathbb{R}}} \right)(\pmb{x}_m) - \pmb{y}_m \right|^2 \right]$$

