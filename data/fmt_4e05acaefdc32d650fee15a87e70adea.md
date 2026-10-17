
`gpr = GaussianProcessRegressor(kernel=kernel,n_restarts=9)`

# Fit to the data and optimize parameters.

`gpr.fit(train,y)`

# Optimized kernel:

`kernel = gpr.kernel_`

`plt.plot(x_train, y, marker='d', c='c')`

`plt.plot(x, y, label='training function')`

`mean, std = gpr.predict(x, return_std=True)`

`plt.plot(mean, 'r-', linestyle='--')`

`plt.fill_between(x, mean-2*std,mean+2*std, alpha=0.5)`

# Draw 4 samples from the posterior.

`f = gpr.sample(x, 4)`

`plt.plot(x, f, linewidth=1)`

`plt.show()`

```
```

列表 8.4：在 Python 中使用不同核从高斯过程中进行采样。对于 MATLAB 请访问：

`https://github.com/ACFau/Regression-Matlab`.

![](img/c6c76bf52016db7e78a5e30d4766ef81_297_0.png)

(a) 高斯核，
$\theta \approx 2.81, l \approx 2.85$.

![](img/c6c76bf52016db7e78a5e30d4766ef81_297_1.png)

(b) 指数核，
$\theta \approx 1.75, l \approx 1.66$.

(c) 逆多二次核，
$\theta \approx 3.21, l \approx 4.74$.

图 8.14：具有优化参数的不同核的后验高斯过程的采样。

因此，需要核函数对其参数的导数。对于高斯核

```
$k(x, y) = \theta^2 \exp \left(-\frac{\|\mathbf{x}-\mathbf{y}\|^2}{2l^2}\right),$
```

例如：

```
$$\frac{\partial}{\partial\theta}k(x,y) = 2\theta \exp \left(-\frac{\|\mathbf{x}-\mathbf{y}\|^2}{2l^2}\right) = \frac{2}{\theta}k(x,y),$
```

```
$$\frac{\partial}{\partial l}k(x,y) = \frac{\\|\mathbf{x}-\mathbf{y}\|^2}{l^3}\theta^2 \exp \left(-\frac{\|\mathbf{x}-\mathbf{y}\|^2}{2l^2}\right) = \frac{\\|\mathbf{x}-\mathbf{y}\|^2}{l^3}k(x,y).$
```

将 $\mathcal{L}$ 的梯度置零并求解参数通常不是简单的。然而，由于梯度是已知的，它可以用于

![](img/c6c76bf52016db7e78a5e30d4766ef81_298_0.png)

图 8.15：具有优化参数的线性核和高斯核的和。

图 8.14 显示了各种核的高斯过程均值和标准差，其中参数已优化，以及如列表 8.4 所示的四次采样。由于核的选择，后验高斯过程的均值在数据点之外返回零，尽管其返回速度比原始参数选择要慢。因此，我们将高斯核与线性核相结合。即核由给出：

```
$k(x,y) = \theta_1^2 + \theta_2^2x + \theta_3^2 \exp\left(-\frac{\|x-y\|^2}{2\theta_4^2}\right)$
```

优化后，参数 $\theta_1 \approx 1.5, \theta_2 \approx 0.9, \theta_3 \approx 1.1$ 和 $\theta_4 \approx 1.6$。图 8.15 在更宽的范围内说明了近似效果。虽然均值偏离真实函数，但通过更多数据可以获得更好的近似。应该使用哪种核组合取决于应用，这是一个正在开发的活跃研究领域。

# 练习

**练习题 8.1.** *给出在五个点测量的标量值回归变量数据如下：*

| | |
|---|---|
| -2 | 1.5 |
| -1 | 0.5 |
| 0 | 0 |
| 1 | 0.5 |
| 2 | 1.5 |

应使用多项式对数据集进行建模。从数据中推导出应该选择哪些多项式。建议的设计矩阵 $D = \begin{pmatrix} 4 & 0 \end{pmatrix}$。根据 OLS 方法计算权重向量 $w$。使用这些权重检查数据集的预测情况。

