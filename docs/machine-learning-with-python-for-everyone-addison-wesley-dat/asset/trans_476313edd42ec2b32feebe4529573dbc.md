
## 调优超参数和管道

```python
# setup
from mlwpy import *
%matplotlib inline

iris = datasets.load_iris()
diabetes = datasets.load_diabetes()
digits = datasets.load_digits()
```

我们已经在第 5.2.2.4 节中介绍了模型、参数和超参数。我即将再次提及它们，有两个原因。首先，我希望你能看到一个具体的类比：(1) 我们通过改变代码和参数以不同方式编写简单 Python 函数，以及 (2) 学习模型如何使用参数和超参数。其次，我们将把注意力转向选择好的超参数。当我们拟合模型时，我们是在选择好的参数。我们需要一种明确的流程来选择好的超参数。我们将启用两种类型的搜索——GridSearch 和 RandomizedSearch。搜索是解决或优化问题的非常通用的方法。通常，搜索可以在数学上不那么“友好”的领域中工作。然而，代价——不出所料——是答案不保证是绝对最好的答案。相反，就像启发式方法一样，我们希望答案足够好。

所有的这些讨论将使我们很好地深入研究构建多学习组件串联的管道。通常，管道的正确使用要求我们为该管道的组件找到好的超参数。因此，如果不讨论 sklearn API 的搜索技术就过早深入管道，可能会导致不良习惯。我们不能允许这种情况！

```python
# a call that creates a function
three_adder = make_adder(3)

# using that created function
three_adder(10) == add_three(10)
```

Out[3]:

True

所以，好消息是 *它起作用了*。坏消息可能是你不知道为什么。让我们分解一下第 7 行发生的事情：`three_adder = make_adder(3)`。当我们调用 `make_adder(3)` 时，我们启动了函数调用的常规机制。3 被关联到 `make_adder` 中的名称 k。然后，我们执行 `make_adder` 中的代码。它做了两件事：定义名称 `add_k`——带有函数的东西——然后返回 `add_k`。这两个步骤几乎就像一个有两个行的函数：m=10 然后 `return 10`。不同之处在于，我们定义了一个名称 `add_k`，其值是一个函数，而不是一个简单的 int。

好吧，定义 `add_k` 到底是什么意思？它是一个只有一个参数 x 的函数。传入 `add_k` 的任何值都将加到传入 `make_adder` 的 k 值上。但这个特定的 `add_k` 永远不会向 x 添加其他任何东西。从它的角度来看，那个 k 对所有时间来说都是一个常数值。获取不同的 `add_k` 的唯一方法是对 `make_adder` 再次调用并创建一个不同的函数。

让我们总结一下从 `make_adder` 得到的内容：

- 返回的 *东西*（严格来说，它是一个 Python 对象）是一个带有一个参数的函数。
- 当返回的函数被调用时，它 (1) 计算 k 加上调用时传入的值，并 (2) 返回该值。

让我们把这一点联系回我们的学习模型。当我们说 `KNeighborsClassifier(3)` 时，我们做的事情类似于 `make_adder(3)`。它给我们一个具体的对象，我们可以对其 `.fit`，其中 3 已烘焙在其配方中。如果我们想要 5-NN，我们需要用不同的调用构造一个新学习机器：`KNeighborsClassifier(5)`，就像构造一个 `five_adder` 需要调用 `make_adder(5)` 一样。现在，在 `three_adder` 和 `five_adder` 的情况下，你可能在对我喊，“直接用 `add(x, y)`，笨蛋！”没关系，我不介意。我们可以那样做。但在 k-NN 的情况下，我们不能。算法内部的设计方式不允许这样做。

我们的收获是什么？我阐述了固定与参数驱动行为的想法，以说明以下几点：

- 1. 在我们创建模型后，我们不会修改学习机器的内部状态。我们可以修改旋钮的值以及通过侧输入托盘提供给它的内容（如我们在第 1.3 节中看到的）。
- 2. 训练步骤为我们提供了首选的旋钮设置和输入托盘内容。
- 3. 如果训练后测试的结果不令人满意，我们也可以选择一个具有不同内部结构的完全不同的学习机器。我们可以选择完全不同类型的机器。我们可以从 k-NN 切换到线性回归。或者，我们可以留在同一类学习机器中并改变超参数：从 3-NN 切换到 5-NN。这是从第 5.2.2.1 节的模型选择过程。

