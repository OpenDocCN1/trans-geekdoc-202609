
为估算 $\bar{f} = \mathbb{E}[f(X, Y)]$。朴素方法是使用 MC 近似

$$\hat{f}_{MC} = \frac{1}{S} \sum_{s=1}^S f(X_s, Y_s)$$ (11.52)

其中 $(X_s, Y_s) \sim p(X, Y)$。这是 $\bar{f}$ 的一个无偏估计量。然而，它可能具有高方差。现在假设我们在已知 $X$ 的情况下可以解析地边缘化掉 $Y$，即，我们可以可计算地求得

$$f_X(X_s) = \int dY p(Y|X_s) f(X_s, Y) = \mathbb{E}[f(X, Y)|X=X_s]$$ (11.53)

让我们定义 Rao-Blackwell 化估计量

$$\hat{f}_{RB} = \frac{1}{S} \sum_{s=1}^S f_X(X_s)$$ (11.54)

其中 $X_s \sim p(X)$。这是一个无偏估计量，因为 $\mathbb{E}[\hat{f}_{RB}] = \mathbb{E}[\mathbb{E}[f(X, Y)|X]] = \bar{f}$。然而，该估计量的方差可能低于朴素估计量。直观的原因是，我们现在在降维空间中进行采样。正式地，我们可以通过使用全方差公式得到

$$\mathbb{V}[\mathbb{E}[f(X, Y)|X]] = \mathbb{V}[f(X, Y)] - \mathbb{E}[\mathbb{V}[f(X, Y)|X]] \le \mathbb{V}[f(X, Y)]$$ (11.55)

关于此在实践中的一些示例，请参见第 6.3.4.2 节、第 13.4 节和第 12.3.8 节。

## 11.6.3 控制变量法

假设我们想要使用无偏估计量 $m(\mathcal{X}) = \frac{1}{S} \sum_{s=1}^S m(x_s)$ 来估计 $\mu = \mathbb{E}[f(X)]$，其中 $x_s \sim p(X)$ 且 $\mathbb{E}[m(X)] = \mu$。（我们略微滥用符号，使用 $m$ 既表示单个随机变量的函数，也表示一组样本。）现在考虑替代估计量

$$m^*(\mathcal{X}) = m(\mathcal{X}) + c(b(\mathcal{X}) - \mathbb{E}[b(\mathcal{X})])$$ (11.56)

这称为 **控制变量**，$b$ 称为 **基线**。（再次，我们滥用符号，使用 $b(\mathcal{X}) = \frac{1}{S} \sum_{s=1}^S b(x_s)$ 和 $m^*(\mathcal{X}) = \frac{1}{S} \sum_{s=1}^S m^*(x_s)$。）

很容易看出 $m^*(\mathcal{X})$ 是一个无偏估计量，因为 $\mathbb{E}[m^*(X)] = \mathbb{E}[m(X)] = \mu$。然而，只要 $b$ 与 $m$ 相关，它的方差可以更低。要看到这一点，注意

$$\mathbb{V}[m^*(X)] = \mathbb{V}[m(X)] + c^2 \mathbb{V}[b(X)] + 2c \text{Cov}[m(X), b(X)]$$ (11.57)

通过对 $\mathbb{V}[m^*(X)]$ 关于 $c$ 求导并令其为 0，我们发现最优值为

$$c^* = - \frac{\text{Cov}[m(X), b(X)]}{\mathbb{V}[b(X)]}$$ (11.58)

新估计量的相应方差现在为

$$\mathbb{V} [m^*(X)] = \mathbb{V} [m(X)] - \frac{\text{Cov} [m(X), b(X)]^2}{\mathbb{V} [b(X)]} = (1 - \rho^2_{m,b}) \mathbb{V} [m(X)] \le \mathbb{V} [m(X)] \tag{11.59}$$

其中 \(\rho^2_{m,b}\) 是基本估计量与基线函数的相关系数。如果我们可以确保此相关系数较高，就可以降低方差。直观地，CV 估计量利用关于已知量（即 \(\mathbb{E} [b(X)]\)）估计误差的信息，来减少在估计未知量（即 \(\mu\)）时的误差。

我们在第 11.6.3.1 节给出了一个简单的示例。关于该技术应用于黑盒变分推断的示例，请参见第 10.2.3 节。

### 11.6.3.1 示例

