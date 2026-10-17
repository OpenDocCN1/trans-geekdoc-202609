
```
Out[3]:

True
```

所以，好消息是 *它起作用了*。坏消息可能是你不知道为什么。让我们分解一下第 7 行发生的事情：`three_adder = make_adder(3)`。当我们调用 `make_adder(3)` 时，我们启动了函数调用的常规机制。3 被关联到 `make_adder` 中的名称 `k`。然后，我们执行 `make_adder` 中的代码。它做了两件事：定义名称 `add_k`——带有函数的东西——然后返回 `add_k`。这两个步骤几乎就像一个有两个行的函数：`m=10` 然后 `return 10`。不同之处在于，我们定义了一个名称 `add_k`，其值是一个函数，而不是一个简单的 int。

好吧，定义 `add_k` 到底是什么意思？它是一个只有一个参数 x 的函数。传入 `add_k` 的任何值都将加到传入 `make_adder` 的 k 值上。但这个特定的 `add_k` 永远不会向 x 添加其他任何东西。从它的角度来看，那个 `k` 对所有时间来说都是一个常数值。获取不同的 `add_k` 的唯一方法是对 `make_adder` 再次调用并创建一个不同的函数。

让我们总结一下从 `make_adder` 得到的内容：

- 返回的 *东西*（严格来说，它是一个 Python 对象）是一个带有一个参数的函数。
- 当返回的函数被调用时，它 (1) 计算 `k` 加上调用时传入的值，并 (2) 返回该值。

让我们把这一点联系回我们的学习模型。当我们说 `KNeighborsClassifier(3)` 时，我们做的事情类似于 `make_adder(3)`。它给我们一个具体的对象，我们可以对其 `.fit`，其中 3 已烘焙在其配方中。如果我们想要 5-NN，我们需要用不同的调用构造一个新学习机器：`KNeighborsClassifier(5)`，就像构造一个 `five_adder` 需要调用 `make_adder(5)` 一样。现在，在 `three_adder` 和 `five_adder` 的情况下，你可能在对我喊，“直接用 `add(x, y)`，笨蛋！”没关系，我不介意。我们可以那样做。但在 k-NN 的情况下，我们不能。算法内部的设计方式不允许这样做。

我们的收获是什么？我阐述了固定与参数驱动行为的想法，以说明以下几点：

- 1. 在我们创建模型后，我们不会修改学习机器的内部状态。我们可以修改旋钮的值以及通过侧输入托盘提供给它的内容（如我们在第 1.3 节中看到的）。
- 2. 训练步骤为我们提供了首选的旋钮设置和输入托盘内容。
- 3. 如果训练后测试的结果不令人满意，我们也可以选择一个具有不同内部结构的完全不同的学习机器。我们可以选择完全不同类型的机器。我们可以从 k-NN 切换到线性回归。或者，我们可以留在同一类学习机器中并改变超参数：从 3-NN 切换到 5-NN。这是从第 5.2.2.1 节的模型选择过程。

## 11.2 调优超参数

现在让我们看看在 `sklearn` 的帮助下如何选择好的超参数。

### 11.2.1 关于计算机科学和学习术语的说明

在计算机科学术语中不幸的怪癖是，当我们描述函数调用的过程时，参数和参数这两个术语经常被互换使用。然而，从最严格的意义上讲，它们有更具体的含义：参数是实际传入调用的值，而参数是函数中接收值的占位符。为了澄清这些术语，一些技术文档使用实际参数/参数和形式参数/参数的名称。我们为什么在意？因为当我们开始谈论调优超参数时，你很快就会听到人们谈论参数调优。然后你会认为我一直在骗你关于内部工厂机器组件由超参数选择设置和外部工厂机器组件（旋钮）由参数优化设置之间的区别。

在这本书中，我专门对计算机科学的小动物们使用了参数这个术语。这 specifically 是为了避免与机器学习的参数和超参数术语冲突。我将继续使用参数（在训练期间优化）和超参数（通过交叉验证调优）。请注意，`sklearn` 文档和函数参数名称通常 (1) 将超参数缩写为 `param` 或 (2) 在计算机科学意义上使用 `param`。在任何一种情况下，在下面的代码中我们将谈论学习构造函数的实际参数——例如在 k-NN 机器中指定 `k=3` 的值。机器学习的说法是我们将 k-NN 的超参数设置为 3。

