
在等式 8.10 中，\(\pi_k = p(z_i = k)\) 是混合比例。

在 M 步中，我们关于模型参数 \(\pi\) 和 \(\theta_k\) 最大化 \(Q\)。首先，让我们找出使拉格朗日量最大化的 \(\pi\)。

$$\frac{\partial Q}{\partial \pi_k}=\frac{\partial}{\partial \pi_k}\left[\sum_i\sum_k r_{ik}\log\pi_k+\lambda\left(1-\sum_k\pi_k\right)\right]$$
$$=\sum_i\frac{r_{ik}}{\pi_k}-\lambda=0 \tag{8.11}$$

将该表达式代入约束条件，我们得到如下等式。

$$\sum_k\pi_k=1\Rightarrow\sum_k\frac{1}{\lambda}\sum_i r_{ik}=1\Rightarrow\lambda=\sum_i\sum_k r_{ik}=\sum_i1=N \tag{8.12}$$

因此，\(\pi_k=1/\lambda\sum_i r_{ik}=1/N\sum_i r_{ik}\)。为了找到最优参数 \(\theta_k=\{\mu_k,\Sigma_k\}\)，我们希望优化 \(Q\) 中依赖于 \(\theta_k\) 的项。

$$l(\mu_k,\Sigma_k)=\sum_i r_{ik}\log p(x_i\mid\theta_k)$$
$$\propto -\frac{1}{2}\sum_i r_{ik}\left[\log|\Sigma_k|+(x_i-\mu_k)^T\Sigma_k^{-1}(x_i-\mu_k)\right] \tag{8.13}$$

为了找到最优的 \(\mu_k\)，我们对该表达式求导。首先，关注和式内的第二项，我们可以进行替换 \(y_i=x_i-\mu_k\)。

$$\frac{\partial}{\partial\mu_k}(x_i-\mu_k)^T\Sigma_k^{-1}(x_i-\mu_k)=\frac{\partial}{\partial y_i}y_i^T\Sigma_k^{-1}y_i\frac{\partial y_i}{\partial\mu_k}$$
$$=-1\times(\Sigma_k^{-1}+\Sigma_k^{-T})y_i \tag{8.14}$$

将等式 8.14 中的表达式代入，我们得到如下等式。

$$\frac{\partial}{\partial\mu_k}l(\mu_k,\Sigma_k)\propto-\frac{1}{2}\sum_i r_{ik}\left[-2\Sigma^{-1}(x_i-\mu_k)\right]$$
$$=\Sigma^{-1}\sum_i r_{ik}(x_i-\mu_k)=0 \tag{8.15}$$

这意味着如下等式。

$$\sum_i r_{ik}(x_i - \mu_k) = 0 \implies \mu_k = \frac{\sum_i r_{ik}x_i}{\sum_i r_{ik}} \tag{8.16}$$

为了计算最优的 $\Sigma_k$，我们可以使用迹恒等式。

$$x^T A x = \operatorname{tr}\left(x^T A x\right) = \operatorname{tr}\left(x x^T A\right) = \operatorname{tr}\left(A x x^T\right) \tag{8.17}$$

使用 $\hat{\lambda}=\Sigma^{-1}$ 记号，我们得到以下结果。

$$l(\Lambda) \propto -\frac{1}{2}\sum_i r_{ik}\log|\Lambda| - \frac{1}{2}\sum_i r_{ik}\operatorname{tr}\left[(x_i - \mu)(x_i - \mu)^T \Lambda\right]$$
$$= -\frac{1}{2}\sum_i r_{ik}\log|\Lambda| - \frac{1}{2}\operatorname{tr}(S_\mu \Lambda) \tag{8.18}$$

对矩阵求导，我们得到如下等式。

$$\frac{\partial l(\Lambda)}{\partial \Lambda} = -\frac{1}{2}\sum_i r_{ik}\Lambda^{-T} - \frac{1}{2}S_\mu^T = 0$$
$$\Lambda^{-1}\sum_i r_{ik} = S_\mu^T \implies \Sigma = \frac{S_\mu^T}{\sum_i r_{ik}}$$
$$\Sigma = \frac{\sum_i r_{ik}(x_i - \mu_k)(x_i - \mu_k)^T}{\sum_i r_{ik}} = \frac{\sum_i r_{ik}x_i x_i^T}{\sum_i r_{ik}} - \mu_k \mu_k^T \tag{8.19}$$

这些方程具有直观意义；簇 $k$ 的均值由 $r_{ik}$ 加权，是所有分配到簇 $k$ 的点的平均值，而协方差是加权经验散度矩阵。我们现在可以准备从头实现 GMM 的 EM 算法了！让我们先看看图 8.3 中的伪代码。

GMM 类由三个主要函数组成：gmm_em、estep 和 mstep。在 gmm_em 中，我们使用 K-means 算法初始化均值，并将协方差初始化为单位矩阵。接下来，我们在 estep 和 mstep 之间迭代：estep 计算数据点 $i$ 对每个簇 $k$ 的职责（又称软分配），mstep 则将职责作为输入，计算模型参数：高斯混合模型（GMM）中每个簇的均值、协方差和混合比例。estep 和 mstep 函数中的代码遵循文中的推导。在以下代码中

