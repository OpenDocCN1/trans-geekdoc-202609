

![](img/ca72c1626f4850f058a9edc138c1ac73_856_0.png)

图 23.2：耦合层示意图 \(\boldsymbol{x} = f(\boldsymbol{u})\)。将由 \(\boldsymbol{u}^B\) 决定参数的双切映射应用于 \(\boldsymbol{u}^A\) 以生成 \(\boldsymbol{x}^A\)；与此同时，\(\boldsymbol{x}^B = \boldsymbol{u}^B\) 保持不变地传递，因此该映射是可逆的。来自 [KPB19] 的图 3。获得 Ivan Kobyzev 的友好许可使用。

从 \(x_{k-1}\) 到 \(x_k\)，使用多项式或有理函数（两个多项式的比值）。通过增加节点的数量，我们可以创建任意灵活的单调函数。

节点之间的不同插值方式会产生不同类型的样条。一种简单的选择是线性插值 [Mül+19a]。然而，这会导致导数在节点处不连续。使用二次多项式插值 [Mül+19a] 提供了足够的灵活性来使导数连续。使用三次多项式 [Dur+19]、线性多项式之比 [DEL20] 或二次多项式之比 [DBP19] 的插值允许节点处的导数为任意参数。

如果采用 \(u_{k-1} < u_k, x_{k-1} < x_k\)，并确保节点间的插值本身是递增的，则样条是严格递增的。取决于插值函数的灵活性，可能存在多个插值；在实践中，我们选择保证始终递增的那个（有关详细信息，请参见上述参考文献）。

样条的一个优点是，如果插值函数仅包含低次多项式，则可以解析地对其求逆。在这种情况下，我们按如下方式计算 \(u = h^{-1}(x)\)：首先，我们使用二分查找定位 \(x\) 所在的区间 \((x_{k-1}, x_k)\)；然后，我们解析地求解得到的低次多项式以得到 \(u\)。

## 23.2.3 耦合流

在本节中，我们描述耦合流，它允许我们使用任意非线性函数（如深度神经网络）来对维度之间的依赖关系进行建模。考虑将输入 \(\boldsymbol{u} \in \mathbb{R}^D\) 划分为两个子空间，\((\boldsymbol{u}^A, \boldsymbol{u}^B) \in \mathbb{R}^d \times \mathbb{R}^{D-d}\)，其中 \(d\) 是 1 到 \(D-1\) 之间的整数。假设有一个由 \(\boldsymbol{\theta}\) 参数化且作用于子空间 \(\mathbb{R}^d\) 的双切映射 \(\hat{\boldsymbol{f}}(\cdot; \boldsymbol{\theta}) : \mathbb{R}^d \rightarrow \mathbb{R}^d\)。我们定义函数 \(\boldsymbol{f} : \mathbb{R}^D \rightarrow \mathbb{R}^D\)，由 \(\boldsymbol{x} = \boldsymbol{f}(\boldsymbol{u})\) 给出，如下所示：

\(\boldsymbol{x}^A = \hat{\boldsymbol{f}}(\boldsymbol{u}^A; \Theta(\boldsymbol{u}^B)) \qquad (23.12)\)
\(\boldsymbol{x}^B = \boldsymbol{u}^B. \qquad (23.13)\)

请参见图 23.2 了解示意图。函数 \(\boldsymbol{f}\) 被称为**耦合层** [DKB15; DSDB17]，因为它通过 \(\hat{\mathbf{f}}\) 和 \(\Theta\) 将 \(\boldsymbol{u}^A\) 和 \(\boldsymbol{u}^B\) “耦合”在一起。我们将由耦合层组成的流称为**耦合流**。

\(\hat{\mathbf{f}}\) 的参数由 \(\boldsymbol{\theta} = \Theta(\mathbf{u}^B)\) 计算得出，其中 \(\Theta\) 是一个称为**条件器**的*任意*函数。与以线性方式混合维度的仿射流以及完全不混合维度的逐元素流不同，耦合流可以使用灵活的非线性条件器 \(\Theta\) 来混合维度。在实践中，我们通常将 \(\Theta\) 实现为深度神经网络；可以使用任何架构，包括 MLP、CNN、ResNet 等。

