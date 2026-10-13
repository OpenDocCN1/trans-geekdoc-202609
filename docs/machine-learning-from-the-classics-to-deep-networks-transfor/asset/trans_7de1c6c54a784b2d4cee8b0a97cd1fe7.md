

### 参数估计的优化问题

$$f(\cdot) := f_{\boldsymbol{\theta}_*}(\cdot):\quad \boldsymbol{\theta}_* = \text{arg}\min_{\boldsymbol{\theta} \in \mathcal{A}} J(\boldsymbol{\theta}), \tag{3.5}$$

其中

$$J(\boldsymbol{\theta}) := \sum_{n=1}^{N} \mathcal{L}\left(y_n, f_{\boldsymbol{\theta}}(\mathbf{x}_n)\right), \tag{3.6}$$

假设最小值存在。请注意，通常可能存在多个最优值 $\boldsymbol{\theta}_*$，这取决于 $J(\boldsymbol{\theta})$ 的形状。

随着本书的深入，我们将看到不同的损失函数和不同的函数参数族。为求简化，本章其余部分我们将坚持使用*平方误差*损失函数，

$$\mathcal{L}(y, f_{\boldsymbol{\theta}}(\mathbf{x})) = (y - f_{\boldsymbol{\theta}}(\mathbf{x}))^2, \tag{3.7}$$

以及线性函数类。

平方误差损失函数归功于伟大的数学家卡尔·弗里德里希·高斯（1777–1855），他在 1795 年年仅 18 岁时提出了最小二乘（LS）法的基础。然而，是阿德里安-马里·勒让德（1752–1833）于 1805 年首次独立发表了该方法。高斯于 1809 年发表了该方法。当该方法被用于预测小行星谷神星的位置时，其威力得到了展示。从那时起，平方误差损失函数就“萦绕”在所有科学领域，即使不直接使用，它最常被用作衡量更现代替代方法性能的标准。这种成功归功于该损失准则所具备的一些良好特性，我们将在本书后续内容中探讨这些特性。

线性与平方误差损失函数的结合选择恰好简化了代数运算，因此非常适合引导初学者了解参数估计领域潜在的各种“奥秘”。此外，理解线性非常重要。处理非线性任务最终往往归结为一个线性问题。以公式 (3.2) 中的非线性模型为例，并考虑变换

$$\mathbb{R} \ni x \longmapsto \boldsymbol{\phi}(x) := \begin{bmatrix} x \\ x^{2} \end{bmatrix} \in \mathbb{R}^{2}. \tag{3.8}$$

那么公式 (3.2) 变为

