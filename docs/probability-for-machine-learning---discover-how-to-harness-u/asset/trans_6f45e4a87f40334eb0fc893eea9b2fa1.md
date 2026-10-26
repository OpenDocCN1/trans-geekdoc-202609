
## 25.2 朴素分类器

分类预测建模问题涉及根据模型输入预测类别标签。分类模型在训练数据集上拟合，并在测试数据集上评估，其性能通常以正确预测数占预测总数的比例来报告，称为准确率。给定一个分类模型，如何判断模型是否有技能？这是每个分类预测建模项目上的常见问题。答案是将给定分类器模型的结果与基线或朴素分类器模型进行比较。

朴素分类器模型是指在做出预测时不使用任何复杂技巧，通常做出随机或恒定的预测。这类模型之所以朴素，是因为它们在做出预测时不使用任何关于领域的知识或任何学习。基线分类器在分类任务上的性能为该问题上所有其他模型的预期性能提供了下限。例如，如果分类模型比朴素分类器表现更好，则它具有一定的技能。如果分类器模型表现不如朴素分类器，则它没有任何技能。应该使用什么分类器作为朴素分类器？这是初学者常见的困惑领域，并且采用了不同的朴素分类器。一些常见选择包括：

- 预测一个随机类别。
- 从训练数据集中预测一个随机选择的类别。
- 预测训练数据集中占多数的类别。

问题是，并非所有朴素分类器都一样，有些表现更好，有些表现更差。因此，我们应该在所有分类预测建模项目中使用表现最好的朴素分类器。我们可以使用简单概率来评估不同朴素分类器模型的性能，并确认应始终用作朴素分类器的策略。在开始评估不同策略之前，让我们定义一个人为构造的二分类问题。为了使其有趣，我们假设每个类别的观测数量不相等（例如问题不平衡），class-0 有 25 个示例，class-1 有 75 个示例。我们可以用下面的 Python 小示例使其具体化。

```python
# summarize a test dataset
# define dataset
class0 = [0 for _ in range(25)]
class1 = [1 for _ in range(75)]
y = class0 + class1
# summarize distribution
print('Class 0: %.3f' % (len(class0) / len(y) * 100))
print('Class 1: %.3f' % (len(class1) / len(y) * 100))
```

Listing 25.1: 定义和汇总测试数据集的示例。

运行该示例会创建数据集并汇总属于每个类别的示例比例，显示 class-0 为 25%，class-1 为 75%，正如我们直观预期的那样。

```text
Class 0: 25.000
Class 1: 75.000
```

Listing 25.2: 定义和汇总测试数据集的示例输出。

最后，我们可以定义一个用于评估朴素分类策略的概率模型。在这种情况下，我们感兴趣的是计算给定二分类模型的分类准确率。

$$P(\hat{y}=y) \tag{25.1}$$

这可以计算为模型预测每个类别值的概率乘以观察到每个类别出现的概率。

$$P(\hat{y}=y) = P(\hat{y}=0) \times P(y=0) + P(\hat{y}=1) \times P(y=1) \tag{25.2}$$

这计算了模型在数据集上的预期性能。它提供了一个非常简单的概率模型，我们可以用它来计算一般情况下朴素分类器模型的预期性能。接下来，我们将使用这个人为构造的预测问题来探索朴素分类器的不同策略。

## 25.3 预测随机猜测

也许最简单的策略是为每次所需的预测随机猜测其中一个可用类别。我们将称之为随机猜测策略。使用我们的概率模型，我们可以计算该模型在我们的人为构造数据集上平均预期表现如何。对每个类别的随机猜测是每个可能类别标签上的均匀概率分布，或者在二分类问题的情况下，每个类别的概率为 0.5。此外，由于我们人为构造了该问题，我们知道我们的数据集中 class-0 和 class-1 值的预期概率；它们分别为 0.25 和 0.75。因此，我们按如下方式计算该策略的平均性能：

$$\begin{aligned} P(\hat{y}=y) &= P(\hat{y}=0) \times P(y=0) + P(\hat{y}=1) \times P(y=1) \\ &= 0.5 \times 0.25 + 0.5 \times 0.75 \\ &= 0.125 + 0.375 \\ &= 0.5 \end{aligned} \tag{25.3}$$

