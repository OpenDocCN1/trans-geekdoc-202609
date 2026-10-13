
$S_{\mu} = \frac{1}{N}\sum\limits_{n = 1}^{N}x_{n}$

![Equation](images/B9780443292385000093/si195.png)

是参数 $\mu$ 的充分统计量。

联合 PDF 由下式给出

$p(\mathcal{X};\mu) = \frac{1}{{(2\pi\sigma^{2})}^{\frac{N}{2}}}\exp\left( - \frac{1}{2\sigma^{2}}\sum\limits_{n = 1}^{N}{(x_{n} - \mu)}^{2} \right).$

![Equation](images/B9780443292385000093/si196.png)

代入显而易见的恒等式

$\sum\limits_{n = 1}^{N}{(x_{n} - \mu)}^{2} = \sum\limits_{n = 1}^{N}{(x_{n} - S_{\mu})}^{2} + N{(S_{\mu} - \mu)}^{2}$

![Equation](images/B9780443292385000093/si197.png)

到联合 PDF 中，我们得到

$p(\mathcal{X};\mu) = \frac{1}{{(2\pi\sigma^{2})}^{\frac{N}{2}}}\exp\left( - \frac{1}{2\sigma^{2}}\sum\limits_{n = 1}^{N}{(x_{n} - S_{\mu})}^{2} \right)\exp\left( - \frac{N}{2\sigma^{2}}{(S_{\mu} - \mu)}^{2} \right),$

![Equation](images/B9780443292385000093/si198.png)

根据因式分解定理，这证明了该断言。
