
然后，创建一个包含 10 行（示例）和 3 个特征（列）的随机集合。将数据多次传递给上述函数，并观察输出的变化。你会发现输出的大小与输入相同，这是装袋法（bagging）和随机森林的默认设置。²

### 7.2.5 随机森林 (random forests)

`Bagging` 仅通过在数据的不同自助样本上进行训练来寻求优化不相关的模型，而随机森林 [5] 通过向树的每个节点提供总可用特征的随机子集进一步增加了随机性。通过这种方式，每个决策桩（decision stump）在训练时并不寻找最优特征，从而强制每棵树为每个分类问题找到多个不同的解决方案，增加了随机性，并进一步降低了所有树之间预测结果的相关性。整体效果是减少模型方差和过拟合概率。（见第 7.2 节，第 8），随机森林总是构建树的集成。

> ² 示例代码和解决方案可以在 `github.com/MachineLearningBiomedicalApplication-notebooks` 获取。

## 7.2.6 使用 scikit-learn 训练装袋和森林

要使用 scikit-learn 实现装袋和森林，请从 ensemble 基类导入模型，例如，用于分类：

```python
from sklearn.ensemble import BaggingClassifier
from sklearn.ensemble import RandomForestClassifier
```

`n_trees=50`

# 创建一个包含 50 棵决策树的装袋集成
`clf=BaggingClassifier(DecisionTreeClassifier(), n_estimators=n_trees)`

# 创建一个包含 50 棵树的随机森林
# 使用总特征数的 30%
`clf=RandomForestClassifier(n_estimators=n_trees, max_features=0.3)`
```

你应该认为装袋分类器的第一个参数是基模型的选择，而随机森林则没有这种选择。在两种情况下，你都可以使用 `n_estimators` 控制集成模型的大小。

随机森林类的参数与决策树类的参数并行，`max_features` 特别决定了每个节点处特征的欠采样程度。例如，使用浮点数（0.3）这会将随机选择的特征数量设置为总可用特征的 30%。有关所有参数的完整选项，请参阅 scikit-learn 文档。

### 7.2.7 袋外误差 (Out-of-bag error)

训练装袋集成的一个优势是，可以通过在自助采样期间遗留的示例上对每棵树进行测试，从而返回一个对可能泛化能力的估计。这些样本被称为袋外（out-of-bag, oob）样本。对于大型数据集，这可以设置为大约 37%。一旦训练了所有模型，可以使用平均值或多数投票合并每个训练示例的袋外预测；然后可以根据所有示例的准确率（分类）或误差（回归）计算最终得分。要使用 scikit-learn 跟踪误差，在实例化模型时设置 `oob_score=True`，例如：

```python
# 在训练期间跟踪 oob 误差
clf=BaggingClassifier(DecisionTreeClassifier(), n_estimators=n_trees, oob_score=True)
```

训练后可以使用 `oob_score_` 属性返回袋外性能：

## 7.2.8 提升 (Boosting)

```python
# 训练模型
clf.fit(X,Y)

