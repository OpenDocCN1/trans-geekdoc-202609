

$P(z_{n_k} = 1) = P_k$

对于满足公式 (13.49) 的任意 $\mathbf{z}_n \in \mathbb{R}^K$，

$$
P(\mathbf{z}_n) = \prod_{k=1}^{K} P_k^{z_{n_k}} \tag{13.50}
$$

因此，集合 $\mathcal{Z} = \{\mathbf{z}_1, \dots, \mathbf{z}_N\}$ 出现的概率为

$$
P(\mathcal{Z}) = \prod_{n=1}^{N} \prod_{k=1}^{K} P_k^{z_{n_k}} \tag{13.51}
$$

通过这种方式，我们利用多项式概率分布描述了 $N$ 个潜在变量的随机性质。

在后续内容中，我们将均值和精度矩阵均视为随机量，并采用以下先验概率密度函数 (PDF)：

$$
p(\boldsymbol{\mu}_k) = \mathcal{N}(\boldsymbol{\mu}_k | \mathbf{0}, \beta^{-1} \mathbf{I})
$$

以及

$$
p(\mathbf{Q}_k) = \mathcal{W}(\mathbf{Q}_k | \mathbf{W}_0, \nu_0),
$$

其中 $\nu_0, \mathbf{W}_0$ 和 $\beta$ 为固定值。也就是说，均值采用高斯先验，精度矩阵采用威沙特先验。我们将 $\mathbf{P} = [P_1, \dots, P_k]^T$ 视为确定性参数，其优化值在 M 步中获得。

遵循变分贝叶斯 EM 的理念，我们采用

