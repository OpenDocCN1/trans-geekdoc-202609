

#### 1.1.3 信息论公式

$$H\left( {Y \mid X} \right) = - \sum\limits_{i = 1}^{2}{\sum\limits_{j = 1}^{2}{p\left( {x_{i},y_{j}} \right)}}\ \ln\ \left( { p\left( {y_{i} \mid x_{j}} \right)} \right) = 0.454$$

(1.14)

$$I\left( {X,Y} \right) = I\left( {Y,X} \right) = \sum\limits_{i = 1}^{2}{\sum\limits_{j = 1}^{2}{p\left( {x_{i},y_{j}} \right)}}\ \ln\ \left( \frac{ p\left( {y_{i},x_{j}} \right)}{p\left( y_{i} \right)p\left( x_{j} \right)} \right) = 0.032$$

(1.15)

$$H\left( X \right) = - \sum\limits_{j = 1}^{2}{p\left( x_{j} \right)\ \ln\ \left( { p\left( x_{j} \right)} \right) = 0.688}$$

(1.16)

$$H\left( Y \right) = - \sum\limits_{j = 1}^{2}{p\left( y_{j} \right)\ \ln\ \left( { p\left( y_{j} \right)} \right) = 0.486}$$

(1.17)

$$I(X,Y) = H(X) - H(X\mid Y) = H(Y) - H(Y\mid X) = 0.032$$

(1.18)

$$H(X,Y) = H(X) + H(Y\mid X) = H(Y) + H(X\mid Y) = 1.142$$

(1.19)

如果随机变量 $X$ 和 $Y$ 不独立，互信息 $I(X,Y)$ 为正数。使用表 [1.1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1t1)–[1.3](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1t3)，你会发现使用均匀硬币和均匀骰子的赌博机的互信息 $I(X,Y)$ 等于零。在第 [6](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6) 章中，互信息 $I(X,Y)$ 将使我们能够控制生成什么图像。

#### 1.1.4 詹森不等式

如果函数 $g(x)$ 在范围 $x \in X$ 内是**凸函数**，且 $E[g(X)]$ 和 $g[E(X)]$ 有限，则该范围内函数值的平均值大于或等于 $X$ 的平均值处的函数值：$E[g(X)] \geqslant g[E(X)]$。$x$ 的 PDF 可以是正态分布或其他类型的分布。

**示例 01**：存在凸函数 $g(x) = x^2$，其中 $x \in [-1,1]$ 且 PDF $p(x) = 1/2$

$$\mu = E_{p}\left\lbrack X \right\rbrack = \overline{X} = \int_{- 1}^{1}{x p\left( x \right) dx = 0}, g\left( {E_{p}\left\lbrack X \right\rbrack} \right) = \left( \mu \right)^{2} = 0$$

$$E_{p}\left\lbrack {g\left( X \right)} \right\rbrack = \overline{X^{2}} = \int_{- 1}^{1}x^{2}p\left( x \right) dx = \frac{1}{3}, E_{p}\left\lbrack {g\left( X \right)} \right\rbrack \geqslant g\left( {E_{p}\left\lbrack X \right\rbrack} \right)$$

**示例 02**：存在另一个凸函数 $g(x) = -\ln(x)$，其中 $x \in [0.5, 4.5]$ 且 PDF $p(x) = 1/4$

$$\mu = E_{p}\left\lbrack X \right\rbrack = \int_{0.5}^{4.5}{x p\left( x \right) dx} = \frac{5}{2}, g(E_{p}\left\lbrack X \right\rbrack) = - \ln\left( \mu \right) = - \ln\left( \frac{5}{2} \right) = - 0.92$$

$$E_{p}\left[g(X)\right] = -\int_{0.5}^{4.5} \ln(x) p(x) dx = -0.78, E_{p}\left[g(X)\right] \geq g(E_{p}\left[X\right])$$

#### 1.1.5 最大似然估计与过拟合

在机器学习中，我们需要了解数据集的概率密度函数以进行图像生成。从数据集的 PDF，我们可以生成新数据（图像）。在大多数情况下，我们只有数据（图像），如何找到隐藏在数据集中的 PDF？最大似然估计（MLE）是一种方法，如果我们有一组数据 $\{x[i]\}$，其中 $i = 1, 2, \dots, n$，它允许我们在数据集中找到一个 PDF。例如，数据集是关于学生身高的，且数据集中的数据遵循高斯分布 $N(x;\mu,\sigma)$。使用 MLE，我们将找到 PDF 的参数：$\mu$ 和 $\sigma$。似然是已发生事件的概率，该事件具有未知的 PDF。学生的身高 $x[i]$ 是来自似然函数 $N(x;\mu,\sigma)$ 的一个样本，其中每个学生的身高是独立的。似然函数是数据集的联合概率：

$${likelihood}\left( {\mu,\sigma^{2} \mid x_{1},x_{2},\ldots x_{n}} \right) = \prod\limits_{i = 1}^{n}N(x_{i};\mu,\sigma^{2})$$

(1.20)

上述似然函数应通过优化其两个参数 $\mu$ 和 $\sigma^2$ 来最大化。为了在 Python 和 PyTorch 编码环境中获得数学上的便利，我们需要最小化负对数似然，并将其用作**损失函数** $L = - \ln\left( {\prod\limits_{i = 1}^{n}{N(x_{i};\mu,\sigma^{2})}} \right)$，如公式 ([1.21](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn21)) 所示。然后从 $\partial L/\partial \mu = 0$ 和 $\partial L/\partial \sigma = 0$，很容易得到 PDF 的均值 $\mu = \overline{X}$，和方差 $\sigma^2 = \overline{X^{2}} - {\overline{X}}^{2}$。

$$L = \frac{n}{2}\ \ln\left( {2\pi} \right) + \frac{n}{2}\ \ln\left( \sigma^{2} \right) + \frac{1}{2\sigma^{2}}\sum\limits_{i = 1}^{n}\left( {x_{i} - \mu} \right)^{2}$$

(1.21)

均方误差（MSE）损失函数可以从最大似然估计推导得出。对于一组数据对 $\{x[i], y[i]\}$，我们假设给定 $x[i]$ 的每个目标 $y[i]$ 是来自独立高斯分布 $p[i](y[i]\mid x[i]) = \mathcal{N}(y[i];\mu[i], \sigma^2)$ 的随机数。所有这些高斯分布具有相同的方差 $(\sigma^2 = 1/\beta)$，其中 $\beta$ 称为“精度”，每个高斯分布的均值是目标 $y[i]$ 的预测值 $(\mu[i])$，其中 $i = 1, 2, \dots, n$。我们假设 $\mu$ 是权重的线性函数：$\mu_{i} = f\left( {x_{i},W} \right) = w_{0} + \sum\limits_{j = 1}^{m}{w_{j}x_{i}^{j}}$ 或 $\mu = X \cdot W$。

$$\begin{bmatrix} \mu_{1} \\ \mu_{2} \\ \ldots \\ \mu_{n} \\ \end{bmatrix} = \begin{bmatrix} 1 & x_{1} & \ldots & x_{1}^{m} \\ 1 & x_{2} & \ldots & x_{2}^{m} \\ \ldots & \ldots & \ldots & \ldots \\ 1 & x_{n} & \ldots & x_{n}^{m} \\ \end{bmatrix} \cdot \begin{bmatrix} w_{0} \\ w_{1} \\ \ldots \\ w_{m} \\ \end{bmatrix}$$

(1.22)