```
1: class GMM
2: function gmm_em(X, k):
3: π_init = 1/K
4: μ_init = KMeans(X, k) ← Initializes with K-means
5: Σ_init = I_d×d
6: for iter = 1, 2, ..., max_iter
7:   r_ik = estep(π_k, μ_k, Σ_k, X) ← Computes responsibilities
8:   π_k, μ_k, Σ_k = mstep(r_ik, X) ← Computes model parameters
9: end for
10: return π_k, μ_k, Σ_k
11: function estep(π_k, μ_k, Σ_k, X):
12: r_ik = N(x_i | μ_k, Σ_k) π_k / Σ_{k=1}^K N(x_i | μ_k, Σ_k) π_k
13: return r_ik
14: function mstep(r_ik, X):
15: π_k = 1/N Σ_i r_ik
16: μ_k = Σ_i r_ik x_i / Σ_i r_ik
17: Σ_k = Σ_i r_ik x_i x_i^T / Σ_i r_ik - μ_k μ_k^T
18: return π_k, μ_k, Σ_k
```

## 图 8.3 高斯混合模型的 EM 算法伪代码

在下面的清单中，我们将使用一个合成数据集，将真实 GMM 参数与 EM 算法推断出的参数进行比较。

## 清单 8.2 高斯混合模型的期望最大化

```
import numpy as np
import matplotlib.pyplot as plt
import matplotlib as mpl

from sklearn.cluster import KMeans
from scipy.stats import multivariate_normal
from scipy.special import logsumexp
from scipy import linalg

np.random.seed(3)

class GMM:
    def __init__(self, n=1e3, d=2, K=4):
        self.n = int(n)
        self.d = d
        self.K = K

        self.X = np.zeros((self.n, self.d))

        self.mu = np.zeros((self.d, self.K))
        self.sigma = np.zeros((self.d, self.d, self.K))
        self.pik = np.ones(self.K)/K

    def generate_data(self):
```

```
alpha0 = np.ones(self.K)
pi = np.random.dirichlet(alpha0)

#ground truth mu and sigma
mu0 = np.random.randint(0, 10, size=(self.d, self.K)) -
    5*np.ones((self.d, self.K))
V0 = np.zeros((self.d, self.d, self.K))
for k in range(self.K):
    eigen_mean = 0
    Q = np.random.normal(loc=0, scale=1, size=(self.d, self.d))
    D = np.diag(abs(eigen_mean + np.random.normal(loc=0, scale=1,
        size=self.d)))
    V0[:,:,k] = abs(np.transpose(Q)*D*Q)

#sample data
for i in range(self.n):
    z = np.random.multinomial(1,pi)
    k = np.nonzero(z)[0][0]
    self.X[i,:] = np.random.multivariate_normal(mean=mu0[:,k],
        cov=V0[:,:,k], size=1)

plt.figure()
plt.scatter(self.X[:,0], self.X[:,1], color='b', alpha=0.5)
plt.title("Ground Truth Data"); plt.xlabel("X1"); plt.ylabel("X2")
plt.show()

return mu0, V0

def gmm_em(self):
    kmeans = KMeans(n_clusters=self.K,
        random_state=42).fit(self.X)
    self.mu = np.transpose(kmeans.cluster_centers_)

    #init sigma
    for k in range(self.K):
        self.sigma[:,:,k] = np.eye(self.d)

    #EM algorithm
    max_iter = 10
    tol = 1e-5
    obj = np.zeros(max_iter)
    for iter in range(max_iter):
        print("EM iter ", iter)
        #E-step
        resp, llh = self.estep()
        #M-step
        self.mstep(resp)
        #check convergence
        obj[iter] = llh
        if (iter > 1 and obj[iter] - obj[iter-1] < tol*abs(obj[iter])):
            break
    #end for
    plt.figure()
```

用 k-means 初始化均值

E 步

M 步

```
plt.plot(obj)
plt.title('EM-GMM objective'); plt.xlabel("iter");
plt.ylabel("log-likelihood")
plt.show()

def estep(self):
    log_r = np.zeros((self.n, self.K))
    for k in range(self.K):
        log_r[:,k] = multivariate_normal.logpdf(self.X,
            mean=self.mu[:,k], cov=self.sigma[:,:,k])
    #end for
    log_r = log_r + np.log(self.pik)
    L = logsumexp(log_r, axis=1)
    llh = np.sum(L)/self.n  #log likelihood
    log_r = log_r - L.reshape(-1,1) #normalize
    resp = np.exp(log_r)
    return resp, llh

def mstep(self, resp):
    nk = np.sum(resp, axis=0)
    self.pik = nk/self.n
    sqrt_resp = np.sqrt(resp)
    for k in range(self.K):
        #update mu
        rx = np.multiply(resp[:,k].reshape(-1,1), self.X)
        self.mu[:,k] = np.sum(rx, axis=0) / nk[k]
        #update sigma
        Xm = self.X - self.mu[:,k]
        Xm = np.multiply(sqrt_resp[:,k].reshape(-1,1), Xm)
        self.sigma[:,:,k] = np.maximum(0, np.dot(np.transpose(Xm), Xm)
            / nk[k] + 1e-5 * np.eye(self.d))
    #end for

if __name__ == '__main__':
    gmm = GMM()
    mu0, V0 = gmm.generate_data()
    gmm.gmm_em()

    for k in range(mu0.shape[1]):
        print("cluster ", k)
        print("----------")
        print("ground truth means:")
        print(mu0[:,k])
        print("ground truth covariance:")
        print(V0[:,:,k])
    #end for

    for k in range(mu0.shape[1]):
        print("cluster ", k)
        print("----------")
```
