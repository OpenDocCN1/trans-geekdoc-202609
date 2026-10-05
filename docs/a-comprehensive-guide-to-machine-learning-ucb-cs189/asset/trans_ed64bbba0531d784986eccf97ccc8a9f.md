

## 第5章 神经网络

根据微分的线性性，我们看到：

```
$$\nabla L(w) = \frac{1}{n} \sum_{i=1}^n \nabla_w \ell(x_i, w, y_i)$$
```

因此，计算梯度的时间与 $n$ 成线性关系。在“大数据”场景下，$n$ 非常大，这种成本可能是不可接受的。

出于这个原因，我们有理由尝试通过对输入取具有代表性的随机样本来计算梯度，从而近似神经网络损失函数的梯度。由于梯度下降是一个迭代过程，为了获得更快的计算速度，我们可以考虑放弃每次迭代更新的精确性。如果我们在每一步中对这些训练样本的随机样本计算梯度，我们将得到真实梯度的带噪声或无偏估计。每一步中的噪声通常是为了换取更多步骤的机会而可以接受的权衡。

在常规下降更新中，我们有如下策略：

```
$w^{(k+1)} \leftarrow w^{(k)} - \alpha_k \nabla_w L(w^{(k)})$
```

在随机梯度下降中，我们有如下更新规则：

```
$w^{(k+1)} \leftarrow w^{(k)} - \alpha_k G_k$
```

其中 $G_k$ 是满足 $\mathbb{E}[G_k] = \nabla L(w^{(k)})$ 的随机变量。通常，$G_k$ 通过均匀随机采样 $m < n$ 个训练点（索引为 $I_k \subset \{1, \dots, n\}$）并计算这些点上的梯度来构造：

```
$G_k = \frac{1}{m} \sum_{i \in I_k} \nabla_w \ell(x_i, y_i)$
```

我们用 $w^*$ 表示最优值。我们的目标是证明：

```
$$\lim_{k \to \infty} \mathbb{E}[\|w^{(k)} - w^*\|^2] = 0$$
```

在分析中，我们做了以下假设：

- 1. 损失函数 $f$ 是 $\ell$-强凸的；即存在一个 $\ell > 0$，使得对于所有 $x, y$，都有 $(\nabla f(x) - \nabla f(y))^T(x - y) \geq \ell \|x - y\|^2$。
- 2. 随机梯度的期望范数由 $\mathbb{E}[\|G_k\|^2] \leq M^2 < \infty$ 限制。

我们从展开目标项开始：

```
$$\mathbb{E}[\|w^{(k+1)} - w^*\|^2] = \mathbb{E}[(w^{(k+1)} - w^*)^T(w^{(k+1)} - w^*)] = \mathbb{E}[((w^{(k)} - w^* - \alpha_k G_k)^T(w^{(k)} - w^*))] = \mathbb{E}[\|w^{(k)} - w^*\|^2 - 2\alpha_k \mathbb{E}[(w^{(k)} - w^*)^T G_k] + \alpha_k^2 \mathbb{E}[\|G_k\|^2]]$

为了简单起见，定义：

```
$d_k = \mathbb{E}[\|w^{(k)} - w^*\|^2]$
```

对 $G_k$ 期望范数的假设意味着：

```
$d_{k+1} \leq d_k - 2\alpha_k \mathbb{E}[(w^{(k)} - w^*)^T G_k] + \alpha_k^2 M^2$
```

## 5.2 神经网络训练

为了计算期望，我们对过去（即产生 $w^{(k)}$ 的所有决策）进行条件化。根据迭代期望律，我们有：

$$E[(w^{(k)} - w^*)G_k] = E_{\text{past}}[E[(w^{(k)} - w^*)G_k \mid \text{past}]]$$

下一个期望是对用于计算随机梯度的训练样本取的。但在给定过去（包括 $w^{(k)}$）的情况下已知 $w^{(k)}$，所以：

$$E[(w^{(k)} - w^*)G_k \mid \text{past}] = (w^{(k)} - w^*)E[G_k \mid \text{past}]$$

当前的 $G_k$ 取决于我们的点选择，假设它与过去是独立的，因此 $E[G_k \mid \text{past}] = E[G_k \mid w^{(k)}]$，因为 $G_k$ 是 $w^{(k)}$ 处真实梯度的无偏估计。结合以上点，我们有：

$$E[(w^{(k)} - w^*)G_k] = E_{\text{past}}[(w^{(k)} - w^*) \nabla f(w^{(k)})]$$

最优性的一阶条件意味着 $\nabla f(w^*) = 0$。根据 $\ell$-强凸假设，我们有：

$$(w^{(k)} - w^*)^T \nabla f(w^{(k)}) = \langle w^{(k)} - w^*, \nabla f(w^{(k)}) - \nabla f(w^*) \rangle \geq \ell \|w^{(k)} - w^*\|_2^2$$

取期望：

$$E[(w^{(k)} - w^*) \nabla f(w^{(k)})] \geq \ell \|w^{(k)} - w^*\|_2^2 = \ell d_k$$

将此代入 $d_{k+1}$，得到：

$$d_{k+1} \leq d_k - 2\alpha_k d_k + \alpha_k^2 M^2 = (1 - 2\alpha_k)d_k + \alpha_k^2 M^2$$

$\alpha_k^2 M^2$ 项是由随机性引入的。我们可以通过随时间缩小步长 $\alpha_k$ 使其趋于 0 —— 但减小 $\alpha_k$ 也会减少前面的影响。

设置 $\alpha_k = \frac{1}{2k}$ 得：

$$d_{k+1} \leq \left(1 - \frac{1}{k}\right)d_k + \frac{1}{(2\ell k)}M^2$$

令 $S = \frac{M^2}{(2\ell)}$，则不等式变为：

$$d_{k+1} \leq \left(1 - \frac{1}{k}\right)d_k + \frac{1}{k^2}S$$

为了分析这个递归式，我们展开前几项：

$$d_2 \le S$$
$$d_3 \le \left(1 - \frac{1}{2}\right)d_2 + \frac{1}{2^2}S = \frac{1}{2}S + \frac{1}{2^2}S$$
$$d_4 \le \left(1 - \frac{1}{3}\right)d_3 + \frac{1}{3^2}S = \frac{1}{3}S + \frac{1}{2 \cdot 3}S + \frac{1}{3^2}S$$
$$d_5 \le \left(1 - \frac{1}{4}\right)d_4 + \frac{1}{4^2}S = \frac{1}{4}S + \frac{1}{3 \cdot 4}S + \frac{1}{2 \cdot 3 \cdot 4}S + \frac{1}{4^2}S$$

归纳法，我们发现当 $k \to \infty$ 时，$d_k \to \frac{S}{k}$。

