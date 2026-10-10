
*引理 6.6.4 的证明。* 在整个证明过程中，设 \(\mathbb{M} = (\mathbb{M}^{(1)}, \ldots, \mathbb{M}^{(\mathfrak{d})}): \mathbb{N}_0 \to \mathbb{R}^\mathfrak{d}\) 满足对于所有 \(n \in \mathbb{N}\)，\(i \in \{1, 2, \ldots, \mathfrak{d}\}\) 均有 \(\mathbb{M}^{(i)}_0 = 0\) 且

\begin{equation}

\mathbb{M}^{(i)}_n = \beta_n \mathbb{M}^{(i)}_{n-1} + (1-\beta_n) |\mathcal{G}_i(\Theta_{n-1})|^2 \tag{6.352}

\end{equation}

并设 \((B_{n,k})_{(n,k) \in (\mathbb{N}_0)^2} \subseteq \mathbb{R}\) 满足对于所有 \(n \in \mathbb{N}\)，\(k \in \{0, 1, \ldots, n-1\}\) 均有

\begin{equation}

B_{n,k} = (1-\beta_{k+1}) \left[\prod_{l=k+2}^{n} \beta_l \right]. \tag{6.353}

\end{equation}

注意 (6.348) 蕴含了第 \((i)\) 项。注意到 \((6.348)\)、\((6.352)\)、\((6.353)\) 以及引理 6.3.3 保证对于所有 \(n \in \mathbb{N}\)，\(i \in \{1, 2, \ldots, \mathfrak{d}\}\) 均有

\begin{equation}

\mathbb{M}^{(i)}_n = \sum_{k=0}^{n-1} B_{n,k} |\mathcal{G}_i(\Theta_k)|^2 \quad \text{且} \quad \sum_{k=0}^{n-1} b_{n,k} = \frac{\sum_{k=0}^{n-1} B_{n,k}}{1-\prod_{k=1}^{n} \beta_k} = \frac{1-\prod_{k=1}^{n} \beta_k}{1-\prod_{k=1}^{n} \beta_k} = 1. \tag{6.354}

\end{equation}

这证明了第 \((ii)\) 项。注意 \((6.346)\)、\((6.347)\)、\((6.352)\) 和 \((6.354)\) 表明，对于所有 \(n \in \mathbb{N}\)，\(i \in \{1, 2, \ldots, \mathfrak{d}\}\) 均有

\begin{equation}

\begin{aligned}

\Theta^{(i)}_n &= \Theta^{(i)}_{n-1} - \gamma_n \left[ \varepsilon + \left[\frac{\mathbb{M}^{(i)}_n}{1-\prod_{k=1}^{n} \beta_k} \right]^{1/2} \right]^{-1} \mathcal{G}_i(\Theta_{n-1}) \tag{6.355} \\

&= \Theta^{(i)}_{n-1} - \gamma_n \left[ \varepsilon + \left[\sum_{k=0}^{n-1} b_{n,k} |\mathcal{G}_i(\Theta_k)|^2 \right]^{1/2} \right]^{-1} \mathcal{G}_i(\Theta_{n-1}).

\end{aligned}

\end{equation}

这确立了第 \((iii)\) 项。引理 6.6.4 的证明至此完成。

### 6.7 AdaDelta GD 优化

本节回顾的 AdaDelta GD 优化方法是 RMSprop GD 优化方法的扩展。与 RMSprop GD 优化方法类似，AdaDelta GD 优化方法为优化过程的每个分量单独调整学习率。为此，AdaDelta GD 优化方法使用了两个指数衰减平均值：一个是对目标函数过去偏导数平方的平均（如 RMSprop GD 优化方法所做的那样，参见下文 (6.358)），另一个是对过去增量平方的平均（参见下文 (6.360)）。与 Adagrad 和 RMSprop 优化一样，AdaDelta 优化最初是在随机设置中引入的（参见 Zeiler [429]），但为了教学目的，我们在本节中展示了 AdaDelta 优化的确定性版本。关于 AdaDelta 优化的原始随机版本，请参阅下文第 7.8 节。

