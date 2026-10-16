
当我们执行 PCA 时，我们的第一步是寻找这条最佳直线：哪条直线具有 *最低误差* 且 *最大方差*？我们可以继续这个过程，并寻找一条与第一条直线垂直——呈直角——的 *下一个* 最佳直线。把这两条直线放在一起就得到一个平面。我们可以继续进行下去。对于原始数据集中拥有的每个特征，我们都可以添加另一个方向。*wine* 数据集有 13 个训练特征，因此我们最多可以有 13 个方向。事实证明，PCA 的一种用途是提前停止该过程，以便我们（1）找到一些好的方向，并且（2）减少我们保留的总信息量。

## 13.3.3 初次 PCA

在手工完成了所有这些工作之后——细节隐藏在 `plot_lines_and_projections` 中，它并不太长，但确实依赖于一些线性代数——我会用我的惯用手法告诉你，我们 *不必* 手工完成。`sklearn` 中有一个自动化的替代方案。上面，我们尝试了几条可能的直线，并看到有些比其他的好。如果存在某种底层数学能够在不尝试不同结果的情况下告诉我们最佳答案，那就理想了。事实证明确实存在这样一个过程。主成分分析（PCA）在最小误差和最大方差约束下找到最佳直线。

想象一下，我们为一个多方面的数据集找到了最佳直线——最佳的单一方向。现在，我们可能想要找到 *第二* 最佳方向——一个具有最大分散度和最小误差的第二个方向——并带有一个轻微的约束。我们希望这个第二方向与第一个方向垂直。由于我们在考虑两个以上的特征，因此存在不止一种垂直的可能性。两个方向确定了一个平面。PCA 选择的方向最大化方差、最小化误差，并且与已选方向垂直。PCA 可以一次性为所有方向完成此操作。在理想情况下，我们可以为数据集中每个特征找到一个新方向，尽管我们通常会提前停止，因为我们使用 PCA 来 *减少* 我们的数据集，通过减少发送到学习算法的特征总数。

让我们创建一些数据，对数据使用 `sklearn` 的 PCA 转换器，并从结果中提取一些有用的部分。我已将结果的两个组件翻译成我们想要绘制的内容：数据的<|message|> 主方向以及该方向上的变异量。方向告诉我们数据驱动的轴指向何处。我们稍后会看到箭头的长度来自何处。

```
In [57]:

# draw data
ax = plt.gca()
ax.scatter(data[:,0], data[:,1], c='b', marker='.')

# draw mean
mean = np.mean(data, axis=0, keepdims=True)
centered_data = data - mean
ax.scatter(mean.T, c='k')
```

```python
# compute PCA
pca = decomposition.PCA()
P = pca.fit_transform(centered_data)

# extract useful bits for drawing
directions = pca.components_
lengths = pca.explained_variance_
print("Lengths:", lengths)
var_wgt_prindirs = -np.diag(lengths).dot(directions)
  # negate to point up/right

# draw principal axes
sane_quiver(var_wgt_prindirs, ax, origin=np.mean(data,axis=0), colors='r')
ax.set_xlim(0,10)
ax.set_ylim(0,10)
ax.set_aspect('equal')
```

Lengths: [5.6067 1.2683]

![](img/d94e4cd766940d79abed0bc6ba4e4344_478_0.png)

那还不错。如果我们倾斜头部——或我们的页面或屏幕——使轴指向左右和上下，突然之间，我们已将数据从任意方向转换到相对于红色箭头的标准网格。我们很快就会在不倾斜头部的情况下执行最后一步。我想花点时间谈谈结果的协方差。在此过程中，我将解释为什么我选择用 explained_variance 的长度来绘制数据轴。作为热身，请记住方差——以及协方差——不受数据平移的影响。具体来说，它不受数据中心化的影响。

```
In [58]:
print(np.allclose(np.cov(data, rowvar=False),
    np.cov(centered_data, rowvar=False)))
```

True