**练习题 8.2.** *给出回归变量 $y = \begin{pmatrix} 1 \\ 2 \\ 3 \end{pmatrix}$ 和设计矩阵 $D = \begin{pmatrix} 1 & -1 & -1 \\ 0 & 1 & 2 \\ 0 & 0 & -1 \end{pmatrix}$。$D$ 的列是线性相关的。$D$ 的秩是多少？根据 PLS 方法计算新的回归变量 $t_1$ 和设计矩阵 $D_1$。$D_1$ 的秩是多少？*

**练习题 8.3.** *函数 $k_1(x,y) = 2^{-\|x-y\|^2} \quad \text{和} \quad k_2(x,y) = 2^{-a\|x-y\|}$（其中 $a = 1, 2$）是有效的核吗？*

**练习题 8.4.** *给出数据点 $x_1 = 0, x_2 = 1.1, x_3 = 2.3$ 和 $x_4 = 3.4$，以及相应的测量值 $t_1 = 2.0, t_2 = 3.0, t_3 = 3.5$ 和 $t_4 = 2.5$。核定义为 $k(x,y) = \begin{cases} 1-|x-y|, & |x-y| < 1 \\ 0 & \text{其他} \end{cases}$。计算 Gram  $C$，其中 $(i, j)$ 项为 $k(x_i, x_j)$，并对该核的适用性进行评论。我们进一步给出 $x_i^1 = 0.7$ 和 $x_i^2 = 2.8$，需要预测 $t_i^1$ 和 $t_i^2$。计算给定 $t = (t_1, t_2, t_3, t_4)$ 时 $\mathbf{t}^* = (t_1^*, t_2^*, t_3^*, t_4^*)$ 的条件概率分布的均值 $\mathbf{m}^t$ 和方差 $\Sigma^t$。*

## 参考文献

Bertsimas, D. & Tsitsikis, J. (1997), *Introduction to Linear Optimization*, Athena Scientific Books, Athens Scientific.

Bishop, C. (2006), *The Life Of James Clerk Maxwell: With a Selection from his Correspondence and Occasional Writings and a Sketch of his Contributions to Science, Cambridge Library Collection - Physical Sciences*, Cambridge University Press.

Campbell, L. & Garnett, W. (2010), *Pattern Recognition and Machine Learning*, Springer.

Chen, B., Zhu, Y., Hu, J. & Principe, J. (2013), *System Parameter Identification*, Elsevier.

Faul, A. (2016), *A Concise Introduction to Numerical Analysis*, Chapman and Hall/CRC Press.

Haenlein, M. & Kaplan, A. (2004), ‘A Beginner’s Guide to Partial Least Squares Analysis, Understanding Statistics* **3**(4), 283–297.

Ockham, W. (1495), *Quaestiones et decisiones in Sententiarum*, https://books.google.co.uk/books?id=1uPlwECAAAJ. Accessed: 2024-08-07.

数量和状态，每种都有其自身的含义和解释。需要从各种数据中提取本质信息。

## 9.1 神经网络

与之前一样，给定数据对 $(\mathbf{x}_n, \mathbf{t}_n), \dots, (\mathbf{x}_1, \mathbf{t}_n)$，其中 $x_n \in \mathbb{R}^D$，且 $\mathbf{x}_n$ 的每个分量都是特征。$\mathbf{t}_n$ 也可以是多维的，$t_n \in \mathbb{R}^K$。

回神经网络连接了一组输入神经元、一组输出神经元以及可能的若干组隐藏神经元。$x$ 的一个分量传递给一个输入神经元。因此，输入神经元的数量为 $D$。在训练过程中，输出神经元的结果与 $\mathbf{t}_n$ 进行比较。因此，输出神经元的数量为 $K$。连接两组神经元的突触数量为 $L$。