我们现在给出控制变量法的一个简单示例。4 考虑估计 \(\mu = \mathbb{E} [f(X)]\)，其中 \(f(X) = 1/(1 + X)\) 且 \(X \sim \text{Unif}(0, 1)$。精确值为

$$\mu = \int_0^1 \frac{1}{1+x} dx = \ln 2 \approx 0.693 \tag{11.60}$$

使用 \(S\) 样本的朴素 MC 估计为 \(m(\mathcal{X}) = \frac{1}{S} \sum_{s=1}^S f(x_s)$。使用 \(S = 1500$，我们发现 \(\mathbb{E} [m(\mathcal{X})] = 0.6935\)，标准误 se = 0.0037。

现在让我们使用 \(b(X) = 1 + X\) 作为基线，因此 \(b(\mathcal{X}) = (1/S) \sum_s (1 + x_s)$。其期望为 \(\mathbb{E} [b(X)] = \int_0^1 (1+x) dx = \frac{3}{2}$。控制变量估计量由以下给出

$$m^*(\mathcal{X}) = \frac{1}{S} \sum_{s=1}^S f(x_s) + c \left( \frac{1}{S} \sum_{s=1}^S b(x_s) - \frac{3}{2} \right) \tag{11.61}$$

最优值可以从 \(m(x_s)\) 和 \(b(x_s)\) 的样本中估算，并代入方程 (11.58) 得到 \(c^* \approx 0.4773$。使用 \(S = 1500$，我们发现 \(\mathbb{E} [m^*(\mathcal{X})] = 0.6941\) 且 se = 0.0007。

另请参见第 11.6.4.1 节，我们在其中使用反迭采样分析此示例。

- 4. 示例来自 [控制变量法](https://en.wikipedia.org/wiki/Control_variates)，符号有所修改。有关代码，请参见 control_variates.ipynb。
- 5. 我们的介绍基于 [反迭变量法](https://en.wikipedia.org/wiki/Antithetic_variates)。有关代码，请参见 antithetic_sampling.ipynb。

## 11.6.4 反迭采样

在本节中，我们讨论 **反迭采样**，这是一种降低方差的简单方法。5 假设我们想要估计 \(\theta = \mathbb{E} [Y]$。令 \(Y_1\) 和 \(Y_2\) 为两个样本。\(\theta\) 的无偏估计由以下给出

\(\hat{\theta} = (Y_1 + Y_2)/2$。该估计的方差为

$$\mathbb{V} [\hat{\theta}] = \frac{\mathbb{V} [Y_1] + \mathbb{V} [Y_2] + 2\text{Cov} [Y_1, Y_2]}{4} \tag{11.62}$$

因此，如果 \(\text{Cov} [Y_1, Y_2] < 0\)，方差会降低。所以，每当我们采样 \(Y_1$ 时，都应将 \(Y_2\) 设为其“反向”，但保持相同的均值。

例如，假设 \(Y \sim \text{Unif}(0, 1)$。如果我们让 \(y_1, \dots, y_n\) 为来自 \(\text{Unif}(0, 1)$ 的独立同分布样本，那么我们可以定义 \(y'_i = 1 - y_i$。\(y'_i\) 的分布仍然是 \(\text{Unif}(0, 1)$，但是 \(\text{Cov} [y_i, y'_i] < 1$。

![](img/ca72c1626f4850f058a9edc138c1ac73_522_0.png)

图 11.7：蒙特卡洛（MC）、基于索博尔序列的准蒙特卡洛（QMC）以及使用扰乱方法的随机 QMC 的示意图。改编自 [OR20] 的图 1。特此感谢 Art Owen 的允许。

### 11.6.4.1 示例

要了解这为什么有用，请考虑第 11.6.3.1 节中的示例。令 \(\hat{\mu}_{\text{mc}}\) 为使用 \(2N\) 个来自 Unif(0, 1) 样本的经典 MC 估计，并令 \(\hat{\mu}_{\text{anti}}\) 为将上述反迭采样方案应用于 \(N\) 个来自 Unif(0, 1) 基础样本的 MC 估计。精确值为 \(\mu = \ln 2 \approx 0.6935\)。对于经典方法，当 \(N = 750\) 时，我们发现 \(\mathbb{E}[\hat{\mu}_{\text{mc}}] = 0.69365\)，标准误为 0.0037。对于反迭方法，我们发现 \(\mathbb{E}[\hat{\mu}_{\text{anti}}] = 0.6939\)，标准误为 0.0007，这与第 11.6.3.1 节的控制变量方法相匹配。

## 11.6.5 准蒙特卡洛（QMC）

准蒙特卡洛（见 [Lem09; Owe13] 等）是一种数值积分方法，它用低差异序列（如 Halton 序列（见 [Owe17] 等）或 Sobol 序列）替代随机样本。直观地说，这些是空间填充点序列，旨在减少随机选择的输入中可能出现的不想要的间隙和聚集。示例请参见图 11.7。

更准确地说，考虑计算以下 \(D\) 维积分的问题：

$$\overline{f} = \int_{[0,1]^D} f(x)dx \approx \hat{f}_N = \frac{1}{N} \sum_{n=1}^N f(x_n)$$ (11.63)

令 \(\epsilon_N = |\overline{f} - \hat{f}_N|\) 为误差。在标准蒙特卡洛中，如果我们抽取 \(N\) 个独立样本，则有 \(\epsilon_N \sim O\left(\frac{1}{\sqrt{N}}\right)\)。在 QMC 中，可以证明 \(\epsilon_N \sim O\left(\frac{(\log N)^D}{N}\right)\)。对于 \(N > 2^D\)，后者小于前者。

QMC 的一个缺点是它只提供 \(\overline{f}\) 的点估计，而不提供不确定性估计。相比之下，在常规 MC 中，我们可以估计 MC 标准误，已在第 11.2.2 节讨论。随机 QMC（见 [L'E18] 等）为这一问题提供了解决方案。基本思路是通过随机扰动 \(N\) 点序列，重复 QMC 方法 \(R\) 次。特别是，定义

$$y_{i,r} = x_i + u_r \pmod 1$$ (11.64)

其中 $x_1, ..., x_N$ 是一个低差异序列，且 $u_r \sim \text{Unif}(0, 1)^D$ 是一个随机扰动。集合 $\{y_j\}$ 是低差异的，并且满足每个 $y_j \sim \text{Unif}(0, 1)^D$，对于 $j = 1 : N \times R$。这比标准 MC 具有低得多的方差。（通常我们取 $R$ 为 2 的幂。）最近，[OR20] 证明了 RQMC 的强大数定律。QMC 和 RQMC 可以用于 MCMC 推断（见 [OT05] 等）和变分推断（见 [BWMI8]）之中。它也常用于为贝叶斯优化（第 6.6 节）选择初始查询点集。

另一种可使用的技术是正交蒙特卡洛，其中样本被条件化为两两正交，但边缘分布与原始分布匹配（见 [Lin+20] 等）。
