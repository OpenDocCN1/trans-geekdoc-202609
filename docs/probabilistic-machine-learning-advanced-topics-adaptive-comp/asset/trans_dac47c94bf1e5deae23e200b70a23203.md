
因此，可以从方程 (15.117) 看出，给定 $\Sigma$，$\mathbf{W}$ 服从矩阵正态分布

$$
\mathbf{W}|\Sigma, \mathbf{X}, \mathbf{Y} \sim \mathcal{MN}(\mathbf{S}_{yx}\mathbf{S}_{xx}^{-1}, \Sigma, \mathbf{S}_{xx}).
$$ (15.120)

将 $\mathbf{W}$ 边缘化（这相当于去除方程 (15.113) 指数中包含 $\mathbf{W}$ 的项），可以证明 $\Sigma$ 的后验分布是逆 Wishart 分布。事实上，通过将方程 (15.117) 替换为方程 (15.113) 中的相应项，可以看出积分掉 $\mathbf{W}$ 后剩下的唯一项是 $\Sigma^{-1}\Psi$ 和 $\Sigma^{-1}\mathbf{S}_{y|x}$，这表明后验逆 Wishart 分布的尺度矩阵是 $\Psi_0 + \mathbf{S}_{y|x}$。

因此，给定观测值，$\{\mathbf{W}, \mathbf{\Sigma}\}$ 的联合后验分布是

$$
\mathbf{W}, \Sigma | \mathbf{X}, \mathbf{Y} \sim \text{MNIW}(\mathbf{M}_1, \mathbf{V}_1, \nu_1, \mathbf{\Psi}_1) \quad (15.121)
$$
$$
\mathbf{M}_1 = \mathbf{S}_{yx}\mathbf{S}_{xx}^{-1} \quad (15.122)
$$
$$
\mathbf{V}_1 = \mathbf{S}_{xx} \quad (15.123)
$$
$$
\nu_1 = N + \nu_0 \quad (15.124)
$$
$$
\mathbf{\Psi}_1 = \mathbf{\Psi}_0 + \mathbf{S}_{y|x} \quad (15.125)
$$

$\mathbf{W}$ 和 $\Sigma$ 的 MAP 估计是后验矩阵正态逆 Wishart 分布的众数。要推导这一点，请注意，$\mathbf{W}$ 仅出现在后验的矩阵正态密度函数中，因此最大化 $\{\mathbf{W}, \mathbf{\Sigma}\}$ 后验密度的矩阵 $\mathbf{W}$ 就是最大化 $\mathbf{W}$ 的矩阵正态后验的矩阵 $\mathbf{W}$。因此，$\mathbf{W}$ 的 MAP 估计是 $\hat{\mathbf{W}} = \mathbf{M}_1 = \mathbf{S}_{yx}\mathbf{S}_{xx}^{-1}$，这对 $\Sigma$ 的任何值都成立。通过将 $\mathbf{W} = \hat{\mathbf{W}}$ 代入 $\{\mathbf{W}, \mathbf{\Sigma}\}$ 的联合后验，并对 $\Sigma$ 求导数，可以看出最大化密度的矩阵是 $(\nu_1 + N_y + N_x + 1)^{-1}\mathbf{\Psi}_1$。由于 $\mathbf{\Psi}_1$ 是正定的，它是 $\Sigma$ 的 MAP 估计。

因此，$\{\mathbf{W}, \mathbf{\Sigma}\}$ 的 MAP 估计是

$$
\hat{\mathbf{W}} = \mathbf{S}_{yx}\mathbf{S}_{xx}^{-1} \quad (15.126)
$$
$$
\hat{\Sigma} = \frac{1}{\nu_1 + N_y + N_x + 1}(\mathbf{\Psi}_0 + \mathbf{S}_{y|x}) \quad (15.127)
$$

## 15.3 逻辑回归