更具体地说，设 $L$ 为层数。这意味着有 $L-1$ 组隐藏神经元。第 $l$ 组隐藏神经元的大小用 $z_m^{(l)}, l=1,\dots,L-1, m=1,\dots,M_l$ 表示。在第 $l$ 层中，连接左侧 $i$ 个神经元到右侧 $j$ 个神经元的突触权重用 $w_{ij}^{(l)}$ 表示。该神经网络如图所示

![](img/c6c76bf52016db7e78a5e30d4766ef81_302_0.png)

虚线连接表示隐藏神经元和层之间的任何组合都是可能的。

对于 $l \neq 1$，传播函数的结果是激活值

$$a_j^{(l)} = \sum_{i=1}^{M_{l-1}} w_{ji}^{(l)} z_i^{(l-1)}$$

将其被传递给该层的*激活函数*（也称为*传递函数*）$h_i$，以生成隐变量

$$z_i^{(l)} = h_i(a_i^{(l)}) = h_i\left(\mathbf{w}_i^{(l)})^T x^{(l-1)}\right)$$

对于 $l = 1$，我们有

$$a_1^{(1)} = \mathbf{w}_1^{(1)T}\mathbf{x} \quad \text{and} \quad z_1^{(1)} = h_1\left(\mathbf{w}_1^{(1)})^T \mathbf{x}\right)$$

对于 $l = L$，计算输出变量 $y_1, \dots, y_K$，

$$y_L = h_L(a_L^{(L)}) = h_L\left(\mathbf{w}_L^{(L)})^T x^{(L-1)}\right)$$

第 5.5 节给出了可能的激活函数列表。选择取决于问题：

- **对于回归**，$K = 1$ 且 $t_i$ 取值为 0 或 1，取决于具有特征 $\mathbf{x}_i$ 的样本分别属于负类还是正类。只有一个输出神经元，且激活函数是*logistic sigmoid* 函数 $h_L^{(L)} = (1 + \exp(-a^{(l)}))^{-1}$。输出被解释为具有特征 $x_1, \dots, x_D$ 的输入属于正类的概率。
- **对于二分类**，对同一数据进行 $K$ 个独立的**二分类**任务，则 $\mathbf{t}_i$ 是由 0 和 1 组成的向量。第 $k$ 个分量表示第 $k$ 个分类任务的类别属性。每个输出神经元都可以使用 logistic sigmoid 函数连接到二分类器。
- **对于多分类**，$\mathbf{t}_i$ 是一种*1-of-K 表示*。这意味着 $\mathbf{t}_i$ 的 $K$ 个分量中只有一个为1，其余全为0。具有特征 $\mathbf{x}_i$ 的样本属于第 $k$ 类。激活函数是*softmax* 函数，它将 $K$ 维激活向量 $a^{(l)} = (a_1^{(l)}, \dots, a_K^{(l)})^T$ 映射到 $K$ 维激活向量 $\sigma(a^{(l)})$，其中 $\sigma(a^{(l)})$ 的第 $k$ 个元素为

$$\sigma(a^{(l)})_k = \frac{\exp(a_k^{(l)})}{\sum_{j=1}^K \exp(a_j^{(l)})}$$

第 $k$ 个输出被解释为具有特征 $\mathbf{x} = (x_1, \dots, x_D)^T$ 的样本属于第 $k$ 类的概率。输出值之和为1，符合概率的要求。

如果神经元的激活函数是 logistic sigmoid，则神经网络通常被称为多层感知机。然而，这是一个误称，因为原始感知机使用不连续的阶跃函数作为激活函数。在关于反传播的章节中，我们将看到连续性带来的优势。更增加混淆的是，“多层感知机”这一术语现在被用于任意架构，以及用于分类或回归任务。由于这种定义的稀释，无法推断出神经网络的形式，因此使用了感知机这一术语。

神经网络是一个将输入 $x = (x_1, \dots, x_D)^T$ 映射到输出 $y = (y_1, \dots, y_D)^T$ 的函数。这种映射是函数的复合，每层都是线性函数与激活函数的复合。层数可以达到数百或数千层，从而产生了深度学习。这些许多可能性是强大的；然而，为了获得对底层过程的洞察，简单性也有其考量量。

