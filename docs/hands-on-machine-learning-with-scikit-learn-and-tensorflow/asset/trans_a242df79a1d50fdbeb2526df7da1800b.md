
特征采样会产生更多的预测器多样性，通过稍微增加偏差来换取更低的方差。

# 随机森林

正如我们讨论过的，随机森林是决策树的集成，通常通过 bagging 方法（有时是 pasting）进行训练，通常将 `max_samples` 设置为训练集的大小。与其构建一个 `BaggingClassifier` 并向其传递一个 `DecisionTreeClassifier`，你可以使用 `RandomForestClassifier` 类，它更方便并且针对决策树进行了优化¹⁰（同样地，对于回归任务，它是 `RandomForestRegressor`）。以下代码使用所有可用核心训练了一个具有 500 棵树（每棵树限制最多 16 个节点）的随机森林分类器：

```
from sklearn.ensemble import RandomForestClassifier

rnd_clf = RandomForestClassifier(n_estimators=500, max_leaf_nodes=16, n_jobs=-1)
rnd_clf.fit(X_train, y_train)
```

除某些例外外，`RandomForestClassifier` 拥有 `DecisionTreeClassifier` 的所有超参数（用于控制树的生长），以及控制集成本身的 `BaggingClassifier` 的所有超参数¹¹。

随机森林算法在生长树时引入了随机性；在分裂节点时，不是搜索最佳特征（见第 6 章），而是在随机特征子集中搜索最佳特征。这导致了更大的多样性，（再次）用更高的偏差换取了更低的方差，通常会产生更好的整体模型。下面的 `BaggingClassifier` 大约等同于随机随机森林：

```
bag_clf = BaggingClassifier(
  DecisionTreeClassifier(splitter="random", max_leaf_nodes=16),
  n_estimators=500, max_samples=1.0, bootstrap=True, n_jobs=-1)
```

> 9 "随机森林决策," T. Ho. (1995).
¹0 如果你想构建一个除决策树以外的对象的包（bag），`BaggingClassifier` 类仍然有用。
¹¹ 有有几个值得注意的例外：`splitter` 不存在（强制为 "random"）、`presort` 不存在（强制为 False）、`max_samples` 不存在（强制为 1.0），且 `base_estimator` 不存在（强制为带有所提供超参数的 `DecisionTreeClassifier`）。

# 极端树 (Extra-Trees)

在随机森林中生长树时，每个节点只考虑特征的随机子集用于分裂（如前所述）。通过对每个特征也使用随机阈值而不是搜索最佳可能的阈值（如普通的决策树），可以使树更加随机。

由极端随机树组成的森林简单称为极端随机树集成（Extremely Randomized Trees ensemble，简称 Extra-Trees）¹。再次，这是用更多的偏差换取更低的方差。它使得 Extra-Trees 的训练速度比普通森林快得多，因为为每个特征寻找可能的阈值是生长树最耗时的任务之一。

你可以使用 Scikit-Learn 的 `ExtraTreesClassifier` 创建 Extra-Trees 分类器。它的 API 与 `RandomForestClassifier` 类相同。同样，`ExtraTreesRegressor` 类与 `RandomForestRegressor` 具有相同的 API。

![](img/0684d2da98e09085c0a622d4fd69aaad_225_0.png)

很难预测随机森林的表现会优于还是劣于 Extra-Trees 分类器。通常情况下，唯一的办法是都尝试并使用交叉验证对它们进行比较（并使用网格搜索调整超参数）。

# 特征重要性

随机森林的另一个伟大特性是它们很容易衡量每个特征的相对重要性。Scikit-Learn 通过观察树节点使用该特征平均减少不纯度的程度（跨越森林中的所有树）来衡量特征重要性。更精确地说，这是一个加权平均值，其中每个节点的权重与其相关的训练样本数量相等（见第 6 章）。

Scikit-Learn 在训练后自动为每个特征计算此值，它缩放了结果，使得所有重要性之和等于 1。你可以通过 `feature_importances_` 变量访问结果。例如，以下代码在 iris 数据集上训练随机森林并输出每个特征的重要性。它发现最重要的特征是花瓣长度（petal length）和花瓣宽度（petal width），而花萼长度（sepal length）和花萼宽度（sepal width）则不重要。

```python
from sklearn.ensemble import RandomForestClassifier
from sklearn.datasets import load_iris

iris = load_iris
rnd = RandomForestClassifier(n_estimators=100)
rnd.fit(iris.data, iris.target)

for name, importance in zip(iris.feature_names, rnd.feature_importances_):
    print(f"{name}: {importance:.3f}")
```

输出示例：
```
sepal length (cm): 0.045
sepal width (cm): 0.040
petal length (cm): 0.449
petal width (cm): 0.466
```

# 提升 (Boosting)

提升（最初称为 Boosting）指的是任何将弱学习器组合成更强学习器的方法。提升方法的通用思想是顺序地训练预测器。有很多提升方法，但最流行的是 AdaBoost³（Adaptive Boosting 的缩写）和梯度提升（Gradient Boosting）。

# AdaBoost

预测器纠正前一个预测器的一种方法是对预测错误的的实例给予更多关注。这是 AdaBoost 使用的技术。例如，为了构建 AdaBoost，训练第一个分类器（如决策树）并用对训练集进行预测，然后增加错误实例的相对权重。第二个分类器使用更新后的权重进行训练，依此类推。这导致预测器更多地关注困难案例（见图 7-7）。

![](img/0684d2da98e09085c0a622d4fd69aaad_227_0.png)

图 7-7. 权重更新的 AdaBoost

图 7-8 显示了 moons 数据集上连续预测器的决策边界（在本例中，每个预测器都是带有 RBF 核的 SVM¹⁴）。第一个分类器弄错了许多实例，因此它们的权重被增加。因此，第二个分类器在这些实例上的表现更好，依此类推。你可以看到，这种顺序学习技术与梯度下降许多相似之处，除了学习率减半（即每次迭代中错误实例的权重增加减半），AdaBoost 是将预测器添加到集成中，逐渐使其更好。

![](img/0684d2da98e09085c0a622d4fd69aaad_228_0.png)

图 7-8. 连续预测器的决策边界

一旦所有预测器训练完成，集成预测的方式与 bagging 或 pasting 非常相似，只是预测器的权重取决于它们在加权训练集上的总准确率。

> 这种顺序学习技术有一个重要的缺点：它无法并行（或只能部分并行），因为每个预测器只有在前一个预测器训练并评估后才能进行训练。因此，它的扩展性不如 bagging 或 pasting。

让我们仔细观察 AdaBoost 算法。每个实例权重 $w^{(i)}$ 初始设置为 $\frac{1}{m}$。训练第一个预测器并在训练集上计算其加权错误率 $r_1$；见公式 7-1。

公式 7-1. 加权错误率

```
r_j = \frac{\sum_{i=1}^{m} w^{(i)} [y^{(i)} \neq \hat{y}^{(i)}]}{\sum_{i=1}^{m} w^{(i)}}
```