耦合层 \(\mathbf{f}\) 是*可逆*的，其逆由 \(\mathbf{u} = \mathbf{f}^{-1}(\mathbf{x})\) 给出，其中

\(\mathbf{u}^A = \hat{\mathbf{f}}^{-1}(\mathbf{x}^A; \Theta(\mathbf{x}^B)) \tag{23.14}\)
\(\mathbf{u}^B = \mathbf{x}^B. \tag{23.15}\)

也就是说，\(\mathbf{f}^{-1}\) 只需将 \(\hat{\mathbf{f}}\) 替换为 \(\hat{\mathbf{f}}^{-1}\) 即可得到。由于 \(\mathbf{x}^B\) 不依赖于 \(\mathbf{u}^A\)，\(\mathbf{f}\) 的雅可比矩阵是分块三角矩阵：

\(\mathbf{J}(\mathbf{f}) = \begin{pmatrix} \partial \mathbf{x}^A / \partial \mathbf{u}^A & \partial \mathbf{x}^A / \partial \mathbf{u}^B \\ \partial \mathbf{x}^B / \partial \mathbf{u}^A & \partial \mathbf{x}^B / \partial \mathbf{u}^B \end{pmatrix} = \begin{pmatrix} \mathbf{J}(\hat{\mathbf{f}}) & \partial \mathbf{x}^A / \partial \mathbf{u}^B \\ \mathbf{0} & \mathbf{I} \end{pmatrix}. \tag{23.16}\)

因此，\(\text{det} \mathbf{J}(\mathbf{f})\) 等于 \(\text{det} \mathbf{J}(\hat{\mathbf{f}})\)。

我们通常将 \(\hat{\mathbf{f}}\) 定义为逐元素双切映射，以便 \(\hat{\mathbf{f}}^{-1}\) 和 \(\text{det} \mathbf{J}(\hat{\mathbf{f}})\) 易于计算。也就是说，我们定义：

\(\hat{\mathbf{f}}(\mathbf{u}^A; \boldsymbol{\theta}) = (h(u_1^A; \theta_1), \dots, h(u_d^A; \theta_d)) , \tag{23.17}\)

其中 \(h(\cdot; \theta_i)\) 是由 \(\theta_i\) 参数化的标量双切映射。本节 23.2.2 中描述的任何标量双切映射均可在此处使用。例如，\(h(\cdot; \theta_i)\) 可以是具有缩放和平移参数 \(\theta_i\) 的仿射双切映射（第 23.2.2.1 节）；或者可以是具有权重和偏置 \(\theta_i\) 的单调 MLP（第 23.2.2.3 节）；或者可以是具有节点坐标 \(\theta_i\) 的单调样条（第 23.2.2.5 节）。

定义 \(\mathbf{u}\) 到 \((\mathbf{u}^A, \mathbf{u}^B)\) 的划分有多种方法。一种简单的方法是将 \(\mathbf{u}\) 划分为两半。我们还可以利用划分中的空间结构。例如，如果 \(\mathbf{u}\) 是图像，我们可以使用“棋盘”模式对其像素进行划分，其中“黑色方格”中的像素位于 \(\mathbf{u}^A\)，而“白色方格”中的像素位于 \(\mathbf{u}^B\) [DSDB17]。由于每个耦合层仅转换部分输入，在实践中，我们通常沿耦合流采用不同的划分，以确保所有变量都得到转换并有机会进行交互。

最后，如果 \(\hat{\mathbf{f}}\) 是逐元素双切映射，我们可以使用二进制掩码 \(\mathbf{b}\) 按如下方式轻松实现任意划分：

\(\mathbf{x} = \mathbf{b} \odot \mathbf{u} + (1 - \mathbf{b}) \odot \hat{\mathbf{f}}(\mathbf{u}; \Theta(\mathbf{b} \odot \mathbf{u})), \tag{23.18}\)