输入通过网络的过程被称为前向传播。不允许循环（即信息不能向后传递）。该架构是严格前馈的。

由于隐变量可以重新标记（这意味着神经元之间可以相互交换），因此存在 $\prod_{M_l!}$ 个等效神经网络，它们具有相同的输入输出映射。另一种等效性源于隐藏神经元的激活函数是偶函数或奇函数。

- 如果网络在同一组数据上处理 $K$ 个独立的二分类任务，则误差函数为：

```
$E(\mathbf{w}) = -\sum_{k=1}^{K} \sum_{n=1}^{N} t_{n,k} \log y_k(\mathbf{x}_n, \mathbf{w}) + (1 - t_{n,k}) \log (1 - y_k(\mathbf{x}_n, \mathbf{w}))$$
```

其中 $t_{n,k}$ 是 $\mathbf{t}_n$ 的第 $k$ 个分量，$y_k(\mathbf{x}_n, \mathbf{w})$ 是当 $\mathbf{x}_n$ 为输入时第 $k$ 个神经元的输出。它是这 $K$ 个独立二分类任务误差的总和。

- 对于多分类，$y_k(\mathbf{x}_n, \mathbf{w})$ 被视为具有特征 $\mathbf{x}_n$ 的样本属于第 $k$ 类别的概率，而 $\mathbf{t}_n$ 是一个 1-of-$K$ 表示。数据的似然为：

```
$$\mathcal{L} = \prod_{n=1}^{N} \prod_{k=1}^{K} y_k(\mathbf{x}_n, \mathbf{w})^{t_{n,k}}$$
```

如之前一样，负对数导致了误差函数：

```
$E(\mathbf{w}) = -\sum_{k=1}^{K} \sum_{n=1}^{N} t_{n,k} \log y_k(\mathbf{x}_n, \mathbf{w})$$$
```

这看起来与上面的非常相似，但现在 $t_{n,k}$（$k=1, \dots, K$）只有一个为非零。

我们通过训练一个具有三个隐藏神经元的二层神经网络来表示函数 $1+x+\sin x$，以此说明神经网络的能力。偏置通过始终具有值的虚拟神经元进行显式建模。网络图如下：

![](img/c6c76bf52016db7e78a5e30d4766ef81_306_0.png)

![](img/c6c76bf52016db7e78a5e30d4766ef81_307_0.png)

(a) 真实函数、预测、偏置和构造函数。

![](img/c6c76bf52016db7e78a5e30d4766ef81_307_1.png)

(b) 训练点的误差。

图 9.1：具有一组三个隐藏神经元的二层神经网络回归。

第一层的激活函数是形式如下的双正切函数：

$h_1(x) = \frac{2}{1 + \exp(-2x)} - 1,$

它也被称为 *tan-sigmoid* 激活函数，因为这种实现速度更快。在第二层中，它是线性激活函数。

使用了 21 个等间距的训练点。一旦神经网络训练完成，就可以对任何输入 $x$ 进行评估。图 9.1a 显示了结果，红色为真实函数，蓝色为预测值，黑色为偏置 $b$。它还显示了 $z_1w_1^1, z_2w_2^1$ 和 $z_3w_3^1$，它们都是输入 $x$ 的函数。依赖于 $x$ 的隐变量 $z_1, z_2$ 和 $z_3$ 可以解释为神经网络从数据构造的基函数。输出层的预测是这些函数与偏置的加权和。

```matlab
clear;

x = -5:0.1:5;

% True function;
t = x .* sin(x);

% 构建一个具有3个隐藏神经元的二层神经网络。
net = fitnet(3);

% 移除归一化和反归一化。
net.input.processFcns = {};
net.output.processFcns = {};

% 训练神经网络。
[net,~] = train(net,x,t);

% 第一层的权重。
LW = net.W{1};

% 第一层的偏置权重。
b1 = net.b{1};

% 第二层的偏置权重。
b2 = net.b{2};

% 第二层的权重。
LW = net.W{2};

X = -5:0.1:5;
T = X .* sin(X);

% 预测
```
