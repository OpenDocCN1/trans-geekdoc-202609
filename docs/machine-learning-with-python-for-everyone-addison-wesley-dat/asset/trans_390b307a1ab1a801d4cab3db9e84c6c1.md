
In [25]:

```python
student_df = pd.read_csv('data/portuguese_student_numeric.csv')
display(student_df[['absences']].describe().T)
```

|  | 计数 | 平均值 | 标准差 | 最小值 | 25% | 50% | 75% | 最大值 |
|---|---|---|---|---|---|---|---|---|
| 缺席 | 395.00 | 5.71 | 8.00 | 0.00 | 0.00 | 4.00 | 8.00 | 75.00 |

In [26]:

```python
student_ftrs = student_df[student_df.columns[:-1]]
student_tgt  = student_df['G3']
```

### 7.5.1 多指标交叉验证结果

以下代码使用 skms.cross_validate 对多个指标进行评分。这是一个非常方便的功能：它允许我们通过一次调用来评估多个指标。它还会做一些工作来记录使用给定模型拟合和预测所花费的时间。我们将忽略这些其他部分，只利用它返回的多个指标评估。与 skms.cross_val_score 类似，它要求将评分器传递给 scoring 参数。

In [27]:

```python
scaler = skpre.StandardScaler()

lr     = linear_model.LinearRegression()
knn_3  = neighbors.KNeighborsRegressor(n_neighbors=3)
knn_10 = neighbors.KNeighborsRegressor(n_neighbors=10)

std_lr_pipe   = pipeline.make_pipeline(scaler, lr)
std_knn3_pipe = pipeline.make_pipeline(scaler, knn_3)
std_knn10_pipe = pipeline.make_pipeline(scaler, knn_10)

# mean with/without Standardization should give same results
regressors = {'baseline' : dummy.DummyRegressor(strategy='mean'),
              'std_knn3' : std_knn3_pipe,
              'std_knn10': std_knn10_pipe,
              'std_lr'   : std_lr_pipe}

msrs = {'MAE'  : metrics.make_scorer(metrics.mean_absolute_error),
        'RMSE' : metrics.make_scorer(rms_error)}

fig, axes = plt.subplots(2, 1, figsize=(6, 4))
fig.tight_layout()
```

In [28]:

fig,ax = plt.subplots(1, 1, figsize=(6, 3))
baseline_results = skms.cross_val_score(regressors['baseline'],
                                        student_ftrs, student_tgt,
                                        scoring = msrs['RMSE'], cv=10)

for mod_name, model in regressors.items():
    if mod_name.startswith("std_"):
        cv_results = skms.cross_val_score(model,
                                          student_ftrs, student_tgt,
                                          scoring = msrs['RMSE'], cv=10)

        my_lbl = "{:12s} {: .3f} {: .2f}".format(mod_name,
                                                cv_results.mean(),
                                                cv_results.std())

        ax.plot(cv_results / baseline_results, 'o--', label=my_lbl)
ax.set_title("RMSE(model) / RMSE(baseline)\n$<$1 is better than baseline")
ax.legend();

![](img/d94e4cd766940d79abed0bc6ba4e4344_256_0.png)

这里很明显，3-NN 生成的误差比基线大得多（其比率大于 1），并且比其他两个回归器更差。我们还看到 LR 在更多折中似乎略占优势，尽管 10-NN 在第 6–9 折中也取得了一些胜利。

虽然它很容易被滥用（如我们在第 7.2.3 节中讨论的），让我们看看此问题的默认 $R^2$ 评分：

## 7.5 以更复杂的方式评估回归器：第二部分

fig, ax = plt.subplots(1, 1, figsize=(6, 3))
for mod_name, model in regressors.items():
    cv_results = skms.cross_val_score(student_ftrs, student_tgt, model, cv=10)
    my_lbl = "{ :12s} {: .3f} {: .2f}".format(mod_name, cv_results.mean(), cv_results.std())
    ax.plot(cv_results, 'o--', label=my_lbl)
ax.set_title("$R^2$");
# ax.legend(); # uncomment for summary stats

![](img/d94e4cd766940d79abed0bc6ba4e4344_257_0.png)

