
既然我们遵守规则并编写了一个直接接入 sklearn 使用模式的学习器（这也称为 API 或应用程序编程接口），我们对代码的使用将会相当熟悉。

In [25]:

```python
# here, we're giving ourselves all the help we can by using
# the same cut points as our data were generated with
model = PiecewiseConstantRegression(cut_points=np.array([3, 7]))
model.fit(ftr, tgt)
preds = model.predict(ftr)
print("Predictions equal target?", np.allclose(preds, tgt))
```

预测等于目标？True

如所写，PiecewiseConstantRegression 由一些超参数（切分点）和一些参数（与每个分段相关联的常数）定义。常数在我们调用 fit 时计算。模型的整体拟合对分割点的数量和位置非常、非常敏感。如果我们考虑使用分段方法，我们要么（1）希望对跳变点的位置有背景知识，要么（2）愿意花时间尝试不同的超参数并交叉验证结果以获得良好的最终产品。

现在，即使我走捷径只谈论分段常数——单个线段有 b 但没有 mx——我们也可以将其扩展到分段线、分段抛物线等。我们也可以要求端点相遇。这一要求会使我们获得一定程度的连续性，但不一定是光滑性。换句话说，我们可以连接分段线段，但仍可能存在尖锐的转折。我们还可以强制执行更高程度的光滑性，要求转折较为平缓。允许分段组件中有更多弯曲会降低我们的偏差。对连接点的约束施加正则化——使模型平滑。

## 9.4 回归树

决策树的一个伟大之处在于其灵活性。由于它们概念上很直接——找到输出相似的区域，以某种方式标记该区域中的所有内容——它们可以轻松地适应其他任务。在回归情况下，如果我们能找到一个单一数值能很好地代表整个区域的区域，那就万事大吉了。因此，在树的叶节点处，我们不是说猫或狗，而是说 27.5。

### 9.4.1 使用树进行回归

从分段常数回归到决策树是一个直接的概念性步骤。为什么？因为你已经做了繁重的工作。决策树为我们提供了一种方法，可以放大足够相似的区域，并在选定区域后预测一个常数。这种放大发生在我们分割空间区域时。

最终，我们会得到一个足够小的区域，其行为相当均匀。基本上，使用决策树进行回归为我们提供了一种自动选择分割点数量和位置的方法。这些分割是通过计算分割将节点处的当前数据集拆分为两个子集时的损失来确定的。导致即时平方误差最低的分割是该节点的所选断点。记住，树构建是一个贪婪过程，并不保证是全局最佳步骤——但一系列贪婪步骤通常足以满足日常使用。

In [26]:

```
dtrees = [tree.DecisionTreeRegressor(max_depth=md) for md in [1, 3, 5, 10]]

for model in dtrees:
    preds = (model.fit(diabetes_train_ftrs, diabetes_train_tgt)
             .predict(diabetes_test_ftrs))
    mse = metrics.mean_squared_error(diabetes_test_tgt, preds)
    fmt = "{} {:2d} {:4.0f}"
    print(fmt.format(get_model_name(model),
                     model.get_params()['max_depth'],
                     mse))
```

DecisionTreeRegressor  1 4341
DecisionTreeRegressor  3 3593
DecisionTreeRegressor  5 4312
DecisionTreeRegressor 10 5190

注意增加深度如何先帮助后损害。我们一起说：过拟合！如果我们允许深度过大，我们会将数据分割成太多部分。如果数据被分割得太细，我们会做出不必要的区分，会过拟合，并且测试误差会逐渐上升。

## 9.5 回归器比较：第三次

我们将回到学生数据集并应用一些更高级的学习器。

In [27]:

```
student_df = pd.read_csv('data/portuguese_student_numeric.csv')
student_ftrs = student_df[student_df.columns[:-1]]
student_tgt  = student_df['G3']
```

In [28]:

```python
student_tts = skms.train_test_split(student_ftrs, student_tgt)

(student_train_ftrs, student_test_ftrs,
 student_train_tgt, student_test_tgt) = student_tts
```

我们将引入第 7 章中介绍的回归方法：

In [29]:

```python
old_school = [linear_model.LinearRegression(),
 neighbors.KNeighborsRegressor(n_neighbors=3),
 neighbors.KNeighborsRegressor(n_neighbors=10)]
```

并添加本章中的一些新回归器：

In [30]:

```python
# L1, L2 penalized (abs, sqr), C=1.0 for both
penalized_lr = [linear_model.Lasso(),
 linear_model.Ridge()]

# defaults are epsilon=.1 and nu=.5, respectively
svrs = [svm.SVR(), svm.NuSVR()]

dtrees = [tree.DecisionTreeRegressor(max_depth=md) for md in [1, 3, 5, 10]]

reg_models = old_school + penalized_lr + svrs + dtrees
```

我们将基于均方根误差（RMSE）进行比较：

In [31]:

```python
def rms_error(actual, predicted):
 ' root-mean-squared-error function '
 # lesser values are better (a<b means a is better)
 mse = metrics.mean_squared_error(actual, predicted)
 return np.sqrt(mse)
rms_scorer = metrics.make_scorer(rms_error)
```

我们将在应用模型之前对数据进行标准化：

In [32]:

```
scaler = skpre.StandardScaler()

scores = {}
for model in reg_models:
    pipe = pipeline.make_pipeline(scaler, model)
    preds = skms.cross_val_predict(pipe,
                                    student_ftrs, student_tgt,
                                    cv=10)
    key = (get_model_name(model) +
           str(model.get_params().get('max_depth', '')) +
           str(model.get_params().get('n_neighbors', '')))
    scores[key] = rms_error(student_tgt, preds)

df = pd.DataFrame.from_dict(scores, orient='index').sort_values(0)
df.columns=['RMSE']
display(df)
```

|  | RMSE |
|---|---|
| **DecisionTreeRegressor1** | 4.3192 |
| **Ridge** | 4.3646 |
| **LinearRegression** | 4.3653 |
| **NuSVR** | 4.3896 |
| **SVR** | 4.4062 |
| **DecisionTreeRegressor3** | 4.4298 |
| **Lasso** | 4.4375 |
| **KNeighborsRegressor10** | 4.4873 |
| **DecisionTreeRegressor5** | 4.7410 |
| **KNeighborsRegressor3** | 4.8915 |
| **DecisionTreeRegressor10** | 5.3526 |

对于前四种模型，让我们看看按折叠划分的性能细节。

In [33]:

```
better_models = [tree.DecisionTreeRegressor(max_depth=1),
                 linear_model.Ridge(),
                 linear_model.LinearRegression(),
                 svm.NuSVR()]
```

```
fig, ax = plt.subplots(1, 1, figsize=(8,4))
for model in better_models:
    pipe = pipeline.make_pipeline(scaler, model)
    cv_results = skms.cross_val_score(pipe,
                                      student_ftrs, student_tgt,
                                      scoring = rms_scorer,
                                      cv=10)

    my_lbl = "{:s} ({:.5f}$\pm${:.2f})".format(get_model_name(model),
                                              cv_results.mean(),
                                              cv_results.std())

ax.plot(cv_results, 'o--', label=my_lbl)
ax.set_xlabel('CV-Fold #')
ax.set_ylabel("RMSE")
ax.legend()
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_345_0.png)

这些模型在性能上都有一些波动。它们的学习性能都非常接近。均值的范围（4.23，4.29）并不宽，而且也略小于标准差。仍有工作需要完成。我们实际上并没有遍历正则化的不同值。我们可以手动完成，方式类似于我们在第 5.7.2 节中看到的复杂度曲线。然而，我们将在第 11.2 节中以更方便的方式处理这个问题。
