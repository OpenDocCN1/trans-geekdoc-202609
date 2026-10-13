

## 数学推导

$$
\mathcal{F}(q,\mathbf{\xi}) = \int q(\mathcal{X}^{l})\ln\frac{p(\mathcal{X}^{l}|\mathcal{X};\mathbf{\xi})p(\mathcal{X};\mathbf{\xi})}{q(\mathcal{X}^{l})}d\mathcal{X}^{l}
= \int q(\mathcal{X}^{l})\ln\frac{p(\mathcal{X}^{l}|\mathcal{X};\mathbf{\xi})}{q(\mathcal{X}^{l})}d\mathcal{X}^{l} + \ln p(\mathcal{X};\mathbf{\xi})
$$

(12.66)

其中上述等式成立是因为 $\ln p(\mathcal{X};\mathbf{\xi})$ 不依赖于 $q(\mathcal{X}^{(l)})$，且后者积分为 1（作为概率分布）。右边第一项是所谓的 KL 散度（公式 [(2.161)](#Chp002_19-64_B9780443292385000081.xhtml)）的负值，该散度在 $q(\mathcal{X}^{(l)})$ 和 $p(\mathcal{X}^{(l)}|\mathcal{X};\mathbf{\xi})$ 之间，我们将其记为 $KL(q \parallel p)$。回顾一下，KL 散度衡量两个分布有多大差异。如果两个分布相等，则它们的 KL 散度为零。因此，最终我们得到：

$$
\ln p(\mathcal{X};\mathbf{\xi}) = \mathcal{F}(q,\mathbf{\xi}) + KL(q \parallel p)
$$

(12.67)

因为 KL 散度是非负量，即 $KL(q \parallel p) \ge 0$（习题 [12.7](#Chp012_583-634_B9780443292385000184.xhtml#o0110)），所以可得：

![Equation](images/B9780443292385000184/fx013.jpg)

(12.68)

