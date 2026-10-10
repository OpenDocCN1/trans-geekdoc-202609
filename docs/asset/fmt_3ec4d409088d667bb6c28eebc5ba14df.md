
![](img/0684d2da98e09085c0a622d4fd69aaad_96_0.png)

## 自定义转换器

尽管 Scikit-Learn 提供了许多实用的转换器，但你可能需要为自定义清理操作或合并属性等任务编写转换器。当你希望你的转换器与 Scikit-Learn 的功能（如管道）无缝工作时，由于 Scikit-Learn 依赖于鸭子类型（而不是继承），你只需要创建一个类并实现三个方法：`fit`（返回 `self`）、`transform()` 和 `fit_transform()`。通过添加 `TransformerMixin` 作为基类，你可以免费获得最后一个方法。此外，如果你使用 `BaseEstimator` 作为基类（并在构造函数中使用 `*args` 和 `**kwargs`），你将获得两个额外的方法（`get_params()` 和 `set_params()`），这些对于自动-

自动超参数调优。例如，这里是一个小的 transformer 类，添加了我们之前讨论的组合属性：

```python
from sklearn.base import BaseEstimator, TransformerMixin

rooms_ix, bedrooms_ix, population_ix, households_ix = 3, 4, 5, 6

class CombinedAttributesAdder(BaseEstimator, TransformerMixin):
    def __init__(self, add_bedrooms_per_room=True): # 没有 *args 或 **kwargs
        self.add_bedrooms_per_room = add_bedrooms_per_room
    def fit(self, X, y=None):
        # 无需其他操作
        return self
    def transform(self, X, y=None):
        rooms_per_household = X[:, rooms_ix] / X[:, households_ix]
        population_per_household = X[:, population_ix] / X[:, households_ix]
        if self.add_bedrooms_per_room:
            bedrooms_per_room = X[:, bedrooms_ix] / X[:, rooms_ix]
            return np.c_[X, rooms_per_household, population_per_household, bedrooms_per_room]
        else:
            return np.c_[X, rooms_per_household, population_per_household]
```

`attr_adder = CombinedAttributesAdder(add_bedrooms_per_room=False)`

`housing_extra_attribs = attr_adder.transform(housing.values)`

在这个示例中，该 transformer 有一个超参数 `add_bedrooms_per_room`，默认设置为 `True`（提供合理的默认值是有帮助的）。这个超参数允许你轻松地发现添加这些属性是否有助于机器学习算法。此外，你还可以为任何你不 100% 确定的数据准备步骤添加超参数。你自动化的这些数据准备步骤越多，你可以自动尝试的组合就越多，这让你找到良好组合的可能性大得多（并节省大量时间）。

## 特征缩放 (Feature Scaling)

你需要对数据应用的最重要转换之一是特征缩放。除少数例外外，当输入数值属性的尺度差异很大时，机器学习算法的表现并不理想。房价数据就是如此：房间总数从约 6 到 39,320 不等，而中位数收入仅在 0 到 15 之间。注意，通常不需要对值进行缩放。

让所有属性具有相同尺度有两种方法：最小极大缩放（min-max scaling）和标准化（standardization）。

最小极大缩放（许多人称为标准化）非常简单：值被平移并重新缩放，使其范围变为 0 到 1。我们通过减去该值并除以最大值来实现。Scikit-Learn 提供了一个名为 `MinMaxScaler` 的 transformer 用于此。它有一个 `feature_range` 超参数，如果你由于某种原因不想希望使用 0–1 的范围，可以通过它更改范围。

标准化则完全不同：它首先减去平均值（使得标准化后的值均值始终为零），然后除以标准差，使得结果分布具有单位方差。与最小极大缩放不同，标准化不会将值限制在特定范围内，这对于某些算法来说可能是一个问题（例如，神经网络期望输入值在 0 到 1 之间）。然而，标准化受离群值的影响要小得多。例如，假设某个地区的中位数收入为 100（错误产生）。最小极大缩放会将所有其他 0–15 之间的值压缩到 0–0.15，而标准化则不会受到太大影响。Scikit-Learn 提供了一个名为 `StandardScaler` 的 transformer 用于标准化。

在所有转换中，重要的是将缩放器固定在训练数据上，而不是整个数据集（包括测试集）。只有这样，你使用它们来转换训练集和测试集（以及新数据）。

![](img/0684d2da98e09085c0a622d4fd69aaad_98_0.png)

## 转换流水线 (Transformation Pipelines)