### 11.2.2 完全搜索的示例

为了防止这一点变得过于抽象，让我们看一个具体的例子。

`KNeighborsClassifier` 有许多可以调用的参数。这些参数中的大多数是超参数，控制我们创建的 `KNeighborsClassifier` 的内部运行。它们如下：

```
In [4]:

knn = neighbors.KNeighborsClassifier()

print(" ".join(knn.get_params().keys()))
```

```
algorithm leaf_size metric metric_params n_jobs n_neighbors p weights
```

我们除了 `n_neighbors` 之外还没有深入研究这些。`n_neighbors` 参数控制我们 k-NN 学习模型中的 `k`。你可能记得，近邻的关键问题是决定不同示例之间的距离。这些正是通过 `metric`、`metric_params` 和 `p` 的某些组合精确控制的。`weights` 决定邻居如何组合以得出最终答案。

#### 11.2.2.1 评估单个超参数

在第 5.7.2 节中，我们手动完成了比较 `k`、`n_neighbors` 的几个不同值的过程。在进入更复杂的示例之前，让我们用 `GridSearch` 的内置 `sklearn` 支持重新处理该示例。

```
In [5]:

param_grid = {"n_neighbors" : [1,3,5,10,20]}

knn = neighbors.KNeighborsClassifier()

# warning! this is with accuracy

grid_model = skms.GridSearchCV(knn,

    return_train_score=True,

    param_grid = param_grid,

    cv=10)

grid_model.fit(digits.data, digits.target)
```

```
Out[5]:

GridSearchCV(cv=10, error_score='raise-deprecating',

    estimator=KNeighborsClassifier(algorithm='auto', leaf_size=30,

        metric='minkowski', metric_params=None,

        n_jobs=None, n_neighbors=5, p=2, weights='uniform'),

    fit_params=None, iid='warn', n_jobs=None,

    param_grid={'n_neighbors': [1, 3, 5, 10, 20]},

    pre_dispatch='2*n_jobs', refit=True, return_train_score=True,

    scoring=None, verbose=0)
```

幸运的是，`skms.GridSearchCV` 的结果只是一个模型，所以你已经知道如何让它运行：对其调用 `fit`。现在，它大约需要单次 k-NN 运行的五倍时间，因为我们为 `k` 的五个值运行它。`fit` 的结果是一个相当庞大的 Python 字典。它包含超参数和交叉验证轮次的每个组合的条目。幸运的是，它可以用 `pd.DataFrame(grid_model.cv_results_)` 快速转换为 `DataFrame`。

```
In [6]:

# many columns in .cv_results_

# all params are also available in 'params' column as dict

param_cols = ['param_n_neighbors']

score_cols = ['mean_train_score', 'std_train_score',

              'mean_test_score', 'std_test_score']

# look at first five params with head()

df = pd.DataFrame(grid_model.cv_results_).head()

display(df[param_cols + score_cols])
```

|   | param_n_neighbors | mean_train_score | std_train_score | mean_test_score | std_test_score |
|---|-------------------|------------------|-----------------|-----------------|----------------|
| 0 | 1 | 1.0000 | 0.0000 | 0.9761 | 0.0180 |
| 1 | 3 | 0.9933 | 0.0009 | 0.9777 | 0.0161 |
| 2 | 5 | 0.9907 | 0.0005 | 0.9738 | 0.0167 |
| 3 | 10 | 0.9861 | 0.0011 | 0.9644 | 0.0208 |
| 4 | 20 | 0.9806 | 0.0018 | 0.9610 | 0.0233 |

我们可以挑选出感兴趣的某些列，并以我们操作的超参数为索引对 `DataFrame` 进行索引。

```
In [7]:

# subselect columns of interest:

# param_* is a bit verbose

grid_df = pd.DataFrame(grid_model.cv_results_,

                       columns=['param_n_neighbors',

                                'mean_train_score',

                                'mean_test_score'])

grid_df.set_index('param_n_neighbors', inplace=True)

display(grid_df)
```

| param_n_neighbors | mean_train_score | mean_test_score |
|-------------------|------------------|-----------------|
| 1 | 1.0000 | 0.9761 |
| 3 | 0.9933 | 0.9777 |
| 5 | 0.9907 | 0.9738 |
| 10 | 0.9861 | 0.9644 |
| 20 | 0.9806 | 0.9610 |

