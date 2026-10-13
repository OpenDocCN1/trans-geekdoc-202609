

$$
\mathbf{v} = - \frac{P^{-1}\nabla J(\mathbf{\theta}_{0})}{\|P^{-1}\nabla J(\mathbf{\theta}_{0})\|_{P}}.
$$

![Equation](images/B9780443292385000123/si421.png)

1.  

2. **6.16** 解释为什么牛顿迭代最小化方法的收敛性对海森矩阵相对不敏感。

3. **提示**：设 `P` 为正定矩阵。定义变量变换，
   $$
   \widetilde{\mathbf{\theta}} = P^{\frac{1}{2}}\mathbf{\theta},
   $$
   并基于新变量执行梯度下降最小化。

4. **6.17** 证明在点 `θ[0]` 处，受约束于
   $$
   \|\mathbf{v}\|_{1} = 1,
   $$
   的 `J(θ)` 最速下降方向 `v` 由 `e[k]` 给出，其中 `e[k]` 是方向 `k` 上的标准基向量，使得
   $$
   |(\nabla J(\mathbf{\theta}_{0}))_{k}| > |(\nabla J(\mathbf{\theta}_{0}))_{j}|, \quad k \neq j.
   $$

5.  

6. **6.18** 证明 TLS 解由下式给出
   $$
   \widehat{\mathbf{\theta}} = \left( X^{T}X - {\overline{\sigma}}_{l + 1}^{2}I \right)^{-1}X^{T}\mathbf{y},
   $$
   其中 `${\overline{\sigma}}_{l + 1}$` 是 `[X ⋮ y]` 的最小奇异值。

