

$w(\mathbf{x}) := \frac{\phi(\mathbf{x})}{q(\mathbf{x})}$.

![Equation](images/B9780443292385000202/si133.png) (14.26)

归一化常数可以很容易地得到为

$$
Z = \int_{-\infty}^{\infty} \phi(\mathbf{x}) \, d\mathbf{x} = \int_{-\infty}^{\infty} \left( \frac{\phi(\mathbf{x})}{q(\mathbf{x})} \right) q(\mathbf{x}) \, d\mathbf{x} \approx \frac{1}{N} \sum_{i=1}^{N} w(\mathbf{x}_i).
$$

![Equation](images/B9780443292385000202/si134.png) (14.27)

结合公式 [(14.25)](#Chp014_717-754_B9780443292385000202.xhtml#deq47) 和 [(14.27)](#Chp014_717-754_B9780443292385000202.xhtml#deq49)，我们最终得到

$$
\mathbb{E}\left[ f(\mathbf{x}) \right] \approx \frac{\sum_{i=1}^{N} w(\mathbf{x}_i) f(\mathbf{x}_i)}{\sum_{i=1}^{N} w(\mathbf{x}_i)},
$$

![Equation](images/B9780443292385000202/si135.png) (14.28)

或者

![Equation](images/B9780443292385000202/fx001.jpg)

其中 $W(\mathbf{x}_i) = \frac{w(\mathbf{x}_i)}{\sum_{i=1}^{N} w(\mathbf{x}_i)}$ 为归一化权重。不难证明（问题 [14.6](#Chp014_717-754_B9780443292385000202.xhtml#o0035)），估计量

$$
\widehat{Z} = \frac{1}{N} \sum_{i=1}^{N} w(\mathbf{x}_i)
$$

![Equation](images/B9780443292385000202/si137.png) (14.29)

对应于归一化常数的无偏估计量。这非常有趣，因为计算归一化常数在许多任务中是特别有用的信息。回顾一下第 [12](#Chp012_583-634_B9780443292385000184.xhtml) 章讨论的证据函数，它就是一个归一化常数；另见文献 [26] 的相关评论。

