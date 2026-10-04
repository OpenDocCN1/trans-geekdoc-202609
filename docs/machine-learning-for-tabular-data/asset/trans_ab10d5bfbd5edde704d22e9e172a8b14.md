

粘贴（Pasting）、装袋（bagging）、随机子空间（random subspaces）和随机补丁（random patches）都可以使用 Scikit-learn 的 bagging 函数实现。通过以下参数，可以控制分类任务中的 `BaggingClassifier` 和回归任务中的 `BaggingRegressor` 在训练数据方面的行为：

- bootstrap
- max_sample
- max_features

通过根据平均方法的规范将这些参数结合起来，你就可以获得我们描述的所有四种平均策略（见表 5.1）。

## 表 5.1 Bagging 和采样策略

| 平均策略 | 数据的处理方式 | BaggingClassifier/BaggingRegressor 的参数 |
| :--- | :--- | :--- |
| Pasting | 不放回地采样训练样本 | bootstrap = False, max_samples < 1.0, max_features = 1.0 |
| Bagging | 有放回地采样训练样本（自助法） | bootstrap = True, max_samples = 1.0, max_features = 1.0 |
| 随机子空间 | 对特征进行采样（不放回） | bootstrap = False, max_samples < 1.0, max_features < 1.0 |
| 随机补丁 | 不放回地对训练样本和特征进行采样 | bootstrap = False, max_samples < 1.0, max_features < 1.0 |

通过在参数估计（parameter estimator）中输入所需的 Scikit-learn 模型类，你可以决定使用何种算法来构建集成模型。默认是决策树，但你可以决定你偏好的弱模型或强模型。在以下示例中，我们应用了一个装袋分类器，并将决策树的数量设置为 300。接下来的列表显示了所有共同有助于改进低性能的模型，正如我们在列表 5.2 中看到的，在这种情况下，单棵决策树倾向于产生这种结果。

## 列表 5.3 基于树的装袋分类器

```python
from sklearn.ensemble import BaggingClassifier
from sklearn.tree import DecisionTreeClassifier
from sklearn.metrics import accuracy_score

accuracy = make_scorer(accuracy)

cv = KFold(shuffle=True, random_state=0)
model = BaggingClassifier(
    estimator=DecisionTreeClassifier(),
    n_estimators=300,
    bootstrap=True,
    max_samples=1.0,
    max_features=1.0,
    random_state=0
)

column_transform = ColumnTransformer(
    (['categorical', OneHotEncoder(), 'categorical']),
    ('numeric', Passthrough(), 'numeric']),
    remainder='drop',
    feature_names_out_out=False
)

model_pipeline = Pipeline([
    ('processing', column_transform),
    ('modeling', model)
])

cv_scores = cross_validate(
    estimator=model_pipeline,
    X=data,
    y=target,
    scoring='accuracy',
    cv=cv,
    return_train=True,
    return_estimator=True
)

mean_cv = np.mean(cv_scores['test_score'])
std_cv = np.std(cv_scores['test_score'])
fit_time = np.mean(cv_scores['fit_time'])
score_time = np.mean(cv_scores['score_time'])
print(f"mean_cv:{mean_cv:.3f} std:{std_cv:.3f}")
print(f"fit:{fit_time:.2f}")
print(f"secs pred:{score_time:.2f}")
```

使用定义的流水线进行五折交叉验证并计算准确率得分的结果需要一段时间，而且看起来很有前景，但它们仍然不足以与之前基于支持机和逻辑回归的解决方案竞争：0.809 (0.004) fit: 37.93 secs pred: 0.83 secs

在下一节中，我们将通过重新回顾利用随机补丁的随机森林来迈集成学习的下一步，这样做是有充分理由的。

### 5.1.2 使用随机森林进行预测

随机森林的工作原理类似于 bagging。但尽管如此，它也应用了随机补丁（不放回地采样训练样本和特征）：它在训练每个模型之前对样本进行自助采样，并在建模期间对特征进行子采样。由于随机森林集成中使用的基本算法是基于二分分裂构建的决策树，因此特征采样发生在每次树的分裂时，此时一组特征被采样作为分裂的潜在候选。

允许集成中的每棵树都生长到极端状态可能会导致数据过拟合和估计的高方差；采用自助法和特征采样可以缓解这些问题。自助法确保模型是在来自相同分布的略有不同的样本上进行训练的，而每次分裂时的特征采样保证了树结构的多样性。这种组合创建了一组截然不同的模型。不同的模型产生非常不同的预测结果（因此，我们可以说它们的预测是不相关的），对于平均技术来说这是一个巨大的优势，在集成结果时，可以获得更可靠、更准确的预测。

图 5.4 展示了随机森林是如何工作的。该图说明了一个具有两个类别数据集的二分类问题。该数据集使用决策树进行建模，并采用了自助法和特征采样技术。这些技术导致了数据集的不同划分，在图中顶部部分由三棵树表示，展示了它们分裂策略的变异。为了简化表示，只显示了两个特征，以便更清晰地理解这一过程。

最后，当所有结果通过多数投票结合在一起时（即选择出现频率最高的分类作为预测类），随机森林将根据所有树的结果提供更好的预测。这在图的底部显示，不同的深浅表示某一类或另一类在特定划分中的流行程度。类之间的确定性边界显示为黑色多边形线条。

图 5.4 随机森林通过多数投票得出结果

![](img/def89cc47fa39f4c5bd34e78d916_0.png)

## 基于树的方法介绍

最初由 Leo Breiman 和 Adele Cutler (https://mnb.bz/QIqp) 设计，虽然是商业化的，但该算法是开源的——因此不同的名称。随机森林提供了更多可能性，在预测之前，你可以使用该算法确定特征重要性。

在示例 5.4 中，我们测试了随机森林如何在 Airbnb 数据集上工作。从算法来看，与我们的标准数据处理没有区别。将类别特征编码为二进制，数值特征保持原样。

## 列表 5.4 随机森林分类器

```python
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score

accuracy = make_scorer(accuracy)

cv = KFold(shuffle=True, random_state=0)
model = RandomForestClassifier(
    estimators=300,
    min_samples_leaf=3,
    random_state=0
)

column_transform = ColumnTransformer(
    (['categorical', OneHotEncoder(), 'categorical']),
    ('numeric', Passthrough(), 'numeric']),
    remainder='drop',
    feature_names_out=False
)
...
（此处后续代码未翻译）
```
