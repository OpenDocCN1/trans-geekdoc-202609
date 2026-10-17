
- 在模型选择中，我们通常希望遵循奥卡姆剃刀原则，选择能很好解释数据的最简单模型。在超参数优化中，除了网格搜索和随机搜索之外，贝叶斯优化使用主动学习方法，以减少不确定性并在探索和利用之间取得平衡。

- 集成方法是将几种机器学习技术组合成一个预测模型的元算法，以降低方差（`bagging`）、降低偏差（`boosting`）或改进预测（`stacking`）。

## 第 3 部分

### 无监督学习

在本书的第三部分，我们将回顾无监督学习算法。当没有训练标签可用时，就会进行无监督学习。在无监督学习的情况下，我们通常对发现数据中的模式和学习数据表示感兴趣。

在第 8 章，我们将首先研究 `K-means` 算法的贝叶斯非参数扩展，然后是高斯混合模型的 `EM` 算法。然后我们将研究两种不同的降维技术——即 `PCA` 和 `t-SNE` 应用于学习图像流形。

在第 9 章，我们将继续讨论选定的无监督学习算法。我们将首先研究用于学习主题模型的潜在狄利克雷分配，然后是密度估计器和结构学习算法，最后是模拟退火和遗传算法。最后，我们将回顾机器学习研究文献，重点关注无监督学习。

### 基础无监督学习算法

![](img/325742126d3ff007c6c385f4ffb5c3be_185_0.png)

**本章涵盖**

- Dirichlet 过程 `K-means`
- 高斯混合模型
- 降维

在之前的章节中，我们研究了用于分类和回归的监督算法；在本章中，我们将重点转向无监督学习算法。*无监督学习* 在没有训练标签可用时进行。在这种情况下，我们对发现数据中的模式和学习数据表示感兴趣。无监督学习的应用范围从电子商务中的客户细分聚类到从图像数据中提取特征。在本章中，我们将首先研究 `K-means` 算法的贝叶斯非参数扩展，然后是高斯混合模型（`GMM`）的 `EM` 算法。然后我们将研究两种不同的降维技术——即 `PCA` 和 `t-SNE`——用于学习图像流形。本章中的算法因其数学深度和在实际应用中的有用性而被选中。

#### 8.1 Dirichlet 过程 *K*-means

Dirichlet 过程（`DP`）*K*-means 是 *K*-Means 算法的贝叶斯非参数扩展。*K*-means 是一种聚类算法，例如可应用于客户细分，其中客户按购买历史、兴趣和地理位置分组。`DP-means` 与 *K*-means 相似，只是当数据点距离所有现有聚类中心足够远时，会创建新的聚类；因此，聚类数量随数据增长。`DP-means` 收敛于一个类似 *K*-means 的目标的局部最优解，该目标包含对聚类数量的惩罚。

我们根据以下方程的最小值选择聚类 `K`。

$$\underset{k}{\arg\min}\{\|x_i-\mu_1\|^2,\ldots,\|x_i-\mu_k\|^2,\lambda\} \tag{8.1}$$

所得到的更新类似于 *K*-means 重新分配步骤，在该步骤中，我们将点重新分配到对应于最近均值的聚类，或者如果平方欧几里得距离大于 `$\lambda$` 则启动新聚类。`DP means` 算法在图 8.1 中进行了总结。

```
1: Init. $K = 1$, $l_1 = \{x_1,\ldots,x_n\}$ and $\mu_1$ the global mean
2: Init. labels $z_i = 1$ for all $i = 1,\ldots,n$
3: Init. $\lambda = \text{kpp\_init}(X, K_{\text{init}})$
4: Repeat until convergence:
5: &nbsp;&nbsp;&nbsp;&nbsp;for each $x_i$:
6: &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;compute $d_{ic} = \|x_i - \mu_c\|^2$ for $c = 1,\ldots,K$
7: &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if $\min_c d_{ic} > \lambda$, set $K = K + 1$ and $\mu_k = x_i$
8: &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;otherwise, set $z_i = \arg\min_c d_{ic}$
9: &nbsp;&nbsp;&nbsp;&nbsp;for each cluster $l_j = \{x_i|z_i = j\}$, compute $\mu_j = \frac{1}{|l_j|}\sum_{x\in l_j}x$
10: &nbsp;&nbsp;&nbsp;&nbsp;Compute the objective: $\sum_{c=1}^{K}\sum_{x\in l_c}\|x-\mu_c\|^2 + \lambda K$
```

图 8.1  
`DP-means` 算法  
伪代码

为了评估聚类性能，我们可以使用以下指标：归一化互信息（`NMI`）、信息变化（`VI`）和调整兰德指数（`ARI`）。`NMI` 定义如下。

$$\operatorname{NMI}(X,Y)=\frac{I(X;Y)}{\frac{H(X)+H(Y)}{2}} \tag{8.2}$$

这里，`$H(X)$` 是 `X` 的熵，`$I(X;Y)$` 是真实标签分配 `X`（当可用时）与计算分配 `Y` 之间的互信息。有关信息度量的综述，请参阅 Thomas M. Cover 和 Joy A. Thomas（Wiley，2006）所著的 *《信息论基础》* 了解详情。

设 `$p_{XY}(i,j)=|x_i\cap y_j|/N$` 为标签属于 `X` 中的簇 `$x_i$` 且属于 `Y` 中的 `$y_j$` 的概率。类似地定义 `$p_X(i)=|x_i|/N$` 和 `$p_Y(j)=|y_j|/N$`。于是我们得到以下方程。

