

## 9.14 具有解析激活函数的人工神经网络的训练中的标准 KL 不等式（针对经验风险）

### 定理 9.14.1（具有解析激活函数的人工神经网络的**经验风险最小化**）。
设 $L, \boldsymbol{\mathfrak{o}} \in \mathbb{N}\backslash\{1\}$，$M, l_0, l_1, \dots, l_L \in \mathbb{N}$，$\boldsymbol{x}_1, \boldsymbol{x}_2, \dots, \boldsymbol{x}_M \in \mathbb{R}^{l_0}$，$\boldsymbol{y}_1, \boldsymbol{y}_2, \dots, \boldsymbol{y}_M \in \mathbb{R}^{l_L}$ 满足 $\boldsymbol{\mathfrak{o}} = \sum_{k=1}^L l_k(l_{k-1}+1)$，令 $a: \mathbb{R} \to \mathbb{R}$ 和 $\mathbf{L}: \mathbb{R}^{l_L} \times \mathbb{R}^{l_L} \to \mathbb{R}$ 为解析函数，令 $\mathcal{L}: \mathbb{R}^{\mathfrak{o}} \to \mathbb{R}$ 满足对于所有 $\boldsymbol{\vartheta} \in \mathbb{R}^{\mathfrak{o}}$ 有

