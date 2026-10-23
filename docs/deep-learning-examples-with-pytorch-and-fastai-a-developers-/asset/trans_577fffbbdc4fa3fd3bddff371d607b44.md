
![](img/d5454da46c702784893ef8b0b539e5b9_362_0.png)

现在获取随机森林模型的预测结果。

```
forest_preds = tree.predict_proba(X_test)
```

并将预测结果导入我们的模型集成中。

```
avgs = (nn_preds + xgb_preds + forest_preds) / 3
```

```
accuracy(tensor(avgs), tensor(y_test))
```

```
tensor(0.8348)
```

我们可以看到，随机森林模型可能不是此问题的最佳模型，因为将其添加到我们的集成中降低了准确率！

## 第 25 章
贝叶斯优化

贝叶斯优化的概念是超参数调优的概念。我们定义一个搜索网格，并在该搜索网格区域内伪随机尝试值，以分析哪些值似乎效果较好。

对于此示例，我们再次使用 ADULTS 数据集。

```python
from fastai.tabular.all import *

path = untar_data(URLs.ADULT_SAMPLE)
df = pd.read_csv(path/'adult.csv')
!pip install bayesian-optimization
from bayes_opt import BayesianOptimization
```

如果我们想使用贝叶斯优化，我们必须实现一个 fit_with 函数，它接受调优参数值并执行我们要求的操作。

```python
def fit_with(lr:float, wd:float, dp:float):
# create a Learner
learn = tabular_learner(data,

layers =[200,100], metrics=accuracy, emb_drop=dp,
wd=wd)

# Train for x epochs with learn.no_bar(): learn.fit_one_cycle(3, lr)

# Save, print, and return the overall accuracy
acc = float(learn.validate()[1])
return acc
```

在此函数内部，我们可以尝试优化任何我们想要的内容。最后，函数需要知道如何对修改进行评分：

`acc = float(learn.validate()[1])`

这就是函数应该返回的内容。该概念与重要性排列相似，但结构更严谨。
让我们进一步调整，以展示如何调整学习率、嵌入权重衰减、dropout 和层大小：

```python
def fit_with(lr:float, wd:float, dp:float, n_layers:float, layer_1:float,
layer_2:float, layer_3:float):
    print(lr, wd, dp)
    if int(n_layers) == 2:
        layers = [int(layer_1), int(layer_2)]
```

```
elif int(n_layers) == 3:
layers = [int(layer_1), int(layer_2), int(layer_3)]
else:
layers = [int(layer_1)]
learn = tabular_learner(dls,
layers=layers,
metrics=accuracy,
embed_p=float(dp),
wd=float(wd))
with learn.no_bar() and learn.no_logging():
learn.fit(5, lr=float(lr))
acc = float(learn.validate()[1])
return acc
```

现在我们可以检查一下！

```
cat_names = ['workclass', 'education', 'marital-status',
'occupation', 'relationship', 'race']
cont_names = ['age', 'fnlwgt', 'education-num']
procs = [Categorify, FillMissing, Normalize]
y_names = 'salary'
y_block = CategoryBlock()
splits = RandomSplitter()(range_of(df))
```

```
to = TabularPandas(df, procs=procs, cat_names=cat_names,
cont_names=cont_names, y_names=y_names, y_block=y_block,
splits=splits)
```

```
dls = to.dataloaders(bs=512)
```

我们需要声明超参数。我们为每个参数传入最小值和最大值。

```
hps = {'lr': (1e-05, 1e-01),
'wd': (4e-4, 0.4),
'dp': (0.01, 0.5),

'n_layers': (1,3),
'layer_1': (50, 200),
'layer_2': (100, 1000),
'layer_3': (200, 2000)}
```

现在我们可以构建优化器并运行它！

```
optim = BayesianOptimization(
 f = fit_with, # our fit function
 pbounds = hps, # our hyper parameters to tune
 verbose = 2, # 1 prints out when a maximum is observed, 0
  -> for silent
 random_state=1
)
%time optim.maximize(n_iter=10)
```

```
| iter | target | dp | layer_1 | layer_2 | ↘ → layer_3 | lr | n_layers | wd |
---------------------------------------------------------------
0.014684121522803134 0.07482958046651729 0.21434078230426126

| [0m 1 [0m | [0m 0.8366 [0m | [0m 0.2143 [0m | [0m 158. → 0 [0m | [0m
100.1 [0m | [0m 744.2 [0m | [0m 0.01468 [0m ↘ → | [0m 1.185 [0m | [0m
0.07483 [0m |

0.06852509784467198 0.3512957275818218 0.1793247562510934

| [0m 2 [0m | [0m 0.8223 [0m | [0m 0.1793 [0m | [0m 109. → 5 [0m | [0m
584.9 [0m | [0m 954.6 [0m | [0m 0.06853 [0m ↘ → | [0m 1.409 [0m | [0m
0.3513 [0m |
0.01404728990137426 0.32037752964274446 0.02341992066698382

| [95m 3 [0m | [95m 0.8381 [0m | [95m 0.02342 [0m | [95m ↘ → 150.6 [0m |
[95m 475.6 [0m | [95m 1.206e+0[0m | [95m 0. → 01405 [0m | [95m 1.396
[0m | [95m 0.3204 [0m |

0.0894617202837497 0.016006291379859792 0.4844481721025048

| [0m 4 [0m | [0m 0.8338 [0m | [0m 0.4844 [0m | [0m 97. → 01 [0m | [0m
723.1 [0m | [0m 1.778e+0[0m | [0m 0.08946 ↘ → [0m | [0m 1.17 [0m | [0m
0.01601 [0m |
```

