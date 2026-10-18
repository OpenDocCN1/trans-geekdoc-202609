

# PYTHON MACHINE LEARNING

## 使用 Python 进行机器学习

Python 是数据科学中最流行的编程语言之一，因此拥有其优秀社区开发的大量有用的附加库。尽管对于计算密集型任务，像 Python 这样的解释型语言的性能不如低级编程语言，但已经开发了 NumPy 和 SciPy 等扩展库，它们基于底层的 Fortran 和 C 实现，用于对多维数组进行快速且向量化的操作。对于机器学习编程任务，我们主要参考 Scikit-learn 库，它是当今最流行且易于使用的开源机器学习库之一。

## 训练机器学习算法

在本章中，我们将使用最早被算法描述的机器学习分类算法之一，即“感知机”和“自适应线性神经元”。我们将从在 Python 中逐步实现感知机开始，并训练它对 Iris 数据集中的不同花卉物种进行分类。这将帮助我们理解分类机器学习算法的概念，以及如何在 Python 中高效地实现它们。

## 人工神经元——机器学习早期历史的简要回顾

在详细讨论感知机及相关算法之前，让我们简要回顾一下机器学习的早期发展。为了理解生物大脑的工作原理以设计人工智能，Warren McCulloch 和 Walter Pitts 于 1943 年发表了简化脑细胞的第一个概念，即所谓的 McCulloch-Pitts (MCP) 神经元 (W. S. McCulloch 和 W. Pitts. ‘A Logical Calculus of the Ideas Immanent in Nervous Activity’. The Bulletin of Mathematical Biophysics, 5(4):115–133, 1943)。

神经元是大脑中相互连接的神经细胞，参与化学和电信号的处理和传输，如下图所示：McCulloch 和 Pitts 将这种神经元描述为具有二进制输出的简单逻辑门；多个信号到达树突，然后整合到细胞体中，如果累积信号超过某个阈值，就会生成一个输出信号，该信号将由轴突传递。

仅仅几年后，Frank Rosenblatt 基于 MCP 神经元模型发表了感知机学习规则的第一个概念 (F. Rosenblatt, ‘The Perceptron, a Perceiving and Recognizing Automaton’. Cornell Aeronautical Laboratory, 1957)。通过他的感知机规则，Rosenblatt 提出了一种算法，该算法将自动学习最佳权重系数，然后将其与输入特征相乘，以决定神经元是否发火。在监督学习和分类的背景下，这样的算法可以用于预测样本属于哪一类。

更正式地说，我们可以将此问题视为一个二分类任务，为了简单起见，我们将两个类称为 1（正类）和 -1（负类）。我们可以定义一个激活函数 `φ(z)`，它接受某些输入值 `x` 和相应的权重向量 `w` 的线性组合，其中 `z` 是所谓的净输入 (`z = w0x0 + w1x1 + ... + wmxm`)：

`w = [w1, ..., wm]`
`x = [x1, ..., xm]`

现在，如果特定样本 `x(i)` 的激活，即 `φ(z)` 的输出，大于定义的阈值 `θ`，我们预测类 1，如果不大于阈值，我们预测类 -1。在感知机算法中，激活函数 `φ(z)` 是一个简单的单位阶跃函数，有时也被称为 Heaviside 阶跃函数：

`φ(z) = { 1 if z ≥ θ; -1 otherwise }`

为了简单起见，我们可以将阈值 `θ` 移到等式左侧，并定义权重零为 `w0 = −θ` 和 `x0 = 1`，这样我们可以用更紧凑的形式写出 `z = w0x0 + w1x1 + ... + wmxm = w^T x` 和 `φ(z) = { 1 if z ≥ 0; -1 otherwise }`。

在接下来的章节中，我们将经常使用线性代数的基本符号。例如，我们将使用向量点积来缩写 `x` 和 `w` 中值的乘积之和，而上标 `T` 代表转置，即将列向量转换为行向量，反之亦然的操作：

`z = w0x0 + w1x1 + ... + wmxm = ∑(j=0 to m) xj wj = w^T x`

