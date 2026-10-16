

|  | mse |
|---|---|
| 常数 | 14,657.6847 |
| 分位数 | 10,216.3874 |
| 均值 | 5,607.1979 |
| 中位数 | 5,542.2252 |

## 7.2 回归的额外度量

到目前为止，我们一直使用均方误差作为回归问题中成功——或者更准确地说，失败——的衡量标准。我们还将 MSE 修改为均方根误差 RMSE，因为 MSE 的尺度与我们的预测相比有点偏差。MSE 与误差平方处于同一尺度；RMSE 将我们带回误差的尺度。我们以一种临时的方式进行了这种转换，在这里那里应用平方根。然而，RMSE 被广泛使用。因此，与其每次都手工拼凑——手动编写代码——让我们更深入地将 RMSE 整合到我们的 sklearn 中。

### 7.2.1 创建我们自己的评估指标

通常，sklearn 希望使用分数进行工作，分数越大越好。因此，我们将分三步开发新的回归评估指标。我们将定义一个误差度量，使用该误差定义一个分数，并使用该分数创建一个评分器。一旦我们定义了评分器函数，我们就可以简单地将评分器与 scoring 参数一起传递给 cross_val_score。记住：（1）对于误差和损失函数，值越小越好，（2）对于分数，值越大越好。因此，我们需要在误差度量和分数之间建立某种反向关系。最简单的方法之一就是取误差的负值。这需要付出一定的心理代价。对于 RMSE，我们基于它的所有分数都将为负数，而越好意味着越接近零，同时仍然为负数。这第一次思考时可能会让你侧过头。只要记住，这就像比原本会损失的钱损失得更少。如果我们必须损失一些钱，我们的理想是损失为零。

让我们继续实现细节。误差和评分函数必须接收三个参数：一个拟合好的模型、预测器和目标。是的，下面的名称有点奇怪；sklearn 有一种命名约定，即“越小越好”以 _error 或 _loss 结尾，而“越大越好”以 _score 结尾。*_scorer 形式负责在特征上应用模型进行预测并将其与实际已知值进行比较。它使用误差或分数函数量化成功。定义这三部分并非必要。我们可以挑选和选择要实现的 RMS 组件。然而，为全部三部分编写代码展示了它们之间的关系。

```
In [4]:

def rms_error(actual, predicted):
    ' root-mean-squared-error function '
    # lesser values are better (a < b means a is better)
    mse = metrics.mean_squared_error(actual, predicted)
    return np.sqrt(mse)

def neg_rmse_score(actual, predicted):
    ' rmse based score function '
    # greater values are better  (a < b means b better)
    return -rms_error(actual, predicted)

def neg_rmse_scorer(mod, ftrs, tgt_actual):
    ' rmse scorer suitable for scoring arg '
    tgt_pred = mod.predict(ftrs)
    return neg_rmse_score(tgt_actual, tgt_pred)

knn = neighbors.KNeighborsRegressor(n_neighbors=3)
skms.cross_val_score(knn,
    diabetes.data, diabetes.target,
    cv=skms.KFold(5, shuffle=True),
    scoring=neg_rmse_scorer)
```

Out[4]:
array([-58.0034, -64.9886, -63.1431, -61.8124, -57.6243])

我们第 6.4.1 节中的 hand_and_till_M_statistic 就像一个分数，我们用 make_scorer 将其转换为评分器。在这里，我们列出了 RMSE 的所有 sklearn 子组件：一个误差度量、一个分数和一个评分器。make_scorer 可以通过 greater_is_better 参数被告知将较大值视为更好的结果。

### 7.2.2 其他内置回归指标

我们在上一章中看到了指标的清单。作为提醒，它们可通过 metrics.SCORERS.keys() 获得。我们可以通过查看 help(lr_score) 来查看线性回归的默认指标。

```
In [5]:

lr = linear_model.LinearRegression()

# help(lr.score) # for full output
print(lr.score.__doc__.splitlines()[0])
```

Returns the coefficient of determination R^2 of the prediction.

线性回归的默认指标是 R²。事实上，R² 是所有回归器的默认指标。我们将在几分钟后对 R² 说更多的话。回归器的其他主要内置性能评估指标是平均绝对误差、均方误差（我们一直在使用）和中位绝对误差。

