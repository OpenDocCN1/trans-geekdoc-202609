
设 $p_{XY}(i,j)=|x_i\cap y_j|/N$ 为标签属于 $X$ 中的簇 $x_i$ 且属于 $Y$ 中的 $y_j$ 的概率。类似地定义 $p_X(i)=|x_i|/N$ 和 $p_Y(j)=|y_j|/N$。于是我们得到以下方程。

$$I(X;Y)=\sum_i\sum_j p_{XY}(i,j)\log\frac{p_{XY}(i,j)}{p_X(i)p_Y(j)} \tag{8.3}$$

因此，NMI 在 0 到 1 之间，值越高表示标签分配越相似。变分信息 ($VI$) 定义如下。

$$VI(X;Y)=H(X)+H(Y)-2I(X;Y)=H(X|Y)+H(Y|X) \tag{8.4}$$

因此，随着标签分配 $X$ 和 $Y$ 之间重叠的增加，$VI$ 减小。ARI 通过考虑所有样本对并统计预测簇和真实簇中分配到相同或不同簇的样本对来计算两个簇之间的相似性度量。

$$\begin{aligned}
ARI &= \frac{RI-E[RI]}{\max RI-E[RI]}\\
RI &= \frac{TP+TN}{TP+FP+FN+TN}
\end{aligned} \tag{8.5}$$

因此，对于彼此相似的簇分配，ARI 接近 1。让我们从头实现 Dirichlet 过程 K-means 算法！

## 清单 8.1 Dirichlet 过程 K-means

```python
import numpy as np
import matplotlib.pyplot as plt

import time
from sklearn import metrics
from sklearn.datasets import load_iris

np.random.seed(42)

class dpmeans:

    def __init__(self,X):
        self.K = 1
        self.K_init = 4
        self.d = X.shape[1]
        self.z = np.mod(np.random.permutation(X.shape[0]),self.K)+1
        self.mu = np.random.standard_normal((self.K, self.d))
        self.sigma = 1
```

```python
self.nk = np.zeros(self.K)
self.pik = np.ones(self.K)/self.K

self.mu = np.array([np.mean(X,0)])
self.Lambda = self.kpp_init(X,self.K_init)
self.max_iter = 100
self.obj = np.zeros(self.max_iter)
self.em_time = np.zeros(self.max_iter)

def kpp_init(self,X,k):

    [n,d] = np.shape(X)
    mu = np.zeros((k,d))
    dist = np.inf*np.ones(n)

    mu[0,:] = X[int(np.random.rand() *n-1),:]
    for i in range(1,k):
        D = X-np.tile(mu[i-1,:], (n,1))
        dist = np.minimum(dist, np.sum(D*D,1))
        idx = np.where(np.random.rand() <
    np.cumsum(dist/float(sum(dist))))
        mu[i,:] = X[idx[0][0],:]
        Lambda = np.max(dist)

    print "Lambda: ", Lambda

    return Lambda

def fit(self,X):

    obj_tol = 1e-3
    max_iter = self.max_iter
    [n,d] = np.shape(X)

    obj = np.zeros(max_iter)
    em_time = np.zeros(max_iter)
    print 'running dpmean !.'

    for iter in range(max_iter):
        tic = time.time()
        dist = np.zeros((n,self.K))

        for kk in range(self.K):
            Xm = X - np.tile(self.mu[kk,:],(n,1))
            dist[:,kk] = np.sum(Xm*Xm,1)

        dmin = np.min(dist,1)
        self.z = np.argmin(dist,1)
        idx = np.where(dmin > self.Lambda)

        if (np.size(idx) > 0):
            self.K = self.K + 1
            self.z[idx[0]] = self.K-1 #cluster labels in [0,...,K-1]
```

初始化均值

初始化 lambda

K++ 初始化

Lambda 是到 k++ 均值的最大距离

分配步骤

更新标签

```python
MI = Hx + Hy - Hxy;
nmi = MI/float(0.5*(Hx+Hy))

return nmi

def generate_plots(self,X):
    plt.close('all')
    plt.figure(0)
    for kk in range(self.K):
        #idx = np.where(self.z == kk)
        plt.scatter(X[self.z == kk,0], X[self.z == kk,1], \
                    s = 100, marker='o', c = np.random.rand(3,),
                    label = str(kk))
    #end for
    plt.xlabel('X1')
    plt.ylabel('X2')
    plt.legend()
    plt.title('DP-means clusters')
    plt.grid(True)
    plt.show()

    plt.figure(1)
    plt.plot(self.obj)
    plt.title('DP-means objective function')
    plt.xlabel('iterations')
    plt.ylabel('penalized l2 squared distance')
    plt.grid(True)
    plt.show()

if __name__ == "__main__":

    iris = load_iris()
    X = iris.data
    Y = iris.target

    dp = dpmeans(X)
    labels, obj, em_time = dp.fit(X)
    dp.generate_plots(X)

    nmi = dp.compute_nmi(Y,labels)
    ari = metrics.adjusted_rand_score(Y,labels)

    print("NMI: %.4f" % nmi)
    print("ARI: %.4f" % ari)
```

