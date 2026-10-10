
从这里，你可以看到 `r(k,n)` 将以分数的形式呈现，一个 0 到 1 之间的数字，你可以将硬 k-means（hard k-means）或普通 k-means 理解为 `r(k,n)` 始终完全等于 0 或 1 的情况。`d` 可以任何有效的距离指标，但欧几里得距离或平方欧几里得距离是最常用的。

然后对于第二步，我们将处理一个与硬 k-means 相似的公式，但我们只是根据我们想要发送的责任度重新计算平均值。我们将为此使用的算法包括：

```
m(k) = sum[n=1..N] { r(k,n)* x(n) ] / sum[n-1..N] {
r(k,n) }
```

所以，当你花时间看上面的算法时，你会发现它类似于加权平均值。这将向你展示，如果 `r(k,n)` 较高，那么平均值对于聚类 `k` 就越重要。当你看到这一点时，它将显示这对平均值的计算影响最大。但如果当你观察算法时平均值更高，你就知道相反也是正确的。

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

### 假设有3个均值

`D = 2` # 这样我们可以更容易可视化

`s = 4` # 间距，我们可以控制均值之间的距离

```python
mu1 = np.array([0, 0])
mu2 = np.array([s, s])
mu3 = np.array([0, s])
```

`N = 900` # 样本数量

`X = np.zeros((N, D))`

`X[:300, :] = np.random.randn(300, D) + mu1`

`X[300:600, :] = np.random.randn(300, D) + mu2`

`X[600:, :] = np.random.randn(300, D) + mu3`

```

### 如果不聚类，看起来是什么样的？

`plt.scatter(X[:,0], X[:,1])`
`plt.show()`

`K = 3` # 幸运的是，我们已经知道了
`plot_k_means(X, K)`

### K = 5 # 如果我们选择了一个“坏”的 K 会发生什么？

### plot_k_means(X, K, max_iter=30)

### K = 5 # 如果我们改变 beta 会发生什么？

### plot_k_means(X, K, max_iter=30, beta=0.3)

```python

if __name__ == '__main__':

    main()
```
