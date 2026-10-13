

## 目标函数与损失函数

$$J(f) = \sum_{n = 1}^{N}\mathcal{L}\left( y_{n},f(\mathbf{x}_{n}) \right)$$

![Equation](images/B9780443292385000172/si315.png)

其中

$$y_{n} = \begin{cases} + 1, & \quad\text{if}\quad\mathbf{x}_{n} \in \omega_{1}, \\ - 1, & \quad\text{if}\quad\mathbf{x}_{n} \in \omega_{2}. \end{cases}$$

![Equation](images/B9780443292385000172/si316.png)

对于二分类任务，首先想到的损失函数是

$$\mathcal{L}\left( y,f(\mathbf{x}) \right) = \begin{cases} 1, & \quad\text{if}\quad yf(\mathbf{x}) \leqslant 0, \\ 0, & \quad\text{otherwise}, \end{cases}$$

![Equation](images/B9780443292385000172/si317.png)(11.58)

这也被称为 **(0, 1)-损失函数**。然而，这是一个不连续函数，其优化是一项艰巨的任务。为此，采用了许多替代损失函数来近似 **(0, 1)-损失函数**。回顾一下，平方误差损失也可以使用，但正如第 [3](#Chp003_65-117_B9780443292385000093.xhtml) 章和第 [7](#Chp007_293-342_B9780443292385000135.xhtml) 章已经指出的那样，这不太适合分类任务，且与 **(0, 1)-损失函数** 差异很大。在本节中，我们将关注所谓的 *hinge*（合页）损失函数，其定义如下（第 [8](#Chp008_343-416_B9780443292385000147.xhtml) 章）：

$$\mathcal{L}_{\rho}(y,f(\mathbf{x})) = \max \{0,\rho - y f(\mathbf{x})\}.$$

![Equation](images/B9780443292385000172/si319.png)(11.59)

换句话说，如果真实标签 ($y$) 与判别函数值 ($f(\mathbf{x})$) 预测值的乘积为正且大于阈值/边界值 $\rho \ge 0$（用户定义），则损失为零。否则，损失呈线性增长。如果 $y f(\mathbf{x})$ 无法达到至少 $\rho$ 的值，我们称犯了一个边界错误。*Hinge* 损失函数如 [图 11.13](#Chp011_519-582_B9780443292385000172.xhtml#f0070) 所示，图中还展示了 **(0, 1)-损失函数** 和平方误差损失函数。

