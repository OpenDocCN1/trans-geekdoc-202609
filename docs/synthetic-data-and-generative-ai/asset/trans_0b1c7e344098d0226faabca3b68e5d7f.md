

### 另一个值得研究的案例

最后，另一个值得研究的案例如下。设 `P` 为所有素数的集合，`p[k]`![Image](images/B9780443218576000217/si112.png) 为第 `k` 个素数，其中 `p[1]` = 2![Image](images/B9780443218576000217/si32.png)。定义 `χ(p[2k+1])` = +1![Image](images/B9780443218576000217/si113.png) 和 `χ(p[2k])` = -1![Image](images/B9780443218576000217/si114.png)。则当 `σ` > 0.5![Image](images/B9780443218576000217/si115.png) 时，公式 [(17.4)](#Chp017_329-360_B9780443218576000217.xhtml#deq5) 中的乘积收敛（针对 `t` = 0![Image](images/B9780443218576000217/si25.png) 证明这一点，利用该乘积为交错乘积这一事实；另见[此处](https://mathoverflow.net/questions/159534/does-this-alternating-euler-product-converge-for-all-res-0)）。因此，该无限乘积（无根）可用于计算 `η[P](z, χ)`![Image](images/B9780443218576000217/si88.png)。但该收敛非绝对收敛。我预期当 0.5 < `σ` < 1![Image](images/B9780443218576000217/si90.png) 时不存在根。但我同时也预期空洞会缩减为单个点（原点），就像标准情况那样。

### 17.2.2.2 概率性质与猜想

此处 `P` 为所有素数的集合，且对所有 `p` 有 `χ(p)` = 1![Image](images/B9780443218576000217/si100.png)。第 [17.2.1.1](#Chp017_329-360_B9780443218576000217.xhtml#s0040) 节介绍的 **Liouville 函数** `λ(·)`![Image](images/B9780443218576000217/si116.png) 和 **Möbius 函数** `μ(·)`![Image](images/B9780443218576000217/si117.png) 具有许多有趣的性质和开放问题。其中许多等价于或推广了 RH。此处我简要总结；更多内容可見[此处](https://mathoverflow.net/questions/391736/normal-numbers-liouville-function-and-the-riemann-hypothesis)。同样，设 `L(n)` = `λ(1)` + ⋯ + `λ(n)`![Image](images/B9780443218576000217/si118.png)。

- 对于正整数 `k`，数值 `λ(k)`![Image](images/B9780443218576000217/si119.png) 以相等比例取 -1 或 +1，因此平均值为零。但由于负值开局领先优势明显，`L(n)`![Image](images/B9780443218576000217/si83.png) 需要很长时间才能转为正值。事实上，**Pólya 猜想** [[Wiki](https://en.wikipedia.org/wiki/P%C3%B3lya_conjecture)] 声称 `L(n)`![Image](images/B9780443218576000217/si83.png) 恒为负，但该猜想于 1958 年被证伪。满足 `L(n)` > 0![Image](images/B9780443218576000217/si120.png) 的最小可能 `n`，即 ![Image](images/B9780443218576000217/fx001.jpg)，于 1980 年被发现。`λ(k)` = ±1![Image](images/B9780443218576000217/si121.png) 的符号变化呈现某种随机性，类似于独立的伯努利试验。如果 +1 和 -1 真的是以零均值随机分布的，它们将满足**迭代对数律** [[Wiki](https://en.wikipedia.org/wiki/Law_of_the_iterated_logarithm)]：

```
\underset{n\rightarrow\infty}{\lim\sup}\frac{|L(n)|}{\sqrt{n\log\log n}} = C,
```

![Image](images/B9780443218576000217/si122.png)(17.7)

其中常数 `C` 满足 0 < `C` < ∞![Image](images/B9780443218576000217/si123.png)。据推测情况并非如此。事实上，`λ(k)`![Image](images/B9780443218576000217/si119.png) 不可能是独立的，甚至渐近上也不是，因为该函数是完全乘法的。但要证明 RH，只需要一个较弱的陈述，即对于任意 `ε` > 0![Image](images/B9780443218576000217/si126.png)，当 `n` → ∞![Image](images/B9780443218576000217/si125.png) 时，`$L(n)/\sqrt{n^{1 + \epsilon}}\rightarrow 0` `![Image](images/B9780443218576000217/si124.png)。这尚未被证明。Möbius 函数存在类似的猜想：**Mertens 猜想** [[Wiki](https://en.wikipedia.org/wiki/Mertens_conjecture)]，它也蕴含 RH，因此也尚未被证明。参见 [[11]](#Chp017_329-360_B9780443218576000217.xhtml#br0055) 中基于随机乘法 **Rademacher 函数** [[Wiki](https://en.wikipedia.org/wiki/Rademacher_distribution)] 的随机版本，后者被用作替代品来模拟 Möbius 函数的“随机性”。

- 一个更强的猜想，但不如迭代对数律强，是：`λ(k)`![Image](images/B9780443218576000217/si119.png) 的行为类似于**正规数** [[Wiki](https://en.wikipedia.org/wiki/Normal_number)] 的二进制数字。简而言之，数值 `` `$\nu = \sum_{k = 1}^{\infty}\lambda(k)2^{- k}` ``![Image](images/B9780443218576000217/si127.png) 是正规数。当然，`ν` 是无理数，否则 `λ(·)`![Image](images/B9780443218576000217/si116.png) 将是周期函数。目前尚不清楚 `ν` 是否为超越数，尽管一些密切相关的数是 [[2]](#Chp017_329-360_B9780443218576000217.xhtml#br0010)。序列 `{λ(k)}`![Image](images/B9780443218576000217/si128.png) 的正规性（或等价地，遍历性）将意味着 **Chowla 猜想** 成立，而后者比 RH 更强；参见 [[6]](#Chp017_329-360_B9780443218576000217.xhtml#br0030)。但这尚未被证明。

- 对于正整数 `k`，数值 `μ(k)`![Image](images/B9780443218576000217/si82.png) 等于 -1、0 或 +1。等于零的比例为 1 - 6/`π`²![Image](images/B9780443218576000217/si129.png)。这是因为 `μ(k)` = 0![Image](images/B9780443218576000217/si130.png) 当且仅当 `k` 有平方因子。众所周知且易于证明，**无平方因子整数** [[Wiki](https://en.wikipedia.org/wiki/Square-free_integer)] 的比例为 6/`π`²![Image](images/B9780443218576000217/si131.png)。`μ(k)`![Image](images/B9780443218576000217/si82.png) 等于 -1 和 +1 的比例相同，这是 **Dirichlet 定理** [[Wiki](https://en.wikipedia.org/wiki/Dirichlet%27s_theorem_on_arithmetic_progressions)] 的推论。

最后，**Kronecker 定理** [[Wiki](https://en.wikipedia.org/wiki/Kronecker%27s_theorem)] 的一个应用导出以下结果：对于任何固定的 `σ`，由公式 [(17.5)](#Chp017_329-360_B9780443218576000217.xhtml#deq6) 定义的 Dirichlet `L`-函数的轨道（假设收敛）最终会在复平面上填满一个稠密区域。无论该轨道是有界还是无界，无论它是否有“可见”的空洞，此结论均成立。换句话说，`η[P](z, χ)`![Image](images/B9780443218576000217/si88.png) 或 `L[P](z, χ)`![Image](images/B9780443218576000217/si107.png) 的像域是一个**稠密集** [[Wiki](https://en.wikipedia.org/wiki/Dense_set)]。我在[练习 17.5](#Chp017_329-360_B9780443218576000217.xhtml#enun0035)中提供了这一事实的一个优雅证明，使用的论证类似于证明其**普适性** [[Wiki](https://en.wikipedia.org/wiki/Zeta_function_universality)] 所用的论证。这意味着如果 0.5 < `σ` < 1![Image](images/B9780443218576000217/si90.png)，假设 `P` 包含足够多的素数，则无论 `χ` 如何，Dirichlet eta 函数都能任意接近零，即使它永远不会真正取到零值。换句话说，在这种情况下，空洞最终会收缩为单个点。

## 17.3 有限 Dirichlet 级数及其推广

