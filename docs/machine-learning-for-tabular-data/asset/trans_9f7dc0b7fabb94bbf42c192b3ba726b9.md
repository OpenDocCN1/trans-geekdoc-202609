

## 第 5 章 决策树与梯度提升

```python
density=True,
color='blue',
alpha=0.7)
plt.xlabel('Predicted Probabilities')
plt.ylabel('Density')
plt.title('Histogram of Predicted Probabilities')
plt.grid(True)
plt.show()
```

使用指定的分箱（bins）和归一化密度创建预测概率的直方图。

![](img/def89cc476fa39f4c54bd34e78d91674_178_0.png)

图 5.6 描述梯度提升分类拟合概率的直方图，显示了模型对大多数情况的正或或负做出的强力决断。

我们的实现在底层使用了回归和二乘损失，其梯度等于将概率转换为 logits 后的残差。关于 logits 的定义，请参阅 https://mng.bz/W214I。

概率 $p$ 的 logits 计算方式为：

> logit(p) = log(p/(1-p))

这种定义的优势在于，log 函数将概率映射到对数尺度，这是一个从负无穷到正无穷的无界尺度，使我们能够将问题视为一个回归问题。

这意味着在每次迭代中，梯度提升算法都会根据损失函数相对于 logit 值的梯度拟合一个回归模型，这对应于真实目标值的 logits 与以 logits 形式表示的当前预测之间的差异。这种方法允许算法通过沿损失函数的最速下降方向调整预测来迭代改进，并得益于 log 的反函数，使得 log 预测限制在 0 到 1 之间的范围内。sigmoid 是一种将其输入映射到 0 到 1 之间数值的数学函数，提供了一个平滑且连续的曲线。

sigmoid 的公式为：

```python
$$\sigma(x) = \frac{1}{1 + \exp(-x)}$$
```

其中

- $\sigma(x)$ 代表应用于输入值 $x$ 的 sigmoid 函数。
- $\exp(-x)$ 是指数函数，其中 $\exp$ 表示欧数（约 2.71828）的 $-x$ 次方。
- $1+\exp(-x)$ 是分母，它确保了 sigmoid 函数的输出始终为正。
- $1 / (1+\exp(-x))$ 代表 1 除以分母，得到 sigmoid 函数的输出值。

它通常用于机器学习和统计模型，以将对数预测转换为概率。

如果我们把问题视为回归问题会怎样？在 5.9 中，我们基于 `GradientBoosting` 类构建了 `GradientBoostingRegression` 类，通过移除 log 和 sigmoid 变换来重写 `fit` 和 `predict` 方法。

> 列表 5.9 测试一个提升回归类

```python
def fit(self, X, y):
    self.init = np.mean(y)
    y_pred = self.init * np.ones((X.shape[0],))

    for k in range(self.n_estimators):
        gradient = y - y_pred
        tree = DecisionTreeRegressor(**self.params)
        tree.fit(X, -gradient)
        self.trees.append(tree)
        y_pred += (
            self.learning_rate * tree.predict(X)
        )

def predict(self, X):
    y_pred = self.init * np.ones((X.shape[0],))
    for tree in self.trees:
        y_pred += (
            self.learning_rate * tree.predict(X))
    return y_pred
```

预测预测需要累积所有树的预测结果。

```python
reg = GradientBoostingRegression(n_estimators=300, learning_rate=0.1, max_depth=4, min_samples_leaf=3, random_state=0)
```

```python
reg.fit(X, y)
```

```python
proba = reg.predict(Xt)
plt.figure(figsize=(8, 6))
plt.hist(proba, bins=10, density=True, color='blue', alpha=0.7)
plt.xlabel('Predicted Probabilities')
plt.ylabel('Density')
plt.title('Histogram of Predicted Probabilities')
plt.grid(True)
plt.show()
```

![](img/def89cc476fa39f4c54bd34e78d91674_180_0.png)

当运行代码列表 5.9 时，它将生成拟合预测的直方图，如图 5.7 所示。5.7 显示了拟合概率如何超出 0-1 边界。与基于特征的加权组合线性回归不同，梯度提升作为基于链序列结果的加权组合，可以超出决策树的限制。这种外推在其他基于决策树的集成方法（如随机森林）中是不可能的。回归中的决策树无法预测任何超过训练期间的值，因为预测是基于训练样本的平均值。GBDT 的外推潜力基于其作为加法集成的事，这是它们在时间序列上取得成功的基础，在时间序列中，你需要外推可能与过去大不同的未来结果。

然而，需要注意的是，始终考虑 GBDT 的外推能力无法达到线性模型所达到的程度。在时间序列预测情况下，如果待预测值距离提供的训练目标太远，例如在离群值的情况下，外推将缺失正确的估计。线性模型直接在输入数据和预测之间建立线性关系，在这些情况下可能更为合适。线性模型能够处理针对完全离群数据点的极端预测。为了在这些情况下提供决策树作为基学习器的替代方案，许多 GBDT 实现通过简单集成线性模型（例如在 XGBoost 实现中）或在决策树的末端节点上构建分段线性梯度提升树（例如在 LightGBM 实现中）来提供线性提升。

![](img/def89cc476fa39f4c54bd34e78d91674_181_0.png)

> 图 5.7
一个描述使用梯度提升回归模型拟合概率的直方图，其中某些概率超 0-1 边界

GBDT 在时间序列中的优势依赖于自动选择预测信息，且需要设置的超参数非常少。对于异构数据，基于树的方法表现出色。这是因为它们可以在不进行人工特征工程的情况下捕捉特征之间的非线性关系和相互作用。然而，GBDT 的性能可能对数据的尺度敏感。例如，在 M5 竞赛中，基于树的方法更优。这是因为 GBDT 对表格数据的噪声和离群值更健壮。

## 5.2 解释提升的有效性

今天，基于树的方法是表格数据的流行选择。但 GBDT 相对于神经网络（NN）的优势究竟来自哪里？《树基模型在表格数据上仍然优于深度学习吗？”由 Leo Grinz, Edouard Oyallard 和 Gael Varoaux 发表（第三六届神经信息系统数据集与基准会议，2022；https://hal.science/hal-0372855v2/document）是一项阐明不同架构性能的最新研究。该研究显示树基方法优于深度学习。作者使用 45 个开放数据集定义了一个标准测试。他们考虑了大约 10,000 个样本，由不同列组成，包括不同单位的数值特征和类别特征，因为这考虑了典型的表格情况。尝试了各种深度学习模型，包括多层感知机（ML）、ResNet、SAINT 和 Transformer，但发现树基方法在任何超参数调优下表现良好。当仅考虑数值特征时，树基方法优于深度学习。在考虑拟合时间时，这种优势更加明显。

作者还研究了解释树基和深度学习方法性能差异的表格数据特征。他们发现，特征空间中的平滑处理缩小了深度架构难以处理的模式差距，而平滑不影响树模型。移除无关特征缩小了类 MLP 神经网络架构的差距。然而，只有在数据应用随机旋转后，深度架构才优于树模型。

随机旋转是指在将数据输入机器学习模型之前，对数据集的输入特征应用随机旋转矩阵。这种旋转矩阵是保持向量长度和向量之间角的方阵，确保旋转后的数据与原始数据等效。随机旋转在机器学习中有多种用途，包括集成的多样性、提高模型的健壮性以及解决计算机视觉和量子化学机器学习任务中的旋转不变性。这种技术是完全可逆的，但往往会模糊与

