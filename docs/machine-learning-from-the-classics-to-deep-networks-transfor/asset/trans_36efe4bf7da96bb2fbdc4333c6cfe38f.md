

$$
\mathcal{F}(q,\mathbf{\xi}) = \ln p(\mathcal{X};\mathbf{\xi}) + \int q(\mathcal{X}^{l},\mathbf{\theta})\ln\frac{p(\mathcal{X}^{l},\mathbf{\theta}|\mathcal{X};\mathbf{\xi})}{q(\mathcal{X}^{l},\mathbf{\theta})}\ d\mathcal{X}^{l}\ d\mathbf{\theta},
$$

![Equation](images/B9780443292385000196/si6.png)(13.2)

由此可得

$$
\ln p(\mathcal{X};\boldsymbol{\xi}) = \mathcal{F}(q,\boldsymbol{\xi}) + \text{KL}(q(\mathcal{X}^{(l)},\boldsymbol{\theta})||p(\mathcal{X}^{(l)},\boldsymbol{\theta}|\mathcal{X};\boldsymbol{\xi})).
$$

![Equation](images/B9780443292385000196/si7.png)

与公式 [(12.67)](#Chp012_583-634_B9780443292385000184.xhtml) 的区别在于，在我们当前的设定中，后验概率 $p(\mathcal{X}^{(l)},\boldsymbol{\theta}|\mathcal{X};\boldsymbol{\xi})$ *不* 假定为已知；因此，为了使泛函值最大化，将库尔巴克-莱布勒（KL）散度 $\text{KL}(q(\mathcal{X}^{(l)},\boldsymbol{\theta})||p(\mathcal{X}^{(l)},\boldsymbol{\theta}|\mathcal{X};\boldsymbol{\xi}))$ 设为零已不再可能。唯一的替代方案是求助于关于 $q$ 的泛函形式的计算上可处理的近似，这将允许对泛函关于 $q$（以及关于非随机参数 $\boldsymbol{\xi}$）进行优化。

关于函数优化泛函在数学上被称为*变分法*。该问题最简单的例子是计算连接曲面上两点的测地线。对该领域的巩固做出重大突破性贡献的两位数学家是瑞士裔德国数学家莱昂哈德·欧拉（1707–1783）和意大利出生的数学家兼天文学家约瑟夫-路易·拉格朗日（1736–1813）。有趣的是，拉格朗日继欧拉之后担任柏林普鲁士科学院数学部主任。

