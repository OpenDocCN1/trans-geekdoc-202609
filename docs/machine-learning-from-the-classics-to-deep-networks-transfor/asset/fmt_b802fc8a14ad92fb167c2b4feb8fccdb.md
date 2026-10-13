
### 数学公式推导

$$
a_{1} = a + \sum\limits_{n = 1}^{n_{0}}x_{n},\quad b_{1} = b + n_{0}.p(\lambda_{2}|n_{0},\lambda_{1},\mathbf{x}_{1:N}) = \text{Gamma}(\lambda_{2}|a_{2},b_{2}),a_{2} = a + \sum\limits_{n = n_{0} + 1}^{N}x_{n},\quad b_{2} = b + (N - n_{0}),
$$

![Equation](images/B9780443292385000202/si338.png)(14.54)

with

$$
P(n_{0}|\lambda_{1},\lambda_{2},\mathbf{x}_{1:N}) = \ln\lambda_{1}\sum\limits_{n = 1}^{n_{0}}x_{n} - n_{0}\lambda_{1} + \ln\lambda_{2}\sum\limits_{n = n_{0} + 1}^{N}x_{n} - (N - n_{0})\lambda_{2} + C,\quad n_{0} = 1,2,\ldots,N.
$$

![Equation](images/B9780443292385000202/si339.png)(14.55)

注意，前两个条件分布服从伽马分布，正如我们在[第14.4节](#Chp014_717-754_B9780443292385000202.xhtml#s0030)末尾所述，有多种不同的方法可用于从中生成样本。最后一个分布是离散分布，可以按照[算法14.1](#Chp014_717-754_B9780443292385000202.xhtml#enun0025)中讨论的方法抽取样本。我们现在准备好应用吉布斯采样了。

### 算法 14.5