我们从实践角度比较平均绝对误差 MAE 和均方误差 MSE。我们暂时忽略 M（平均）部分，因为在两种情况下它都只是——哈！——除以示例数量。MAE 以与误差大小相同的量惩罚实际值的大和小差异。偏差 10 会得到 10 的惩罚。然而，MSE 对更大的误差惩罚更多：偏差 10 会得到 100 的惩罚。在 MAE 中，误差从 2 变到 4，惩罚从 2 变到 4；在 MSE 中，我们从惩罚 4 变到惩罚 16。净效应是较大的误差会变成非常大的惩罚。最后一点：如果两个预测偏差都是 5——它们的误差都是 5——对 MAE 的贡献是 5 + 5 = 10。对于 MSE，两个误差为 5 的贡献是 5² + 5² = 25 + 25 = 50。对于 MAE，我们可以有 10 个数据点偏差 5（因为 5 * 10 = 50），两个点各偏差 25，或一个点偏差 50。对于 MSE，我们只能有一个点偏差约 7，因为 7² = 49。更糟的是，对于 MSE，一个误差为 50 的数据点会让我们付出 50² = 2500 个平方误差点。我想我们破产了。

中位绝对误差以稍微不同的方式出现。回顾我们在第 4.2.1 节中关于均值和中位数与余额的讨论。使用中位数的理由是保护我们免受单个大误差压倒其他表现良好的误差的影响。如果我们对少数几个严重的错误是可以接受的——只要其余预测保持在轨道上——MAE 可能是一个不错的选择。

### 7.2.3 R²

R² 是一个本质上统计的概念。它带有大量的统计包袱——但这不是一本统计书。R² 在概念上也与线性回归紧密相连——而这也不是一本线性回归书。虽然这些主题当然在机器学习书籍的范围内，但我想专注于大局问题，而不是被数学细节困住——尤其是当有书籍、课程、系和学科来处理它时。因此，我只会对 R² 提供几句话。为什么还要费心？因为 R² 是 scikit-learn 中的默认回归指标。

R² 是什么？我将以 sklearn 计算的方式来定义它。为了达到这一点，让我先列出两个量数。注意，这不是你在统计教科书中看到的确切表述，但我要以两种模型的形式描述 R²。模型 1 是我们感兴趣的模型。从中，我们可以使用我们在第 2.5.3 节中看到的平方误差和来计算我们的模型表现如何。

$$SSE_{ours} = \sum_{i} our\_errors_i^2 = \sum_{i} (our\_preds_i - actual_i)^2$$

我们的第二个模型是一个简单的基线模型，始终预测目标的均值。均值模型的平方误差和为：

$$SSE_{mean} = \sum_{i} mean\_errors_i^2 = \sum_{i} (mean\_preds_i - actual_i)^2 = \sum_{i} (mean - actual_i)^2$$

抱歉向你抛出了这么多 Σ。这里是代码视图：

```
In [6]:

our_preds = np.array([1, 2, 3])
mean_preds = np.array([2, 2, 2])
actual = np.array([2, 3, 4])

sse_ours = np.sum(( our_preds - actual)**2)
sse_mean = np.sum((mean_preds - actual)**2)
```

有了这两个组成部分，我们就可以像 sklearn 文档中描述的那样计算 R²。严格来说，我们在这里做的事情与稍后要讲到的略有不同。

```
In [7]:

r_2 = 1 - (sse_ours / sse_mean)
print("manual r2:{:.2f}".format(r_2))
```

manual r2: 0.40

sklearn 文档引用的公式是：

$$R^2 = 1 - \frac{SSE_{ours}}{SSE_{mean}}$$

那里第二个项是什么？$\frac{SSE_{ours}}{SSE_{mean}}$ 是我们做得如何与一个简单模型做得如何之间的比率，当两个模型都以平方误差和衡量时。事实上，特定的基线模型是我们在本章开头看到的 dummy.DummyRegressor( strategy='mean' )。例如，如果我们花哨的预测器的误差为 2500，而简单地预测均值的误差为 10000，则两者之间的比率为 $\frac{1}{4}$，我们将有 $R^2 = 1 - \frac{1}{4} = \frac{3}{4} = 0.75$。我们将我们模型的性能归一化或重新调整为始终预测均值目标值的模型。公平 enough。但，1 减去该比率是什么？
