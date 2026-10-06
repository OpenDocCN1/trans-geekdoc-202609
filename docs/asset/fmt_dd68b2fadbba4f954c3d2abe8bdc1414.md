
# 附录 B K最近邻和支持向量机

```python
from sklearn.compose import ColumnTransformer
```

```python
from sklearn.preprocessing import OneHotEncoder

from sklearn.preprocessing import KBinsDiscretizer

from sklearn.metrics import accuracy_score
```

使用 `accuracy_score` 指标创建评分函数

```python
categorical_onehot_encoding = OneHotEncoder(handle_unknown='ignore')
```

```python
accuracy = make_scorer(accuracy_score)

cv = KFold(5, shuffle=True, random_state=0)

model = KNeighborsClassifier(n_neighbors=30,
                             weights='uniform',
                             algorithm='auto',
                             n_jobs=-1)
```

创建一个带有洗牌和固定随机状态五折验证迭代器

```python
column_transform = ColumnTransformer(
  (['', categorical_onehot_encoding, low_cardinality),
  ['numeric', numeric_discretizing, continuous]),
  remainder='drop',
  verbose_feature_names=False,
  sparse_threshold=0.0)
```

创建一个具有特定超参数的 `KNeighborsClassifier` 实例

```python
model_pipeline = Pipeline(
  ('preprocessing', column_transform),
  ('pca', PCA(components='hle'))
  ('modeling', model))
```

定义一个 `ColumnTransformer` 来预处理特征，对低基数的分类特征进行独热编码，对数值特征进行离散化

```python
cv_scores = cross_validate(estimator=model_pipeline,
                              X=data,
                              y=target_median,
                              scoring=accuracy,
                              cv=cv,
                              return_train_score=True,
                              estimator=True)
```

创建一个管道，按顺序应用列转换、执行 PCA 降维，然后将 k-nn 模型拟合到数据

```python
mean_cv = np.mean(cv_scores['test_score'])
std_cv = np.std(cv_scores['test_score'])
fit_time = np.mean(cv_scores['fit_time'])
score_time = np.mean(cv_scores['score_time'])
print(f'mean: {mean_cv:.2f} (std: {std_cv:.0f})')
      f'fit: {fit_time:.2f}s')
      f'score pred: {score_time:.2f}s')
```

使用定义的管道对数据进行交叉验证，并使用准确率评分

打印测试分数的平均值和标准差

运行脚本后，你将获得一个与朴素贝叶斯方案性能对比的结果：

- 0.814 (0.005): 预测 0.13 秒。训练 8.75 秒

性能良好，尽管推理时间相对较高。由于该算法通过类比工作（它将在你的训练集中寻找某些案例以获取对可能预测的想法），因此在大型数据集上表现更好，因为在大型数据更有可能找到待预测的实例。自然地，数据集的合适大小取决于所使用的特征数量，因为特征越多，算法就需要越多案例来进行泛化。

## k-NN

虽然重点放在了为 k 参数设置最佳值上，但为了平衡算法对训练的欠拟合和过拟合，我们转而关注其他方面，以有效使用该模型。由于该算法通过类比和复杂空间中的距离工作，我们考虑了关于这种方法的两个重要问题：

- 待测量的维度和维度灾难
- 适当的距离量以及如何处理特征

在 k-NN 中，分类或回归估计取决于基于特征计算的距离度量的最相似示例。然而，在数据集中，并不是所有特征都能被认为是判断一个示例类似于另一个是重要的，并不是所有特征都能以相同的方式进行比较。在使用 K-NN 时，问题的先验知识非常，因为你必须选择与你想要解决的任务相关的特征。如果你为问题收集了太多特征，图 B 显示了 kN 算法如何使用两个特征（在 x 和 y 维度上表示）工作，你可以直观地理解，如果一个区域存在混合类别，或者如果新实例附近没有训练示例，那么分类实例可能是困难的。你必须依靠更远的示例。

维度灾难出现了，它说随着特征数量的增加，你应该有更多的示例来保持点之间有意义的距离。此外，灾难意味着必要的示例数量随特征数量呈指数级增长。对于 k-NN，这种灾难意味着如果你提供了太多特征，即使样本足够也会变得令人困扰。结果特征不相关是 PCA 处理数据的特性，这适用于 k-NN：它是基于距离的，如果维度之间不相关，距离测量就能正常工作。因此，任何距离的变化都是由于单个维度的变化，而不是多个维度的变化。下面的列表了实现数据转换过程和训练 k-NN 的代码。