其中 \(\odot\) 表示逐元素乘法。\(\mathbf{b}\) 中值为 0 表示 \(\mathbf{u}\) 中的相应元素被转换（属于 \(\mathbf{u}^A\)）；值为 1 表示该元素保持不变（属于 \(\mathbf{u}^B\)）。

作为示例，我们将由分段有理二次样条创建的掩码耦合流拟合到两月亮数据集。拟合模型中每层的样本如图 23.3 所示。

## 23.2.4 自回归流

在本节中，我们讨论**自回归流**，它们是由自回归双切映射组成的流。与耦合流类似，自回归流允许我们使用任意非线性函数（如深度神经网络）来对变量之间的依赖关系进行建模。

![](img/ca72c1626f4850f058a9edc138c1ac73_858_0.png)

图 23.3：（a）两月亮数据集。（b）拟合到此数据集的标准化流样本。由 two_moons_nsf_normalizing_flow.ipynb 生成。

假设输入 \(\boldsymbol{u}\) 包含 \(D\) 个标量元素，即 \(\boldsymbol{u} = (u_1, ..., u_D) \in \mathbb{R}^D\)。我们定义一个**自回归双切映射** \(\mathbf{f}: \mathbb{R}^D \rightarrow \mathbb{R}^D\)，其输出表示为 \(\boldsymbol{x} = (x_1, ..., x_D) \in \mathbb{R}^D\)，如下所示：

\(\begin{array}{ c c }
x_i = h(u_i; \Theta_i(\boldsymbol{x}_{1:i-1})), & i = 1, ..., D. \\
\end{array}\) (23.19)

每个输出 \(x_i\) 取决于相应的输入 \(u_i\) 和所有先前的输出 \(\boldsymbol{x}_{1:i-1} = (x_1, ..., x_{i-1})\)。函数 \(h(\cdot; \boldsymbol{\theta}) : \mathbb{R} \rightarrow \mathbb{R}\) 是一个标量双切映射（例如，第 23.2.2 节中描述的一种），并由 \(\boldsymbol{\theta}\) 参数化。函数 \(\Theta_i\) 是一个条件器，它基于所有先前的输出 \(\boldsymbol{x}_{1:i-1}\) 输出生成 \(x_i\) 的参数 \(\boldsymbol{\theta}_i\)。与耦合流一样，\(\Theta_i\) 可以是任意非线性函数，并且通常参数化为深度神经网络。

由于 \(h\) 是可逆的，\(\mathbf{f}\) 也是可逆的，其逆由以下给出：

\(\begin{array}{ c c }
u_i = h^{-1}(x_i; \Theta_i(\boldsymbol{x}_{1:i-1})), & i = 1, ..., D. \\
\end{array}\) (23.20)

\(\mathbf{f}\) 的一个重要属性是，每个输出 \(\boldsymbol{x}_i\) 取决于 \(\boldsymbol{u}_{1:i} = (u_1, ..., u_i)\)，但不取决于 \(\boldsymbol{u}_{i+1:D} = (u_{i+1}, ..., u_D)\)；因此，当 \(j > i\) 时，偏导数 \(\partial x_i / \partial u_j\) 恒等于零。因此，雅可比矩阵 \(\mathbf{J}(\mathbf{f})\) 是三角矩阵，其行列式只是其对角线元素的乘积：

\(\begin{array}{ c c }
\det \mathbf{J}(\mathbf{f}) = \prod_{i=1}^D \frac{\partial x_i}{\partial u_i} = \prod_{i=1}^D \frac{dh}{du_i}. &  \\
\end{array}\) (23.21)

换句话说，\(\mathbf{f}\) 的自回归结构导致雅可比行列式可以在 \(O(D)\) 时间内高效计算。

虽然可逆，但自回归双切映射在计算上是非对称的：评估 \(\mathbf{f}\) 本质上是顺序的，而评估 \(\mathbf{f}^{-1}\) 本质上是并行的。这是因为我们需要 \(\boldsymbol{x}_{1:i-1}\) 以