我们也可以图形化地查看它：

```
In [8]:

ax = grid_df.plot.line(marker='.')

ax.set_xticks(grid_df.index);
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_393_0.png)

这种方法的优点之一——与我们在第 5 章中手动操作的做法相比——是我们不必手动管理任何结果收集工作。当我们开始尝试处理一个以上的超参数时，主要的好处就显现出来了。

#### 11.2.2.2 评估多个超参数

即使对于简单的 k-NN 模型，也有很多可能性。如果你查看文档，你会看到 `n_neighbors` 和 `p` 只是整数。我们可以尝试很多不同的值。记住，我们需要为所有这些组合管理训练集和测试集——一个整体的交叉验证过程。否则，我们就有风险用某些特定的超参数使数据过拟合，因为我们从未在新鲜数据上评估过它们。

如果我们要手动为一个接受三个参数的模型尝试这种方法，它在快速而粗糙的 Pythonic 伪代码中可能看起来像这样：

```
In [9]:

def best_model_hyper_params(make_a_model,

                            some_hyper_params,

                            data):

    results = {}

    for hyper_params in it.combinations(some_hyper_params):

        for train,test in make_cv_split(data):

            model = make_a_model(*hyper_params).fit(train)

            key = tuple(hyper_params)

            if key not in results:

                results[key] = []

            results[key].append(score(test, model.predict(test)))

            # or, rock stars can use this instead of the prior 4 lines:

            # (results.setdefault(tuple(hyper_params), [])

            #     .append(score(test, model.predict(test)))

    best_hp = max(results, key=results.get)

    best_model = make_a_model(*best_hp).fit(data)

    return best_model

def do_it():

    model = pick_a_model  # e.g., k-NN

    some_hyper_params = [values_for_hyper_param_1, # e.g., n_neighbors=[]

                         values_for_hyper_param_2,

                         values_for_hyper_param_3]

    best_model_hyper_params(model_type,

                            some_hyper_params,

                            data)
```

幸运的是，评估超参数是在设计和构建学习系统时常见的任务。因此，我们不必自己编写它。假设我们想尝试这些超参数的所有组合：

| 超参数 | 值 |
|---|---|
| `n_neighbors` | 1, ..., 10 |
| `weights` | `uniform`, `distance` |
| `p` | 1, 2, 4, 8, 16 |

两点说明：

- 1. `distance` 表示我的邻居的贡献会根据其与 *我* 的距离加权。`uniform` 表示所有我的邻居都被同等对待，没有加权。

2. `p` 是 Minkowski 距离构造器的一个参数。我们在第 2 章笔记中简要提到过它。只需知道 `p = 1` 是曼哈顿距离（L1 类似），`p = 2` 是欧几里得距离（L2 类似），而更高的 `p` 会趋近于一种称为无穷范数的东西。

以下代码执行了为 k-NN 模型尝试这些可能性的设置。它没有涉及实际的处理。

```
In [10]:

param_grid = {"n_neighbors" : np.arange(1,11),

              "weights"    : ['uniform', 'distance'],

              "p"          : [1,2,4,8,16]}

knn = neighbors.KNeighborsClassifier()

grid_model = skms.GridSearchCV(knn, param_grid = param_grid, cv=10)
```

这段代码的运行时间会比我们之前对 kNN 使用 `GridSearch` 的 `fit` 调用长一些，因为我们要拟合 10 × 2 × 5 × 10 = 200 个总模型（最后的 10 来自交叉验证步骤中的多次拟合）。但好消息是所有脏活都由我们来管理。

```
In [11]:

# digits takes ~30 mins on my older laptop

# %timeit -r1 grid_model.fit(digits.data, digits.target)

%timeit -r1 grid_model.fit(iris.data, iris.target)
```

```
1 loop, best of 1: 3.72 s per loop
```

调用 `grid_model.fit` 后，我们有一个可以调查的大量结果篮子。这可能有点难以处理。一些 Pandas-fu 可以得到我们可能感兴趣的内容：哪些模型——即哪些超参数集——表现最好？这次我将以稍微不同的方式提取值：

```
In [12]:

param_df = pd.DataFrame.from_records(grid_model.cv_results_['params'])

param_df['mean_test_score'] = grid_model.cv_results_['mean_test_score']

param_df.sort_values(by=['mean_test_score']).tail()
```