**逻辑回归** 是一种非常广泛使用的判别式分类模型，它将输入向量 $\mathbf{x} \in \mathbb{R}^D$ 映射到类别标签 $y \in \{1, \dots, C\}$ 上的分布。如果 $C = 2$，这称为 **二元逻辑回归**；如果 $C > 2$，它称为 **多项逻辑回归**，或者也称为 **多类逻辑回归**。

### 15.3.1 二元逻辑回归

在二元情况下，其中 $y \in \{0, 1\}$，模型具有以下形式

$$
p(y|\mathbf{x}; \boldsymbol{\theta}) = \text{Ber}(y|\sigma(\mathbf{w}^T\mathbf{x} + b)) \quad (15.128)
$$

其中 $\mathbf{w}$ 是权重，$b$ 是偏差（偏移量），$\sigma$ 是 **sigmoid** 或 **logistic** 函数，定义为

$$
\sigma(a) \triangleq \frac{1}{1 + e^{-a}} \quad (15.129)
$$

让 \(\eta_n = \boldsymbol{w}^\mathsf{T}\boldsymbol{x}_n + b\) 成为示例 \(n\) 的 **logits**，并让 \(\mu_n = \sigma(\eta_n) = p(y=1|\boldsymbol{x}_n)\) 成为输出的均值。然后我们可以将对数似然写成负交叉熵：

\(\log p(\mathcal{D}|\boldsymbol{\theta}) = \log \prod_{n=1}^N \mu_n^{y_n} (1-\mu_n)^{1-y_n} = \sum_{n=1}^N y_n \log \mu_n + (1-y_n) \log(1-\mu_n)\) (15.130)

通过执行一些简单的代数运算，我们可以将此方程展开为更显式的形式（这在实现中很常见）。首先请注意

\(\mu_n = \frac{1}{1+e^{-\eta_n}} = \frac{e^{\eta_n}}{1+e^{\eta_n}}, \quad 1-\mu_n = 1-\frac{e^{\eta_n}}{1+e^{\eta_n}} = \frac{1}{1+e^{\eta_n}}\) (15.131)

因此

\(\log p(\mathcal{D}|\boldsymbol{\theta}) = \sum_{n=1}^N y_n[\log e^{\eta_n} - \log(1+e^{\eta_n})] + (1-y_n)[\log 1 - \log(1+e^{\eta_n})]\) (15.132)

\(= \sum_{n=1}^N y_n[\eta_n - \log(1+e^{\eta_n})] + (1-y_n)[-\log(1+e^{\eta_n})]\) (15.133)

\(= \sum_{n=1}^N y_n \eta_n - \sum_{n=1}^N \log(1+e^{\eta_n})\) (15.134)

请注意，函数 \(\log(1+e^a)\) 通常使用 `np.log1p(np.exp(a))` 实现。

### 15.3.2 多项逻辑回归

**多项逻辑回归** 是以下形式的判别式分类模型：

\(p(y|\boldsymbol{x};\boldsymbol{\theta}) = \text{Cat}(y|\text{softmax}(\boldsymbol{W}\boldsymbol{x} + \boldsymbol{b}))\) (15.135)

