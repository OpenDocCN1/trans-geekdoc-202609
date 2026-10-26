

Listing 19.20: 从头运行贝叶斯优化算法的示例最终输出。

## 19.5 使用贝叶斯优化进行超参数调优

实现贝叶斯优化以了解其工作原理可能是一个有用的练习。在实际项目中使用贝叶斯优化时，使用开源库提供的标准实现是一个好主意。这样既可以避免错误，又可以利用更广泛的配置选项和速度改进。贝叶斯优化的两个流行库包括 Scikit-Optimize 和 HyperOpt。在机器学习中，这些库通常用于调整算法的超参数。超参数调优非常适合贝叶斯优化，因为评估函数计算成本高（例如为每组超参数训练模型）且存在噪声（例如训练数据中的噪声和随机学习算法）。

在本节中，我们将简要介绍如何使用 Scikit-Optimize 库为一个简单的测试分类问题优化 k 近邻分类器的超参数。这将提供一个有用的模板，可供您在自己的项目中使用。Scikit-Optimize 项目旨在为使用 SciPy 和 NumPy 的应用程序或使用 scikit-learn 机器学习算法的应用程序提供贝叶斯优化访问。首先，必须安装该库，这可以使用 pip 轻松实现；例如：

```bash
sudo pip install scikit-optimize
```

Listing 19.21: 安装 scikit-optimize 库的示例。

假设您已为此示例安装了 scikit-learn。安装后，scikit-optimize 有两种方式可用于优化 scikit-learn 算法的超参数。第一种是直接在搜索空间上执行优化，第二种是使用 BayesSearchCV 类，它是 scikit-learn 用于随机和网格搜索的原生类的同类。在本示例中，我们将使用更简单的直接优化超参数的方法。第一步是准备数据并定义模型。我们将通过 make_blobs() 函数使用一个简单的测试分类问题，其中包含 500 个示例，每个示例有两个特征和三个类别标签。然后我们将使用 KNeighborsClassifier 算法。

```python
...
# generate 2d classification dataset
X, y = make_blobs(n_samples=500, centers=3, n_features=2)
# define the model
model = KNeighborsClassifier()
```

Listing 19.22: 定义测试问题和基础分类器的示例。

接下来，我们必须定义搜索空间。在本例中，我们将调整邻居数量 (n_neighbors) 和邻域函数的形状 (p)。这需要为给定数据类型定义范围。在本例中，它们是 Integers，使用最小值、最大值以及传递给 scikit-learn 模型的参数名称定义。对于您的算法，您同样可以轻松优化 Real() 和 Categorical() 数据类型。

```python
...
# define the space of hyperparameters to search
search_space = [Integer(1, 5, name='n_neighbors'), Integer(1, 2, name='p')]
```

Listing 19.23: 定义超参数搜索空间的示例。

接下来，我们需要定义一个函数来评估给定的超参数集。我们希望最小化此函数，因此返回的较小值必须表示模型性能更好。我们可以在函数定义上使用 scikit-optimize 项目中的 `use_named_args()` 装饰器，该装饰器允许函数直接使用来自搜索空间的特定参数集调用。因此，我们的自定义函数将以超参数值作为参数，这些参数可以直接提供给模型以配置它。我们可以使用函数的 `**params` 参数在 Python 中以通用方式定义这些参数，然后通过 `set_params(**params)` 函数将它们传递给模型。

现在模型已配置好，我们可以对其进行评估。在本例中，我们将对数据集使用 5 折交叉验证并评估每个折的准确率。然后我们可以将模型的性能报告为这些折的平均准确率的 1 减去。这意味着准确率为 1.0 的完美模型将返回 0.0（1.0 − 平均准确率）。在加载数据集并定义模型后定义此函数，以便数据集和模型都在作用域内并可直接使用。

```python
# define the function used to evaluate a given configuration
@use_named_args(search_space)
def evaluate_model(**params):
    # something
    model.set_params(**params)
    # calculate 5-fold cross-validation
    result = cross_val_score(model, X, y, cv=5, n_jobs=-1, scoring='accuracy')
    # calculate the mean of the scores
    estimate = mean(result)
    return 1.0 - estimate
```

Listing 19.24: 用于评估一组模型超参数的函数的示例。

接下来，我们可以执行优化。这是通过使用目标函数名称和定义的搜索空间调用 `gp_minimize()` 函数实现的。默认情况下，此函数将使用尝试找出最佳策略的 gp_hedge 采集函数，但这可以通过 `acq_func` 参数进行配置。优化默认将运行 100 次迭代，但这可以通过 `n_calls` 参数控制。

```python
...
# perform optimization
result = gp_minimize(evaluate_model, search_space)
```

Listing 19.25: 运行贝叶斯优化的示例。

运行后，我们可以通过 `fun` 属性访问最佳分数，并通过 `x` 数组属性访问最佳超参数集。

```python
...
# summarizing findings:
print('Best Accuracy: %.3f' % (1.0 - result.fun))
print('Best Parameters: n_neighbors=%d, p=%d' % (result.x[0], result.x[1]))
```

Listing 19.26: 汇总贝叶斯优化结果的示例。

将所有内容整合在一起，完整的示例如下所示。

```python
# example of bayesian optimization with scikit-optimize
from numpy import mean
from sklearn.datasets import make_blobs
from sklearn.model_selection import cross_val_score
from sklearn.neighbors import KNeighborsClassifier
from skopt.space import Integer
from skopt.utils import use_named_args
from skopt import gp_minimize

# generate 2d classification dataset
X, y = make_blobs(n_samples=500, centers=3, n_features=2)
# define the model
model = KNeighborsClassifier()
# define the space of hyperparameters to search
search_space = [Integer(1, 5, name='n_neighbors'), Integer(1, 2, name='p')]

# define the function used to evaluate a given configuration
@use_named_args(search_space)
def evaluate_model(**params):
    # something
    model.set_params(**params)
    # calculate 5-fold cross validation
    result = cross_val_score(model, X, y, cv=5, n_jobs=-1, scoring='accuracy')
    # calculate the mean of the scores
    estimate = mean(result)
    return 1.0 - estimate

# perform optimization
result = gp_minimize(evaluate_model, search_space)
# summarizing finding:
print('Best Accuracy: %.3f' % (1.0 - result.fun))
print('Best Parameters: n_neighbors=%d, p=%d' % (result.x[0], result.x[1]))
```

Listing 19.27: 模型超参数贝叶斯优化的示例。

运行示例将使用贝叶斯优化执行超参数调优。代码可能会报告许多警告消息，例如：

```
UserWarning: The objective has been evaluated at this point before.
```

Listing 19.28: 可能的警告消息示例。

这是预期的，是由于相同的超参数配置被评估多次造成的。鉴于测试问题的随机性，您的具体结果会有所不同。尝试多次运行示例。在本例中，模型通过平均 5 折交叉验证实现了约 97% 的准确率，邻居数为 3，p 邻域形状值为 2。

```
Best Accuracy: 0.976
Best Parameters: n_neighbors=3, p=2
```

Listing 19.29: 在模型超参数上运行贝叶斯优化的最终结果示例。

