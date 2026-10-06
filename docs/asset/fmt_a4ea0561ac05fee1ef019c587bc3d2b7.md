
model_for_pruning.fit(X_train, y_train, callbacks=callbacks, epochs=300, validation_split=0.2, verbose=0)
%tensorboard --logdir={log_dir}

![](img/src158.jpg)

其他的剪枝摘要也可以在 Tensorboard 上查看。(rsrc159.jpg)

现在我们定义一个函数来计算模型的大小。

```python
def get_gzipped_model(model, mode_name, zip_name):
    # 返回压缩模型的大小（字节）。
    model.save(mode_name, include_optimizer=False)
    with zipfile.ZipFile(zip_name, 'w', compression=zipfile.ZIP_DEFLATED) as f:
        f.write(mode_name)
    return os.path.getsize(zip_name)
```

现在我们定义导出模型并计算大小。对于剪枝模型，使用 `tfmot.sparsity.keras.strip_pruning()` 来恢复原始稀疏权重。注意剥离和未剥离模型大小的差异。

```python
model_for_export = tfmot.sparsity.keras.strip_pruning(model_for_pruning)

print("Size of gzipped model without stripping: %.2f bytes" % (get_gzipped_model(model_for_pruning, '.models/for_pruning.h5', '.models/for_pruning.zip')))

print("Size of gzipped model with stripping: %.2f bytes" % (get_gzipped_model(model_for_export, '.models/for_export.h5', '.models/for_export.zip')))
```

未剥离压缩模型大小：6101.00 字节
剥离压缩模型大小：5140.00 字节

在对两个模型上运行预测，我们看到它们具有相同的均方误差。

```python
model_for_pruning_predictions = model_for_pruning.predict(X_test)

print('Model for Pruning Error %.4f' % mean_squared_error(y_test, model_for_pruning_predictions.reshape(3300)))

model_for_export_predictions = model_for_export.predict(X_test)

print('Model for Export Error %.4f' % mean_squared_error(y_test, model_for_export_predictions.reshape(3300)))
```

剪枝误差 0.0264
导出误差 0.0264

## 最后想法

你可以继续测试不同的剪枝计划如何影响模型大小。显然，这里的观察结果并不是通用的。你必须尝试不同的剪枝参数，并学习它们如何根据你的问题影响模型大小、预测误差和或准确率。为了进一步优化模型，你可以对其进行量化。如果你想探索这些更多，请查看[仓库](https://github.com/mwitiderrick/Pruning-in-TensorFlow) 和[资源](https://www.google.com/url?q=https://www.tensorflow.org/model_optimization/guide/pruning/comprehensive_guide)

## 特征选择

特征选择是任何机器学习应用的一项任务。当涉及的数据具有许多特征时，这尤为关键。最佳特征数量也可以提高模型准确率。获取最重要的特征和最佳特征数量可以通过特征重要性或特征排名获得。在本文中，我们将探索特征排名。

### 递归特征消除

递归消除所需的第一个项目是估计器；例如线性模型或决策树。这些模型在线性模型中具有系数，在决策树模型中具有重要性。在选择最佳特征数量时，训练估计器并通过系数或特征重要性选择特征。移除不重要的特征。这个过程递归进行，直到获得最佳特征数量。

### Sklearn 中的应用

Scikit-learn 可以通过 `sklearn.feature_selection.RFE` 实现递归消除。该类接受以下参数：

- `estimator`：一个可以通过 `coef_` 或 `feature_importances_` 提供重要性的机器学习估计器。
- `n_features_select`：要选择的特征数量。如果不指定，则为一半。
- `step`：每次迭代移除的特征数量，或者 0 到 1 之间的数字表示移除特征的百分比。

一旦拟合，可以获得以下属性：

- `ranking_`：特征排名。
- `n_features_`：已选择的特征数量。
- `support_`：表示特征是否被选择的数组。

### 应用

如前，我们需要与提供 `feature_importances_` 或 `coef_` 属性的估计器工作。通过快速示例。数据集有 13 个特征——我们将获取最佳特征数量。

```python
import pandas as pd

df = pd.read_csv('heart.csv')

df.head()
```

![](img/rsrc1A.jpg)

获取 X 和 y 特征。

```python
X = df.drop(['target'], axis=1)
y = df['target']
```

将其分为测试集和训练集以准备建模：

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=0)
```

为了避免数据泄露，最佳实践是执行交叉验证：

```python
from sklearn.pipeline import Pipeline
from sklearn.model_selection import RepeatedStratifiedKFold
from sklearn.model_selection import cross_val_score
from sklearn.feature_selection import RFE
import numpy as np

