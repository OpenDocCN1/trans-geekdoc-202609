
如果我们使用线性回归，我们会相当好地捕捉到中间点，但每个阶梯的末端会被遗漏。直白地说，线性回归的偏差对我们追踪模式的能力施加了根本性的限制。

你可能会想，决策树可以将输入分解成小桶。你完全正确——我们将在下一节讨论这个问题。但我想在线性回归的使用和修改决策树以执行回归之间取一个中间立场。我们将以最简单的方式进行*分段*线性回归：使用*分段常数回归*。对于输入特征的每个区域，我们将预测一条简单的水平线。这意味着我们为该区域预测一个单一的常数值。

我们原始的成本与账单图就是一个这种模型合适的例子。这里还有另一个关系不太一致的例子。随着 x 的增加，我们不再一直向上，而是上下波动。我们首先定义一些分割点。如果我们想要四条线，我们就需要定义三个分割点（记住，当你剪断一根绳子时，你会从一根绳子变成两根）。想象我们在 a、b 和 c 处分割。然后，我们将在数据上拟合四条线：（1）从非常小到 a，（2）从 a 到 b，（3）从 b 到 c，（4）从 c 开始到非常大。稍微具体一点，想象 a,b,c=3,8,12。结果可能看起来像

In [22]:

```
fig, ax = plt.subplots(1,1,figsize=(4,3))
ax.plot([0,3], [0,0],
[3,8], [5,5],
[8,12], [2,2],
[12,15], [9,9])
ax.set_xticks([3,8,12]);
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_337_0.png)

你也许能对分割数量与偏差之间的关系做出一些有根据的猜测。如果没有分割，我们只是执行没有斜率的线性回归——使用均值在处处预测一个常数值。如果走向另一个极端，我们将有 n 个数据点并制作 n − 1 条迷你线。该模型在训练上表现会好吗？应用到测试集上预测呢？该模型在训练上会很棒，但在测试上会很糟糕：它过拟合了数据。

在某些方面，分段常数回归类似于 k-Nearest Neighbors Regression (k-NN-R)。然而，k-NN-R是基于相对距离而不是原始数值来考虑示例的。我们认为一个新的测试示例类似于训练示例 3、17 或 21，因为它们与新示例接近，而不管原始数值如何。分段常数回归根据预设的分割范围给示例相同的目标值：我与值在 5 到 10 之间的示例相似，因为我的值是 6，即使我更接近值为 4 的示例。

在数据科学中，我们使用短语*let the data speak for itself*。在这里，这个想法是核心的：对于 k-NN-R，数据决定了预测之间的边界*并且*这些边界会随着数据的密度而移动。密度更高的区域会有更多潜在的边界。而对于分段常数回归，我们的分割是预先确定的。对于数据密度高或低的区域没有回旋余地。净效果是，如果我们对数据有一些强有力的背景信息，选择分段回归的分割点时我们可能会做得非常好。例如，在美国，税级是由预先确定的断点设定的。如果我们没有正确的信息，我们的分割点可能比 k-NN-R 差得多。

### 9.3.1 实现分段常数回归器

到目前为止，我们只使用了预建模型。出于完全披露的精神，我在上一章末尾偷偷加入了一个定制的对角 LDA 模型，但我们根本没有讨论其实现。由于 `sklearn` 没有内置的分段回归能力，我们将借此机会实现自己的学习器。实现它的代码并不太糟糕：它大约有 40 行，并使用了两个主要思想。第一个思想相对直接：为了对各个片段执行常数回归，我们只需在数据的重写形式上重用 `sklearn` 的内置线性回归。第二个思想是我们需要从输入特征——我们现在只限制为一个——映射到我们绳子的适当部分。这个映射有点棘手，因为它有两步。

第一步涉及使用 `np.searchsorted`。`searchsorted` 本身有点棘手，但我们可以概括它的作用：它为新元素在已排序的值序列中找到一个插入点。换句话说，它说明某人应该在哪里进入按身高排序的人群以保持顺序。我们希望能够将特征值 60 翻译为段，或绳段，3。我们需要在训练和测试阶段都做到这一点。

第二步是我们将绳段转换为真/假指示符。因此，与其 Piece = 3，我们有 Piece₁ = False，Piece₂ = False，Piece₃ = True。然后，我们从片段指示符学习到输出目标的回归模型。当我们想要预测一个新示例时，我们只需将其通过映射过程以获得正确的片段指示符，然后将其传递给常数线性回归。重新映射全部封装在下面的代码中的 `_recode` 成员函数中。

### 9.3.2 实现模型的一般说明

sklearn 文档讨论了如何实现自定义模型。我们将忽略一些可能的替代方案并列出一个简化的流程。

- 由于我们实现的是回归器，我们将继承自 `BaseEstimator` 和 `RegressorMixin`。
- 我们将*不*在 `__init__` 中对模型参数做任何事情。
- 我们将定义 `fit(X,y)` 和 `predict(X)` 方法。
- 我们可以使用 `check_X_y` 和 `check_array` 来验证参数在 `sklearn` 意义上是否有效。

代码的两个快速评论：

- 以下代码仅适用于单个特征。将它扩展到多个特征将是一个有趣的项目。我们将在第 10 章看到一些可能有帮助的技术。
- 如果未指定切分点，我们每十个示例使用一个切分点，并且我们在均匀间隔的分位数处选择切分点。

如果我们有两个区域，一个分割点将在 50%，即中位数。对于三个或四个区域，分割点将在 33–67% 或 25–50–75%。请记住，分位数是指 x% 的数据小于该值的位置。例如，如果 50% 的数据小于 5'11''，那么 5'11'' 就是第 50 个百分位值。具有讽刺意味的是，如果数据集中在中间，如身高可能的情况，单个 50% 的分割点可能特别糟糕。

In [23]:
```python
from sklearn.base import BaseEstimator, RegressorMixin
from sklearn.utils.validation import (check_X_y,
                                    check_array,
                                    check_is_fitted)

