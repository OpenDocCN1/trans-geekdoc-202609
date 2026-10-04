

# 第 4 章 针对表格数据的经典算法

有趣的是，正则化也用于神经网络中。神经网络根据系数矩阵进行顺序乘法以实现从预测的转换，这是线性回归原理的扩展。神经网络具有更复杂的性；但在这种乘法方面，它们与回归相似。基于相似的工作原理，你可能会发现，寻找一个深度学习架构对你的数据问题是有益的，并在此过程中应用 L2 惩罚，使得网络的系数被衰减并分布；或者应用 L1 惩罚，使得系数变得稀疏，其中许多系数为零。在下一节中，我们将通过发现如何解决分类问题来继续对线性模型的讨论。

## 4.3.3 逻辑回归

线性回归模型可以有效地扩展到分类。在二分类问题中，即你有两个类别（一个正类和一个负类），你使用与回归中相同的方法（特征矩阵、系数向量、偏置）。尽管如此，你仍然使用 log 函数对目标进行转换（有关该分布的详情，请参阅 https://mg.bz/JY20）。这种转换被称为链接函数。在优化方面，算法使用了伯努利分布（如需修订此分布，请参阅 https://mg.bz/wjoj）而不是正态分布。并且你得到从 0 到 1 的输出值，代表样本属于正类的概率。这被称为逻辑回归。逻辑回归是解决二分类问题以及多类和多标签问题的一种直观且实用的方法。

在 4.7 中，我们回顾了与线性回归中相同的方法——这次是为了构建一个模型来猜测一个示例的目标值是否高于中位数。请注意，转换是相同的，尽管我们这次使用的是逻辑回归模型。我们的目标是一个告知目标值是否高于中值的类别。这种目标是一个二分类平衡结果，一半的标签为正类，另一半为负类。

## 4.7 逻辑回归

```python
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import make_scorer, accuracy_score
```

accuracy = make_scorer(accuracy_score)
cv = KFold(5, shuffle=True, random_state=0)
model = LogisticRegression(solver='saga', penalty=None, max_iter=1000) # 使用 'saga' 求解器、无惩罚且最大迭代次数为 1000 的逻辑回归模型实例。

```python
column_transform = ColumnTransformer(
  [('categories', categorical_onehot_encoding, low_card_categorical),
   ('numeric', numeric_standardization, continuous)],
  remainder='drop', feature_names_out=False, sparse_threshold=0.0
)
```

> 对类别特征应用独热编码并对数值特征应用标准化的列转换器

```python
model_pipeline = Pipeline([
    ('processing', column_transform),
    ('modeling', model)])
cv_scores = cross_validate(
    estimator=model_pipeline,
    X=data,
    y=target_multiclass,
    scoring='accuracy',
    cv=cv,
    return_train_score=True,
    return_estimator=True)
```

> 顺序应用转换和逻辑回归建模的流水线

```python
mean_cv = np.mean(cv_scores['test_score'])
std_cv = np.std(cv_scores['test_score'])
fit_time = np.mean(cv_scores['fit_time'])
score_time = np.mean(cv_scores['score_time'])
print(f"mean: {mean_cv:0.3f}")
print(f"fit: {fit_time:0.2f}")
print(f"secs pred: {score_time:0.2f} secs")
```

> 使用定义的流水线进行交叉验证并计算准确率分数

> 打印交叉验证测试准确率分数的平均值和标准差

脚本结果如下：
0.821 (0.004) fit: 3.0 secs pred: 0.02 secs

在处理特征时，我们专注于逻辑回归相对于线性回归的工作方式。特别是，可以在不改变算法的情况下设置惩罚，并决定使用哪种优化器。每个优化器都允许特定的惩罚，并根据你的数据特征具有高或低效率：
- lbfgs 适用于 L2——更适用于较小数据集
- newton 适用于 L2——对于多类问题局限于“一对多”方案
- newton-cg 适用于 L2
-- 适用于无惩罚——适用于大型数据集
- saga 适用于 L1, L2, elasticnet（L1 和 L2 的混合）——适用于大型数据集

在列表 4.8 中，我们在多类目标上使用 L2 惩罚来处理多个目标，并使用 `multi_class` 参数设置为 "ovr" 为每个类构建二分类模型。在预测时，所有概率归一化为和为 1（这是神经网络中使用的一种方法，将任意值的向量转换为概率分布，所有元素之和为 1），并取概率最高的类别作为预测类别。这种方法类似于 softmax。“一对多”方案的替代方案是多项选项，其中单个回归模型同时对跨类的概率分布建模。当类间关系重要（例如用于排序或基于置信度的决策）或需要紧凑的单模型解决方案时，优选多项方法。

列表 4.8 L2 正则化的多类线性回归 带有 L2 惩罚、C=0.1、“sag" 求解器、“ovr" 模式的逻辑回归模型实例。

```python
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import make_scorer, accuracy_score

accuracy = make_scorer(accuracy_score)
cv = KFold(5, shuffle=True, random_state=0)
model = LogisticRegression(solver='saga', penalty=None, max_iter=1000)

column_transform = ColumnTransformer(
  [('categories', categorical_onehot_encoding, low_card_categorical),
   ('numeric', numeric_standardization, continuous)],
  remainder='drop', feature_names_out=False, sparse_threshold=0.0
)

model_pipeline = Pipeline([
    ('processing', column_transform),
    ('modeling', model)])
cv_scores = cross_validate(
    estimator=model_pipeline,
    X=data,
    y=target_multiclass,
    scoring='accuracy',
    cv=cv,
    return_train_score=True,
    return_estimator=True)

mean_cv = np.mean(cv_scores['test_score'])
std_cv = np.std(cv_scores['test_score'])
fit_time = np.mean(cv_scores['fit_time'])
score_time = np.mean(cv_scores['score_time'])
print(f"mean: {mean_cv:0.3f}")
print(f"fit: {fit_time:0.2f}")
print(f"secs pred: {score_time:0.2f} secs")
```
*(注：上述代码块中的注释已在原文中包含，翻译时已按要求保留)*