例如：`[1 2 3] · [4 5 6] = 1×4 + 2×5 + 3×6 = 32`。

此外，转置操作也可以应用于矩阵以沿其对角线反射，例如：

`[1 2; 3 4; 5 6]^T = [1 3 5; 2 4 6]`

在本书中，我们只将使用线性代数的非常基本概念。但是，如果您需要快速复习，请查看 Zico Kolter 的优秀线性代数复习与参考，可在 `http://www.cs.cmu.edu/~zkolt/course/linalg/linalg_notes.pdf` 免费获取。

下图说明了感知机的激活函数如何将净输入 `z = w^T x` 压缩为二进制输出（-1 或 1）（左子图），以及如何用于区分两个线性可分类（右子图）：

MCP 神经元和 Rosenblatt 阈值感知机模型背后的整个想法是使用还原论方法来模拟大脑中单个神经元的工作方式：它要么发火，要么不发火。因此，Rosenblatt 最初的感知机规则非常简单，可以由以下步骤总结：

- 将权重初始化为 0 或小随机数。
- 对于每个训练样本 `x(i)`，执行以下步骤：
  - 计算输出值 `ŷ`。
  - 更新权重。

这里，输出值是我们之前定义的单位阶跃函数预测的类标签，权重向量 `w` 中每个权重 `wj` 的同时更新可以更正式地写为：

`wj := wj + ∆wj`

用于更新权重 `wj` 的 `∆wj` 值由感知机学习规则计算：

`∆wj = η( y(i) − ŷ(i) ) x(j,i)`

其中 `η` 是学习率（0.0 到 1.0 之间的常数），`y(i)` 是第 i 个训练样本的真实类标签，`ŷ(i)` 是预测的类标签。需要注意的是，权重向量中的所有权重都在同时更新，这意味着在所有权重 `∆wj` 更新之前，我们不会重新计算 `ŷ(i)`。

具体来说，对于一个 2D 数据集，我们将更新写为：

`∆w0 = η( y(i) − output(i) )`
`∆w1 = η( y(i) − output(i) ) x1(i)`
`∆w2 = η( y(i) − output(i) ) x2(i)`

在 Python 中实现感知机规则之前，这里有一个简单的思想实验来说明这个学习规则是多么简单优雅。在感知机正确预测类标签的两种场景中，权重保持不变：

`∆wj = η(−1 − 1)x(j,i) = 0`
`∆wj = η(1 − 1)x(j,i) = 0`

但是，在预测错误的情况下，权重将分别向正或负目标类的方向推动：

`∆wj = η(1 − (−1))x(j,i) = η(2)x(j,i)`
`∆wj = η(−1 − 1)x(j,i) = η(−2)x(j,i)`

为了更好地理解乘数因子 `x(j,i)`，让我们看另一个简单的例子，其中：

`y(i) = +1`, `ŷ(i) = −1`, `η = 1`

假设 `x(j,i) = 0.5`，我们将此样本错误分类为 -1。在这种情况下，我们将相应的权重增加 1，这样下次遇到此样本时，激活 `x(j,i) × w(j,i)` 将更加正，并且更有可能高于单位阶跃函数的阈值，从而将样本分类为 +1：

`∆w(j,i) = (1 − (−1)) × 0.5 = 2 × 0.5 = 1`

权重更新与 `x(j,i)` 的值成正比。例如，如果我们有另一个样本 `x(j,i) = 2` 被错误分类为 -1，我们将以更大的程度推动决策边界，以便下次正确分类此样本：

`∆wj = (1 − (−1)) × 2 = 2 × 2 = 4`

需要注意的是，感知机的收敛性只有在两个类线性可分且学习率足够小时才能保证。如果两个类无法由线性决策边界分离，我们可以设置遍历训练数据集的最大次数（epochs）和/或可容忍的误分类数量阈值——否则，感知机将永远不会停止更新权重。

现在，在进入下一节的实现之前，让我们用一个简单的图来总结我们刚刚学到的内容，该图说明了感知机的一般概念：