其中 \(\boldsymbol{x} \in \mathbb{R}^D\) 是输入向量，\(y \in \{1, \dots, C\}\) 是类别标签，\(\boldsymbol{W}\) 是 \(C \times D\) 权重矩阵，\(\boldsymbol{b}\) 是 \(C\) 维偏差向量，\(\text{softmax}()` 是 **softmax 函数**，定义为

\(\text{softmax}(\boldsymbol{a}) \triangleq \left[ \frac{e^{a_1}}{\sum_{c'=1}^C e^{a_{c'}}}, \dots, \frac{e^{a_C}}{\sum_{c'=1}^C e^{a_{c'}}} \right]\) (15.136)

如果我们将 logits 定义为 \(\boldsymbol{\eta}_n = \boldsymbol{W}\boldsymbol{x}_n + \boldsymbol{b}\)，将概率定义为 \(\boldsymbol{\mu}_n = \text{softmax}(\boldsymbol{\eta}_n)\)，并让 \(\boldsymbol{y}_n\) 成为标签 \(y_n\) 的 one-hot 编码，那么对数似然可以写成负交叉熵：

\(\log p(\mathcal{D}|\boldsymbol{\theta}) = \log \prod_{n=1}^N \prod_{c=1}^C \mu_{nc}^{y_{nc}} = \sum_{n=1}^N \sum_{c=1}^C y_{nc} \log \mu_{nc}\) (15.137)

### 15.3.3 处理类别不平衡和长尾

在许多问题中，某些类别比其他类别稀少得多；这个问题称为 **类别不平衡**。在这种情况下，标准最大似然训练可能效果不佳，因为它旨在最小化（0-1 损失的一个界限），而该损失可能受最频繁类别的支配。一种自然的替代方法是考虑 **平衡误差率**，它计算分类器 $f$ 的每类误差率的平均值：

$$\text{BER}(f) = \frac{1}{C} \sum_{y=1}^C p^*_{x|y} \left( y \notin \underset{y' \in \mathcal{Y}}{\text{argmax}} f_{y'}(x) \right)$$

其中 $p^*` 是真实分布。优化此损失的分类器 $f^*` 必须满足

$$\underset{y \in \mathcal{Y}}{\text{argmax}} f^*_y(x) = \underset{y \in \mathcal{Y}}{\text{argmax}} p^*_\text{bal}(y|x) = \underset{y \in \mathcal{Y}}{\text{argmax}} p^*(x|y)$$

其中 $p^*_\text{bal}(y|x) \propto \frac{1}{C} p^*(x|y)$ 是使用平衡类别时的预测器。因此，为了最小化 BER，我们应该使用类条件似然 $p(x|y)`，而不是类后验 $p(y|x)`。

在 [Men+21] 中，他们提出了一种称为 **logit 调整** 的简单方案，可以实现这个最优分类器。我们假设模型使用 $f_y(x) = w^\text{T}_y \phi(x)$ 计算 logits，其中 $\phi(x) = x` 对于 GLM。在事后版本中，模型以常规方式训练，然后在预测时，我们使用

$$\underset{y \in \mathcal{Y}}{\text{argmax}} p(x|y) = \underset{y \in \mathcal{Y}}{\text{argmax}} \frac{p(y|x)p(x)}{p(y)} = \underset{y \in \mathcal{Y}}{\text{argmax}} \frac{\exp(w^\text{T}_y \phi(x))}{\pi_y}$$

其中 $\pi_y = p(y)` 是经验标签先验。在实践中，引入调谐参数 $\tau > 0` 并使用预测器很有帮助

$$\hat{f}(x) = \underset{y \in \mathcal{Y}}{\text{argmax}} f_y(x) - \tau \log \pi_y$$

或者，我们可以更改训练期间使用的损失函数，使用以下 **logit 调整 softmax 交叉熵损失**：

$$\ell(y, f(x)) = - \log \frac{e^{f_y(x) + \tau \log \pi_y}}{\sum_{y'=1}^C e^{f_{y'}(x) + \tau \log \pi_{y'}}}$$

这就像使用 $g_y(x) = f_y(x) + \tau \log \pi_y` 形式的预测器进行训练，然后在测试时使用 $\underset{y}{\text{argmax}} f_y(x) = \underset{y}{\text{argmax}} g_y(x) - \tau \log \pi_y`，如上所示。

我们还可以将上述损失与参数先验相结合并执行贝叶斯推断，如下面所述。（使用非标准似然可以使用广义贝叶斯推断框架来证明，如第 14.1.3 节中所述。）

### 15.3.4 参数先验

与线性回归一样，在逻辑回归模型中使用高斯先验作为权重是标准的做法。将先验均值设置为 0 是很自然的，以反映输出可能是
