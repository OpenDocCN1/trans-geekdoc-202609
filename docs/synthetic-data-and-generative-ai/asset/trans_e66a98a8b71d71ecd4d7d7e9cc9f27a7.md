
## 9.2 正交函数逼近

### 9.2.1 一般公式

其中 `D` 是我们希望逼近效果最好的定义域。如果 `f` 仅在整数值处已知，或者我们处理的是数据集，则积分被求和取代，且 `D` 是离散的插值节点集合（即整数），或者在数据集情况下是观测特征的集合。引入以下符号很方便：

`β[k] = ∫[D] p[k](x) f(x) dx`, `γ[k] = ∫[D] p[k]²(x) dx`, `β[ij] = ∫[D] p[i](x) p[j](x) dx`。

![Image](images/B9780443218576000138/si100.png)

然后我们有 `α[0] = β[0]/γ[0]`![Image](images/B9780443218576000138/si101.png) 且对于 `n > 0`![Image](images/B9780443218576000138/si102.png)，

$$
\alpha_n = \frac{1}{\gamma_n}\left\lbrack \beta_n - \sum_{k=0}^{n-1} \alpha_k \beta_{kn} \right\rbrack.
$$

![Image](images/B9780443218576000138/si103.png)

### 9.2.2 使用正交函数