该计算表明，在我们的人为构造问题上预测均匀随机类别标签的性能为 0.5 或 50% 分类准确率。这可能令人惊讶，这很好，因为它突出了系统计算朴素策略预期性能的好处。我们可以通过一个小实验来确认该估计是否正确。该策略可以实现为一个函数，该函数为每次所需的预测随机选择 0 或 1。

```python
# guess random class
def random_guess():
    if random() < 0.5:
        return 0
    return 1
```

Listing 25.3: 预测随机猜测的函数示例。

然后可以为数据集中所需的每次预测调用它，并评估准确率。

```python
...
yhat = [random_guess() for _ in range(len(y))]
acc = accuracy_score(y, yhat)
```

Listing 25.4: 使用该策略进行预测的示例。

这是一次试验，但每次使用该策略时准确率都会不同。为了解决这个问题，我们可以重复实验 1,000 次并报告该策略的平均性能。我们期望平均性能与上面计算的预期性能相匹配。完整示例如下所示。

```python
# example of a random guess naive classifier
from numpy import mean
from numpy.random import random
from sklearn.metrics import accuracy_score

# guess random class
def random_guess():
    if random() < 0.5:
        return 0
    return 1

# define dataset
class0 = [0 for _ in range(25)]
class1 = [1 for _ in range(75)]
y = class0 + class1
# average performance over many repeats
results = list()
for _ in range(1000):
    yhat = [random_guess() for _ in range(len(y))]
    acc = accuracy_score(y, yhat)
    results.append(acc)
print('Mean: %.3f' % mean(results))
```

Listing 25.5: 评估随机猜测分类策略的示例。

运行该示例执行我们实验的 1,000 次试验并报告该策略的平均准确率。

**注意：** 由于学习算法的随机性，您的具体结果可能会有所不同。考虑多次运行示例并比较平均性能。

在这种情况下，我们可以看到预期性能与计算性能非常接近。根据大数定律，我们执行的试验次数越多，我们的估计就越接近我们计算的理论值。

```text
Mean: 0.499
```

Listing 25.6: 评估随机猜测分类策略的示例输出。

这是一个好的开始，但如果我们在策略中使用有关训练数据集构成的一些基本信息会怎样。我们接下来将探索这一点。

## 25.4 预测随机选择的类别

另一种朴素分类器方法是某种程度上利用训练数据集。也许最简单的方法是使用训练数据集中的观测值作为预测。具体来说，我们可以随机选择训练集中的观测值并将其返回以用于每次请求的预测。这是有道理的，我们可能会期望训练数据集的这种原始使用会导致比随机猜测略好的朴素准确率。

我们可以通过使用我们的概率框架计算该方法的预期性能来了解这一点。如果我们以均匀概率分布从训练数据集中选择示例，我们将以其在训练数据集中出现的相同概率抽取每个类别的示例。也就是说，我们将以 25% 的概率抽取 class-0 的示例，以 75% 的概率抽取 class-1 的示例。这也将是模型独立预测的概率。

有了这些知识，我们可以将这些值代入概率模型。

$$\begin{aligned}
P(\hat{y}=y) &= P(\hat{y}=0) \times P(y=0) + P(\hat{y}=1) \times P(y=1) \\
&= 0.25 \times 0.25 + 0.75 \times 0.75 \\
&= 0.0625 + 0.5625 \\
&= 0.625
\end{aligned} \tag{25.4}$$

结果表明，使用从训练数据集中均匀随机选择的类别作为预测会产生比在此数据集上简单预测均匀随机类别更好的朴素分类器，显示为 62.5% 而不是 50%，提升了 12.5%。不错！让我们再次通过一个小模拟来确认我们的计算。

下面的 random_class() 函数通过从训练数据集中选择并返回一个随机类别标签来实现这种朴素分类器策略。

```python
# predict a randomly selected class
def random_class(y):
    return y[randint(len(y))]
```

Listing 25.7: 预测随机选择标签的函数示例。

然后我们可以使用上一节的相同框架评估模型 1,000 次并报告这些试验的平均分类准确率。我们期望该经验估计值与我们的预期值相匹配，或非常接近。完整示例如下所示。

```python
# example of selecting a random class naive classifier
from numpy import mean
from numpy.random import randint
from sklearn.metrics import accuracy_score

# predict a randomly selected class
def random_class(y):
    return y[randint(len(y))]
```