$$\mathcal{L}(\vartheta) = \frac{1}{M} \left[ \sum_{m=1}^{M} \mathbf{L} \left( \mathcal{N}_{\boldsymbol{\mathfrak{o}}, l_0}^{\vartheta, l_0} \left( \boldsymbol{\mathfrak{m}}_{a, l_1, \boldsymbol{\mathfrak{m}}_{a, l_2, \dots, \boldsymbol{\mathfrak{m}}_{a, l_{L-1}, \operatorname{id}_{\mathbb{R}^{l_L}}} (\boldsymbol{x}_m) \right), \boldsymbol{y}_m \right) \right],$$

且令 $\Theta \in \mathcal{C}([0, \infty), \mathbb{R}^{\mathfrak{o}})$ 满足

$$\lim \inf_{t \to \infty} \| \Theta_t \|_2 < \infty \quad \text{ 以及 } \quad \forall\, t \in [0, \infty)\colon \Theta_t = \Theta_0 - \int_0^t (\nabla \mathcal{L}) (\Theta_s) \, \mathrm{d} s$$

（参见定义 1.1.3、1.2.1、3.3.4 和 9.7.1）。则存在 $\vartheta \in \mathbb{R}^{\mathfrak{o}}$ 以及 $c, \beta \in (0, \infty)$，使得对于所有 $t \in (0, \infty)$ 均有

$$\| \Theta_t - \vartheta \|_2 \leq c t^{- \beta}, \quad 0 \leq \mathcal{L} (\Theta_t) - \mathcal{L} (\vartheta) \leq c t^{- 1}, \quad \text{ 且 } \quad (\nabla \mathcal{L}) (\vartheta) = 0.$$

**定理 9.14.1 的证明**。注意，推论 9.13.5 表明 $\mathcal{L}$ 是解析的。将此与推论 9.11.7 结合可得 (9.278)。从而定理 9.14.1 得证。 $\blacksquare$

### 引理 9.14.2。
设 $a: \mathbb{R} \to \mathbb{R}$ 为 softplus 激活函数（参见定义 1.2.11）。则 $a$ 是解析的（参见定义 9.7.1）。

**引理 9.14.2 的证明**。在整个证明过程中，令 $f: \mathbb{R} \to (0, \infty)$ 满足对于所有 $x \in \mathbb{R}$ 有 $f (x) = 1 + \exp(x)$。观察到 $\mathbb{R} \ni x \mapsto \exp(x) \in \mathbb{R}$ 是解析函数这一事实蕴含 $f$ 是解析的（参见定义 9.7.1）。将此与 $\left(0, \infty\right) \ni x \mapsto \ln(x) \in \mathbb{R}$ 是解析函数的事实以及命题 9.13.1 和 (1.47) 结合，可证得 $a$ 是解析的。从而引理 9.14.2 得证。 $\blacksquare$

### 引理 9.14.3。
设 $d \in \mathbb{N}$，且令 $\mathbf{L}$ 为基于 $\mathbb{R}^d \ni x \mapsto \| x \|_2 \in [0, \infty)$ 的**均方误差**损失函数（参见定义 3.3.4 和 5.4.2）。则 $\mathbf{L}$ 是解析的（参见定义 9.7.1）。

**引理 9.14.3 的证明**。注意，引理 5.4.3 保证 $\mathbf{L}$ 是解析的（参见定义 9.7.1）。从而引理 9.14.3 得证。 $\blacksquare$

### 推论 9.14.4（具有 softplus 激活函数的人工神经网络的**经验风险最小化**）。
设 $L, \mathfrak{o} \in \mathbb{N}\backslash\{1\}$，$M, l_0, l_1, \dots, l_L \in \mathbb{N}$，$\boldsymbol{x}_1, \boldsymbol{x}_2, \dots, \boldsymbol{x}_M \in \mathbb{R}^{l_0}$，$\boldsymbol{y}_1, \boldsymbol{y}_2, \dots, \boldsymbol{y}_M \in \mathbb{R}^{l_L}$ 满足

$\boldsymbol{\mathfrak{o}} = \sum_{k=1}^{L} l_k(l_{k-1}+1)$，令 $a$ 为 softplus 激活函数，令 $\mathcal{L}: \mathbb{R}^{\mathfrak{o}} \rightarrow \mathbb{R}$ 满足对于所有 $\boldsymbol{\vartheta} \in \mathbb{R}^{\mathfrak{o}}$ 有

$$\mathcal{L}(\boldsymbol{\vartheta})=\frac{1}{M}\left\|\sum_{m=1}^{M}\left[\pmb{y}_{m}-\mathscr{A}^{\widehat{\Theta}_{0},\theta_{0}},\widehat{\Theta}_{n_{1}},\widehat{\Theta}_{n_{2}},\ldots,\widehat{\Theta}_{n_{L-1}},\widehat{\Theta}_{\mathrm{d},\mathrm{L}}\left(\pmb{x}_{m}\right)\right]\right\|_{2}^{2},$$

且令 $\Theta \in \mathcal{C}([0, \infty), \mathbb{R}^{\mathfrak{o}})$ 满足

$\begin{equation}\operatorname{lim}\inf_{t \rightarrow \infty}\|\Theta_{t}\|_{2}<\infty \quad \text { 以及 } \quad \forall t \in[0, \infty): \Theta_{t}=\Theta_{0}-\int_{0}^{t}(\nabla \mathcal{L})(\Theta_{s}) \, \mathrm{d} s,\end{equation}$

（参见定义 1.1.3、1.2.1、1.2.11 和 3.3.4）。则存在 $\vartheta \in \mathbb{R}^{\mathfrak{o}}$ 以及 $c, \beta \in(0, \infty)$，使得对于所有 $t \in(0, \infty)$ 均有

$$\left\|\Theta_{t}-\vartheta\right\|_{2} \leq c t^{-\beta}, \quad 0 \leq \mathcal{L}\left(\Theta_{t}\right)-\mathcal{L}(\vartheta) \leq c t^{-1} \quad \text { 且 } \quad(\nabla \mathcal{L})(\vartheta)=0 .$$

**推论 9.14.4 的证明**。注意到引理 9.14.2、引理 9.14.3 和定理 9.14.1 确立了 (9.281)。从而推论 9.14.4 得证。

**注 9.14.5**（收敛到良性的次优临界点，其风险值接近最优风险值）。推论 9.14.4 确立了在全连接前馈 $A N N s$ 训练中，非发散 GF 轨迹收敛到目标函数的临界点 $\vartheta \in \mathbb{R}^{\mathfrak{o}}$。在 $A N N s$ 训练的多种场景中，这些极限临界点似乎以高概率不是全局极小点，而是次优临界点，但目标函数在这些点上的值却并不远离目标函数的最小值（参见 Ibragimov 等人 [216]，以及 [144, 409]）。鉴于此，人们对与目标函数相关的景观分析（landscape analyses）的兴趣日益浓厚，旨在获取更多关于目标函数临界点的信息（参见，例如，[12, 72, 79, 80, 92, 113, 141, 215, 216, 239, 312, 357, 358, 365, 381-383, 400, 435, 436] 及其中的参考文献）。

通常，在大多数情况下，严格证明目标函数在极限临界点处的值确实以高概率接近目标函数的最小值/下界值$^{1}$，并由此建立完整的收敛性分析，仍然是一个开放问题。然而，在所谓的过参数化（overparameterized）区域，即 $A N N$ 参数远多于输入-输出训练数据对的情况下，已经取得了几项关于 $A N N s$ 训练的收敛性分析（参见，例如，[74, 75, 114, 218] 及其中的参考文献）。

**注 9.14.6**（几乎必然排除严格鞍点）。我们还注意到，在几种情况下，已经证明所考虑的 $G F$ 轨迹在随机初始化下，或所考虑的 **GD** 过程在随机初始化下的极限临界点，几乎必然不是鞍点，而是局部极小值点；参见，例如，[71, 265, 266, 322, 323]。

**注 9.14.7**（先验界与极小化子的存在性）。假设所考虑的 **GF** 轨迹是非发散的，即满足

$$ \liminf_{t\rightarrow \infty} \|\Theta_t\|_2 < \infty \tag{9.282}$$

（参见上文的 (9.280)），则我们有推论 9.14.4 确立了在全连接前馈 **ANNs** 训练中，**GF** 轨迹收敛到目标函数的临界点 $\vartheta \in \mathbb{R}^\mathfrak{d}$（参见上文的 (9.281)）。这类非发散以及稍强的有界性假设，分别是关于 **ANNs** 训练中基于梯度的优化方法的收敛性结果中非常常见的假设（参见，例如，[2, 8, 44, 100, 101, 126, 224, 391]，第 9.11.2 节，以及在 **KL** 方法背景下的定理 9.14.1，以及在其他方法背景下的 [93, 101, 225, 296]）。

在 **ANNs** 训练的大部分场景中，证明或反驳这种非发散性和有界性假设仍然是一个开放问题。在 Gallon 等人 [142] 中，(9.282) 中的条件已被证伪，并且针对特定的目标函数，确立了浅层全连接前馈 **ANNs** 训练中 **GF** 轨迹的发散性；参见 Petersen 等人 [332]。

关于基于梯度的优化方法的非发散性问题，似乎与目标函数的优化景观中是否存在极小化子密切相关。我们引用 [99, 102, 224, 233] 中证明 **ANNs** 训练的优化景观中存在极小化子的结果，并引用 [142, 332] 中证明 **ANNs** 训练的优化景观中不存在极小化子的结果。我们还引用，例如，[125, 216]，其中建立了形式如 (9.282) 的非发散性和有界性条件的强简化 **ANN** 训练场景。

## 9.15 Fréchet 次微分与极限 Fréchet 次微分

### 定义 9.15.1（Fréchet 次梯度与极限 Fréchet 次梯度）。
设 $\mathfrak{d} \in \mathbb{N}$，$\mathscr{L} \in C(\mathbb{R}^\mathfrak{d}, \mathbb{R})$，$x \in \mathbb{R}^\mathfrak{d}$。*我们将由下式给出的集合记为* $(\mathcal{D}\mathscr{L})(x) \subseteq \mathbb{R}^\mathfrak{d}$

$$(\mathcal{D}\mathscr{L})(x) = \left\{ y \in \mathbb{R}^\mathfrak{d}\colon \left[\liminf_{\substack{\mathbb{R}^\mathfrak{d} \setminus \{0\} \ni h\rightarrow 0}} \frac{\mathscr{L}(x + h) - \mathscr{L}(x) - \langle y, h\rangle}{\|h\|_2}\right] \geq 0 \right\}, \tag{9.283}$$

*我们称* $(\mathcal{D}\mathscr{L})(x)$ *为* $\mathscr{L}$ *在* $x$ *处的 Fréchet 次梯度集合，我们将由下式给出的集合记为* $(\mathfrak{D}\mathscr{L})(x) \subseteq \mathbb{R}^\mathfrak{d}$

$$(\mathfrak{D}\mathscr{L})(x) = \bigcap_{\varepsilon\in (0,\infty)} \left[\bigcup_{y\in \{z\in \mathbb{R}^\mathfrak{d}\colon \|x-z\|_2<\varepsilon\}} (\mathcal{D}\mathscr{L})(y)\right], \tag{9.284}$$