**定义 6.7.1 (AdaDelta GD 优化方法)。** 设 \(\mathfrak{d} \in \mathbb{N}\)，\((\beta_n)_{n \in \mathbb{N}} \subseteq [0, 1]\)，\((\delta_n)_{n \in \mathbb{N}} \subseteq [0, 1]\)，\(\varepsilon \in (0, \infty)\)，\(\xi \in \mathbb{R}^\mathfrak{d}\) 且设 \(\mathcal{L}: \mathbb{R}^\mathfrak{d} \rightarrow \mathbb{R}\) 和 \(\mathcal{G} = (\mathcal{G}_1, \ldots, \mathcal{G}_\mathfrak{d}): \mathbb{R}^\mathfrak{d} \rightarrow \mathbb{R}^\mathfrak{d}\) 满足对于所有 \(U \in \{V \subseteq \mathbb{R}^\mathfrak{d}: V \text{ 是开集}\}\)，\(\theta \in U\) 且 \(\mathcal{L}|_U \in C^1(U, \mathbb{R}^\mathfrak{d})\)，均有

\begin{equation}

\mathcal{G}(\theta) = (\nabla\mathcal{L})(\theta). \tag{6.356}

\end{equation}

则我们称 \(\Theta\) 为目标函数 \(\mathcal{L}\) 具有广义梯度 \(\mathcal{G}\)、二阶矩衰减因子 \((\beta_n)_{n \in \mathbb{N}}\)、delta 衰减因子 \((\delta_n)_{n \in \mathbb{N}}\)、正则化因子 \(\varepsilon\) 和初始值 \(\xi\) 的 AdaDelta GD 过程（我们称 \(\Theta\) 为目标函数 \(\mathcal{L}\) 具有二阶矩衰减因子 \((\beta_n)_{n \in \mathbb{N}}\)、delta 衰减因子 \((\delta_n)_{n \in \mathbb{N}}\)、正则化因子 \(\varepsilon\) 和初始值 \(\xi\) 的 AdaDelta GD 过程）当且仅当 \(\Theta = (\Theta^{(1)}, \ldots, \Theta^{(\mathfrak{d})}): \mathbb{N}_0 \rightarrow \mathbb{R}^\mathfrak{d}\) 是从 \(\mathbb{N}_0\) 到 \(\mathbb{R}^\mathfrak{d}\) 的函数，且满足存在 \(\mathbb{M} = (\mathbb{M}^{(1)}, \ldots, \mathbb{M}^{(\mathfrak{d})}): \mathbb{N}_0 \rightarrow \mathbb{R}^\mathfrak{d}\) 和 \(\Delta = (\Delta^{(1)}, \ldots, \Delta^{(\mathfrak{d})}): \mathbb{N}_0 \rightarrow \mathbb{R}^\mathfrak{d}\)，使得对于所有 \(n \in \mathbb{N}\)，\(i \in \{1, 2, \ldots, \mathfrak{d}\}\) 均有

\begin{equation}

\Theta_0 = \xi, \quad \mathbb{M}_0 = 0, \quad \Delta_0 = 0, \tag{6.357}

\end{equation}

\begin{equation}

\mathbb{M}^{(i)}_n = \beta_n \mathbb{M}^{(i)}_{n-1} + (1 - \beta_n) |\mathcal{G}_i(\Theta_{n-1})|^2, \tag{6.358}

\end{equation}

\begin{equation}

\Theta^{(i)}_n = \Theta^{(i)}_{n-1} - \left[\frac{\varepsilon + \Delta^{(i)}_{n-1}}{\varepsilon + \mathbb{M}^{(i)}_n}\right]^{1/2} \mathcal{G}_i(\Theta_{n-1}), \tag{6.359}

\end{equation}

