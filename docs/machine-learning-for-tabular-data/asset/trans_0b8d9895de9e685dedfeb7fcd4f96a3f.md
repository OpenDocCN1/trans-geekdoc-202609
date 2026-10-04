

# 第 6 章 高级特征处理方法

```python
max_depth=4,
min_child_weight=3)
column_transform = ColumnTransformer(
  ('low_card_categories',
   categorical_onehot_encoding,
   low_card_categorical),
  ('high_card_categories',
   target_encoder,
   high_card_categorical),
  ('numeric',
   numeric_standardization,
   continuous),
  remainder='drop',
  verbose_feature_names_out=True,
  sparse_threshold=0.0)
```

> 使用特定的超参数初始化 XGBoost

```python
model_pipeline = Pipeline(
  ('processing', column_transform),
  ('model', xgb))
```

> 定义 ColumnTransformer，使用 TargetEncoder 对高基数类别特征进行预处理

```python
cv_scores = cross_validate(estimator=model_pipeline,
  X=data,
  y=target_median,
  scoring=accuracy,
  cv=cv,
  return_score=True,
  return_estimator=True)
```

> 创建一个结合预处理和建模的流水线

```python
mean_cv = np.mean(cv_scores['test_score'])
std_cv = np.std(cv_scores['test_score'])
fit_time = np.mean(cv_scores['fit_time'])
print(f"mean_cv: {mean_cv:.0f}")
print(f"fit_time: {fit_time:.2f}")
print(f"sec_pred: {sec_pred:.2f}")
```

> 执行五折交叉验证并获取指标。打印交叉验证的平均准确率、拟合时间和预测时间

执行时，代码将产生在带有额外高基数类别特征的问题上运行 XGBoost 的结果。结果显示准确率略有提高。在本章稍后部分，我们将在解释解释性时调查目标编码的贡献权重：

0.840 (0.004) 4.52 secs. pred: 0.06 secs

虽然目标编码是一种方便的方法，因为它可以快速地将任何类别特征转换为数值特征，但你必须注意保留数据中的所有重要信息。目标编码使得特征之间的任何交互建模变得不可能。例如，假设你正在处理一个带有点击格式的广告响应数据集。使用这两个特征，对两个可能具有成千上万个值的高基数类别进行转换，你可以轻松地创建任何经典模型的树。然而，在编码之后，你的模型（无论是线性还是基于树的）都无法捕捉编码特征之间任何可能的交互。在这种情况下，解决方案是预先创建一个新特征，将两个高基数类别特征结合，然后对它们的组合进行编码。

因此，对于其他工具，我们应该考虑这种高级编码技术的优缺点。根据我们的经验，取决于情况，在诉诸目标编码之前，经典机器学习算法和梯度提升在处理高基数类别特征方面有少数几个方案：

- 直接丢弃类别特征
- 使用 OneHotEncoder
- 使用 OrdinalEncoder 将类别视为有序的等距分量
- 使用 OrdinalEncoder 并依赖基于直方图的提升算法的原生类别支持
- 将目标编码作为最后的手段

丢弃特征只在某些情况下被考虑。然而，我们已经在第 2 章中提到过如何利用克梅 V 值（Cramer's V）关联测量指标来评估名义特征对预测目标的贡献。

当遇到高基数类别特征时，对于线性模型，选择独热编码几乎是必要的。在处理其他模型（如决策树及其集成）时，可能会有更合适的方法。这是因为独热编码为类别特征的每个值创建了一个额外的特征。这导致树状模型在拟合过程中必须考虑的分叉点数量增加。因此，使用独热编码需要决策树具有更深的深度，才能实现与使用不同方法处理类别特征时单个分叉点等效的划分。

对于序数编码器（Ordinal encoder），类别被编码为 0, 1, 2 等，将它们视为连续特征。虽然这种方法对线性模型可能有误导性，但它对决策树来说非常有效。决策树可以根据序数编码精确地划分数据，根据类别与目标变量的关系分离类别。而 XGBoost 则将所有特征都视为数值型连续特征。

如果我们决定使用对类别特征的支持，该选项在 LightGBM 和 H2O.ai 库提供的 XGBoost 版本（https://mng.bz/6ce75）中是可用。原生类别支持允许这些模型更有效地处理类别特征，而无需将其转换为数值。在这种情况下，由于原生处理需要对类别进行排序，我们预计在使用原生处理类别特征作为序数时，算法速度会略慢。在原生类别支持中，特征类别的排序基于每个类别相关的目标方差。一旦排序完成，该特征就可以作为连续数值属性使用。

## 6.1.4转换数值数据

决策树可以自动处理数据中的非线性和交互。这是因为它们可以在任何点将变量拆分为两部分，然后反复进一步拆分。这种属性对于处理数据中细微且深层的交互特别有用，但有一点是，决策树是相当粗糙的近似器。在精确建模数据中复杂关系方面，具有足够示例的神经网络是更好的近似器。

图 6.1 显示了决策树袋集成（bagged ensemble）如何近似非线性函数。结果是由一组递归划分空间的 if-else 决策规则构建的近似。然而，数据中的噪声可能导致空间某些部分出现不准确。相比之下，与袋装决策树中使用的树数量相同的神经网络可以提供更平滑、更准确的曲线估计。

![](img/def89cc476fa39f4c54bd34e78d91674_226_0.png)

**图 6.1** 对于带有噪声正弦函数的随机数据集，神经网络与袋装决策集成之间预测的对比

由于 GBDT 也基于决策树，它可能以类似的方式使用二分划分来塑造自身的非线性函数。因此，当在使用 GBDT 时，如果你知道特定的非线性或交互，通过通过向线性形式的转换、分箱或离散化以及预计算的特征交互来显式定义它们将对你有益。对于非线性，转换有助于减少分叉次数。在应用转换之前，你需要了解你的数据。线性和非线性（即使与目标没有关系）在拟合训练数据后也可以通过部分依赖图（PDP）轻松发现。这种与模型无关的图表解释了通过你训练的模型，特征和目标之间是如何相关的。

PDP 显示了在忽略其他特征影响的情况下，目标输出如何随特定特征变化。换说，它显示了在设置输入特征某个值时的平均预测值。分析的底层假设是由 PDP 表示的输入与其他特征是独立的。在这种情况下，PDP 代表了输入如何影响目标。然而，这一假设在实践中是被违反的，意味着我们正在检查的输入特征通常与其他特征完全独立。

# 处理特征

在列表 6.5 中，我们探索了 PDP 的可能用法和局限性。给定在我们的 Airbnb 数据上训练的 XGBoost 模型，我们展示了目标如何随我们的数值特征变化，试图发现任何非线性或其他特征。生成的四个图表使用 matplotlib 轴绘制并对其进行分析。

## 6.5 部分依赖图

```python
from XGBoost import XGBClassifier
import matplotlib.pyplot as plt
from sklearn.inspection import PartialDependenceDisplay
```

```python
xgb = XGBClassifier(booster='gbtree',
objective='reg:logistic',
n_estimators=300,
max_depth=4,
min_child_weight=3)
```

```python
model_pipeline = Pipeline(
  (['processing', column_transform),
   ('XGBoost', xgb))

```

创建一个结合了数据处理和 XGBoost 分类器的流水线

```python
model_pipeline.fit(X_data, y=target_median)
```

```python
fig, ax = plt.subplots(
rows=2,
cols=2,
figsize=(8, 4)
)
fig.subplots_adjust(hspace=0.4, wspace=0.2)
```

创建一个 2×2 的子图布局

```python
PartialDependenceDisplay.from_estimator(
```

