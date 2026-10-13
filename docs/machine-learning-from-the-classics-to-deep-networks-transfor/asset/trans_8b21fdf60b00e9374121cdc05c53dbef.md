
公式为：

$$\psi(\mathbf{\theta}) = \frac{1}{2}||\mathbf{\theta} - \mathbf{\theta}_{n - 1}||^{2},$$

并用最近值 $\mathcal{L}_{n-1}^{\prime}$ 代替平均梯度。则公式 [(8.140)](#Chp008_343-416_B9780443292385000147.xhtml#deq257) 等价于：

```
0 ∈ ℒ[n-1]′ + ∂ϕ(θ) + μ[n](θ - θ[n-1])
```

这与从公式 [(8.131)](#Chp008_343-416_B9780443292385000147.xhtml#deq244) 导出的关系相同，如果我们设定：

$$f \rightarrow \phi,\ \mathbf{x}_{k} \rightarrow \mathbf{\theta}_{n},\ \mathbf{x}_{k - 1} \rightarrow \mathbf{\theta}_{n - 1},\ g \rightarrow \mathcal{L},\ \lambda_{k} \rightarrow \frac{1}{\mu}_{n}.$$

实际上，使用这些替换并设定 $\phi(\cdot) = ||\cdot||_{1}$，可得到 FOBOS 算法 [36]。然而，在公式 [(8.140)](#Chp008_343-416_B9780443292385000147.xhtml#deq257) 的情况下，可以使用其他函数来代替 $\mathbf{\theta}_{n-1}$ 的平方欧几里得距离。

一种常用的辅助函数是 **Bregman 散度**。关于函数 $\psi$，两点 $\mathbf{x}, \mathbf{y}$ 之间的 Bregman 散度定义为：

![Equation](images/B9780443292385000147/fx044.jpg)(8.142)

留作简单练习验证：若 $\psi(\mathbf{x}) = ||\mathbf{x}||^{2}$，则欧几里得距离即为 Bregman 散度。