这里有两个有趣的模式。第一个是我们的线性回归似乎 consistently 比 k-NN-R 更稳定。第二个是我们的两个指标之间的模式看起来相当一致。毫无疑问，每个折中获胜者的顺序似乎是相同的——请记住，R² 越接近 1 越好。鉴于我们上面看到的 R² 与 MSE 之间的关系，我们对此可能并不太惊讶。

其次，如果你一直很注意，你可能会想知道为什么基线模型——这是一个均值预测模型——的 R² 不是零。顺便说一下，注意到这一点你会得到一颗金星。你能想出原因吗？正如所讨论的，训练集和测试集的均值会有不同的值。由于我们在交叉验证中进行了训练-测试分割，我们的训练均值和测试均值会有些偏差，但不会太多。你会注意到，均值模型的 R² 值大多在零附近。这就是我们为随机性和使用 R² 所付出的代价。

### 7.5.2 汇总交叉验证结果

另一种交叉验证预测的方法是将整个交叉验证过程视为单个学习器。如果你翻阅笔记，可能会发现当我们进行交叉验证时，每个示例只在一种测试场景中出现一次。因此，我们可以简单地收集所有预测——由训练于数据不同分区的一组学习器做出——并将其与我们已知的目标进行比较。将评估指标应用于这些预测和目标会为每个模型和指标给出一个单一值的净结果。我们通过 cross_val_predict 访问这些预测。

In [30]:

```
msrs = {'MAD' : metrics.mean_absolute_error,
        'RMSE' : rms_error} # not scorer, no model

results = {}
for mod_name, model in regressors.items():
    cv_preds = skms.cross_val_predict(model,
                                      student_ftrs, student_tgt,
                                      cv=10)
    for ax, msr in zip(axes, msrs):
        msr_results = msrs[msr](student_tgt, cv_preds)
        results.setdefault(msr, []).append(msr_results)
df = pd.DataFrame(results, index=regressors.keys())
df
```

Out[30]:

|  | 平均绝对偏差 | 均方根误差 |
|---|---|---|
| 基线 | 3.4470 | 4.6116 |
| std_knn3 | 3.7797 | 4.8915 |
| std_knn10 | 3.3666 | 4.4873 |
| std_lr | 3.3883 | 4.3653 |

### 7.5.3 残差

由于我们之前做了一些基本的残差图，让我们通过（1）查看基线模型的残差以及（2）使用标准化后的预处理数据来使其更有趣。

In [31]:

```
fig, axes = plt.subplots(1, 4, figsize=(10, 5),
                        sharex=True, sharey=True)
fig.tight_layout()
```

for model_name, ax in zip(regressors, axes):
    model = regressors[model_name]
    preds = skms.cross_val_predict(model,
                                   student_ftrs, student_tgt,
                                   cv=10)

    regression_residuals(ax, preds, student_tgt)
    ax.set_title(model_name + " residuals")
pd.DataFrame(student_tgt).describe().T

Out[31]:

|  | 计数 | 平均值 | 标准差 | 最小值 | 25% | 50% | 75% | 最大值 |
|---|---|---|---|---|---|---|---|---|
| G3 | 395.00 | 10.42 | 4.58 | 0.00 | 8.00 | 11.00 | 14.00 | 20.00 |

![](img/d94e4cd766940d79abed0bc6ba4e4344_259_0.png)

几点有趣的发现：

- 尽管我们使用均值模型作为基线模型，但我们有多个均值——每个训练分割对应一个。但请放心，我们的预测值对于仅均值模型来说只有轻微变化。
- 我们标准化后拟合模型的残差有一些显著的模式。
  1. 它们都显示出带状分布。带状分布是由于目标的整数值造成的：存在 17 和 18 的目标值，但没有 17.5。因此，我们有明显的间隙。
  2. 每个非基线模型的整体模式似乎都相当相似。
  3. 存在一整条“误差异常值”带，其中所有残差都是负的，并且随着预测量的增加而不断减小。负残差是正误差。它们表明我们在高估。右侧，我们预测 15，而实际值接近零，高估了约 15。左侧，我们预测接近 5，而实际值再次接近零，高估了约 5。所以，

