
# Python scikit-learn ensemble 模块包含用于回归问题的随机森林算法

该模块还包含梯度提升算法。首先，本节解释实例化 `RandomForestRegressor` 类成员所需的参数。然后，本节使用 `RandomForestRegressor` 类为葡萄酒口味数据训练随机森林模型，并探索模型的性能。

## 构建 RandomForestRegressor 对象

以下是 `sklearn.ensemble.RandomForestRegressor` 的类构造函数：

```
sklearn.ensemble.RandomForestRegressor(n_estimators=10, criterion=
'mse', max_depth=None, min_samples_split=2, min_samples_leaf=1,
max_features= 'auto', max_leaf_nodes=None, bootstrap=True, 
oob_score=False, n_jobs=1, random_state=None, verbose=0, 
min_density=None, compute_importances=
None)
```

以下描述参考了 sklearn 文档，但仅涵盖您最可能想要更改的参数值。对于这些参数，列表描述了如何选择默认值的替代方案。要查看此处未涵盖的参数的描述，请参阅 sklearn 包文档。以下列表描述了这些参数：

### `n_estimators`

*integer, optional (default = 10)*

这是集成中树的数量。如果您编码正确，默认值可以使用，但通常您需要超过 10 棵树才能获得最佳性能。您可以尝试不同的数量，以了解需要多少棵树。正如本书始终强调的，合适的模型复杂度（树的深度和树的数量）取决于底层问题的复杂性以及您拥有的数据量。一个好的起点是 100–500。

### `max_depth`

*integer or None, optional (default=None)*

如果此参数设置为 `None`，则树将生长直到所有叶节点要么是纯净的，要么包含的样本少于 `min_samples_split` 个。作为指定树深度的替代方案，您可以使用 `max_leaf_nodes` 来指定树中的叶节点数量。如果您指定了 `max_leaf_nodes`，则 `max_depth` 将被忽略。将 `max_depth` 设置为 `auto` 并生长全深度树可能具有性能优势。这也伴随着与全深度树相关的训练时间成本。如果您需要多次训练运行来完成建模过程，可能需要尝试不同的深度。

### `min_samples_split`

*integer, optional (default=2)*

包含样本数少于 `min_samples_split` 的节点将不会被分裂。分裂较小的节点是过拟合的来源。

### `min_samples_leaf`

*integer, optional (default=1)*

如果分裂导致节点包含的样本数少于 `min_samples_leaf`，则不会进行该分裂。此参数的默认值导致该参数被忽略，这通常没问题——特别是在您对数据集进行前几次训练运行时。您可以从几个方面考虑为该参数选择一个有意义的值。一是分配给叶节点的值是该叶节点中样本的平均值，如果叶节点中有不止一个样本，您将获得方差更低的平均值。另一种考虑该参数的方式是将其作为控制树深度的替代方法。

### `max_features`

*integer, float or string, optional (default=None)*

寻找最佳分裂时考虑的特征数量取决于 `max_features` 设置的值以及问题中的特征数量。将问题中的特征数量称为 `nFeatures`。则：

*   如果 `max_features` 的类型是 `int`，则在每次分裂时考虑 `max_features` 个特征。注意：`max_features > nFeatures` 会抛出错误。
*   如果 `max_features` 的类型是 `float`，则 `max_features` 是要考虑的特征比例：`int(max_features * nFeatures)`。
*   可能的字符串值包括以下内容：

```
auto max_features=nFeatures
sqrt max_features=sqrt(nFeatures)
log2 max_features=log2(nFeatures)
If max_features=None, then max_features=nFeatures.
```

Breiman 和 Cutler 建议对回归问题使用 `sqrt(nFeatures)`。答案通常对 `max_features` 不太敏感，但该参数可能有一些影响，因此您需要测试一些替代值。

### `random_state`

*int, RandomState instance, or None (default=None)*

*   如果类型是 `integer`，该整数将用作随机数生成器的种子。
*   如果 `random_state` 是 `RandomState` 的实例，则该实例将用作随机数生成器。
*   如果 `random_state` 为 `None`，则随机数生成器是 `numpy.random` 使用的 `RandomState` 实例。

`RandomForestRegressor` 有几个属性，包括组成集成的训练好的树。有一个 predict 方法将使用训练好的树进行预测，因此您通常不会直接访问那些树。您会想要访问变量 `feature_importances_`。以下是描述：

### `feature_importances_`

这是一个数组，其长度等于问题中的特征数量（前文称为 `nFeatures`）。数组中的值为正浮点数，表示相应属性的相对重要性。`importances` 由 Breiman 在随机森林原始论文中发明的程序确定。基本思想是，一次随机打乱每个属性的值，并确定模型预测准确性的变化。预测准确性受损越大，该属性越重要。

以下是所用方法的描述：

### `fit(XTrain, yTrain, sample_weight=None)`

`XTrain` 是属性值的数组。它有 `nInstances` 行和 `nFeature` 列。`yTrain` 是目标值数组。`y` 也有 `nInstances` 行。在本章您将看到的示例中，`yTrain` 将只有一列，但该方法可以拟合具有不同目标的多个模型。为此，`y` 将有 `nTargets` 列——每组结果一列。`sample_weight` 使得为训练数据中的每个实例分配不同的权重成为可能。它可以采取两种形式之一。默认值 `None` 导致所有输入实例权重相等。要对每个实例应用不同的权重，`sample_weight` 应为具有 `nInstances` 行和一列的数组。

### `predict(XTest)`

`XTest` 是用于生成预测的属性值数组。输入 `predict()` 的数组与用于 `fit()` 方法训练的数组具有相同数量的列，但可以有不同数量的行，包括可能只有一行。`predict()` 输出中的行与训练中使用的目标数组 `y` 中的行具有相同的形式。

## 使用 RandomForestRegressor 对葡萄酒口味建模

[Listing 7-2](#c07.xhtml#c07-fea-0002) 展示了如何使用 sklearn 版本的随机森林算法构建集成模型来预测葡萄酒口味。