现在，统计学家有时关心数据中的总变异量。它来自协方差矩阵的对角线条目（参见第 8.5.1 节）。由于 data 和 centered_data 具有相同的协方差，我们可以使用其中任何一个来计算协方差。以下是协方差矩阵以及从左上到右下的对角线之和：

```
In [59]:
orig_cov = np.cov(centered_data, rowvar=False)
print(orig_cov)
print(np.diag(orig_cov).sum())
```

[[3.3333 2.1667]
 [2.1667 3.5417]]
6.875

当我们执行 PCA 时，我们得到一组新的方向，总方差量相同。然而，我们的方向会以不同的方式分配方差。事实上，我们会尽可能多地将总方差堆叠到第一个方向上。该方差完全与我们之前讨论的最大方差/最小误差标准有关。在下一个方向上，我们获得尽可能多的剩余变异，依此类推。如果我们把所有新方向的方差加起来，我们会看到总和相同。

```
In [60]:
EPS = 2.2e-16 # EPS (epsilon) is computer-sciency for "really small"
p_cov = np.cov(P, rowvar=False)
p_cov[p_cov<EPS] = 0.0  # throw out "really small" values
print(p_cov)
print(p_cov.sum())
```

[[5.6067 0.  ]
 [0.    1.2683]]
6.875000000000002

对角线值是我们用来绘制数据轴的长度。我们还看到 cov(P) 在对角线外的所有条目都为零。我们消除了特征之间的协方差。这正是我们通过 PCA 选择方向的原因，这些方向在彼此之间不是线性相关的（它们呈直角）。我们已自行决定将任何足够小的值（小于 EPS）替换为精确的 0.0，主要是为了处理浮点问题。

## 13.3.4 PCA 的内部原理

我们可以快速看看 sklearn 计算数据集 PCA 时发生了什么。执行 PCA 的标准方法依赖于矩阵的奇异值分解（SVD）。我想展示这个过程有三个原因：（1）整体策略和算法相当直接，但阅读起来可能令人困惑，（2）将表格数据视为矩阵为理解其他技术打开了很大的机会窗口，（3）它是为什么你可能想要学习线性代数的绝佳介绍，即使你真正关心的是机器学习和数据分析。

线性代数的主要工具之一是矩阵分解或矩阵因子分解——它们是同一事物的两种名称。当我们分解某物时，我们将其分解为组成部分。当我们对一个整数——一个整数——进行因式分解时，我们将其分解为组成部分。64 = 8 · 8 或 24 = 12 · 2 = 3 · 2 · 2 · 2 = 3 · 2³。因式分解整数的方式有很多。我们可以寻找无法进一步分解的部分：这称为素数分解。或者，我们可以简单地要求一对两个因子。或者，我们可以问数字是否可以分解为相同的值——它是平方数、立方数等。

矩阵分解或因子分解是矩阵的等效过程。我们取一个已知的矩阵并询问如何将其分解为更原始、更小的组成部分。有趣的是，我们通常可以用这些部分如何影响数据矩阵的散点图来谈论这些部分。例如，矩阵的 SVD 基本上说任何数据矩阵都可以分解——分解或分离——为三个组成部分：旋转或旋转、拉伸和另一个旋转。反过来，如果我们从我们能想象的最普通的<|message|> 数据开始，并旋转、拉伸并再次旋转，我们可以得到任何数据矩阵作为结果。另一种分解，特征分解，将矩阵分解为旋转、拉伸，然后是第一次旋转的撤销。让我们在这里检查一下。

我们需要一个可以围绕原点（0，0）旋转数据点给定角度的快速助手：

```
In [61]:
def make_rotation(theta):
    ''' ccw rotation of theta when it post-multiplies
        a row vector (an example) '''
    return np.array([[np.cos(theta), -np.sin(theta)],
                    [np.sin(theta),  np.cos(theta)]]).T
```

有了它，我们可以创建一些在圆周上等间距的点，并设置我们想要执行的旋转和缩放量：

```
In [62]:
spacing = np.linspace(0,2*np.pi,17)
points  = np.c_[np.sin(spacing), np.cos(spacing)]
# sin/cos walk around circle
```