你可以看到，有很多按正确顺序执行的数据转换步骤。幸运的是，Scikit-Learn 提供了 `Pipeline` 类来帮助此类转换序列。这里有一个针对数值属性的小流水线：

```python
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
```

```python
num_pipeline = Pipeline([
    ('imputer', SimpleImputer(strategy="median")),
    ('attribs_adder', CombinedAttributesAdder()),
    ('std_scaler', StandardScaler())
])
```

`housing_num_tr = num_pipeline.fit_transform(housing_num)`

`Pipeline` 构造函数接受一个名称/估计器对列表来定义步骤序列。除了最后一个外，所有的必须是 transformer（即它们必须具有 `fit_transform` 方法）。名称可以是任意的（只要是唯一的且不包含双下划线 `__`）；它们在稍后的超参数调优将非常有用。

当你调用 `pipeline.fit()` 方法时，它会按顺序对所有 transformer 调用 `fit_transform()`，将每次调用的输出作为下一次调用的参数，直到到达最终的估计器，对于该估计器它只调用 `fit()`。

流水线暴露了与最终估计器相同的方法。在这个示例中，最后一个估计器是 `StandardScaler`，它是一个 transformer，因此流水线有一个 `transform()` 方法，可以将所有转换应用到数据上（当然还有一个 `fit_transform()` 方法，这是我们使用的那个）。

到为止，我们分别处理了类别列和数值列。如果有一个的 transformer 来处理所有列，并对每列应用适当的转换，会更方便。在 20 版本中，引入了 `ColumnTransformer` 来实现这一目的，并对每列应用相应的转换：

```python
from sklearn.compose import ColumnTransformer

housing_num = housing.select_dtypes(include=[np.number])
num_cols = list(housing_num.columns)
housing_cat = housing.select_dtypes(exclude=[np.number])
cat_cols = list(housing_cat.columns)

full_pipeline = ColumnTransformer([
    ("num", num_pipeline, num_cols),
    ("cat", OneHotEncoder(), cat_cols),
])

housing_prepared = full_pipeline.fit_transform(housing)
```

`ColumnTransformer` 构造函数接受一个元组列表，每个元组包含一个名称、一个估计器和列的列表。它会按顺序对所有估计器调用 `fit_transform()`，将每次调用的输出作为下一次调用的参数，直到到达最终的估计器，对于该估计器它只调用 `fit()`。

`ColumnTransformer` 暴露了与最终估计器相同的方法。在这个示例中，最后一个估计器是 `StandardScaler`，它是一个 transformer，因此流水线有一个 `transform()` 方法，可以将所有转换应用到数据上（当然还有一个 `fit_transform()` 方法，这是我们使用的那个）。

如果你使用的是 Scikit-Learn 0.19 或更早版本，可以使用第三方库如 `sklearn-pandas`，或者尝试自定义 transformer 来获得 `ColumnTransformer` 的功能。或者，你可以使用 `FeatureUnion` 类，它可以应用不同的 transformer 并合并它们的输出，但你无法为每个 transformer 指定列，它们都应用于整个数据。可以通过自定义 transformer 绕过此限制（参见 Jupyter 笔记本中的示例）。

它确实有效，尽管预测结果并不完全准确（例如，第一个预测值偏差了近 40%！）。让我们使用 Sikit-Learn 的 `mean_squared_error` 函数测量整个训练集的回归模型 RMSE：

```
>>> from sklearn.metrics import mean_squared_error
>>> housing_predictions = lin_reg.predict(housing_prepared)
>>> lin_mse = mean_squared_error(housing_labels, housing_predictions)
>>> lin_rmse = np.sqrt(lin_mse)
>>> lin_rmse
6828.198194822
```

好吧，这总比没有要强，但显然是一个糟糕的分：大多数地区的房价中位数介于 $120,000 到 $265,000 之间，$68,628 的典型预测误差并不令人满意。这是模型对训练数据出现欠拟合（underfitting）的例子。当这种情况发生时，可能意味着特征没有提供足够的信息来做出良好的预测，或者模型不够强大。正如我们在上一章中看到的，修复欠拟合的主要方法是选择更强大的模型、使用更好的特征调优训练算法，或者减少对模型的约束。这个模型没有进行正则化，因此排除了最后一种选择。你可以添加更多特征（例如人口的对数），但让我们尝试一个更复杂的模型看看效果如何。

让我们训练一个 `DecisionTreeRegressor`。这是一个强大的模型，能够发现数据中复杂的非线性关系（决策树将在第 6 章中详细介绍）。代码看起来应该像这样：

