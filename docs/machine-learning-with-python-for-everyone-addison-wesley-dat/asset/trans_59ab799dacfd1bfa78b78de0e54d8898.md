
### 7.2.3.1 对机器学习世界中 R² 的一种解释

在线性回归情况下，该第二项 SSE_ours / SSE_mean 将介于零和一之间。在高端，如果线性回归仅使用常数项，它将与均值相同，其值将为 1。在低端，如果线性回归对数据没有误差，它将为零。线性回归模型在拟合训练数据并在训练数据上进行评估时，不会比均值模型表现更差。

然而，对于我们来说，这种限制不一定成立，因为我们不一定使用线性模型。最容易理解这一点的方法是意识到我们的“花哨”模型可能比均值更差。虽然很难想象在训练数据上会失败得如此严重，但在测试数据上却开始显得合理。如果我们有一个比均值差的模型并且使用 sklearn 的 R² 公式，突然间我们就得到了一个负值。对于标记为 R² 的值来说，这真的很令人困惑。平方数通常是正的，对吧？

所以，我们有一个 1− 某物的公式，看起来我们可以将其读作“100% 减去某物”——这将给我们剩余部分。我们不能这样做，因为我们的某物可能是正的也可能是负的，我们不知道如何称呼一个超过真实最大值 100% 的值，该最大值涵盖了所有可能性。

在我们剩下的东西中，我们如何以合理的方式思考 sklearn 的 R²？SSE 之间的比率为我们提供了相对于标准基线模型的归一化性能。在内部，SSE 实际上与我们的均方误差相同，只是没有均值。有趣的是，我们可以利用一些你从未想过需要的代数。如果我们将比率中的两个 SSE 都除以 n，我们得到

R² = 1 − (SSE_ours / n) / (SSE_mean / n) = 1 − MSE_ours / MSE_mean

我们看到我们实际上一直在处理伪装的 MSE 比率。让我们去掉 1− 以便更轻松地解释右边：

R² = 1 − SSE_ours / SSE_mean = 1 − MSE_ours / MSE_mean
1 − R² = SSE_ours / SSE_mean = MSE_ours / MSE_mean

总之，我们可以将 1 − R²（对于任意机器学习模型）视为 MSE，该 MSE 由我们从一个预测均值的简单基线模型得到的 MSE 进行归一化。如果我们有两个感兴趣的模型，并且如果我们比较（除以）我们的模型 1 的 1 − R² 和我们的模型 2 的 1 − R²，我们得到：

(1 − R²_M1) / (1 − R²_M2) = (MSE_M1 / MSE_mean) / (MSE_M2 / MSE_mean) = MSE_M1 / MSE_M2

这只是两个模型之间 MSE — 或 SSE — 的比率。

### 7.2.3.2 一个冷酷的现实：sklearn 的 R²

让我们手动和用 sklearn 计算几个简单的 R² 值。我们从实际值和来自简单预测均值模型的测试集预测值计算 r2_score：

In [8]:

```
baseline = dummy.DummyRegressor(strategy='mean')

baseline.fit(diabetes_train_ftrs, diabetes_train_tgt)
base_preds = baseline.predict(diabetes_test_ftrs)

# r2 is not symmetric because true values have priority
# and are used to compute target mean
base_r2_sklearn = metrics.r2_score(diabetes_test_tgt, base_preds)
print(base_r2_sklearn)
```

-0.014016723490579253

现在，让我们通过一些手动计算来查看这些值：

In [9]:

```
# sklearn-train-mean to predict test tgts
base_errors = base_preds - diabetes_test_tgt
sse_base_preds = np.dot(base_errors, base_errors)

# train-mean to predict test targets
train_mean_errors = np.mean(diabetes_train_tgt) - diabetes_test_tgt
sse_mean_train = np.dot(train_mean_errors, train_mean_errors)

# test-mean to predict test targets (Danger Will Robinson!)
test_mean_errors = np.mean(diabetes_test_tgt) - diabetes_test_tgt
sse_mean_test = np.dot(test_mean_errors, test_mean_errors)

print("sklearn train-mean model SSE(on test):", sse_base_preds)
print(" manual train-mean model SSE(on test):", sse_mean_train)
print(" manual test-mean model SSE(on test):", sse_mean_test)
```

sklearn 训练均值模型 SSE(在测试上): 622398.9703179051
    手动 训练均值模型 SSE(在测试上): 622398.9703179051
    手动 测试均值模型 SSE(在测试上): 613795.5675675676

