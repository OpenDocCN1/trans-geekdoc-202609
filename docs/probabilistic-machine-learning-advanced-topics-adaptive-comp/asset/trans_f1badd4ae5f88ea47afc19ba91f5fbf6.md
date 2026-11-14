

## 3.4.3 一元高斯模型

在本节中，我们推导一元高斯的后验 \(p(\mu, \sigma^2 | \mathcal{D})\)。为简化起见，我们分三步考虑：仅推导 \(\mu\)、仅推导 \(\sigma^2\)，然后两者同时推导。多元情况请参见第 3.4.4 节。

### 3.4.3.1 给定 \(\sigma^2\) 时 \(\mu\) 的后验

如果 \(\sigma^2\) 是已知常数，则 \(\mu\) 的似然函数形式为

```
\( p(\mathcal{D}|\mu) \propto \exp \left( - \frac{1}{2\sigma^2} \sum_{n=1}^N (y_n - \mu)^2 \right) \) (3.97)
```

可以证明，共轭先验是另一个高斯分布，\(\mathcal{N}(\mu | \tilde{m}, \tilde{\tau}^2)\)。对高斯分布应用贝叶斯法则（公式 (2.121)），我们发现相应的后验由下式给出：

```
\( p(\mu | \mathcal{D}, \sigma^2) = \mathcal{N}(\mu | \hat{m}, \hat{\tau}^2) \) (3.98)
\( \hat{\tau}^2 = \frac{1}{\frac{N}{\sigma^2} + \frac{1}{\tilde{\tau}^2}} = \frac{\sigma^2 \tilde{\tau}^2}{N \tilde{\tau}^2 + \sigma^2} \) (3.99)
\( \hat{m} = \hat{\tau}^2 \left( \frac{\tilde{m}}{\tilde{\tau}^2} + \frac{N \bar{y}}{\sigma^2} \right) = \frac{ \frac{\sigma^2}{N \tilde{\tau}^2 + \sigma^2} \tilde{m} + \frac{N \tilde{\tau}^2}{N \tilde{\tau}^2 + \sigma^2} \bar{y} }{1} \) (3.100)
```

其中 \(\bar{y} \triangleq \frac{1}{N} \sum_{n=1}^N y_n\) 是经验均值。

如果用精度参数（即方差的倒数）来表示，此结果更易于理解。具体来说，令 \(\lambda = 1/\sigma^2\) 为观测精度，\(\tilde{\lambda} = 1 / \tilde{\tau}^2\) 为先验精度。我们可以将后验改写如下：

```
\( p(\mu | \mathcal{D}, \lambda) = \mathcal{N}(\mu | \hat{m}, \hat{\lambda}^{-1}) \) (3.101)
\( \hat{\lambda} = \tilde{\lambda} + N \lambda \) (3.102)
\( \hat{m} = \frac{N \lambda \bar{y} + \tilde{\lambda} \tilde{m}}{\hat{\lambda}} = \frac{N \lambda}{N \lambda + \tilde{\lambda}} \bar{y} + \frac{\tilde{\lambda}}{N \lambda + \tilde{\lambda}} \tilde{m} \) (3.103)
```

这些方程相当直观：后验精度 \(\hat{\lambda}\) 等于先验精度 \(\tilde{\lambda}\) 加上 \(N\) 个单位的观测精度 \(\lambda\)。此外，后验均值 \(\hat{m}\) 是经验均值 \(\bar{y}\) 和先验均值 \(\tilde{m}\) 的凸组合。这清楚地表明，后验均值是经验均值与先验之间的折中。如果先验相对于信号强度较弱（\(\tilde{\lambda}\) 相对于 \(\lambda\) 较小），我们会更倾向于经验均值。如果先验相对于信号强度较强（\(\tilde{\lambda}\) 相对于 \(\lambda\) 较大），我们会更倾向于先验。图 3.5 对此进行了说明。还要注意，后验均值是用 \(N \lambda \bar{x}\) 表示的，因此 \(N\) 个精度均为 \(\lambda\) 的观测相当于一次值为 \(\bar{x}\)、精度为 \(N \lambda\) 的观测。

为了进一步理解这些方程，考虑观察到单个数据点后的后验：

![](img/ca72c1626f4850f058a9edc138c1ac73_117_0.png)

![](img/ca72c1626f4850f058a9edc138c1ac73_117_1.png)