$$I(X;Y)=\sum_i\sum_j p_{XY}(i,j)\log\frac{p_{XY}(i,j)}{p_X(i)p_Y(j)} \tag{8.3}$$

因此，`NMI` 在 0 到 1 之间，值越高表示标签分配越相似。变分信息 (`VI`) 定义如下。

$$VI(X;Y)=H(X)+H(Y)-2I(X;Y)=H(X|Y)+H(Y|X) \tag{8.4}$$

因此，随着标签分配 `X` 和 `Y` 之间重叠的增加，`VI` 减小。`ARI` 通过考虑所有样本对并统计预测簇和真实簇中分配到相同或不同簇的样本对来计算两个簇之间的相似性度量。

$$\begin{aligned}
ARI &= \frac{RI-E[RI]}{\max RI-E[RI]}\\
RI &= \frac{TP+TN}{TP+FP+FN+TN}
\end{aligned} \tag{8.5}$$

因此，对于彼此相似的簇分配，`ARI` 接近 1。让我们从头实现 Dirichlet 过程 `K-means` 算法！

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

`DP-means` 算法的性能如图 8.2 所示。`DP-means` 算法的性能在鸢尾花数据集上进行了评估。我们可以看到基于高 `NMI` 和 `ARI` 指标的良好聚类结果。在下一节中，我们将讨论一种流行的聚类算法，该算法将每个簇建模为高斯分布，不仅考虑均值，还考虑协方差信息。

![](img/325742126d3ff007c6c385f4ffb5c3be_191_0.png)

![](img/325742126d3ff007c6c385f4ffb5c3be_191_1.png)

图 8.2 鸢尾花数据集的 `DP-means` 簇中心（左）和目标函数（右）

#### 8.2 高斯混合模型

混合模型通常用于建模复杂的密度分布。例如，你可能对发现包含个人年龄、收入、职业和其他维度信息的人口普查数据中的模式感兴趣。如果我们在高维空间中绘制所得数据，我们很可能会发现由数据点组或簇表征的非均匀密度。我们可以使用基础概率分布来建模每个簇。混合模型由 `K` 个基础模型的凸组合构成。在高斯混合模型的情况下，基础分布为高斯分布，可写为如下形式。

$p(x_i|\theta)=\sum_{k=1}^{K}\pi_k p_k(x_i|\theta)=\sum_{k=1}^{K}\pi_k\mathcal{N}(x_i|\mu_k,\Sigma_k)\tag{8.6}$

这里，`$\pi_k$` 为混合比例，满足 `0 ≤ π_k ≤ 1` 且 `$\sum\pi_k=1$`。与仅建模簇均值的 `K-means` 不同，`GMM` 还对簇协方差建模。因此，`GMM` 可以更准确地捕捉数据。

##### 8.2.1 期望最大化（EM）算法

期望最大化（`EM`）算法提供了一种在存在未观测潜在变量或缺失数据时计算 `ML/MAP` 估计的方法。`EM` 利用了这样一个事实：如果数据完全可观测，则 `ML/MAP` 估计很容易计算。特别是，`EM` 是一种迭代算法，在给定参数的情况下推断潜在变量（E 步），然后在填充数据的情况下优化参数（M 步）之间交替进行。

在 `EM` 算法中，我们定义完整数据对数似然 `$l_c(\theta)$`，其中 `$x_i$` 为观测随机变量，`$z_i$` 为未观测。由于我们不知道 `$z_i$`，我们无法计算 `$p(x_i, z_i | \theta)$`，但我们可以计算关于上一迭代参数 `$\theta^{(k-1)}$` 的 `$\ell_c(\theta)$` 的期望。

$$l_c(\theta) = \sum_{i=1}^{N} \log p(x_i, z_i | \theta) \tag{8.7}$$

E 步的目标是计算 `$Q(\theta, \theta^{(k-1)})$`，`ML/MAP` 估计依赖于它。M 步的目标是通过找到 `ML/MAP` 估计来重新计算 `$\theta$`。

$$\text{E-step} : \quad Q\left(\theta, \theta^{(k-1)}\right) = E_{\theta^{(k-1)}}\left[\ell_c(\theta) | D, \theta^{(k-1)}\right]$$ $$\text{M-step} : \quad \theta^{(k)} = \arg\max_{\theta} Q\left(\theta, \theta^{(k-1)}\right) + \log p(\theta) \tag{8.8}$$

为了推导 `GMM` 的 `EM` 算法，我们首先需要计算期望的完整数据对数似然。

$$Q(\theta, \theta^{(k-1)}) = E\left[\sum_i \log p(x_i, z_i | \theta)\right]$$ $$= \sum_i E\left[\log \prod_{k=1}^{K} \left(\pi_k p(x_i | \theta_k)\right)^{\mathbf{1}\{z_i=k\}}\right]$$ $$= \sum_i \sum_k E\left[\mathbf{1}\{z_i = k\}\right] \log \left[\pi_k p(x_i | \theta_k)\right]$$ $$= \sum_i \sum_k p\left(z_i = k | x_i, \theta^{(k-1)}\right) \log \left[\pi_k p(x_i | \theta_k)\right]$$ $$= \sum_i \sum_k r_{ik} \log \pi_k + \sum_i \sum_k r_{ik} \log p(x_i | \theta_k) \tag{8.9}$$

这里，`$r_{ik} = p(z_i = k | x_i, \theta^{(k-1)})$` 是点 `$x_i$` 对簇 `k` 的软分配。
