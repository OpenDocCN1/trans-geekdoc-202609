

### 4. 对于 $n = 2, 3, \dots$，执行以下步骤：

#### (a) 
$\mathbf{p}[n] = \beta \mathbf{p}[n-1] + \mathbf{x}[n-1] e[n-1]$。

#### (b) 获取当前支撑集：
$$S = \text{supp}\{\boldsymbol{\theta}(n - 1)\} \cup \left\{ \frac{\text{indices of the } t \text{ largest in}}{\text{magnitude components of } \mathbf{p}_n} \right\}.$$

#### (c) 执行 LMS 更新：
$$\begin{aligned}
\tilde{e}_n &= y_n - \mathbf{x}_{n|S}^T \tilde{\boldsymbol{\theta}}_{|S}(n - 1), \\
\tilde{\boldsymbol{\theta}}_{|S}(n) &= \tilde{\boldsymbol{\theta}}_{|S}(n - 1) + \mu \mathbf{x}_{n|S} \tilde{e}_n.
\end{aligned}$$

#### (d) 获取 $\tilde{\boldsymbol{\theta}}_{|S}(n)$ 中幅值最大的 $k$ 个分量的索引集合 $S_k$。

#### (e) 获取 $\boldsymbol{\theta}(n)$ 使得

