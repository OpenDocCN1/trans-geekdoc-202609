
具有分量 $d_i(x_1), \dots, d_i(x_N)$ 的 $d_i$ 可以唯一地分解为两个向量，一个位于由 **D** 的列张成的空间，另一个位于该空间的正交补空间：

```
$d_i = \mathbf{Da} + \mathbf{b},$
```

其中 $\mathbf{D}^T b = 0$。
如果 $||b|| > 0$，则 $d_i$ 与 **D** 的列线性无关，并可以添加到模型中。我们还希望避免近线性依赖，换句话说，避免 $||b||$ 的值较小。
由于分解是正交的，

```
$||d_i||^2 = ||\mathbf{Da}||^2 + ||\mathbf{b}||^2$.
```

虽然 $d_i$ 的长度是已知的，但 **Da** 和 **b** 的长度是未知的。
考虑

```
$$\sigma^2 S_i = \sigma^2 d_i^T \mathbf{C}^T d_i = d_i^T (I - \sigma^{-2}\mathbf{D}\Sigma\mathbf{D}^T) d_i = (\mathbf{a}^T + \mathbf{b}^T) (I - \sigma^{-2}\mathbf{D}\Sigma\mathbf{D}^T) (\mathbf{Da} + \mathbf{b}) = \mathbf{a}^T \mathbf{D}^T (I - \sigma^{-2}\mathbf{D}\Sigma\mathbf{D}^T) \mathbf{a} + \mathbf{b}.$
```

由于正交性。使用 $\sigma^{-2}\Sigma = (\sigma^2\mathbf{A} + \mathbf{D}^T\mathbf{D})^{-1}$，我们可以简化第一项的一部分：

```
$I - \sigma^{-2}\mathbf{D}^T\mathbf{D} = I - (\sigma^2\mathbf{A} + \mathbf{D}^T\mathbf{D})^{-1}(\sigma^2\mathbf{A} + \mathbf{D}^T\mathbf{D} - \sigma^2\mathbf{A}) = \mathbf{\Sigma}.$
```

结合最后的结果，我们得到

```
$$\sigma^2 S_i = \mathbf{a}^T \mathbf{D}^T\mathbf{D}\mathbf{Aa} + ||\mathbf{b}||^2.$
```

然而，右侧的第一个量是未知的。
为了克服未知数，注意我们可以通过一个因子缩放向量 **Da**，使得

```
$||\mathbf{Da}||^2 = \alpha \mathbf{a}^T \mathbf{D}^T\Sigma\mathbf{Aa}.$
```

由于 $\mathbf{Da}$ 和 $\mathbf{b}$ 是正交的，向量 **Da**+**b** 的长度平方为

```
$||\mathbf{Da} + \mathbf{b}||^2 = ||\mathbf{Da}||^2 + ||\mathbf{b}||^2 = \mathbf{a}^T \mathbf{D}^T\Sigma\mathbf{Aa} + ||\mathbf{b}||^2 = \sigma^2 S_i.$
```

图 8.11 从几何上说明了各种向量及其长度之间的关系。根据线定理

```
$$\sin \theta = \frac{\sigma \sqrt{S_i}}{||d_i||} = \sigma \sqrt{\frac{d_i^T}{||d_i||^2}C^{-1} \frac{d_i}{||d_i||}}.$$
```

![](img/c6c76bf52016db7e78a5e30d4766ef81_288_0.png)

图 8.11：几何插图。

由于 $\phi \le 1$，$\sigma \sqrt{S_i}/||d_i||$ 是 $\theta$ 的上界。如果这个值变得太小，则 $\mathbf{d}$ 被认为与 $\mathbf{D}$ 的列近线性相关，如果 $Q_i^2 > S_i$ 表明通过此函数增加模型会增加边际似然对数，则不将 $d_i(\mathbf{x})$ 添加到模型。由于 $\mathbf{d}$ 可以被 $\mathbf{D}$ 列的线性组合很好地近似，因此通过完全更新模型的系数也可以类似的增长。

注意，在此阶段不使用 $d_i(x)$ 并不意味着它被完全从模型中排除。由于算法还会删除线性依赖中的基函数，这种依赖可能会在以后阶段出现。

当 $d_i(x)$ 已经在模型中且 $\alpha_i$ 为有限时，可以推导出类似的共线性。在这种情况下，如果 $s_i/||d_i||$ 很小，则 $\mathbf{D}$ 的列被认为近线性相关。这种共线性被用于推迟在未来的更新中重构基函数，因为近线性依赖可以在算法的后续步骤中得到解决。这增加了稳定性。否则，算法可能会进入基函数重构的循环。这些基函数的超参数通常很小，表明这些基函数的系数分布广泛，从而存在不确定性。其他策略可以在一步步内更新一组基函数，或从一组函数创建一个新的基函数。