### 11.2 调优超参数

现在让我们看看在 sklearn 的帮助下如何选择好的超参数。

### 11.2.1 关于计算机科学和学习术语的说明

在计算机科学术语中不幸的怪癖是，当我们描述函数调用的过程时，参数和参数这两个术语经常被互换使用。然而，从最严格的意义上讲，它们有更具体的含义：参数是实际传入调用的值，而参数是函数中接收值的占位符。为了澄清这些术语，一些技术文档使用实际参数/参数和形式参数/参数的名称。我们为什么在意？因为当我们开始谈论调优超参数时，你很快就会听到人们谈论参数调优。然后你会认为我一直在骗你关于内部工厂机器组件由超参数选择设置和外部工厂机器组件（旋钮）由参数优化设置之间的区别。

在这本书中，我专门对计算机科学的小动物们使用了参数这个术语。这 specifically 是为了避免与机器学习的参数和超参数术语冲突。我将继续使用参数（在训练期间优化）和超参数（通过交叉验证调优）。请注意，sklearn 文档和函数参数名称通常 (1) 将超参数缩写为 param 或 (2) 在计算机科学意义上使用 param。在任何一种情况下，在下面的代码中我们将谈论学习构造函数的实际参数——例如在 k-NN 机器中指定 k=3 的值。机器学习的说法是我们将 k-NN 的超参数设置为 3。

### 11.2.2 完全搜索的示例

为了防止这一点变得过于抽象，让我们看一个具体的例子。

KNeighborsClassifier 有许多可以调用的参数。这些参数中的大多数是超参数，控制我们创建的 KNeighborsClassifier 的内部运行。它们如下：

```
In [4]:
knn = neighbors.KNeighborsClassifier()
print(" ".join(knn.get_params().keys()))
```

algorithm leaf_size metric metric_params n_jobs n_neighbors p weights

我们除了 n_neighbors 之外还没有深入研究这些。n_neighbors 参数控制我们 k-NN 学习模型中的 k。你可能记得，近邻的关键问题是决定不同示例之间的距离。这些正是通过 metric、metric_params 和 p 的某些组合精确控制的。weights 决定邻居如何组合以得出最终答案。

### 11.2.2.1 评估单个超参数

在第 5.7.2 节中，我们手动完成了比较 k、n_neighbors 的几个不同值的过程。在进入更复杂的示例之前，让我们用 GridSearch 的内置 sklearn 支持重新处理该示例。

In [5]:

```
param_grid = {"n_neighbors" : [1,3,5,10,20]}

knn = neighbors.KNeighborsClassifier()
# warning! this is with accuracy
grid_model = skms.GridSearchCV(knn,
    return_train_score=True,
    param_grid = param_grid,
    cv=10)

grid_model.fit(digits.data, digits.target)
```

Out[5]:

```
GridSearchCV(cv=10, error_score='raise-deprecating',
    estimator=KNeighborsClassifier(algorithm='auto', leaf_size=30,
        metric='minkowski', metric_params=None,
        n_jobs=None, n_neighbors=5, p=2, weights='uniform'),
    fit_params=None, iid='warn', n_jobs=None,
    param_grid={'n_neighbors': [1, 3, 5, 10, 20]},
    pre_dispatch='2*n_jobs', refit=True, return_train_score=True,
    scoring=None, verbose=0)
```

幸运的是，skms.GridSearchCV 的结果只是一个模型，所以你已经知道如何让它运行：对其调用 fit。现在，它大约需要单次 k-NN 运行的五倍时间，因为我们为 k 的五个值运行它。fit 的结果是一个相当庞大的 Python 字典。它包含超参数和交叉验证轮次的每个组合的条目。幸运的是，它可以用 pd.DataFrame(grid_model.cv_results_) 快速转换为 DataFrame。
