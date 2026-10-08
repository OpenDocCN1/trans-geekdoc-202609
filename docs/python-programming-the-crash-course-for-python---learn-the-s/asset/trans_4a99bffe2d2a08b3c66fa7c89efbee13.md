
计算成本将会要高得多。当你尝试将其与其他一些可以处理相似或相同工作的算法进行比较时，这一点更为明显。成本增加的原因是，该算法将获取所有数据，并尽可能地遍历每一个微点，而不是尝试将它们聚类并发送一个预测结果。

当系统必须实际查看每个点时，在包含数百万个点的大型数据集中，这将消耗大量的精力和时间，这正是额外成本产生的地方。在本节之后，我们将查看 K-Means 聚类，并看看为什么聚类过程有时是一个有益的选择。

尽管如此，KNN 算法仍然是一个非常强大的工具，可以让你在工作中获得巨大的收益，并帮助你真正理清拥有的所有不同数据点和信息，即使数据集非常大且看起来无法处理。

学习我们下面将介绍的步骤，将确保你已经做好准备，可以使用这种机器学习算法进行工作。

## K-最近邻算法是如何工作的

现在我们已经花了几分钟时间讨论了这类算法以及随之而来的一切，是时候查看你需要遵循的一些步骤了，以确保你能以正确的方式使用 KNN 算法。开始使用 KNN 算法的一些最佳步骤包括：

- 1. 将数据加载到算法中进行读取。
- 2. 初始化你将使用并依赖的 k 值。
- 3. 当你准备好获取预测类别时，从 1 到用于训练的数据点总数进行迭代，可以使用以下步骤来帮助：
   a. 首先计算每个测试数据与训练数据中每一行之间的距离。
      我们将使用欧几里得距离（Euclidean distance）作为距离指标，因为它是最流行的方法。你可能选择使用的的其他指标还包括余弦距离（cosine）和切比雪夫距离（Chebyshev）。
   b. 根据距离值将计算出的距离按升序排序。
   c. 从排序后的数组中获取 k 行。
   d. 获取这些行中频率最高的类别。
   e. 返回类别预测。

## K-means 聚类

我们将花费时间查看的下一个算法被称为 k-means 聚类（均值聚类）。这是该主题中许多不同算法中的基本思想，但它是你能操作的最简单、最常见的聚类形式之一。

它也是无监督机器学习的一个很好的示例。当你的数据没有带标签时，大多数情况下都会应用它。使用该算法的目标是确保你可以看到数据内部发现的聚类或分组。

这些聚类的重点在于，位于同一个聚类中的对象与属于同一聚类的其他点密切相关。此外，这些点与你设置的任何其他聚类中的项目没有多少相似性。这里的相似性是用来用于查看数据集中对象之间关系强弱的指标。

你很多时候都会使用这种聚类，但一个例子是在进行数据挖掘过程时，特别是当数据挖掘更具探索性时。它也可以在其他领域发挥作用，包括数据压缩、图像分析、计算机图形、模式识别和机器学习等。

当你使用这种算法时，它将根据数据自带的值帮助你形成所需的一些数据聚类。作为程序员，你的任务就是遍历并指定你希望 k 的值是多少。这意味着你需要确定算法从数据中创建多少个聚类。然后算法将取 K 值并用它来选择你所处理的所有聚类的质心值。

当完成上述步骤后，该是 k-means 算法继续完成另外三个步骤了。这些步骤包括：

- 1. 你将从每个数据实例与所有聚类质心之间的欧几里得距离开始。
- 2. 将数据实例分配到距离最近的质心聚类。
- 3. 根据相应聚类中数据实例坐标的平均值，计算新的质心值。

## 写出 K-means 聚类的公式

所以我们首先需要做的步骤是计算聚类责任度（responsibilities）。我们将使用的公式如下：

```
r(kn) = exp[ -b * d(m(k), x(n)) ] / sum[j=1..K] { exp[ -b * d(m(j), x(n)) ] }
```

从这里，你可以看到 r(k,n) 将以分数的形式呈现，一个 0 到 1 之间的数字，你可以将硬 k-means（hard k-means）或普通 k-means 理解为 r(k,n) 始终完全等于 0 或 1 的情况。d 可以任何有效的距离指标，但欧几里得距离或平方欧几里得距离是最常用的。

然后对于第二步，我们将处理一个与硬 k-means 相似的公式，但我们只是根据我们想要发送的责任度重新计算平均值。我们将为此使用的算法包括：

```
m(k) = sum[n=1..N] { r(k,n)* x(n) ] / sum[n-1..N] {
r(k,n) }
```

所以，当你花时间看上面的算法时，你会发现它类似于加权平均值。这将向你展示，如果 r(k,n)较高，那么平均值对于聚类 k 就越重要。当你看到这一点时，它将显示这对平均值的计算影响最大。但如果当你观察算法时平均值更高，你就知道相反也是正确的。

现在，根据我们已经讨论的一些信息，是时候查看实现以下功能所需的代码了：

```python
import numpy as np
import matplotlib.pyplot as plt

def d(u, v):
    diff = u - v
    return diff.dot(diff)

def cost(X, R, M):
    cost = 0
    for k in range(len(M)):
        for n in range(len(X)):
            cost += R[n,k] * d(M[k], X[n])
    return cost

def plot_k_means(X, K, max_iter=20, beta=1.0):
    N, D = X.shape
    M = np.zeros((K, D))
    R = np.ones((N, K)) / K

    # initialize M to random
    for k in range(K):
        M[k] = X[np.random.choice(N)]

    grid_width = 5
    grid_height = max_iter / grid_width
    random_colors = np.random.random((K, 3))
    plt.figure()

    costs = np.zeros(max_iter)
    for i in range(max_iter):
        # moved the plot inside the for loop
        colors = R.dot(random_colors)
        plt.subplot(grid_width, grid_height, i+1)
        plt.scatter(X[:,0], X[:,1], c=colors)

        # step 1: determine assignments / responsibilities
        # is this inefficient?
        for k in range(K):
            for n in range(N):
                R[n,k] = np.exp(-beta*d(M[k], X[n])) / \
                         np.sum([np.exp(-beta*d(M[j], X[n])) for j in range(K)])

        # step 2: recalculate means
        for k in range(K):
            M[k] = R[:,k].dot(X) / R[:,k].sum()

        costs[i] = cost(X, R, M)
        if i > 0:
            if np.abs(costs[i] - costs[i-1]) < 10e-5:
                break
    plt.show()

def main():
    pass
```