如果系数 `β[ij]`![Image](images/B9780443218576000138/si104.png) 全为零，公式会大大简化。如果 (`p[k]`)![Image](images/B9780443218576000138/si105.png) 是一组**正交函数** [[Wiki](https://en.wikipedia.org/wiki/Orthogonal_functions)]，就会出现这种情况。最著名的例子是 `p[2k](x) = cos(kπx/L)`![Image](images/B9780443218576000138/si106.png) 结合 `p[2k+1](x) = sin(kπx/L)`![Image](images/B9780443218576000138/si107.png)，其中 `k = 0, 1`![Image](images/B9780443218576000138/si108.png)，依此类推。如果 `D = [-L, L]`![Image](images/B9780443218576000138/si109.png)，这对应于利用其**傅里叶级数** [[Wiki](https://en.wikipedia.org/wiki/Fourier_series)] 在 `D` 上逼近或插值周期函数 `f`。在这种情况下，若 `k > 0`![Image](images/B9780443218576000138/si111.png)，则 `γ[k] = L`![Image](images/B9780443218576000138/si110.png)，而 `γ[0] = 2L`![Image](images/B9780443218576000138/si112.png)。

遗憾的是，多项式 `p[x](x) = x^(k)`![Image](images/B9780443218576000138/si113.png) 在任何区间上都不正交。然而，存在一个称为**格拉姆-施密特正交化** [[Wiki](https://en.wikipedia.org/wiki/Gram%E2%80%93Schmidt_process)] 的过程，可将任何线性无关函数序列转换为正交函数。将其应用于 `1, x, x², x³`![Image](images/B9780443218576000138/si114.png) 等，可得到用于 `p[k](x)`![Image](images/B9780443218576000138/si93.png) 的**勒让德多项式** [[Wiki](https://en.wikipedia.org/wiki/Legendre_polynomials)]。它们在 `D = [-1, 1]`![Image](images/B9780443218576000138/si115.png) 上正交。

像往常一样，我们不必最小化公式 [(9.9)](#Chp009_147-168_B9780443218576000138.xhtml#deq11) 中 `f` 与 `f[n]`![Image](images/B9780443218576000138/si98.png) 之间的距离，而可以使用加权距离。所有结果都可相应调整。特别是，许多正交函数涉及权重。例如，**埃尔米特多项式** [[Wiki](https://en.wikipedia.org/wiki/Hermite_polynomials)] 涉及权重 `w(x) = exp(-x²/2)`![Image](images/B9780443218576000138/si116.png)，并满足

```
∫[-∞]^∞ p[i](x) p[j](x) w(x) dx = 0 if i ≠ j.
```

![Image](images/B9780443218576000138/si117.png)

在这种情况下，`D` 是整条实线，双向无限延伸。最后，也可以直接处理离散集合 `D` 和**离散正交函数** [[Wiki](https://en.wikipedia.org/wiki/Discrete_orthogonal_polynomials)]。积分照常变为求和。与所有这些概念相关的通用框架是**施图姆-刘维尔理论** [[Wiki](https://en.wikipedia.org/wiki/Sturm%E2%80%93Liouville_theory)]。

### 9.2.3 回归应用

你可以按如下方式将傅里叶级数方法应用于多元回归。它最适合连续特征。对于离散特征，我建议改用**离散傅里叶级数** [[Wiki](https://en.wikipedia.org/wiki/Discrete_Fourier_series)]。你需要分别转换每个连续特征，使其值在转换后尽可能均匀分布在区间 `[-1, 1]`![Image](images/B9780443218576000138/si118.png) 上。这分两步完成：首先对特征向量的第 `k` 个分量应用变换 `F[k]`![Image](images/B9780443218576000138/si119.png)。然后应用变换 `Q`。对每个分量 `k = 1, …, n`![Image](images/B9780443218576000138/si63.png) 执行此操作。其中

- `F[k]`![Image](images/B9780443218576000138/si119.png) 是与特征 `k` 关联的**经验分布函数** [[Wiki](https://en.wikipedia.org/wiki/Empirical_distribution_function)]。在 Python 中，使用 `statsmodel` 库中的 `ECDF()` 函数。
- `Q` 是 `[-1, 1]`![Image](images/B9780443218576000138/si118.png) 上均匀分布的**分位数函数** [[Wiki](https://en.wikipedia.org/wiki/Quantile_function)]。因此 `Q(u) = -1 + 2u`![Image](images/B9780443218576000138/si120.png)。

现在对转换后的数据使用公式 [(9.8)](#Chp009_147-168_B9780443218576000138.xhtml#deq10)，其中 `p[k]`![Image](images/B9780443218576000138/si121.png) 和 `α[k]`![Image](images/B9780443218576000138/si122.png) 来自第 [9.2.2](#Chp009_147-168_B9780443218576000138.xhtml#s0045) 节第一段，同时令 `L = 1`![Image](images/B9780443218576000138/si123.png)。注意此过程不涉及矩阵求逆。这是一种特殊的**样条回归** [[Wiki](https://en.wikipedia.org/wiki/Multivariate_adaptive_regression_spline)]。Python 代码见第 [9.3.3](#Chp009_147-168_B9780443218576000138.xhtml#s0070) 节。关于基于精确插值的另一种样条回归（类似于第 [9.1.3](#Chp009_147-168_B9780443218576000138.xhtml#s0025) 节讨论的方法），请参阅第 [8](#Chp008_131-145_B9780443218576000126.xhtml) 章。

对于多项式回归，在将特征转换为值保持在 `[-1, 1]`![Image](images/B9780443218576000138/si118.png) 内且均匀分布后，使用勒让德多项式。同样，无需矩阵求逆，过程快速简便。关于使用勒让德多项式进行回归的另一个示例，请参阅 [[3]](#Chp009_147-168_B9780443218576000138.xhtml#br0015)。

此处介绍的方法源于数学函数插值，其中求和公式中的连续项（本例中为公式 [(9.8)](#Chp009_147-168_B9780443218576000138.xhtml#deq10)）平均影响力递减。否则，该求和（通常包含无限项）将不收敛。因此，按重要性递减顺序排列特征是合理的。带有系数 `α[1]`![Image](images/B9780443218576000138/si124.png) 的第一个特征可选为残差误差最小的特征。带有系数 `α[2]`![Image](images/B9780443218576000138/si125.png) 的第二个特征为对残差误差改进最大的特征，以此类推。

此外，出于同一原因，在多元回归中，该方法适用于特征数 `n` 很大且能被模型 [(9.8)](#Chp009_147-168_B9780443218576000138.xhtml#deq10) 很好逼近的数据集，即使观测样本很少，见 [[4]](#Chp009_147-168_B9780443218576000138.xhtml#br0020)。此类数据集有时被称为**宽数据**。更通用的版本使用**多维傅里叶级数** [[2]](#Chp009_147-168_B9780443218576000138.xhtml#br0010)。

## 9.3 Python 代码
