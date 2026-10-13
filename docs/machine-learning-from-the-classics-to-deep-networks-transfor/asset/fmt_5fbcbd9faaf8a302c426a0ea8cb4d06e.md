
## 数学推导与共轭先验分析

### 基础函数定义

$$f(x) = \frac{1}{\sqrt{2\pi}},\quad \phi(\beta) = -\beta,\quad u(x) = \frac{1}{2}(x - \mu)^2$$

![Equation](images/B9780443292385000184/si314.png)

### 归一化常数计算

$$g(\beta) = \frac{1}{\int_{-\infty}^{+\infty}\frac{1}{\sqrt{2\pi}}\exp\left( -\frac{1}{2}\beta(x - \mu)^2 \right)dx} = \beta^{1/2}$$

![Equation](images/B9780443292385000184/si315.png)

### 共轭先验分布

**2.** 方程 [(12.78)](#Chp012_583-634_B9780443292385000184.xhtml#deq102) 的共轭先验服从伽马分布。

方程 [(12.74)](#Chp012_583-634_B9780443292385000184.xhtml#deq98) 对应的共轭先验变为：

$$p(\beta;\lambda,v) = h(\lambda,v)\beta^{\frac{\lambda}{2}}\exp(-\beta v)$$

![Equation](images/B9780443292385000184/si316.png) (12.80)

### 伽马分布形式

其形式为：

$$\text{Gamma}(\beta|a,b) = \frac{1}{\Gamma(a)}b^{a}\beta^{a - 1}\exp(-b\beta)$$

![Equation](images/B9780443292385000184/si317.png) (12.81)

### 参数定义

参数为（参见第 [2](#Chp002_19-64_B9780443292385000081.xhtml) 章）：

$$a = \frac{\lambda}{2} + 1$$

![Equation](images/B9780443292385000184/si318.png)

$$b = v$$

![Equation](images/B9780443292385000184/si319.png)

归一化常数 $h(\lambda,v)$ 必然等于：

$$\frac{b^a}{\Gamma(a)}$$

![Equation](images/B9780443292385000184/si320.png) ![Equation](images/B9780443292385000184/si321.png)

函数 $\Gamma(a)$ 定义为：

$$\Gamma(a) = \int_{0}^{\infty} x^{a-1} e^{-x} dx$$

![Equation](images/B9780443292385000184/si323.png)