由于如此，在使用 k-NN 时，除了仔细选择使用哪些特征外，我们建议使用相同类型的特征（或分类特征），并在必要时对其进行标准化，并通过如 PCA（https://mng.bz/8OrZ）等方法减少其信息冗余，这将数据集重构为一个特征之间不相关的新数据集。

## B.2 SVMs

在 21 世纪 10 年之前，SVM 被誉为表格问题最有前景算法。在过去的 10 年里，基于树的模型在表格数据的主流方法中取代了 SVM。然而，SVM 仍然是处理二分类、多分类、回归和异常检测的技术族。它们基于这样一个观点：如果你的观测值可以表示为多维空间中的点，则有一个超平面（即穿过多个维度的分割平面）可以将它们分成类或值，通过确保它们之间最大的间隙，同时也保证了最稳健可靠的预测。图 B.2 显示了应用于具有两个特征的二分类问题的简单示例，特征表示在 x 轴和 y 轴。SVM 模型产生了一条在两组之间具有最大间隙的分割线，如图所示虚线限制了间隙。通过这样做，它只考虑了分割线附近的少数点，这些点被称为支持向量。相反，它忽略了附近但让算法困惑的点，例如，它们在错误的一侧。它还忽略了离分割线远的点。离群值对该算法的影响很小。

![](img/def89cc476fa39f4c54bd34e78d91674_490_0.png)

图 B.2 来自 SVM 的分割平面

### SVM

SVM 的优点在于对过拟合、数据噪声和离群值的鲁棒处理能力，并且能够成功处理包含许多多共线性特征数据集。通过对数据应用各种非线性方法，SVM 不需要像我们在逻辑回归中看到的那些变换（如多项式扩展）。然而，它们可以像其他机器学习算法一样，使用基于领域的特征工程。

在缺点方面，SVM 的优化非常复杂，且仅适用于有限数量的样本。此外，它们最适用于二分类预测和单类预测；它们不是概率算法，你需要将它们封装在另一个算法（如逻辑回归）中进行校准，以便从中提取属性。这使得 SVM 仅适用于有限的风险估计范围。

在我们的示例中，我们使用带有径向基核的简单分类 SVM 结合 Airbnb 数据来解决问题，这种方法能够自动对所提供特征之间的非线性关系建模。

#### 列表 B.2 svm 支持向量分类器

```python
from sklearn.svm import SVC
from sklearn.metrics import accuracy_score
from sklearn.impute import SimpleImputer
from sklearn.preprocessing import StandardScaler
```

```python
numeric_standardization = Pipeline(
    ("imputation", SimpleImputer(strategy="constant", fill_value=0)),
    ("standardizing", StandardScaler())
)
```

> 使用 `accuracy_score` 创建一个评分函数

```python
accuracy = make_scorer(accuracy_score)
cv = KFold(5, shuffle=True, random_state=0)
model = SVC(
    C=1.0,
    kernel='rbf',
    gamma='scale',
    probability=False)
```

> 创建一个带有洗乱和固定随机状态五折交叉验证器

> 创建一个指定超参数的支持向量分类器实例

```python
column_transform = ColumnTransformer(
    (['categories', categorical.onehot_encoding, low_card_categorical),
    (['numeric', numeric_standardization, continuous]),
    ('remainder', 'drop'),
    verbose_feature_names=False,
    sparse_threshold=0.0)
```

> 定义一个 `ColumnTransformer` 来预处理特征，对低基数的类别特征应用独热编码，对数值特征进行标准化

```python
model_pipeline = Pipeline(
    (['processing', column_transform),
    ('modeling', model))
```

> 创建一个按顺序将列变换和模型应用于数据的流水

```python
cv_scores = cross_validate(estimator=model_pipeline,
    x_data,
    y_target,
    scoring=accuracy)
```

# 附录 B K 近邻算法与支持向量机

```python
cv=cv,
return_train_score=True,
return_estimator=True
```