图 3.5：在已知 \(\sigma^2\) 的情况下推导一元高斯的均值。（a）使用强先验，\(p(\mu) = \mathcal{N}(\mu|0, 1)\)。（b）使用弱先验，\(p(\mu) = \mathcal{N}(\mu|0, 5)\)。由 `gauss_infer_1d.ipynb` 生成。

y（因此 N = 1）。此时后验均值可写为以下等价形式：

```
\(\tilde{m} = \frac{\tilde{\lambda}}{\lambda}\tilde{m} + \frac{\lambda}{\lambda}y\) (3.104)

\(=\tilde{m} + \frac{\lambda}{\tilde{\lambda}}(y - \tilde{m})\) (3.105)

\(= y - \frac{\tilde{\lambda}}{\lambda}(y - \tilde{m})\) (3.106)
```

第一个方程是先验均值与数据的凸组合。第二个方程是向数据 \(y\) 调整后的先验均值。第三个方程是向先验均值调整后的数据；这被称为**收缩**估计。如果我们定义权重 \(w = \tilde{\lambda} / \lambda\)，则更容易看出这一点。此时有

```
\(\bar{m} = y - w(y - \bar{m}) = (1 - w)y + w \bar{m}\) (3.107)
```

请注意，对于高斯分布，后验均值和后验众数相同。因此，我们可以使用上述方程进行 MAP 估计。

### 3.4.3.2 给定 \(\mu\) 时 \(\sigma^2\) 的后验

如果 \(\mu\) 是已知常数，则 \(\sigma^2\) 的似然函数形式为

```
\(p(\mathcal{D}|\sigma^2) \propto (\sigma^2)^{-N/2} \exp \left( - \frac{1}{2\sigma^2} \sum_{n=1}^N (y_n - \mu)^2 \right)\) (3.108)
```

此时不能再忽略前面的 \(1/(\sigma^2)\) 项。标准共轭先验是逆伽马分布（第 2.2.3.4 节），由下式给出：

```
\(\text{IG}(\sigma^2 | \tilde{a}, \tilde{b}) = \frac{\tilde{b}^{\tilde{a}}}{\Gamma(\tilde{a})} (\sigma^2)^{-(\tilde{a}+1)} \exp(-\frac{\tilde{b}}{\sigma^2})\) (3.109)
```

![](img/ca72c1626f4850f058a9edc138c1ac73_118_0.png)

图 3.6：从非信息先验开始，对 \(\sigma^2\) 的后验进行顺序更新。数据来自均值已知为 \(\mu = 5\)、方差未知为 \(\sigma^2 = 10\) 的高斯分布。由 `gauss_seq_update_sigma_1d.ipynb` 生成

将似然函数和先验相乘，我们发现后验也是 IG：
\(p(\sigma^2|\mu, \mathcal{D}) = \text{IG}(\sigma^2| \hat{a}, \hat{b})\) (3.110)
\(\hat{a} = \tilde{a} + N/2\) (3.111)
\(\hat{b} = \tilde{b} + \frac{1}{2} \sum_{n=1}^N (y_n - \mu)^2\) (3.112)

图 3.6 予以说明。

使用 IG(\(\tilde{a}, \tilde{b}\)) 分布的一个小不便之处在于，先验强度同时编码在 \(\tilde{a}\) 和 \(\tilde{b}\) 中。因此，在贝叶斯统计文献中，通常使用 IG 分布的另一种参数化，称为（缩放）**逆卡方分布**：
\(\chi^{-2}(\sigma^2| \tilde{\nu}, \tilde{\tau}^2) = \text{IG}(\sigma^2| \frac{\tilde{\nu}}{2}, \frac{\tilde{\nu} \tilde{\tau}^2}{2}) \propto (\sigma^2)^{-\tilde{\nu}/2 - 1} \exp(-\frac{\tilde{\nu} \tilde{\tau}^2}{2\sigma^2})\) (3.113)

这里 \(\tilde{\nu}\)（称为自由度或 dof 参数）控制先验的强度，而 \(\tilde{\tau}^2\) 编码先验均值。使用此先验，后验变为
\(p(\sigma^2|\mathcal{D}, \mu) = \chi^{-2}(\sigma^2| \hat{\nu}, \hat{\tau}^2)\) (3.114)
\(\hat{\nu} = \tilde{\nu} + N\) (3.115)
\(\hat{\tau}^2 = \frac{\tilde{\nu} \tilde{\tau}^2 + \sum_{n=1}^N (y_n - \mu)^2}{\hat{\nu}}\) (3.116)

