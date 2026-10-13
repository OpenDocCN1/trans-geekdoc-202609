

$\mathbf{e}_{n - 1|n - 1} := \mathbf{x}_{n - 1} - \widehat{\mathbf{x}}_{n - 1|n - 1}$.

![Equation](images/B978044329238500010X/si465.png)

**步骤 1**：利用 $\widehat{\mathbf{x}}_{n - 1|n - 1}$![Equation](images/B978044329238500010X/si466.png)，根据状态方程预测 $\widehat{\mathbf{x}}_{n|n - 1}$![Equation](images/B978044329238500010X/si462.png)；即，

$\widehat{\mathbf{x}}_{n|n - 1} = F_{n}\widehat{\mathbf{x}}_{n - 1|n - 1}$.

![Equation](images/B978044329238500010X/si467.png)(4.114)

换句话说，忽略噪声的贡献。这是自然的，因为预测不可能涉及未观测到的变量。

**步骤 2**：获得相应的误差协方差矩阵，

$P_{n|n - 1} = \mathbb{E}\left\lbrack (\mathbf{x}_{n} - \widehat{\mathbf{x}}_{n|n - 1}){(\mathbf{x}_{n} - \widehat{\mathbf{x}}_{n|n - 1})}^{T} \right\rbrack$.

![Equation](images/B978044329238500010X/si468.png)(4.115)

然而，

