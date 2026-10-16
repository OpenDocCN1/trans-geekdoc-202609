

![](img/d94e4cd766940d79abed0bc6ba4e4344_402_0.png)

图11.4 用于GridSearch的嵌套交叉验证。

```
In [15]:

param_grid = {"n_neighbors" : np.arange(1,11),
    "weights"    : ['uniform', 'distance'],
    "p"          : [1,2,4,8,16]}

knn = neighbors.KNeighborsClassifier()
grid_knn = skms.GridSearchCV(knn,
                param_grid = param_grid,
                cv=3)
```

正如在无交叉验证的参数层面发生的情况一样，现在我们无意中缩小到了对这个数据集表现良好的超参数范围内。为了消除这种偷窥效应，我们可以将`GridSearchCV(knn)`再包裹一层五折交叉验证：

```
In [16]:

outer_scores = skms.cross_val_score(grid_knn,
                    iris.data, iris.target,
                    cv=5)
print(outer_scores)
```

[0.9667 1.      0.9333 0.9667 1.    ]

在我们的示例中，我们使用了5次重复的3折交叉验证，构成5×3嵌套交叉验证策略——也称为双重交叉策略。我选择这些数字是为了让示例和图表更清晰。然而，对于嵌套交叉验证，最常见的建议是5×2交叉验证方案，这一方案由Tom Dietterich推广。数字5和2并非魔法，但Dietterich确实为它们提供了一些实际依据。选择2作为内层循环的值，是因为它使训练集不相交：它们完全没有重叠。选择5是因为Dietterich发现，较少的重复次数会导致结果中的变异性（即差异）过大，因此我们需要更多的重复次数来获得可靠、可重复的估计。如果超过5次，拆分之间的重叠过多，这会牺牲训练集之间的独立性，导致估计结果彼此之间越来越相关。因此，5是在这两个相互竞争的标准之间的一个理想折中。

## 11.3.4 对嵌套交叉验证的评述

为了理解刚才发生了什么，让我扩展我在前面11.2.2.2节中编写的GridSearch伪代码。

In [17]：

```
def nested_cv_pseudo_code(all_data):
    results = []
    for outer_train, test in make_cv_split(all_data):
        for hyper_params in hyper_parameter_possibilities:
            for train, valid in make_cv_split(outer_train):
                inner_score = evaluate(model.fit(train).predict(valid))
    best_mod = xxx # choose model with best inner_score
    preds = best_model.fit(outer_train).predict(test)
    results.append(evaluate(preds))
```

让我回顾一下扁平交叉验证的过程。学习的训练阶段会设置参数，我们需要一个训练-验证步骤来评估这些参数的表现。但实际上，我们需要交叉验证——即多次训练-验证拆分——通过平均来生成更好的估计，并评估这些估计的变异性。我们必须将这一思想扩展到GridSearch。

当我们使用网格搜索来选取偏好的超参数值时，我们实际上是在确定——或者说，是在另一个层面上优化——这些超参数值。至少，我们需要网格搜索的训练-验证步骤来评估这些结果。然而，实际上，我们想要对我们整个流程的性能有一个更好的估计。我们还很想知道我们对结果有多大把握。如果我们再执行一次该流程，是否会得到相似的结果？相似性可以体现在几个不同的方面：(1) 预测结果是否相似？(2) 整体性能是否相似？(3) 选定的超参数是否相似？(4) 不同的超参数是否会导致相似的性能结果？

在嵌套交叉验证中，外层交叉验证告诉我们，当我们通过网格搜索来选取超参数时，可以预期到的变异性。这类似于通常的交叉验证，后者告诉我们，在估计参数时，不同的训练-测试拆分会导致性能如何变化。

正如我们不使用交叉验证来确定模型的参数——参数由交叉验证内部的训练步骤设定——我们也不使用GridSearch的外层交叉验证来挑选最佳超参数。最佳超参数是在GridSearch内部确定的。外层交叉验证只是为我们提供一个更现实的估计，即当这些由内层选定的超参数被用于最终模型时，它们会有怎样的表现。

嵌套交叉验证的实际应用远比试图理解它要容易得多。我们可以使用嵌套交叉验证：

In [18]：

```
param_grid = {"n_neighbors" : np.arange(1,11),
              "weights"    : ['uniform', 'distance'],
              "p"          : [1,2,4,8,16]}

knn = neighbors.KNeighborsClassifier()
```

```
grid_knn = skms.GridSearchCV(knn,
                            param_grid = param_grid,
                            cv=2)

outer_scores = skms.cross_val_score(grid_knn,
                                    iris.data,
                                    iris.target,
                                    cv=5)

# how does this do over all??
print(outer_scores)
```

[0.9667 0.9667 0.9333 0.9667 1.  ]

这些值向我们展示了，当我们随机分割数据并将其送入底层的超参数和参数计算时，可以预期的学习性能。重复几次可以让我们了解可以预期的答案。反过来，这告诉我们估计可能有多大的变异性。现在，我们实际上可以根据GridSearchCV中的参数来训练我们首选模型：

In [19]：

```
grid_knn.fit(iris.data, iris.target)
preferred_params = grid_knn.best_estimator_.get_params()
final_knn = neighbors.KNeighborsClassifier(**preferred_params)
final_knn.fit(iris.data, iris.target)
```

Out[19]：

```
KNeighborsClassifier(algorithm='auto', leaf_size=30, metric='minkowski',
                     metric_params=None, n_jobs=None, n_neighbors=7, p=4,
                     weights='distance')
```

我们对其性能的估计基于刚才执行的外层5折交叉验证。我们现在可以使用`final_knn`对新的数据进行预测，但在此之前，我们应该花一点时间，先将其指向一个留出的测试集（见练习）。

## 11.4 流水线

我们在特征工程中最大的限制之一——来自第10章的任务——是组织计算并遵守不向测试集泄露信息的规则。幸运的是，流水线使我们能够同时做到这两点。我们在7.4节中简要介绍了流水线。在这里，我们将了解关于流水线的更多细节，并展示它们如何与网格搜索集成。

如果我们回到工厂的类比，可以很容易地想象将一台机器的输出连接到下一台机器的输入。如果其中一些组件是特征工程步骤（如第10章所述），我们就有了一个非常自然的传送带。传送带可以方便地将样本从一个步骤移动到下一个步骤。

### 11.4.1 一个简单流水线

在最简单的示例中，我们可以从多个模型和转换器创建一个学习组件的流水线，然后将该流水线用作模型。`make_pipeline`将其变成了一行代码：

```
In [20]:

scaler = skpre.StandardScaler()
logreg = linear_model.LogisticRegression()

pipe = pipeline.make_pipeline(scaler, logreg)
print(skms.cross_val_score(pipe, iris.data, iris.target, cv=10))
```

[0.8 0.8667 1. 0.8667 0.9333 0.9333 0.8 0.8667 0.9333 1. ]

如果我们使用方便的`make_pipeline`，流水线中各步骤的名称是根据各步骤的`__class__`属性构建的。例如：

```
In [21]:

def extract_name(obj):
    return str(logreg.__class__).split('.')[-1][:-2].lower()

print(logreg.__class__)
print(extract_name(logreg))
```

<class 'sklearn.linear_model.logistic.LogisticRegression'>
logisticregression

名称被转换为小写，并且仅保留最后一个`.`之后字母字符。得到的名称是`logisticregression`，我们可以在这里看到：

```
In [22]:

pipe.named_steps.keys()

Out[22]:

dict_keys(['standardscaler', 'logisticregression'])
```

如果我们想自己命名这些步骤，我们使用更具可定制性的`Pipeline`构造函数：