# 报告 oob 分
print("the oob score is ".format(clf.oob_score))
```

提升与装袋和森林的区别在于，它是串行地标记弱学习器。在拟合完每个模型后，会识别被错误分类的示例并在后续运行中赋予其更高的权重。

要查看它是如何工作的，请参考图 7.8 中的示例。在这种情况下，不同类别的示例由加号或减号表示。从图 7.8a 可以看出，完美的监督需要一个非线性决策边界。7.8b-f 模拟了提升的过程。7.8b 中，红框拟合了一个初始的轴对齐决策步。它正确地分类了两个红色交叉和所有的减号类。然而，有三个红色交叉被错误分类为属于蓝色类。图 7.8c 显示了提升如何在第二轮中升级被错误分类的示例，确保这些示例被第二个分类器正确分类（如图 7.8d 所示）；现在这里有三个蓝色被错误分类，因此在第三轮中被提升。第三个也是最终的分类器是图 7.8e 中的集成模型。它在垂直轴上训练了一个轴对齐的分类器，正确地分类了加权的交叉和减号类。我们可以看到，当集成模型中的所有三个分类器结合时（权重如图 7.8f 所示），最终结果实现了所有示例的正确分类。

通过这种方式，提升可以学习到精确的非线性模型，与单个学习器相比，这显著提高了集集的准确性。事实证明，即使训练性能已经饱和，提升仍然通过边际继续优化预测并进一步优化每个基学习器的损失 [42]。换句话之，它试图使类别之间的边际更大，类似于支持机的行为。

## 7.2.9 AdaBoost

提升有许多变体，主要区别在于它们在训练期间组合和加权的方式。在这里，我们将关注最早且最广为人知的算法之一 AdaBoost [15]，其中我们假设每个学习器都是一个轴对齐的决策桩，类似于图 7.8 所示的。

AdaBoost 分类器（算法 7.2）首先为训练集中的所有示例分配相同的权重（$w_i = \frac{1}{n}$）。然后，对于每棵树或桩，算法首先估计 $p^i$（它代表每个示例的归一化权重或概率）。

决策树与集成学习 167

`img/d219b4c20ff50f4b97845decacecb185_0.png`
`img/d219b4c20ff50f4b97845decacecb185_1.png`
`img/d219b4c20ff50f4b97845decacecb185_2.png`
`img/d219b4c20ff50f4b97845decacecb185_3.png`
`img/d219b4c20ff50f4b97845decacecb185_4.png`
`img/d219b4c20ff50f4b97845decacecb185_5.png`

**图 7.8** 提升玩具示例。

**算法 7.2** AdaBoost 分类器。
给定 $\mathbf{x} \in \mathbf{X}$ 和 $y_i \in \{0, 1\}$
为所有 $n$ 个示例分配相同的权重 $w_t' = 1/n$
**for** $t$ 在 $E$ 中 **do**
$\quad \mathbf{w}^t' = \mathbf{w}^t / \sum w_i^t$ // 对于集成中的每棵树 $t$
$\quad$ 将权重转换为概率
$\quad \quad f_i = \text{decision\_stump}(\mathbf{x}_i)$ // 拟合决策桩
$\quad \quad \epsilon = \frac{1}{n} \sum w_i [y_i \neq f_i]$ // 计算误差
$\quad \quad \beta_t = \ln(\frac{1-\epsilon}{\epsilon})$ // 计算权重
$\quad \quad w_i^{t+1} = w_i^t \exp(\beta_t [y_i \neq f_i])$ // 更新权重
**end for**

## 算法 7.3 Adaboost 回归

给定 $x_i \in \mathbf{X}$ 和 $y_i \in \{0, 1\}$

为所有 $n$ 个样本分配相等权重 $u_i^1 = 1/n$

```python
for $t$ in $E$ do
  $p \leftarrow w^t / \sum^n w^t$
  $f_t(\mathbf{X}, \theta) = \text{train\_stump}(\mathbf{X}, \mathbf{y})$
  $D \leftarrow |f_t(x_i, \theta) - y_i|$
  $L \leftarrow \sum^n p_i L_i$
  $\bar{L} = \sum p_i$
  $\beta_t \leftarrow 1/\bar{L}$
  $w_i^{t+1} \leftarrow w_i^t \beta_t^{1-L_i}$
end
```

- 对于集成中的每个树 $t$
- 将权重转换为概率
- 以 $D$ 为归一化因子计算损失
- 平均损失
- 更新权重

与 bagging 类似，可以传递任何选择的基估计器，默认是 `max_depth=1` 的决策树——在其他方法中，则是轴对齐的决策树（decision stump）。与之前一样，集集的规模由 `n_estimators` 控制。

## 7.2.11 集成学习的 GridSearchCV

在 scikit-learn 中优化模型方法时，需要注意的一点是基模型参数传递给 `GridSearchCV` 的各种方式。通常情况下，待优化的网格搜索函数接受字典形式的参数范围，其中参数作为字典键提供（例如，下文的 `n_estimators` 参数）。对于基学习器，你还需要指定以 `base_estimator__` 关键字为前缀的参数；随后将展示 `DecisionTreeClassifier` 的 `min_samples_leaf` 参数为例，该参数作为 bagging 集成的一部分进行优化的。

```python
from sklearn.tree import Classifier
from sklearn.ensemble import BaggingClassifier
from sklearn.model_selection import GridSearchCV
```

```python
# 参数字典
param_dist = {"base_estimator__min_samples_leaf": [5, 10, 20], # 基模型的参数
  "n_estimators": [50, 100, 250, 500] # 集成模型的参数
}
```

```python
# 实例化模型
model=BaggingClassifier(DecisionTreeClassifier())
```

```python
# 创建 GridSearchCV 实例
grid = GridSearchCV(estimator=model, param_grid=param_dist)
# 在训练数据上运行网格搜索
grid.fit(X, y)
```

```python
# 使用优化后的参数创建模型
model=BaggingClassifier(base_estimator=DecisionTreeClassifier(min_samples_leaf=grid.best_estimator_base_estimator_min_samples_leaf, n_estimators=grid.best_estimator_n_estimators)
```