```python
mean_cv = np.mean(cv_scores['test_score'])
std_cv = np.std(cv_scores['test_score'])
fit_time = np.mean(cv_scores['fit_time'])
score_time = np.mean(cv_scores['score_time'])
print(f"mean_cv:{0.3f} ({std_cv:0.3f})",
      f"fit:{fit_time:0.2f}",
      f"secs:{score_time:0.2f} secs") )
```

> 使用定义的流水对数据进行交叉验证，并使用准确率评分

> 打印测试分的平均值和标准差

结果非常令人印象，通过调整超参数甚至可能变得更好：

0.821 (0.004) fit: 10.28 secs: 9.80 secs

然而，与之前所有的机器学习算法相比，训练单折所需的时间是昂贵的。在附录的下一节中，我们将讨论如何在使用 Scikit-learn API 的情况下加速这一过程。

## B.3 使用 GPU 进行机器学习

由于深度学习在数据科学领域的快速兴起，GPU 已经广泛普及并适用于本地和云端计算。早些，你只在 3D 游戏、图形处理渲染和动画中听过 GPU。由于它们廉价且擅长快速矩阵乘法任务，学术界和从业者已迅速开始使用 GPU 进行神经网络计算。RAPIDS 由 NVIDIA（顶级 GPU 制造商之一）开发，是一组用于在 GPU 上执行全方位数据科学任务的包，而不仅仅是深度学习。RAPIDS 包承诺帮助机器学习流水线的从所有阶段。对于许多经典机器学习算法来说，这是一个规则改变者，特别是对于 SVM，它是处理涉及噪声、离群观测值和数据集（具有大量特征，尤其是多分类或稀疏数据集）复杂任务的最可靠选择。在 RAPIDS 包（表 B.1）中，所有命令都采用了用户现有的 API，无需重新学习轮子如何工作。

**表 B.1** Rapids 包

| Rapids 包 | 任务 | 模仿的 API |
|---|---|---|
| cuPy | 数组操作 | NumPy |
| cuDF | 数据处理 | pandas |
| cuML | 机器学习 | Scikit-learn |

## 使用 GPU 进行机器学习

本节将关注如何轻松用 cuML 替换 Scikit-learn 算法。目前，该包包含了线性模型、k-NN 以及聚类和降维实现。以下代码显示了我们在使用相同代码但依赖 cuML 的情况下获得相同的结果。然而，处理时间从每折 102 秒下降到每折 4 秒。如果你计算节省的时间，那是 25 倍的速度提升。

列表 B.3 来自 GPU 加速 cuML 支持向量分类器在 P100 GPU 上测试径向基核。

```python
from cuml.svm import SVC
from sklearn.metrics import accuracy_score

accuracy = make_scorer(accuracy_score)
cv = CV(5, shuffle=True, random_state=0)
model = SVC(
    C=1.0,
    kernel='rbf',
    gamma='scale',
    probability=False)
```

```python
column_transform = ColumnTransformer(
    ['categorical', encoding, low_card_categorical],
    ['numeric', numeric_standardization, continuous]),
    remainder='drop',
    verbose_feature_names_out=False,
    sparse_threshold=0.0)

model_pipeline = Pipeline(
    ['processing', column_transform),
    ('modeling', model])

cv_scores = cross_validate(estimator=model_pipeline,
    X=data,
    y=target_median,
    scoring=accuracy,
    cv=cv,
    return_train=True,
    return_estimator=True)
```

> 创建一个评分函数

> 创建一个带有洗乱和固定随机状态五折交叉验证

> 创建一个指定超参数的支持向量分类器实例

```python
mean_cv = np.mean(cv_scores['test_score'])
std_cv = np.std(cv_scores['test_score'])
fit_time = np.mean(cv_scores['fit_time'])
score_time = np.mean(cv_scores['score_time'])
print(f"mean_cv:{0.3f} {std_cv:0.3f}")
print(f"fit_time:{0.2f}")
print(f"secs: {score_time:0.2f} secs")
```

> 定义一个 `ColumnTransformer`，对低基数的类别特征应用独热编码，对数值特征进行标准化

> 创建一个按顺序将列变换和模型应用于数据的流水

> 使用定义的流水对数据进行交叉验证，并使用准确率评分

> 打印测试分的平均值和标准差

我们获得的结果是

0.821 (0.004) fit: 4.09 secs pred: 0.1 secs