pipe = Pipeline([('Feature Selection', rfe), ('Model', model)])

cv = RepeatedStratifiedKFold(n_splits=10, n_repeats=5, random_state=36851234)

n_scores = cross_val_score(pipe, X_train, y_train, scoring='accuracy', cv=cv, n_jobs=-1)

np.mean(n_scores)
```

第一步是创建 `RFE` 类实例，指定估计器和想要选择的特征数量。在这种情况下，我们选择 6：

```python
rfe = RFE(estimator=GradientBoostingClassifier(), n_features_select=6)
```

接下来，我们创建一个使用的模型实例：

```python
model = GradientBoostingClassifier()
```

我们将使用 `Pipeline` 中指定用于特征选择步骤的 `rfe` 和下一步使用的模型。然后我们指定具有 10 次划分和 5 次重复的 `RepeatedStratifiedKFold`。分层 K 折确保每个折中的样本数是平衡的。`RepeatedStratifiedKFold` 以指定的次数重复分层 K 折，每次重复都有不同的随机化。

```python
pipe = Pipeline([('Feature Selection', rfe), ('Model', model)])
```

下一步是将此流水线拟合到数据集。

```python
pipe.fit(X_train, y_train)
```

一旦完成，我们可以检查 `support_` 和排名。`support_` 表示特征是否被选择。

```python
rfe.support_
# array([ True, False, True, False, True, False, False, True, False, True, True, True])
```

我们可以将其放入 dataframe 并检查结果：

```python
pd.DataFrame(rfe.support_, index=df.columns, columns=['Rank'])
```

![](img/rsrc1B.jpg)

我们也可以检查相对排名。

```python
rf_df = pd.DataFrame(rfe.ranking_, index=df.columns, columns=['Rank']).sort_values(by='Rank', ascending=True)
rf_df.head()
```

![](img/rsrc1C.jpg)

### 自动特征选择

与其手动配置特征数量，如果我们可以自动选择它们就太好了。这可以通过递归特征消除和交叉验证来实现。这是通过 `sklearn.feature_selection.RFECV` 完成的。该类接受以下参数：

- `estimator`：与 `RFE` 类相同。
- `min_features_select`：选择的最少特征数量。
- `cv`：交叉验证策略。

返回的属性有：

- `n_features_`：通过交叉验证选择的最佳数量。
- `support_`：包含特征选择信息的数组。
- `ranking_`：特征排名。
- `grid_scores_`：从交叉验证中获得的分数。

第一步是导入该类并创建其实例。

```python
from sklearn.feature_selection import RFECV

rfecv = RFECV(estimator=GradientBoostingClassifier())
```

下一步是指定流水线和 `cv`。

```python
model = GradientBoostingClassifier()

pipeline = Pipeline([('Feature Selection', rfecv), ('Model', model)])

cv = RepeatedStratifiedKFold(n_splits=10, n_repeats=5, random_state=36851234)

n_scores = cross_val_score(pipeline, X_train, y_train, scoring='accuracy', cv=cv, n_jobs=-1)

np.mean(n_scores)
```

让我们拟合流水线，然后获得最佳特征数量。

```python
pipeline.fit(X_train, y_train)

print(rfecv.n_features_)
```

最佳特征数量：7。排名和支持可以像时间一样获得。

```python
rfecv_df = pd.DataFrame(rfecv.ranking_, index=df.columns, columns=['Rank']).sort_values(by='Rank', ascending=True)
rfecv_df.head()
```