以及

\begin{equation}

\Delta^{(i)}_n = \delta_n \Delta^{(i)}_{n-1} + (1 - \delta_n) |\Theta^{(i)}_n - \Theta^{(i)}_{n-1}|^2. \tag{6.360}

\end{equation}

## 6.8 自适应矩估计 GD 优化方法（Adam）

在本节中，我们介绍 Adam **GD** 优化方法（参见 Kingma & Ba [247]）。粗略地说，Adam **GD** 优化方法可以被视为偏置校正动量 **GD** 优化方法（参见第 6.3.2 节）与偏置校正 RMSprop **GD** 优化方法（参见第 6.6.2 节）的结合。与 Adagrad、RMSprop 和 Adadelta 优化方法类似，Adam 优化方法是在 Kingma & Ba [247] 中引入的随机设定下的方法，但为了教学目的，我们在本节中呈现 Adam 优化方法的确定性版本。关于 Adam 优化方法的原始随机版本，请参阅下文第 7.9 节。

**定义 6.8.1**（Adam **GD** 优化方法），*设* $\mathfrak{d} \in \mathbb{N}$，$(\gamma_{n})_{n \in \mathbb{N}} \subseteq [0, \infty)$，$(\alpha_{n})_{n \in \mathbb{N}} \subseteq [0, 1)$，$(\beta_{n})_{n \in \mathbb{N}} \subseteq [0, 1]$，$\varepsilon \in (0, \infty)$，$\xi \in \mathbb{R}^{\mathfrak{d}}$ *满足*

$$\max \{\alpha_{1}, \beta_{1}\} < 1 \tag{6.361}$$

*且设* $\mathcal{L}: \mathbb{R}^{\mathfrak{d}} \rightarrow \mathbb{R}$ *以及* $\mathscr{G} = (\mathscr{G}_{1}, \ldots, \mathscr{G}_{\mathfrak{d}}): \mathbb{R}^{\mathfrak{d}} \rightarrow \mathbb{R}^{\mathfrak{d}}$ *满足：对于所有* $U \in \{V \subseteq \mathbb{R}^{\mathfrak{d}}: V \text{ is open }\}$ 和 $\theta \in U$，*使得* $\left.\mathscr{L}\right|_{U} \in C^{1}(U, \mathbb{R}^{\mathfrak{d}})$ *有*

$$\mathscr{G}(\theta)=(\nabla \mathcal{L})(\theta). \tag{6.362}$$

*则我们称* $\Theta$ *为目标函数* $\mathcal{L}$ 具有广义梯度 $\mathscr{G}$、学习率 $(\gamma_{n})_{n \in \mathbb{N}}$、动量衰减因子 $(\alpha_{n})_{n \in \mathbb{N}}$、二阶矩衰减因子 $(\beta_{n})_{n \in \mathbb{N}}$、正则化因子 $\varepsilon$ 和初始值 $\xi$ 的 Adam **GD** 过程 *（我们称* $\Theta$ *为目标函数* $\mathcal{L}$ 具有学习率 $(\gamma_{n})_{n \in \mathbb{N}}$、动量衰减因子 $(\alpha_{n})_{n \in \mathbb{N}}$、二阶矩衰减因子 $(\beta_{n})_{n \in \mathbb{N}}$、正则化因子 $\varepsilon$ 和初始值 $\xi$ 的 Adam **GD** 过程 *当且仅当* $\Theta=(\Theta^{(1)}, \ldots, \Theta^{(\mathfrak{d})}): \mathbb{N}_{0} \rightarrow \mathbb{R}^{\mathfrak{d}}$ *是从* $\mathbb{N}_{0}$ *到* $\mathbb{R}^{\mathfrak{d}}$ 的函数，且存在* $\mathbf{m}=(\mathbf{m}^{(1)}, \ldots, \mathbf{m}^{(\mathfrak{d})}): \mathbb{N}_{0} \rightarrow \mathbb{R}^{\mathfrak{d}}$ *和* $\mathbb{M}=(\mathbb{M}^{(1)}, \ldots, \mathbb{M}^{(\mathfrak{d})}): \mathbb{N}_{0} \rightarrow \mathbb{R}^{\mathfrak{d}}$ *使得对于所有* $n \in \mathbb{N}$ 和 $i \in \{1, 2, \ldots, \mathfrak{d}\}$，*有*