0.0957893741197487 0.27687409473460917 0.09321690558663875

| [0m 5 [0m | [0m 0.8159 [0m | [0m 0.09322 [0m | [0m 181. → 7 [0m | [0m
188.5 [0m | [0m 958.0 [0m | [0m 0.09579 [0m┌ →| [0m 2.066 [0m | [0m
0.2769 [0m |

0.010278165724320144 0.09525641811550664 0.039180893394315415

| [0m 6 [0m | [0m 0.8366 [0m | [0m 0.03918 [0m | [0m 169. → 8 [0m | [0m
995.0 [0m | [0m 206.4 [0m | [0m 0.01028 [0m┌ →| [0m 1.351 [0m | [0m
0.09526 [0m |

0.072169727771627 0.035039066808375346 0.1710613610736308

| [0m 7 [0m | [0m 0.8355 [0m | [0m 0.1711 [0m | [0m 57. → 63 [0m | [0m
100.2 [0m | [0m 1.93e+03[0m | [0m 0.07217 ┌ →[0m | [0m 2.868 [0m | [0m
0.03504 [0m |

0.013570829135142702 0.031451918940067894 0.2730913244726432

| [0m 8 [0m | [0m 0.8318 [0m | [0m 0.2731 [0m | [0m 91. → 85 [0m | [0m
721.2 [0m | [0m 1.776e+0[0m | [0m 0.01357 ┌ →| [0m 2.68 [0m | [0m
0.03145 [0m |

0.05453843492810724 0.30190468577026874 0.39944160084921443

| [0m 9 [0m | [0m 0.8311 [0m | [0m 0.3994 [0m | [0m 195. → 8 [0m | [0m
135.7 [0m | [0m 218.7 [0m | [0m 0.05454 [0m┌ →| [0m 2.424 [0m | [0m
0.3019 [0m |

0.061613299507949554 0.05174472685269531 0.085706981737216

| [0m 10 [0m | [0m 0.8249 [0m | [0m 0.08571 [0m | [0m 195. → 5 [0m | [0m
994.7 [0m | [0m 1.25e+03[0m | [0m 0.06161 [0m┌ →| [0m 2.452 [0m | [0m
0.05174 [0m |

0.05537157580234801 0.2905569552495946 0.4663821732597001

| [0m 11 [0m | [0m 0.8271 [0m | [0m 0.4664 [0m | [0m 54. → 71 [0m | [0m
110.6 [0m | [0m 237.7 [0m | [0m 0.05537 ↙ _ [0m | [0m 1.148 [0m | [0m
0.2906 [0m |
0.061688937033612945 0.16814808642307333 0.302605595448633

| [0m 12 [0m | [0m 0.8291 [0m | [0m 0.3026 [0m | [0m 190. → 2 [0m | [0m
357.1 [0m | [0m 1.99e+03[0m | [0m 0.06169 [0m↙ →| [0m 1.245 [0m | [0m
0.1681 [0m |

0.08706685388671734 0.2815475542319707 0.0263005243239511

| [0m 13 [0m | [0m 0.8257 [0m | [0m 0.0263 [0m | [0m 199. → 1 [0m | [0m
990.5 [0m | [0m 1.991e+0[0m | [0m 0.08707 [0m↙ →| [0m 2.941 [0m | [0m
0.2815 [0m |

0.09659606295207694 0.3605505901264276 0.1096990839327761

| [0m 14 [0m | [0m 0.8269 [0m | [0m 0.1097 [0m | [0m 53. → 56 [0m | [0m
107.6 [0m | [0m 1.453e+0[0m | [0m 0.0966 ↙ →[0m | [0m 2.126 [0m | [0m
0.3606 [0m |

0.09731696484910228 0.09079549937527154 0.34595395028767806

| [0m 15 [0m | [0m 0.8303 [0m | [0m 0.346 [0m | [0m 197. → 6 [0m | [0m
643.4 [0m | [0m 207.3 [0m | [0m 0.09732 [0m↙ →| [0m 1.222 [0m | [0m
0.0908 [0m |

============================================================
CPU times: user 39.6 s, sys: 2.84 s, total: 42.5 s
Wall time: 36 s

```
print(optim.max)
```

**瞧！我们得到了结果** 我们可以清楚地看到，最佳层数为 2。第一层的大小为 57，第二层的大小为 100。

## 第 26 章
### 使用 SHAP 库分析神经网络

SHAP 库专为分析和解释神经网络而构建。我们今天使用它来分析表格数据。对于本章，我们使用 FastSHAP，它是由 Zachary Mueller 将 shap 库移植到 fastai 的版本（https://github.com/muellerzr/fastinference）——请注意，FastSHAP 库最近已集成到 fast inference 框架中，并且仅适用于 TabularData。

首先让我们安装它：

```
!pip install fastinference
```

因为我们想要对神经网络进行一些解释，所以我们必须事先构建一个神经网络。让我们再次使用 ADULTS 数据集。此模型将是我们分析神经网络的基线。

```
from fastai.tabular.all import *
path = untar_data(URLs.ADULT_SAMPLE)
df = pd.read_csv(path/'adult.csv')
dep_var = 'salary'
cat_names = ['workclass', 'education', 'marital-status',
             'occupation', 'relationship', 'race']
cont_names = ['age', 'fnlwgt', 'education-num']
procs = [Categorify, FillMissing, Normalize]

splits = IndexSplitter(list(range(800,1000)))(range_of(df))
to = TabularPandas(df, procs, cat_names, cont_names, y_names="salary",
                   splits=splits)

dls = to.dataloaders()
learn = tabular_learner(dls, layers=[200,100], metrics=accuracy)
learn.fit(1,
```
