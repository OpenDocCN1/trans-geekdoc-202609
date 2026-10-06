

## 8 非线性输入变换与核

推导矩阵等式（push-through matrix identity）表明，对于任何矩阵 $A$，$A(A^\top+I)^{-1} = (AA^\top+I)^{-1}A$ 成立。通过在 (8.6) 中使用该等式，我们可以重写 $\widetilde{Y}(\mathbf{x}_*)$

$$\widetilde{Y}(\mathbf{x}_*) = \frac{\mathbf{y}^\top\Phi(\mathbf{x})}{n} (\Phi(\mathbf{x})^\top\Phi(\mathbf{x}) + n\mathbf{I})^{-1}\Phi(\mathbf{x})^\top\phi(\mathbf{x}_*) \quad (8.7)$$

在 (8.7) 中似乎我们不需要处理任何 $d$ 维向量或矩阵就可以计算 $\phi(\mathbf{x}_*)$，或者说 (8.7) 中的矩阵乘法 $\Phi(\mathbf{x})\Phi(\mathbf{x})^\top$ 和 $\Phi(\mathbf{x})^\top\phi(\mathbf{x})$ 是是可以被计算的。让我们仔细观察一下：

$$\Phi(\mathbf{x})\Phi(\mathbf{x})^\top = \begin{bmatrix} \phi(x_1)^\top\phi(x_1) & \phi(x_1)^\top\phi(x_2) & \dots \\ \phi(x_2)^\top\phi(x_1) & \phi(x_2)^\top\phi(x_2) & \dots \\ \vdots & \vdots & \vdots \\ \phi(x_n)^\top\phi(x_1) & \phi(x_n)^\top\phi(x_2) & \dots \end{bmatrix} \quad \text{and} \quad \begin{bmatrix} \phi(x_1)^\top\phi(x_n) \\ \phi(x_2)^\top\phi(x_n) \\ \vdots \\ \phi(x_n)^\top\phi(x_n) \end{bmatrix} \quad (8.8)$$

记住 $\phi(\mathbf{x})^\top\phi(\mathbf{x}')$ 是 $d$ 维向量 $\phi(\mathbf{x})$ 和 $\phi(\mathbf{x}')$ 之间的内积。关键洞察在于，变换后的输入 $\phi(\mathbf{x})$ 仅以内积 $\phi(\mathbf{x})^\top\phi(\mathbf{x}')$ 的形式进入 (8.7)，其中每个内积都是标量。也就是说，如果我们能够直接计算内积 $\phi(\mathbf{x})^\top\phi(\mathbf{x}')$，而无需先计算 $d$ 维的 $\phi(\mathbf{x})$，我们就达到了我们的目标。

作为一个具体的说明，让我们简化考虑多项式。当 $p=1$（意味着 $x$ 是一个标量），且 $x$ 是一个阶为 $(d=4)$ 的多项式，且第二、第三项被 $\sqrt{3}$ 缩放时，我们有：

$$\phi(\mathbf{x})^\top\phi(\mathbf{x}') = [ \begin{bmatrix} 1 & \sqrt{3}x & \sqrt{3}x^2 & \sqrt{3}x^3 \end{bmatrix}^\top \begin{bmatrix} 1 \\ \sqrt{3}x' \\ \sqrt{3}(x')^2 \\ \sqrt{3}(x')^3 \end{bmatrix} = 1 + 3xx' + 3x^2(x')^2 + x^3(x')^3 = (1+xx')^3 ] \quad (8.10)$$

可以证明，如果 $\phi(\mathbf{x})$ 是（经过缩放的）阶为 $d-1$ 的多项式，那么 $\phi(\mathbf{x})^\top\phi(\mathbf{x}') = (1+xx')^d$。我们提出的观点是，与其先计算 $d$ 维向量 $\phi(\mathbf{x})$ 和 $\phi(\mathbf{x}')$ 然后计算它们的内积，我们不如直接评估表达式 $(1+xx')^d$。对于二次或三阶多项式，这可能差别不大，但在 $d$ 达到数百或数千的情况下，这种计算上的节省将意义重大。

我们要表达的核心点是，如果我们选择 $\phi(\mathbf{x})$ 使得内积 $\phi(\mathbf{x})^\top\phi(\mathbf{x}')$ 可以在不计算 $\phi(\mathbf{x})$ 的情况下计算出来，我们就使得定义无限维向量之间的内积成为可能，没有什么能阻止我们的学习。

缩放因子 $\sqrt{3}$ 可以通过 $\theta$ 中第二个和第三元素的反向缩放来补偿。

> 《Machine Learning — A First Course for Engineers and Scientists》的草案（2021 年 4 月 30 日）。http://mlbook.org
> Andreas Lindholm, Niklas Wahliford, Fredrik Lindstein, and Thomas B. Schön. 2021.

## 8.2 核岭回归

核函数 $\kappa(x, x')$（在本书中）取来自同一空间的两个参数 $x$ 和 $x'$ 并返回一个标量。在整本书中，我们仅限于实值且对称的核，即对于所有 $x$ 和 $x'$，$\kappa(x, x') = \kappa(x', x)$。例如，方程 (8.10) 就是这样一个核。更一般地说，两个非线性变换的内积是一个核：

$$\kappa(x, x') = \phi(x)^\top \phi(x'). \quad (8.11)$$

此阶段的重要点是，$\phi(x)$ 仅通过内积出现在线性回归模型 (8.7) 中，我们不需要设计一个 $d$ 维向量 $\phi(x)$ 并推导其内积。相反，我们可以直接选择一个核 $\kappa(x, x')$，这就是核技巧（kernel trick）。

- 如果 $x$ 仅以 $\phi(x)^\top \phi(x')$ 的形式进入，我们可以选择核 $\kappa(x, x')$ 而不是选择 $\phi(x)$。

为了明确我们在实践中的意图，我们将 (8.7) 写为 (8.12)：

$$\hat{y}(x^*) = y^\top (K(x^*, x^*) + n\lambda I)^{-1} K(x, x^*). \quad (8.12a)$$

$$K(X, X) = \begin{bmatrix} \kappa(x_1, x_1) & \kappa(x_1, x_2) & \dots & \kappa(x_1, x_n) \\ \kappa(x_2, x_1) & \kappa(x_2, x_2) & \dots \\ \vdots & \vdots & \vdots & \vdots \\ \kappa(x_n, x_1) & \kappa(x_n, x_2) & \dots \end{bmatrix} \quad (8.12b)$$

$$\hat{y}(x^*) = y^\top \begin{bmatrix} \kappa(x^*, x_1) & \kappa(x^*, x_2) & \dots & \kappa(x^*, x_n) \end{bmatrix} \quad (8.12c)$$

