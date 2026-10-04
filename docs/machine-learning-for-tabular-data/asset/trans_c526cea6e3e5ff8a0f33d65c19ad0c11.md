

# 第 5 章 决策树与梯度提升

如果说梯度下降在优化中提供了最优结果和灵活性，那么将决策树作为基础学习（正如所见，集成学习并不限于决策树）则提供了许多优势。这是因为它可以自动选择它所需的特征。它不需要指定函数形式（如回归中的公式）、缩放，或特征与目标之间的线性关系。

在下一节中，在看到 Scikit-learn、XGBoost、LightGBM 中具体算法的运行之前，我们将尝试构建一个我们自己的梯度提升的简单实现版本，以理解如何使用这一强大的算法。

## 5.2.1 梯度提升如何工作



GBDT 的所有实现都提供了多种需要设置的超参数，以便在你正尝试解决的数据问题上获得最佳结果。弄清楚每个设置的作用是一项挑战，而采取不可感知策略并将任务交给自动调优程序并没有太大帮助，因为你将面临调优算法应该调优什么以及如何调优的挑战。

根据我们的经验，编写一个简单的实现是理解算法工作原理以及确定超参数与性能、结果之间关系的最佳方式。列表 5.6 展示了一个 `GradientBoosting` 类，它能够处理任何二分类问题，例如我们正在作为示例处理的 Airbnb 数据集，它使用了两个梯度下降过程的参数以及来自 Scikit-learn 提供的决策树模型的参数。

代码创建了 `GradientBoosting` 类，该类包含了拟合、预测概率和预测类别的方法。在内部，它将拟合的决策树序列存储在一个列表中，从该列表中可以顺序访问，以重构以下公式：

> H(X) = \sum_{m=1}^{M} \nu \cdot h_m(X, w_m)

在公式中，

- H(X) 是应用于预测变量 X 的梯度提升模型
- M 对应于使用的树估计器数量
- $\nu$ 代表学习率
- $w^m$ 代表必须预测的来自之前树的修正值
- 符号 $h^m$ 指所使用的第 m 棵决策树

有趣的是，梯度提升树总是回归树（即使对于分类问题也是如此）——这就是为什么我们选择使用 Scikit-learn 的 `DecisionTreeRegressor`。这也解释了为什么 GBDT 在预测概率方面比其他基于树的集成模型更好：梯度提升直接对类别概率的对数进行回归，从而以一种与逻辑回归相似的方式进行优化。另一方面，像随机森林这样的梯度提升算法是针对纯度指标优化的，它们通过计算叶子节点中某一类别的比例来估计概率，这并不是真正的概率估计。通常情况下，GBDT 输出的概率是正确的，它们很少需要概率校准，概率校准是一种后处理步骤，用于调整预测概率，以提高它们在如医疗诊断（疾病检测）、欺诈检测或信用风险评估等应用中的准确性和可靠性。

在我们的代码实现中，我们允许传递任何参数给 `DecisionTreeRegressor`（如[此处所示](https://mnz.b/9VQQs)），尽管最有用的是与树生长复杂度相关的参数，例如 `max_depth` 和 `min_samples_leaf`，它们分别是拆分内部节点或成为叶子节点所需的最小样本数。

每个树回归器的作用是提供一个 `w` 向量，其中包含与之前的估计值相加的修正值，并由学习率加权。每个 `w` 都依赖于前一个，因为它是一个在梯度上训练的树回归器，用于修正估计以匹配真实的分类。这些链式向量类似于梯度修正序列——起初很大，然后越细越细，最终收敛于一个最优预测。梯度下降与我们在第 4 章介绍的梯度优化过程完全相似。此外，通过改变你计算梯度的基础的代价函数，你可以要求 GBDT 针对不同的损失进行优化。

# 列表 5.6 构建一个梯度提升分类器

```python
from sklearn.tree import DecisionTreeRegressor
import numpy as np

class GradientBoosting:
    def __init__(self, learning_rate=0.1, n_estimators=10, **params):
        self.learning_rate = learning_rate
        self.n_estimators = n_estimators
        self.params = params
        self.trees = []

    def sigmoid(self, x):
        x = np.clip(x, -100, 100)
        return 1 / (1 + np.exp(-x))

    def logit(self, x, eps=1e-6):
        xp = np.clip(x, eps, 1-eps)
        return np.log(xp / (1 - xp))

    def gradient(self, y, y_true, y_pred):
        gradient = y_pred - y_true
        return gradient

    def fit(self, X, y):
        self.init = self.logit(np.mean(y))
        y_pred = self.init * np.ones(X.shape[0])
        for k in range(self.n_estimators):
            gradient = self.gradient(y, y, y_pred)
            tree = DecisionTreeRegressor(**self.params)
            tree.fit(X, gradient)
            self.trees.append(tree)
            y_pred += self.learning_rate * tree.predict(X)

    def predict_proba(self, X):
        y_pred = self.init * np.ones(X.shape[0])
        for tree in self.trees:
            y_pred += self.learning_rate * tree.predict(X)
        return self.sigmoid(y_pred)

    def predict(self, X, threshold=0.5):
        proba = self.predict_proba(X)
        return np.where(proba >= threshold, 1, 0)
```