```
tree_reg = DecisionTreeRegressor()
tree_reg.fit(housing_prepared, housing_labels)
```

现在模型已经训练好了，让我们在训练集上对其进行评估：

```
>>> housing_predictions = tree_reg.predict(housing_prepared)
>>> tree_mse = mean_squared_error(housing_labels, housing_predictions)
>>> tree_rmse = np.sqrt(tree_mse)
>>> tree_rmse
0.0
```

等一下，完全不是！这个模型可能是绝对完美的吗？当然，更有可能是模型对数据导致了过拟合（overfit）。你如何能确定呢？正如我们之前看到的，在准备好发布模型之前，你不想触碰测试集，因此你需要使用部分训练集进行训练，另一部分用于模型验证。

## 使用交叉验证进行更好的评估

评估决策树模型的一种方法是使用 `train_test_split` 将训练集拆分为一个较小的训练集和一个验证集，然后

```
>>> lin_scores = cross_val_score(lin_reg, housing_prepared, housing_labels,
               scoring="neg_mean_squared_error", cv=10)
...
>>> lin_rmse = np.sqrt(lin_scores)
>>> display_scores(lin_rmse)

Scores: [6782.73843989 66960.118071 70347.952441 74739.570525
60831.133893 71938.841826 64969.63056405 68281.613799
71552.9156558 46352.100826]

Mean: 69052.461364508
Standard deviation: 2731.6740179
```

决策树模型过拟合非常严重，表现甚至不如线性回归模型。让我们尝试最后一个模型：`RandomForestRegressor`。正如我们在第 7 章中看到的，随机森林通过在特征子集上训练许多决策树并取平均值来工作。在其他模型之上构建模型被称为集成学习（Ensemble Learning），通常是进一步提升机器学习算法的好方法。我们将跳过大部分代码，因为它与其他模型基本相同：

```
>>> sklearn.ensemble import RandomForestRegressor
>>> forest_reg = RandomForestRegressor()
>>> forest_reg.fit(housing_prepared, housing_labels)
>>> [...]
>>> forest_rmse
18083.518213763
>>> display_scores(forest_rmse)
Scores: [49519.80364233 47461.915823 50029.02762854 52325.2086953
49308.3926421 53446.379262 48634.8036574 47585.7383231
53490.1069751 50021.582592]

Mean: 50182.33103396
Standard deviation: 2097.081050963
```

哇，这好得多：随机森林看起来很有前景。但注意，训练集上的得分仍然低于验证集，这意味着模型仍然在过拟合训练集。过拟合的解决方案是简化模型、约束模型（即正则化）或获取更多训练数据。然而在深入研究随机森林之前，你应该尝试来自各种机器学习算法的模型（带有不同内核的支持机、可能的神经网络等），而不是花费大量时间在调优超参数上。目标是筛选出几个最有前景的模型。

你应该保存每个模型实验，这样就可以轻松回到任何你需要的模型。确保同时保存超参数和训练后的参数，以及交叉验证得分，也许还有实际预测值。这将让你能够轻松比较不同模型类型的得分并比较错误类型。你可以使用 Python 的 `pickle` 模块或使用 `sklearn.externals` 来轻松保存 Scikit-Learn：

```python
from sklearn.externals import joblib
joblib.dump(forest_reg, "my_model.pkl")
model_loaded = joblib.load("my_model.pkl")
```

## 调优你的模型

当你不知道什么值合适时，简单的方法是尝试 10 的幂（如果你想要更小的数字）。相反，使用 Scikit-Learn 的 `GridSearchCV` 来搜索所有组合。你只需要像示例所示告诉它：

```python
from sklearn.model_selection import GridSearchCV

param_grid = {
  'n_estimators': [3, 10, 30],
  'max_features': [2, 4, 6, 8],
  'bootstrap': [False],
}

forest_reg = RandomForestRegressor()

grid_search = GridSearchCV(forest_reg, param_grid, cv=5,
  scoring='neg_mean_squared_error',
  return_train_score=True)

grid_search.fit(housing_prepared, housing_labels)
```

总而言，网格搜索将探索 3 x 6 = 18 种随机森林组合，它将训练每个模型五次（使用五折交叉）。换句话说，总而言，将有 18 x 5 = 90 轮训练！这可能需要很长时间，但完成后你将得到这样的最佳参数组合：

```
>>> grid_search.best_params_
{'max_features': 8, 'n_estimators': 30}
```

> 8 和 30 是评估过的最大值，你可能应该尝试更高的值，因为得分可能会继续提高。

你也可以直接获取最佳估计器：
