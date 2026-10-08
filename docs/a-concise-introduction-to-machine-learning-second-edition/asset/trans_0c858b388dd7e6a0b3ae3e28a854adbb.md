
数据似然对给出：

$$\mathcal{L}=\sum_{n=1}^{N} \log p(\mathbf{v}_{n})=\sum_{k=1}^{K} \sum_{n=1}^{N} q(\hat{z}_{n,k}=1) \log p(\mathbf{v}_{n},\hat{z}_{n,k}=1)$$
$$\sum_{k=1}^{K} \sum_{n=1}^{N} q(\hat{z}_{n,k}=1) \log p(\mathbf{v}_{n},\hat{z}_{n,k}=1)$$

在右侧减去并加上项

$$\sum_{k=1}^{K} \sum_{n=1}^{N} q(\hat{z}_{n,k}=1) \log q(\hat{z}_{n,k}=1)$$

可以保持方程不变，我们得到：

$$\mathcal{L}=\sum_{k=1}^{K} \sum_{n=1}^{N} q(\hat{z}_{n,k}=1) \log p(\mathbf{v}_{n},\hat{z}_{n,k}=1)$$
$$\sum_{k=1}^{K} \sum_{n=1}^{N} q(\hat{z}_{n,k}=1) \log \frac{q(\hat{z}_{n,k}=1)}{p(\mathbf{v}_{n},\hat{z}_{n,k}=1)} \quad (6.10)$$

现在，在最后一行中对 $k=1,\dots,K$ 求和是从离散分布 $p(\mathbf{z}_{n}|\mathbf{v}_{n})$ 到离散分布 $q(\mathbf{z}_{n})$ 的 Kullback-Leibler 散（KL 散）。

更一般，给定两个离散概率分布 $P$ 和 $Q$，从 $Q$ 到 $P$ 的 KL 散定义为：

$$D_{KL}(P||Q)=\sum_{i} P(i) \log \frac{P(i)}{Q(i)}$$

为了避免除以零，它仅在 $Q(i)>0$ 时有定义。在这种情况下，和中的该特定部分被解释为零，因为 $\lim_{x\to0} x \log x=0$。如果两个分布相同，则 KL 散为零。它是非负的；如果我们反转分数并使用 $\log x \leq x-1$，我们得到：

$$D_{KL}(P||Q)=-\sum_{i} P(i) \log \frac{P(i)}{Q(i)} \geq-\sum_{i} P(i) \frac{Q(i)}{P(i)}$$
$$=-\sum_{i} Q(i)+\sum_{i} P(i)=0,$$

因为概率之和需要为 1。

(6.10) 中的最后一行始终是非负的，因此第一行是数据似然对数的下界。我们可以将此

下界重写为：

```
$$\mathcal{L} = \sum_{k=1}^{K} \sum_{n=1}^{N} q(z_{n,k}) \log \frac{p(\mathbf{v}_n, z_{n,k}=1)}{q(z_{n,k}=1)}$$
$$= \sum_{k=1}^{K} \sum_{n=1}^{N} q(z_{n,k}) \log (p(z_{n,k}=1)p(\mathbf{v}_n|z_{n,k}=1))$$
$$= - \sum_{k=1}^{K} q(z_{n}=1) \log q(z_n).$$
```

下界包含数据似然对 $\mathcal{L}$；如果 $q(z_n)$ 等于 $p(z_n|\mathbf{v}_n)$，则 KL 散为零。
(6.10) 的最大值通过交替进行关于 $q(z_n)$ 的下界以及关于 $\pi_k = p(z_k=1)$ 和参数 $p_k(\mathbf{v}) = p(z_k=1|\mathbf{v})$，$k=1, \dots, K$ 来估计的。前者意味着将 $q(z_n)$ 设置为 $p(z_n|\mathbf{v}_n)$，其中响应度使用 $p_k(\mathbf{v})$ 的当前参数进行评估。然而，通过这种对 $q(z_n)$ 的选择，下界的第一项变成了 $\mathcal{L}$。第二项独立于参数 $p_k(\mathbf{v})$，因此对最大化没有影响。无论最大化 $\mathcal{L}$ 还是 $\tilde{\mathcal{L}}$，最大值的位置都是相同的。

![](img/c6c76bf52016db7e78a5e30d4766ef81_195_0.png)

**图 6.4** 最大化步骤的说明。

图 6.4 展示了这一点。横轴代表由 $\pi_k=p(z_k=1)$ 和参数 $p_k(\mathbf{v})=p(z_k=1|\mathbf{v})$，$k=1, \dots, K$ 形成的空间。通常，它具有很高的维度。数据样本联合似然的对数，即目标函数 $\mathcal{L}$ 用黑色画出。菱形选出了 $\pi_k$ 和参数 $p_k(\mathbf{v})$，$k=1, \dots, K$ 的特定选择。如果将 $q(z_n)$ 设置为为计算出的响应度 $p(z_n|\mathbf{v}_n)$，则迭代 $\mathcal{L}$ 和 $\hat{\mathcal{L}}$ 具有相同的值。对于这些 $q(z_n)$ 选择之一，下界 $\underline{\mathcal{L}}$ 用蓝色画出。它的曲线在菱形处触碰 $\mathcal{L}$ 的曲线。这表示关于 $q(z_n)$ 的最大化。在下一次迭代中，一组新的 $\pi_k = p(z_k=1)$ 和参数 $p_k(v) = p(v|z_k)=1$，$k=1, \dots, K$ 通过寻找 $\hat{\mathcal{L}}$ 对数的最大值来选择，这与完全数据似然对数的期望一致，并用红色画出。注意 $\mathcal{L}$ 和 $\hat{\mathcal{L}}$ 的最大值是相同的，由垂直线表示，关于 $\pi_k$ 的最大化。

以下思想引导我们进行最大化：

- 1. 初始化 $p_k(v)$ 的所有参数
- 2. 评估响应度 $p(z_n|\mathbf{v}_n)$
- 3. 最大化：
- 4. 更新参数
- 5. 如果所有变化均低于阈值，则终止。

该方法简称为期望极大化（EM）算法。

