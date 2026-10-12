

# 17.2 非线性潜变量模型

在非线性潜变量模型中，数据 `x` 和潜变量 `z` 均为连续且多元的。先验 `Pr(z)` 是标准多元正态分布：

```
c17-fig-5006.jpg
```
 (17.5)

---

**附录 C.3.2**

**多元正态分布**

---

似然 `Pr(x|z, ϕ)` 同样服从正态分布；其均值是潜变量的非线性函数 `f[z, ϕ]`，其协方差 `σ²I` 是球形的：

```
c17-fig-5007.jpg
```
 (17.6)

函数 `f[z, ϕ]` 由具有参数 `ϕ` 的深度网络描述。潜变量 `z` 的维度低于数据 `x`。模型 `f[z, ϕ]` 描述了数据的重要方面，而剩余的未建模方面被归因于噪声 `σ²I`。

通过对潜变量 `z` 进行边缘化，可得到数据概率 `Pr(x|ϕ)`：

```
c17-fig-5008.jpg
```
 (17.7)

---

**笔记本 17.1**

**潜变量模型**

---

这可以视为具有不同均值的球形高斯分布的无限加权求和（即无限混合），其中权重为 `Pr(z)`，均值为网络输出 `f[z, ϕ]`（[图 17.2](#c017.xhtml#c17-fig-0002)）。

![Figure 17.2 Nonlinear latent variable model. A complex 2D density Pr(x) (right) is created as the marginalization of the joint distribution Pr(x, z) (left) over the latent variable z; to create Pr(x), we integrate the 3D volume over the dimension z. For each z, the distribution over x is a spherical Gaussian (two slices shown) with a mean f[z, ϕ] that is a nonlinear function of z and depends on parameters ϕ. The distribution Pr(x) is a weighted sum of these Gaussians.](images/c17-fig-0002.jpg)

[图 17.2](#c017.xhtml#c17-fig-0002a) 非线性潜变量模型。通过对联合分布 `Pr(x, z)`（左）在潜变量 `z` 上进行边缘化，创建了一个复杂的二维密度 `Pr(x)`（右）；为创建 `Pr(x)`，我们沿维度 `z` 对三维体积进行积分。对于每个 `z`，`x` 上的分布是一个球形高斯分布（显示了两个切片），其均值 `f[z, ϕ]` 是 `z` 的非线性函数并取决于参数 `ϕ`。分布 `Pr(x)` 是这些高斯分布的加权求和。

### 17.2.1 生成

可以使用祖先采样生成新样本 `x*`（[图 17.3](#c017.xhtml#c17-fig-0003)）。我们从潜变量的先验概率 `Pr(z)` 中抽取 `z*`，并将其通过网络 `f[z*, ϕ]` 以计算似然 `Pr(x|z*, ϕ)` 的均值（公式 17.6），然后从中抽取 `x*`。先验和似然均为正态分布，因此这很直观。

---

**附录 C.4.2**

**祖先采样**

---

![Figure 17.3 Generation from nonlinear latent variable model. a) We draw a sample z* from the prior probability Pr(z) over the latent variable. b) A sample x* is then drawn from Pr(x|z*, ϕ). This is a spherical Gaussian with a mean that is a nonlinear function f[•, ϕ] of z* and a fixed variance σ²I. c) If we repeat this process many times, we recover the density Pr(x|ϕ).](images/c17-fig-0003.jpg)

[图 17.3](#c017.xhtml#c17-fig-0003a) 从非线性潜变量模型生成。a) 我们从潜变量的先验概率 `Pr(z)` 中抽取样本 `z*`。b) 然后从 `Pr(x|z*, ϕ)` 中抽取样本 `x*`。这是一个球形高斯分布，其均值是 `z*` 的非线性函数 `f[•, ϕ]`，方差固定为 `σ²I`。c) 如果我们重复此过程多次，即可恢复密度 `Pr(x|ϕ)`。

## 17.3 训练

为了训练模型，我们针对模型参数最大化训练数据集 `c17-fig-5009.jpg` 上的对数似然。为简化起见，我们假设似然表达式中的方差项 `σ²` 已知，并专注于学习 `ϕ`：

```
c17-fig-5010.jpg
```
 (17.8)

其中：

```
c17-fig-5011.jpg
```
 (17.9)

不幸的是，这是难以处理的。该积分没有闭式表达式，也没有简单的方法针对特定的 `x` 值对其进行求值。

### 17.3.1 证据下界 (ELBO)

为了取得进展，我们在对数似然上定义一个*下界*。对于给定的 `ϕ` 值，这是一个始终小于或等于对数似然的函数，同时也将依赖于其他一些参数 `θ`。最终，我们将构建一个网络来计算该下界并对其进行优化。为了定义这个下界，我们需要*詹森不等式*。

### 17.3.2 詹森不等式

詹森不等式指出，数据 `y` 的期望的凹函数 `g[•]` 大于或等于数据函数的期望：

```
c17-fig-5012.jpg
```
 (17.10)

---

**附录 B.1.2**

**凹函数**

---

在本例中，凹函数是对数，因此我们有：

```
c17-fig-5013.jpg
```
 (17.11)

---

**习题 17.2–17.3**

---

或者写出期望的完整表达式，我们有：

```
c17-fig-5014.jpg
```
 (17.12)

这在[图 17.4–17.5](#c017.xhtml#c17-fig-0004)中进行了探讨。事实上，稍微更一般的陈述也是成立的：

```
c17-fig-5015.jpg
```
 (17.13)

其中 `h[y]` 是 `y` 的函数。这成立是因为 `h[y]` 是具有新分布的另一个随机变量。由于我们从未指定 `Pr(y)`，该关系保持成立。

![Figure 17.4 Jensen's inequality (discrete case). The logarithm (black curve) is a concave function; you can draw a straight line between any two points on the curve, and this line will always lie underneath it. It follows that any convex combination (weighted sum with positive weights that sum to one) of the six points on the log function must lie in the gray region under the curve. Here, we have weighted the points equally (i.e., taken the mean) to yield the cyan point. Since this point lies below the curve, log[𝔼[y]] > 𝔼[log[y]].](images/c17-fig-0004.jpg)

[图 17.4](#c017.xhtml#c17-fig-0004a) 詹森不等式（离散情况）。对数（黑色曲线）是一个凹函数；你可以在曲线上的任意两点之间画一条直线，这条线将始终位于曲线下方。由此可见，对数函数上六个点的任意凸组合（权重为正且和为一的加权求和）必须位于曲线下的灰色区域内。这里，我们对这些点赋予相等的权重（即取平均值）以得到青色点。由于该点位于曲线下方，`log[𝔼[y]] > 𝔼[log[y]]`。