我们可以看到，后验自由度 \(\hat{\nu}\) 等于先验自由度 \(\tilde{\nu}\) 加上 \(N\)，后验平方和 \(\hat{\nu} \hat{\tau}^2\) 等于先验平方和 \(\tilde{\nu} \tilde{\tau}^2\) 加上数据平方和。

### 3.4.3.3 \(\mu\) 和 \(\sigma^2\) 的后验：共轭先验

现在假设我们要同时推导均值和方差。相应的共轭先验是**正态逆伽马分布**：
\(\text{NIG}(\mu, \sigma^2| \tilde{m}, \tilde{\kappa}, \tilde{a}, \tilde{b}) \triangleq \mathcal{N}(\mu| \tilde{m}, \sigma^2 / \tilde{\kappa}) \text{IG}(\sigma^2| \tilde{a}, \tilde{b})\) (3.117)

![](img/ca72c1626f4850f058a9edc138c1ac73_119_0.png)

图 3.7：\(NI\chi^2(\mu, \sigma^2|m, \kappa, \nu, \sigma^2)\) 分布。\(m\) 是先验均值，\(\kappa\) 表示我们对该均值的信念强度；\(\sigma^2\) 是先验方差，\(\nu\) 表示我们对该方差的信念强度。（a）\(m = 0, \kappa = 1, \nu = 1, \sigma^2 = 1\)。请注意，下方的等高线图呈“压扁蛋”形状。（b）我们通过设置 \(\kappa = 5\) 增加对均值的信念强度，因此围绕 \(m = 0\) 的 \(\mu\) 分布变得更窄。由 nix_plots.ipynb 生成。

不过，通常使用一种称为正态逆卡方或 **NIX** 分布 [Gel+14a, p67] 的重参数化，其定义如下

```
\(NI\chi^2(\mu, \sigma^2 | \tilde{m}, \tilde{\kappa}, \tilde{\nu}, \tilde{\tau}^2) \triangleq \mathcal{N}(\mu | \tilde{m}, \sigma^2 / \tilde{\kappa}) \chi^{-2}(\sigma^2 | \tilde{\nu}, \tilde{\tau}^2)\) (3.118)
\(\propto (\frac{1}{\sigma^2})^{(\tilde{\nu}+3)/2} \exp \left( -\frac{\tilde{\nu}\tilde{\tau}^2 + \tilde{\kappa} (\mu - \tilde{m})^2}{2\sigma^2} \right)\) (3.119)
```

请参见图 3.7 中的一些图示。沿 \(\mu\) 轴，分布呈高斯形状；沿 \(\sigma^2\) 轴，分布呈 \(\chi^{-2}\) 形状；联合密度的等高线呈“压扁蛋”外观。有趣的是，我们看到当 \(\sigma^2\) 取较小值时，\(\mu\) 的等高线更尖锐，这是合理的，因为如果数据方差较低，我们就能更可靠地估计其均值。

可以证明（基于第 3.4.4.3 节）后验由下式给出

```
\(p(\mu, \sigma^2 | \mathcal{D}) = NI\chi^2(\mu, \sigma^2 | \tilde{m}, \tilde{\kappa}, \tilde{\nu}, \tilde{\tau}^2)\) (3.120)
\(\widehat{m} = \frac{\tilde{\kappa}\tilde{m} + N\overline{x}}{\widehat{\kappa}}\) (3.121)
\(\widehat{\kappa} = \tilde{\kappa} + N\) (3.122)
\(\widehat{\nu} = \tilde{\nu} + N\) (3.123)
\(\widehat{\nu}\widehat{\tau}^2 = \tilde{\nu}\tilde{\tau}^2 + \sum_{n=1}^N (y_n - \overline{y})^2 + \frac{N\tilde{\kappa}}{\tilde{\kappa} + N} (\tilde{m} - \overline{y})^2\) (3.124)
```

其解释如下。对于 \(\mu\)，后验均值 \(\widehat{m}\) 是先验均值 \(\tilde{m}\) 与极大似然估计 \(\overline{x}\) 的凸组合；该后验的强度 \(\widehat{\kappa}\) 是先验强度 \(\tilde{\kappa}\) 加上

