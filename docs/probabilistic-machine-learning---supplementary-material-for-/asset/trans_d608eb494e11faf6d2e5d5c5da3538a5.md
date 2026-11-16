

![](img/c73db5a1f734ebb7c0655f19e5bc9daa_89_0.png)

图 10.1: (a) 一个图。(b-d) 其部分生成树。引自 [WJ08] 中的图 7.1。经 Martin Wainwright 友好允许使用。

这是一个在凸集上最大化的凹目标函数，因此具有唯一最优解。此外，结果始终是 log Z 的上界，因为熵是一个上界，并且我们优化的集合比边缘多面体更大。

还需要指定可处理子模型集合 F 和分布 ρ。我们将在下文讨论一些选项。

### 10.1.5 树加权置信传播

本节讨论树加权 BP [WJW05b; Kol06]，这是一种使用生成树作为可处理模型集合 F 的凸 BP 形式，如下文所述。

### 10.1.5.1 生成树多面体

还需要指定可处理子模型集合 F 和分布 ρ。我们将考虑 F 为图中所有生成树的情况。对于任意给定的树，熵由方程 10.12 给出。要计算通过对所有树取平均得到的上界，请注意，单个节点的项 \(\sum_F \rho(F)H(\mu(F)_s)\) 将仅为 H_s，因为节点 s 出现在每棵树中，且 \(\sum_F \rho(F) = 1\)。但是，互信息项 I_st 接受权重 \(\rho_{st} = E_\rho [ I((s,t) \in E(T))]\)，称为**边出现概率**。因此，我们有以下关于熵的上界：

```
\mathbb{H}(\boldsymbol{\mu}) \le \sum_{s \in V} H_s(\mu_s) - \sum_{(s,t) \in E} \rho_{st} I_{st}(\mu_{st}) \triangleq \mathbb{H}_{\text{TRBP}}(\boldsymbol{\mu}) \quad (10.34)
```

