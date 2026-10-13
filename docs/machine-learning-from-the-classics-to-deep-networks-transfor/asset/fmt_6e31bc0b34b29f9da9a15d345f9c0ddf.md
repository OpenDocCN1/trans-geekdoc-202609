
## 数学推导

$$
\mathbb{E}[q_{\boldsymbol{\theta}}^{(j+1)}][\boldsymbol{\theta}\boldsymbol{\theta}^{(T)}] = \Sigma_{\boldsymbol{\theta}}^{(j+1)} + \boldsymbol{\mu}_{\boldsymbol{\theta}}^{(j+1)}\boldsymbol{\mu}_{\boldsymbol{\theta}}^{(j+1)(T)}
$$

![Equation](images/B9780443292385000196/si113.png)

或者

$$
\mathbb{E}[\theta_k^2] = [\mathbb{E}[q_{\boldsymbol{\theta}}^{(j+1)}][\boldsymbol{\theta}\boldsymbol{\theta}^{(T)}]]_{kk} = [\Sigma_{\boldsymbol{\theta}}^{(j+1)}+\boldsymbol{\mu}_{\boldsymbol{\theta}}^{(j+1)}\boldsymbol{\mu}_{\boldsymbol{\theta}}^{(j+1)(T)}]_{kk}, \quad k = 0, 1, \dots, K-1
$$

![Equation](images/B9780443292385000196/si114.png) (13.41)

其中 `[A]_{kk}` 表示矩阵 `A` 的第 `k` 行第 `k` 列元素。为了完成计算，我们需要计算 $\mathbb{E}[\alpha_k]$，其中 $k = 0, 1, \dots, K-1$，以便在下一次迭代中用于公式 [(13.33)](#Chp013_635-716_B9780443292385000196.xhtml#deq43)。然而，因为每个 $\alpha_k$ 都服从伽马分布，我们知道（第 [2.3.2](#Chp002_19-64_B9780443292385000081.xhtml) 节）