我为什么要做第三种替代方案？我计算了测试集的均值并查看了相对于测试目标的误差。不出所料，由于我们在“为测试而教”，我们比其他情况做得稍好一些。让我们看看如果我们使用这些为测试而教的值作为计算 R2 的基线会发生什么：

In [10]:

```
1 - (sse_base_preds / sse_mean_test)
```

Out[10]:

-0.014016723490578809

Shazam。你没注意到吗？我再做一次。

```
In [11]:

print(base_r2_sklearn)
print(1 - (sse_base_preds / sse_mean_test))
```

-0.014016723490579253
-0.014016723490578809

sklearn 的 R² specifically 从我们正在测试的真实值中计算其基线模型——均值模型。我们并不是在比较 my_model.fit(train) 和 mean_model.fit(train) 的性能。使用 sklearn 的 R²，我们是在比较 my_model.fit(train) 与 mean_model.fit(test)，并在测试集上对它们进行评估。由于这很违反直觉，让我们用长的方式把它画出来：

```
In [12]:

#
# WARNING! Don't try this at home, boys and girls!
# We are fitting on the *test* set... to mimic the behavior
# of sklearn R^2.
#
testbase = dummy.DummyRegressor(strategy='mean')
testbase.fit(diabetes_test_ftrs, diabetes_test_tgt)
testbase_preds = testbase.predict(diabetes_test_ftrs)
testbase_mse = metrics.mean_squared_error(testbase_preds, diabetes_test_tgt)

models = [neighbors.KNeighborsRegressor(n_neighbors=3), linear_model.LinearRegression()]
results = co.defaultdict(dict)
for m in models:
    preds = (m.fit(diabetes_train_ftrs, diabetes_train_tgt)
             .predict(diabetes_test_ftrs))
    mse = metrics.mean_squared_error(preds, diabetes_test_tgt)
    r2 = metrics.r2_score(diabetes_test_tgt, preds)
    results[get_model_name(m)]['R^2'] = r2
    results[get_model_name(m)]['MSE'] = mse

print(testbase_mse)
```

```
df = pd.DataFrame(results).T
df['Norm_MSE'] = df['MSE'] / testbase_mse
df['1-R^2'] = 1-df['R^2']
display(df)
```

5529.689797906013

|  | MSE | R^2 | Norm_MSE | 1-R^2 |
|---|---|---|---|---|
| KNeighborsRegressor | 3,471.4194 | 0.3722 | 0.6278 | 0.6278 |
| LinearRegression | 2,848.2953 | 0.4849 | 0.5151 | 0.5151 |

因此，sklearn 计算的 1 − R² 等价于我们的模型 MSE 除以拟合到测试样本均值模型的归一化。如果我们知道测试目标的均值，该值就会告诉我们在与预测该已知均值相比时表现如何。

### 7.2.3.3 关于 R² 的建议

综上所述，我建议除非你是高级用户并且相信自己知道自己在做什么，否则不要使用 R²。原因如下：

- 1. R² 带有大量科学和统计上的包袱。当你说 R² 时，人们可能会认为你的意思比这里给出的计算更多。如果你用它的统计名称决定系数在 Google 上搜索 R²，你会发现成千上万条与我们此处的讨论不适用的陈述。任何包含“百分比”或“线性”或“解释”的陈述在应用于 sklearn 的 R² 时都应持极度怀疑态度。其中一些陈述在某些情况下是正确的。但并非总是如此。
- 2. R² 有多种公式——sklearn 使用其中一种。使用带截距的线性模型时，R² 的多种公式是等价的，但在其他情况下它们并不等价。这种公式的巴别塔加剧了与前一点的混淆。我们有一个 R² 的计算，在某些情况下，其含义超出了我们在 sklearn 中使用它的范围。我们现在不关心那些额外的东西。
- 3. R² 与一个非常奇怪的东西有简单的关系：在测试样本训练的均值模型上计算的归一化 MSE。我们可以通过直接采用替代方案来避免这些包袱。

而不是使用 R²，我们将简单地使用 MSE 或 RMSE。如果我们真的想归一化这些分数，我们可以将回归模型与训练集训练的均值模型进行比较。

## 7.3 残差图

我们深入研究了一些数学的繁琐细节。让我们退一步，看看评估回归器的一些图形技术。我们将开发回归的混淆矩阵类比。