前面的图说明了感知机如何接收样本 `x` 的输入，并将其与权重 `w` 结合以计算净输入。然后将净输入传递给激活函数（这里：单位阶跃函数），该函数生成二进制输出 -1 或 +1——样本的预测类标签。在学习阶段，此输出用于计算预测误差并更新权重。

## 在 Python 中实现感知机学习算法

在上一节中，我们学习了 Rosenblatt 的感知机规则是如何工作的；让我们继续在 Python 中实现它，并将其应用于我们之前介绍的 Iris 数据集。我们将采用面向对象的方法来定义感知机接口作为 Python `Class`，这允许我们初始化新的感知机对象，这些对象可以通过 `fit()` 方法从数据中学习，并通过单独的 `predict()` 方法进行预测。按照惯例，我们为那些在对象初始化时未创建，而是通过调用对象的其他方法创建的属性添加下划线——例如，`self.w_`。

如果您还不熟悉 Python 的科学库或需要复习，请参阅以下资源：

- NumPy: `http://wiki.scipy.org/Tentative_NumPy_Tutorial`
- Pandas: `http://pandas.pydata.org/pandas-docs/stable/tutorials.html`
- Matplotlib: `http://matplotlib.org/users/beginners.html`

另外，为了更好地跟上代码示例，我建议您从 Packt 网站下载 IPython 笔记本。有关 IPython 笔记本的一般介绍，请访问 `https://ipython.org/ipython-doc/3/notebook/index.html`。

```python
import numpy as np

class Perceptron(object):
    """Perceptron classifier.
    Parameters
    -----------
    eta : float
        Learning rate (between 0.0 and 1.0)
    n_iter : int
        Passes over the training dataset.
    Attributes
    ----------
    w_ : 1d-array
        Weights after fitting.
    errors_ : list
        Number of misclassifications in every epoch.
    """
    def __init__(self, eta=0.01, n_iter=10):
        self.eta = eta
        self.n_iter = n_iter

    def fit(self, X, y):
        """Fit training data.
        Parameters
        ----------
        X : {array-like}, shape = [n_samples, n_features]
            Training vectors, where n_samples is the number of samples and
            n_features is the number of features.
        y : array-like, shape = [n_samples]
            Target values.
        Returns
        -------
        self : object
        """
        self.w_ = np.zeros(1 + X.shape[1])
        self.errors_ = []
        for _ in range(self.n_iter):
            errors = 0
            for xi, target in zip(X, y):
                update = self.eta * (target - self.predict(xi))
                self.w_[1:] += update * xi
                self.w_[0] += update
                errors += int(update != 0.0)
            self.errors_.append(errors)
        return self

    def net_input(self, X):
        """Calculate net input"""
        return np.dot(X, self.w_[1:]) + self.w_[0]

    def predict(self, X):
        """Return class label after unit step"""
        return np.where(self.net_input(X) >= 0.0, 1, -1)
```

使用此感知机实现，我们现在可以初始化具有给定学习率 `eta` 和 `n_iter` 的新感知机对象，其中 `n_iter` 是 epoch 数（遍历训练集的次数）。通过 `fit()` 方法，我们将 `self.w_` 中的权重初始化为零向量 `m+1`，其中 `m` 代表数据集中的维度（特征）数量，我们加 1 是为了零权重（即阈值）。

NumPy 对一维数组的索引与 Python 列表类似，使用方括号 (`[]`) 表示法。对于二维数组，第一个索引器指行号，第二个索引器指列号。例如，我们将使用 `X[2, 3]` 来选择二维数组 `X` 的第三行和第四列。

权重初始化后，`fit()` 方法遍历训练集中的所有单个样本，并根据我们在上一节中讨论的感知机学习规则更新权重。类标签由 `predict()` 方法预测，我们还在 `fit()` 方法中调用它来预测权重更新的类标签，但 `predict()` 也可以在我们拟合模型后用于预测新数据的类标签。此外，我们还在列表 `self.errors_` 中收集每个 epoch 期间的误分类数量，以便以后分析我们的感知机在训练期间的表现。`net_input()` 方法中使用的 `np.dot()` 函数只是计算向量点积 `w^T X`。