class PiecewiseConstantRegression(BaseEstimator, RegressorMixin):
    def __init__(self, cut_points=None):
        self.cut_points = cut_points

    def fit(self, X, y):
        X, y = check_X_y(X,y)
        assert X.shape[1] == 1 # one variable only

        if self.cut_points is None:
            n = (len(X) // 10) + 1
            qtiles = np.linspace(0.0, 1.0, n+2)[1:-1]
            self.cut_points = np.percentile(X, qtiles, axis=1)
        else:
            # ensure cutpoints in order and in range of X
            assert np.all(self.cut_points[:-1] < self.cut_points[1:])
```

## 第 9 章 更多回归方法

```
assert (X.min() < self.cut_points[0] and
self.cut_points[-1] < X.max())

recorded_X = self._recode(X)
# even though the _inner_ model is fit without an intercept,
# our piecewise model *does* have a constant term (but see notes)
self.coeffs_ = (linear_model.LinearRegression(fit_intercept=False)
.fit(recorded_X, y).coef_)

def _recode(self, X):
    cp = self.cut_points
    npieces = len(cp) + 1
    recorded_X = np.eye(npieces)[np.searchsorted(cp, X.flatten())]
    return recorded_X

def predict(self, X):
    check_is_fitted(self, 'coeffs_')
    X = check_array(X)
    recorded_X = self._recode(X)
    return np.dot(self.coeffs_, recorded_X)
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_340_0.png)

为了测试和演示该代码，让我们生成一个简单的示例数据集来训练。

In [24]:
```
fr = np.random.randint(0,10,(100,1)).astype(np.float64)
cp = np.array([3,7])
tgt = np.searchsorted(cp, fr.flat) + 1
fig, ax = plt.subplots(1,1,figsize=(4,3))
ax.plot(fr, tgt, '.');
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_340_1.png)

