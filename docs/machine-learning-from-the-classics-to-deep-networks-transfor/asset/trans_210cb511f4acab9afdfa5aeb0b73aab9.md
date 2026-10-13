

## 2. 初始化

*   $P[-1] = \lambda^{-1}I$；$\lambda > 0$ 为用户定义变量。

## 3. 选择 $\beta$

*   接近 1。

## 迭代过程

**For** $n = 0, 1, \dots$ **Do**

1.  $e[n] = y[n] - \boldsymbol{\theta}[n-1]^T \boldsymbol{x}[n]$
2.  $\boldsymbol{z}[n] = P[n-1] \boldsymbol{x}[n]$
3.  $\boldsymbol{k}_n = \frac{\boldsymbol{z}_n}{\beta + \boldsymbol{x}_n^T \boldsymbol{z}_n}$
4.  $\boldsymbol{\theta}[n] = \boldsymbol{\theta}[n-1] + \boldsymbol{k}[n] e[n]$
5.  $P[n] = \beta^{-1} P[n-1] - \beta^{-1} \boldsymbol{k}[n] \boldsymbol{z}[n]^T$

**End For**

## 备注 6.2

*   RLS 算法的复杂度为 $\mathcal{O}(l^2)$ 每次迭代，这是由于矩阵-向量乘积运算导致的。也就是说，与第 5 章讨论的 LMS 和其他算法相比，存在一个数量级的差异。换句话说，RLS 不适合高维场景。

