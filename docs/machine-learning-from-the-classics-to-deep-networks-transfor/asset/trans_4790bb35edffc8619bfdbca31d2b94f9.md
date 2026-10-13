

## 示例 8.7：投影 Landweber 方法

设我们的优化任务为

$$
\text{minimize } \frac{1}{2}{\|\mathbf{y} - X\mathbf{\theta}\|}^{2}, \text{ subject to } \mathbf{\theta} \in C,
$$

其中 $X \in \mathbb{R}^{(m \times l)}$，$\mathbf{y} \in \mathbb{R}^{(m)}$。展开并求梯度，可得

$$
J(\mathbf{\theta}) = \frac{1}{2}\mathbf{\theta}^{T}X^{T}X\mathbf{\theta} - \mathbf{y}^{T}X\mathbf{\theta} + \frac{1}{2}\mathbf{y}^{T}\mathbf{y}, \quad \nabla J(\mathbf{\theta}) = X^{T}X\mathbf{\theta} - X^{T}\mathbf{y}.
$$

首先我们检查 $\nabla J(\mathbf{\theta})$ 是否为 $\gamma$-Lipschitz 连续。为此，我们有

$$
\|X^{T}X(\mathbf{\theta} - \mathbf{h})\| \leq \|X^{T}X\|\|\mathbf{\theta} - \mathbf{h}\| \leq \lambda_{\text{max}}\|\mathbf{\theta} - \mathbf{h}\|.
$$

如果

$$
\|\nabla J(\mathbf{\theta}) - \nabla J(\mathbf{h})\| \leq \gamma \|\mathbf{\theta} - \mathbf{h}\|, \quad \gamma > 0, \quad \forall \mathbf{\theta}, \mathbf{h} \in \mathbb{R}^{(l)},
$$

且

$$
\mu \in \left( 0, \frac{2}{\gamma} \right),
$$

则从任意点 $\mathbf{\theta}^{(0)}$ 开始，公式 [(8.62)](#Chp008_343-416_B9780443292385000147.xhtml#deq128) 中的序列收敛（在一般希尔伯特空间中弱收敛）到 [(8.50)](#Chp008_343-416_B9780443292385000147.xhtml#deq110) 的一个解 [41,52]。