$\Theta_{0}=\xi, \quad \mathbf{m}_{0}=0, \quad \mathbb{M}_{0}=0,$

$\mathbf{m}_{n}=\alpha_{n} \mathbf{m}_{n-1}+(1-\alpha_{n}) \mathscr{G}\left(\Theta_{n-1}\right)$

$\mathbb{M}_{n}^{(i)}=\beta_{n} \mathbb{M}_{n-1}^{(i)}+\left(1-\beta_{n}\right) \mathscr{G}_{i}\left(\Theta_{n-1}\right)^{2},$

*以及* $\Theta_{n}^{(i)}=\Theta_{n-1}^{(i)}-\gamma_{n}\left[\varepsilon+\left(\frac{\mathbb{M}_{n}^{(i)}}{1-\prod_{l=1}^{n} \beta_{l}}\right)^{\frac{1}{2}}\right]^{-1}\left[\frac{\mathbf{m}_{n}^{(i)}}{1-\prod_{l=1}^{n} \alpha_{l}}\right] .$

## 第 7 章

## 随机梯度下降（SGD）优化方法

本章回顾和研究 SGD 类型的优化方法，包括经典的普通 SGD 优化方法（参见第 7.2 节），以及更复杂的 SGD 类型优化方法，包括带有动量的 SGD 类型优化方法（参见下文第 7.4、7.5 和 7.9 节）以及带有学习率自适应修正的 SGD 类型优化方法（参见下文第 7.6、7.7、7.8 和 7.9 节）。

关于科学文献中提供基于梯度的优化方法综述的简要资源列表，请参阅第 6 章的开头。

### 7.1 关于使用 SGD 训练 ANN 的引言

在第 6 章中，我们引入并研究了确定性 GD 类型的优化方法。在深度学习算法中，通常不使用确定性 GD 类型的优化方法，而是使用 GD 类型优化方法的随机变体。这种 SGD 类型的优化方法可以被视为确定性 GD 类型方法的适当蒙特卡罗近似，在本节中，我们将粗略概述此类 SGD 类型优化方法的一些主要思想。为此，我们现在简要回顾前文引言和第 5.1 节中开发的深度监督学习框架。

具体而言，设 $d, M \in \mathbb{N}$，$\mathcal{E} \in C(\mathbb{R}^d, \mathbb{R})$，$x_1, x_2, \ldots, x_{M+1} \in \mathbb{R}^d$，$y_1, y_2, \ldots, y_M \in \mathbb{R}$ 满足：对于所有 $m \in \{1, 2, \ldots, M\}$ 有

$y_m = \mathcal{E}(x_m). \quad (7.1)$

如同在引言和第 5.1 节中，我们将 $M \in \mathbb{N}$ 视为可用的已知输入-输出数据对的数量，将 $d \in \mathbb{N}$ 视为输入数据的维度，将 $\mathcal{E}: \mathbb{R}^{d} \rightarrow \mathbb{R}$ 视为我们想要近似的一个未知函数，将 $\boldsymbol{x}_{1}, \boldsymbol{x}_{2}, \ldots, \boldsymbol{x}_{M+1} \in \mathbb{R}^{d}$ 视为可用的已知输入数据，将 $y_{1}, y_{2}, \ldots, y_{M} \in \mathbb{R}$ 视为可用的已知输出数据，并且我们试图利用可用的已知输入-输出数据对通过 ANN$\mathfrak{s}$ 来近似未知函数 $\mathcal{E}$。