DP-means 算法的性能如图 8.2 所示。DP-means 算法的性能在鸢尾花数据集上进行了评估。我们可以看到基于高 NMI 和 ARI 指标的良好聚类结果。在下一节中，我们将讨论一种流行的聚类算法，该算法将每个簇建模为高斯分布，不仅考虑均值，还考虑协方差信息。

![](img/325742126d3ff007c6c385f4ffb5c3be_191_0.png)

![](img/325742126d3ff007c6c385f4ffb5c3be_191_1.png)

图 8.2 鸢尾花数据集的 DP-means 簇中心（左）和目标函数（右）

## 8.2 高斯混合模型

混合模型通常用于建模复杂的密度分布。例如，你可能对发现包含个人年龄、收入、职业和其他维度信息的人口普查数据中的模式感兴趣。如果我们在高维空间中绘制所得数据，我们很可能会发现由数据点组或簇表征的非均匀密度。我们可以使用基础概率分布来建模每个簇。混合模型由 K 个基础模型的凸组合构成。在高斯混合模型的情况下，基础分布为高斯分布，可写为如下形式。

$p(x_i|\theta)=\sum_{k=1}^{K}\pi_k p_k(x_i|\theta)=\sum_{k=1}^{K}\pi_k\mathcal{N}(x_i|\mu_k,\Sigma_k)\tag{8.6}$

这里，$\pi_k$ 为混合比例，满足 $0 \le \pi_k \le 1$ 且 $\sum\pi_k=1$。与仅建模簇均值的 K-means 不同，GMM 还对簇协方差建模。因此，GMM 可以更准确地捕捉数据。

### 8.2.1 期望最大化（EM）算法

期望最大化（EM）算法提供了一种在存在未观测潜在变量或缺失数据时计算 ML/MAP 估计的方法。EM 利用了这样一个事实：如果数据完全可观测，则 ML/MAP 估计很容易计算。特别是，EM 是一种迭代算法，在给定参数的情况下推断潜在变量（E 步），然后在填充数据的情况下优化参数（M 步）之间交替进行。

在 EM 算法中，我们定义完整数据对数似然 $l_c(\theta)$，其中 $x_i$ 为观测随机变量，$z_i$ 为未观测。由于我们不知道 $z_i$，我们

无法计算 $p(x_i, z_i | \theta)$，但我们可以计算关于上一迭代参数 $\theta^{(k-1)}$ 的 $\ell_c(\theta)$ 的期望。

$$l_c(\theta) = \sum_{i=1}^{N} \log p(x_i, z_i | \theta) \tag{8.7}$$

E 步的目标是计算 $Q(\theta, \theta^{(k-1)})$，ML/MAP 估计依赖于它。M 步的目标是通过找到 ML/MAP 估计来重新计算 $\theta$。

$$\text{E-step} : \quad Q\left(\theta, \theta^{(k-1)}\right) = E_{\theta^{(k-1)}}\left[\ell_c(\theta) | D, \theta^{(k-1)}\right]$$ $$\text{M-step} : \quad \theta^{(k)} = \arg\max_{\theta} Q\left(\theta, \theta^{(k-1)}\right) + \log p(\theta) \tag{8.8}$$

为了推导 GMM 的 EM 算法，我们首先需要计算期望的完整数据对数似然。

$$Q(\theta, \theta^{(k-1)}) = E\left[\sum_i \log p(x_i, z_i | \theta)\right]$$ $$= \sum_i E\left[\log \prod_{k=1}^{K} \left(\pi_k p(x_i | \theta_k)\right)^{\mathbf{1}\{z_i=k\}}\right]$$ $$= \sum_i \sum_k E\left[\mathbf{1}\{z_i = k\}\right] \log \left[\pi_k p(x_i | \theta_k)\right]$$ $$= \sum_i \sum_k p\left(z_i = k | x_i, \theta^{(k-1)}\right) \log \left[\pi_k p(x_i | \theta_k)\right]$$ $$= \sum_i \sum_k r_{ik} \log \pi_k + \sum_i \sum_k r_{ik} \log p(x_i | \theta_k) \tag{8.9}$$

这里，$r_{ik} = p(z_i = k | x_i, \theta^{(k-1)})$ 是点 $x_i$ 对簇 $k$ 的软分配。

我们现在开始 E 步。给定 $\theta^{(k-1)}$，我们希望计算软分配。

$$r_{ik} = p\left(z_i = k | x_i, \theta^{(k-1)}\right)$$ $$= \frac{p\left(z_i = k, x_i | \theta^{(k-1)}\right)}{\sum_{k=1}^{K} p\left(z_i = k, x_i | \theta^{(k-1)}\right)}$$ $$= \frac{p\left(x_i | z_i = k, \theta^{(k-1)}\right) \pi_k}{\sum_{k=1}^{K} p\left(x_i | z_i = k, \theta^{(k-1)}\right) \pi_k} \tag{8.10}$$