总结来说，贝叶斯学习提供了一个框架，其中模型是系数向量，获得 $\mathbf{c}$ 的后验分布。这引导我们得到对未见数据的预测分布。这使得我们可以通过此函数增强模型来增加边际似然对数。

## 8.4 高斯过程

高斯过程是定义在 $\mathbf{x}$ 上的一个随机函数 $f(\mathbf{x})$。对于任意一组点 $\mathbf{x}_1, \dots, \mathbf{x}_N$，其值 $f(\mathbf{x}_1), \dots, f(\mathbf{x}_N)$ 服从一个联合高斯分布。我们将 $f(\mathbf{x})$ 表示为基函数集合的线性组合 $f(\mathbf{x}) = \sum_{m=1}^M c_m \phi_m(\mathbf{x})$，其中 $\phi_m$ 是基函数。由于系数 $\mathbf{c}$ 服从高斯分布 $p(\mathbf{c}) = \mathcal{N}(\mathbf{0}, \mathbf{\Sigma})$，因此 $f(\mathbf{x}_1), \dots, f(\mathbf{x}_N)$ 也服从联合高斯分布。其均值和协方差矩阵分别为：

$$E[f(\mathbf{x}_i)] = \sum_{m=1}^M E[c_m] \phi_m(\mathbf{x}_i) = 0,$$
$$\text{cov}(f(\mathbf{x}_i), f(\mathbf{x}_j)) = \sum_{m=1}^M \sum_{l=1}^M \text{cov}(c_m, c_l) \phi_m(\mathbf{x}_i) \phi_l(\mathbf{x}_j) = \sum_{m=1}^M \sum_{l=1}^M \Sigma_{ml} \phi_m(\mathbf{x}_i) \phi_l(\mathbf{x}_j).$$

当 $M \to \infty$ 时，通过选择适当的基函数和协方差矩阵，可以构造任何高斯过程。例如，如果我们选择基函数 $\phi_m(\mathbf{x}) = \exp(i \mathbf{\omega}_m^T \mathbf{x})$，其中 $\mathbf{\omega}_m$ 是从谱密度 $s(\omega)$ 中采样的样本，那么得到的高斯过程的谱密度就是 $s(\omega)$。这正是布尔纳格-梅恩定理的体现。

高斯过程由均值函数 $m(\mathbf{x})$ 和协方差函数 $k(\mathbf{x}, \mathbf{x}')$ 确定：

$$m(\mathbf{x}) = E[f(\mathbf{x})],$$
$$k(\mathbf{x}, \mathbf{x}') = \text{cov}(f(\mathbf{x}), f(\mathbf{x}')).$$

常用的协方差函数包括：

- 径向基 (RBF) 核：$k(\mathbf{x}, \mathbf{x}') = \sigma^2 \exp\left(-\frac{||\mathbf{x}-\mathbf{x}'||^2}{2\ell^2}\right)$
- 质指数核：$k(\mathbf{x}, \mathbf{x}') = \sigma^2 \exp\left(-\frac{||\mathbf{x}-\mathbf{x}'||}{\ell}\right)$
- 周期核：$k(\mathbf{x}, \mathbf{x}') = \sigma^2 \exp\left(-\frac{2\sin^2(\pi||\mathbf{x}-\mathbf{x}'||/P)}{\ell^2}\right)$

对于高斯过程，给定观测数据 $\{\mathbf{x}_i, y_i\}_{i=1}^N$，我们对新点 $\mathbf{x}^*$ 的预测分布也是高斯分布：

$$p(f(\mathbf{x}^*) | \mathbf{X}, \mathbf{y}, \mathbf{x}^*) = \mathcal{N}(\mu^*, \sigma^{*2}),$$

其中：

$$\mu^* = \mathbf{k}^*^T \mathbf{K}^{-1} \mathbf{y},$$
$$\sigma^{*2} = k(\mathbf{x}^*, \mathbf{x}^*) - \mathbf{k}^*^T \mathbf{K}^{-1} \mathbf{k}^*,$$

这里 $\mathbf{K}_{ij} = k(\mathbf{x}_i, \mathbf{x}_j)$，$\mathbf{k}^*_i = k(\mathbf{x}_i, \mathbf{x}^*)$。