这称为**树加权 BP** 近似 [WJW05b; Kol06]。这与熵的 Bethe 近似类似，除了关键的 \(\rho_{st}\) 权重之外。只要所有边 (s,t) 的 \(\rho_{st} > 0$，这就给出了精确熵的有效凹上界。

边出现概率存在于称为**生成树多面体**的空间中。这是因为它们受限于源自树分布。图 10.1 给出了一个图及其三棵生成树的示例。假设每棵树在 \(\rho\) 下具有相同的权重。边 f 出现在 3 棵树中的 1 棵，因此 \(\rho_f = 1/3\)。边 e 出现在 3 棵树中的 2 棵，因此 \(\rho_e = 2/3\)。边 b 出现在所有树中，因此 \(\rho_b = 1\)。以此类推。理想情况下，我们可以找到一个分布 \(\rho\)，或等价地，生成树多面体中的边概率，使上述上界尽可能紧。一种实现此目的的算法在 [WJW05a] 中描述。一种更简单的方法是对所有单独边使用权重 \(\rho_e = 1/E\)。

关于我们正在优化的集合呢？我们要求每棵树 T 的 \(\boldsymbol{\mu}(T) \in \mathbb{M}(T)\)，这意味着强制执行归一化和局部一致性。由于我们需要对每棵树这样做，我们在每条边上强制执行归一化和局部一致性。因此，我们实际上是在伪边缘多面体 \(\mathbb{L}(G)\) 中优化。因此，我们的最终优化问题如下：

```
\max_{\boldsymbol{\tau} \in \mathbb{L}(G)} \boldsymbol{\tau}^T \boldsymbol{\theta} + \mathbb{H}_{\text{TRBP}}(\boldsymbol{\tau}) \ge \log Z \quad (10.35)
```

### 10.1.5.2 消息传递实现

最小化方程 (10.35) 的最简单方法是一种称为**树加权置信传播**的置信传播变体。从 \(t\) 到 \(s\) 的消息现在是来自其他邻居 \(v\) 到 \(t\) 的所有消息的函数，与以前一样，但现在它也是从 \(s\) 到 \(t\) 发送的消息的函数。具体来说，我们有以下 [WJ08, Sec 7.2.1]:

\(m_{t \to s}(x_s) \propto \sum_{x_t} \exp \left( \frac{1}{\rho_{st}} \theta_{st}(x_s, x_t) + \theta_t(x_t) \right) \frac{\prod_{v \in \text{nbr}(t) \setminus s} [m_{v \to t}(x_t)]^{\rho_{vt}}}{[m_{s \to t}(x_t)]^{1 - \rho_{st}}}\)

在收敛时，节点和边伪边缘由以下给出：

\(\tau_s(x_s) \propto \exp(\theta_s(x_s)) \prod_{v \in \text{nbr}(s)} [m_{v \to s}(x_s)]^{\rho_{vs}}\)

\(\tau_{st}(x_s, x_t) \propto \varphi_{st}(x_s, x_t) \frac{\prod_{v \in \text{nbr}(s) \setminus t} [m_{v \to s}(x_s)]^{\rho_{vs}}}{[m_{t \to s}(x_s)]^{1 - \rho_{st}}} \frac{\prod_{v \in \text{nbr}(t) \setminus s} [m_{v \to t}(x_t)]^{\rho_{vt}}}{[m_{s \to t}(x_t)]^{1 - \rho_{st}}}\)

\(\varphi_{st}(x_s, x_t) \triangleq \exp \left( \frac{1}{\rho_{st}} \theta_{st}(x_s, x_t) + \theta_s(x_s) + \theta_t(x_t) \right)\)

如果所有边 \((s, t) \in E\) 的 \(\rho_{st} = 1\)，算法将退化为标准 LBP 算法。但是，条件 \(\rho_{st} = 1\) 意味着每条边以概率 1 出现在每棵生成树中，这仅在原始图为树时才可能。因此，该方法仅在树上等价于标准 LBP，而此时该方法当然是精确的。

一般来说，这种消息传递方案不能保证收敛到唯一的全局最优解。可以设计保证收敛的双循环方法 [HS08]，但在实践中，如在方程 ?? 中所示，使用阻尼更新通常足以确保收敛。

### 10.1.5.3 最大-积版本

我们可以修改 TRBP 以求解 MAP 估计问题（与估计后验边缘相反），方法是在方程 (10.36) 中将求和替换为乘积（详情见 [WJ08, Sec 8.4.3]）。在适当的调度下，这保证收敛到 9.1.3 节讨论的 LP 松弛，该调度称为**顺序树加权消息传递** [Kol06]。

### 10.1.6 凸 BP 的其他可处理版本

除了树之外，还可以使用其他类型的可处理模型的凸组合来对熵进行上界。一个例子是**平面 MRF**（即图中没有交叉边的图），具有二值节点且没有外场，即模型形式为 \(p(\mathbf{x}) \propto \exp(\sum_{(s,t) \in E} \theta_{st} x_s x_t)\)。结果表明，可以在此模型中进行精确推断。因此，可以使用此类图的凸组合，有时可以产生比 TRBP 更准确的结果，尽管计算成本更高。详情见 [GJ07]，以及用于平面 Ising 模型的相关 *精确* 方法 [Sch10b]。

## 第 11 章

## 蒙特卡洛推断

## 第 12 章

## 马尔可夫链蒙特卡洛 (MCMC) 推断

## 第 13 章

## 序列蒙特卡洛 (SMC) 推断

## 第三部分

## 预测

## 第 14 章

## 判别模型：概述

## 第 15 章

## 广义线性模型

### 15.1 逻辑回归的变分推断

本节讨论了一种基于似然局部上界的逻辑回归模型贝叶斯推断的变分方法。我们将使用高斯先验 \( p(w) = \mathcal{N}(w|\mu_0, V_0) \)。我们将创建似然的“高斯类”下界，该下界将与此先验共轭。然后我们迭代改进这个下界。

### 15.1.1 二进制逻辑回归

本节讨论二进制逻辑回归的变分推断。我们的介绍遵循 [Bis06, Sec 10.6]。

让我们首先将单个观测的似然重写如下：

```
\(\begin{aligned} p(y_n|x_n, w) &= \sigma(\eta_n)^{y_n}(1 - \sigma(\eta_n))^{1-y_n} \tag{15.1} \\ &= \left( \frac{1}{1+e^{-\eta_n}} \right)^{y_n} \left( 1 - \frac{1}{1+e^{-\eta_n}} \right)^{1-y_n} \tag{15.2} \\ &= e^{-\eta_n y_n} \frac{e^{-\eta_n}}{1 + e^{-\eta_n}} = e^{-\eta_n y_n} \sigma(-\eta_n) \tag{15.3} \end{aligned}\)
```

其中 \(\eta_n = w^T x_n\) 为 logits。这与高斯先验不是共轭的。因此，我们将使用 [JJ96; JJ00] 提议的以下 sigmoid 函数的“高斯类”变分下界：

```
\(\sigma(\eta_n) \ge \sigma(\psi_n) \exp [(\eta_n - \psi_n)/2 - \lambda(\psi_n)(\eta_n^2 - \psi_n^2)] \tag{15.4}\)
```

其中 \(\psi_n\) 是数据点 \(n\) 的变分参数，并且

```
\(\lambda(\psi) \triangleq \frac{1}{4\psi} \tanh(\psi/2) = \frac{1}{2\psi} \left[ \sigma(\psi) - \frac{1}{2} \right] \tag{15.5}\)
```

我们将其称为 JJ 界，以其发明者 Jaakkola 和 Jordan 命名。有关图示，请参见图 15.1(a)；有关推导，请参见 6.5.4.2 节。

使用此界，我们可以写成

```
\(p(y_n|x_n, w) = e^{-\eta_n y_n} \sigma(-\eta_n) \ge e^{-\eta_n y_n} \sigma(\psi_n) \exp [(-\eta_n + \psi_n)/2 - \lambda(\psi_n)(\eta_n^2 - \psi_n^2)] \tag{15.6}\)
```

我们现在可以对 log 联合分布求下界如下：

```
\(\begin{aligned} \log p(y|X, w) + \log p(w) \ge {} &-\frac{1}{2}(w - \mu_0)^T V_0^{-1}(w - \mu_0) \tag{15.7} \\ &+ \sum_{n=1}^N [\eta_n(y_n - 1/2) - \lambda(\psi_n)w^T(x_n x_n^T)w] \tag{15.8} \end{aligned}\)
```
