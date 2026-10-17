
```python
import numpy as np
import matplotlib.pyplot as plt

from scipy.stats import uniform
from scipy.stats import multivariate_normal

np.random.seed(42)

class mh_gauss:

    def __init__(self, dim, K, num_samples, target_mu, target_sigma,
        target_pi, proposal_mu, proposal_sigma):
        self.dim = dim
        self.K = K
        self.num_samples = num_samples
        self.target_mu = target_mu
        self.target_sigma = target_sigma
        self.target_pi = target_pi

        self.proposal_mu = proposal_mu
        self.proposal_sigma = proposal_sigma

        self.n_accept = 0
        self.alpha = np.zeros(self.num_samples)
        self.mh_samples = np.zeros((self.num_samples,
            self.dim))

    def target_pdf(self, x):
        prob = 0
        for k in range(self.K):
            prob += self.target_pi[k]*
                multivariate_normal.pdf(x,self
                .target_mu[:,:,k],self.target_sigma[:,:,k])
        #end for
        return prob

    def proposal_pdf(self, x):
        return multivariate_normal.pdf(x, self
            .proposal_mu, self.proposal_sigma)

    def sample(self):
        x_init = multivariate_normal
        .rvs(self.proposal_mu, self.proposal_sigma, 1)
        self.mh_samples[0,:] = x_init

        for i in range(self.num_samples-1):
```

### 目标参数：

$p(x) = \sum_k pi(k) N(x; mu_k, Sigma_k)$

### 提议参数：

$q(x) = N(x; mu, Sigma)$

采样链参数

目标概率密度函数：$p(x) = \sum_k pi(k) N(x; mu_k,Sigma_k)$

提议概率密度函数：

$q(x) = N(x; mu, Sigma)$

从提议分布中抽取初始样本。

```python
x_new = multivariate_normal.rvs(x_curr, self
    .proposal_sigma, 1)

self.alpha[i] = self.proposal_pdf(x_new) /
    self.proposal_pdf(x_curr)
self.alpha[i] = self.alpha[i] *
    (self.target_pdf(x_new)/self.target_pdf(x_curr))

r = min(1, self.alpha[i])            <-- MH acceptance probability
u = uniform.rvs(loc=0, scale=1, size=1)
if (u <= r):
    self.n_accept += 1
    self.mh_samples[i+1,:] = x_new      <-- Accept
else:
    self.mh_samples[i+1,:] = x_curr      <-- Reject
#end for
print("MH acceptance ratio: ", self.n_accept/float(self.num_samples))
```

```python
if __name__ == "__main__":

    dim = 2
    K = 2
    num_samples = 5000
    target_mu = np.zeros((dim, K))
    target_mu[:,0] = [4,0]
    target_mu[:,1] = [-4,0]
    target_sigma = np.zeros((dim, dim, K))
    target_sigma[:,:,0] = [[2,1],[1,1]]
    target_sigma[:,:,1] = [[1,0],[0,1]]
    target_pi = np.array([0.4, 0.6])

    proposal_mu = np.zeros((dim,1)).flatten()
    proposal_sigma = 10*np.eye(dim)

    mhg = mh_gauss(dim, K, num_samples, target_mu, target_sigma, target_pi,
        proposal_mu, proposal_sigma)
    mhg.sample()

    plt.figure()
    plt.scatter(mhg.mh_samples[:,0], mhg.mh_samples[:,1], label='MH samples')
    plt.grid(True); plt.legend()
    plt.title("Metropolis-Hastings Sampling of 2D Gaussian Mixture")
    plt.xlabel("X1"); plt.ylabel("X2")
    plt.show()
```

从图 2.14 可以看出，MH 样本非常接近真实的两个二维高斯混合分布，其均值分别为 $\mu_1 = [4,0]$，$\mu_2 = [−4,0]$；协方差分别为 $\Sigma_1 = [[2,1],[1,1]]$ 和 $\Sigma_2 = [[1,0],[0,1]]$；混合比例为 $\pi = [0.4,0.6]$。

请注意，我们可以自由选择任何提议分布 $q(x'|x)$，这使方法非常灵活。一个好的提议选择将带来较高的样本接受率。

![](img/325742126d3ff007c6c385f4ffb5c3be_55_0.png)

图 2.14 多元高斯混合的 Metropolis-Hastings 采样

在我们的实现中，我们选择了一个以当前状态为中心的对称高斯分布，如公式 2.21 所示。

$q(x'|x) = \mathcal{N}(x'|x, \Sigma)$

(2.21)

这被称为随机游走 Metropolis 算法。如果我们使用形如 $q(x'|x) = q(x')$ 的提议分布，即新状态独立于旧状态，就得到了独立采样器，它类似于我们下一节将要讨论的重要性采样。

另外，注意计算 MH 比率时，我们不需要知道分布的归一化常数 $Z$，因为比率中的 $Z$ 会相互抵消。MH 算法与 Gibbs 采样之间存在联系：Gibbs 算法的接受比率始终为 1。

#### 2.7 重要性采样

重要性采样（IS）是一种蒙特卡洛算法，用于估计如下形式的积分。

$E[f(x)] = \int p(x) f(x) dx$

(2.22)

重要性采样背后的思想是在感兴趣的区域（即 $p(x)$ 和 $|f(x)|$ 都较大的区域）抽取样本。重要性采样通过从一个更易采样的提议分布 $q(x)$ 中抽取样本来工作。因此，我们可以通过从提议分布 $q(x)$ 中抽取样本并使用蒙特卡洛积分来计算 $f(x)$ 关于目标分布 $p(x)$ 的期望值。

$E[f(x)] = \int f(x) p(x)/q(x) q(x) dx \approx 1/N \sum_{i=1}^N w(x_i) f(x_i)$，其中 $x_i \sim q(x)$  (2.23)

在公式 2.23 中，我们将重要性权重定义为 $w(x) = p(x) / q(x)$。让我们看一个例子，其中我们使用重要性采样来近似 $f(x) = 2 \sin(\pi x/1.5), x \ge 0$ 的期望值。我们需要对由非整数自由度（DoF）参数 $k$ 参数化的未归一化 $\chi$ 分布求期望。

$p(x) \sim x^{(k-1)} \exp{ -x^2/2 }, x \ge 0$  (2.24)

我们将使用一个更易采样的提议分布 $q(x)$：

$q(x) \sim N(x; 0.8, 1.5)$  (2.25)

让我们查看图 2.15 中的伪代码。

```
1: class importance_sampler
2: function sample(N):
3: for i = 1 to N:
4: x_i ~ q(x) = N(x; μ, σ²) ← Samples from the proposal
5: w(x_i) = p(x_i)/q(x_i) ← Computes importance weights
6: end for
7: E[f(x)] = 1/N Σ_{i=1}^N w(x_i) f(x_i)
8: return w(x), E[f(x)]
```

图 2.15 重要性采样器伪代码

我们的 `importance_sampler` 类包含一个名为 `sample` 的函数，该函数将样本数 $N$ 作为输入。在 `sample` 函数内部，我们遍历样本数，对于每次迭代，我们从提议分布 $q(x)$ 中采样，并将重要性权重计算为目标分布 $p(x)$ 与提议分布 $q(x)$ 之比。最后，我们通过使用重要性权重对感兴趣的函数 $f(x)$ 进行加权，对所有样本求和并除以 $N$ 来计算蒙特卡洛积分。让我们查看以下代码清单，它包含了所有细节。

## 清单 2.6 重要性采样

```python
import numpy as np
import matplotlib.pyplot as plt

from scipy.integrate import quad
from scipy.stats import multivariate_normal

np.random.seed(42)

class importance_sampler:
    def __init__(self, k=1.5, mu=0.8, sigma=np.sqrt(1.5), c=3):
        self.k = k                # Target parameters p(x)
        self.mu = mu              # Proposal parameters q(x)
        self.sigma = sigma
        self.c = c                # Fixes c, s.t. p(x) < c q(x)

    def target_pdf(self, x):
        return (x**(self.k-1)) * np.exp(-x**2/2.0)   # p(x) ~ Chi(k=1.5)

    def proposal_pdf(self, x):
        return self.c * 1.0/np.sqrt(2*np.pi*1.5) *
            np.exp(-(x-self.mu)**2/(2*self.sigma**2))   # q(x) ~ N(mu,sigma)

    def fx(self, x):
        return 2*np.sin((np.pi/1.5)*x)   # Function of interest f(x), x >= 0

    def sample(self, num_samples):
        x = multivariate_normal.rvs(self.mu,
            self.sigma, num_samples)   # Sample from the proposal

        idx = np.where(x >= 0)          # Discards negative samples, since
        x_pos = x[idx]                  # f(x) is defined for x >= 0

        isw = self.target_pdf(x_pos) /
            self.proposal_pdf(x_pos)    # Computes importance weights

        fw = (isw/np.sum(isw))*self.fx(x_pos)   # Computes E[f(x)] = sum_i f(x_i)
        f_est = np.sum(fw)                      # w(x_i), where x_i ~ q(x)

        return isw, f_est

if __name__ == "__main__":

    num_samples = [10, 100, 1000, 10000, 100000, 1000000]

    F_est_iter, IS_weights_var_iter = [], []
    for k in num_samples:
        IS = importance_sampler()
        IS_weights, F_est = IS.sample(k)
        IS_weights_var = np.var(IS_weights/np.sum(IS_weights))
        F_est_iter.append(F_est)
        IS_weights_var_iter.append(IS_weights_var)

#ground truth (numerical integration)
k = 1.5
```

```python
I_gt, _ = quad(lambda x: 2.0*np.sin((np.pi/1.5)*x) * (x**(k-1))*np.exp(-x**2/2.0), 0, 5)

#generate plots
plt.figure()
xx = np.linspace(0,8,100)
plt.plot(xx, IS.target_pdf(xx), '-r', label='target pdf p(x)')
plt.plot(xx, IS.proposal_pdf(xx), '-b', label='proposal pdf q(x)')
plt.plot(xx, IS.fx(xx) * IS.target_pdf(xx), '-k', label='p(x)f(x) integrand')
plt.grid(True); plt.legend(); plt.xlabel("X1"); plt.ylabel("X2")
plt.title("Importance Sampling Components")
plt.show()

plt.figure()
plt.hist(IS_weights, label = "IS weights")
plt.grid(True); plt.legend();
plt.title("Importance Weights Histogram")
plt.show()

plt.figure()
plt.semilogx(num_samples, F_est_iter, label = "IS Estimate of E[f(x)]")
plt.semilogx(num_samples, F_gt*np.ones(len(num_samples)), label = "Ground Truth")
plt.grid(True); plt.legend(); plt.xlabel('iterations'); plt.ylabel("E[f(x)] estimate")
plt.title("IS Estimate of E[f(x)]")
plt.show()
```

图 2.16（左）显示了目标概率密度函数 $p(x)$、提议概率密度函数 $q(x)$ 以及被积函数 $p(x)f(x)$。请注意，我们用常数 $c$ 对提议概率密度函数 $q(x)$ 进行了缩放，使得对于所有 $x \ge 0$，都有 $p(x) < c q(x)$。此外，我们将来自 $q(x)$ 的样本限制为正数（因此，是从截断高斯分布中采样），以满足 $f(x)$ 对 $x \ge 0$ 的约束。图 2.16 展示了 $E[f(x)]$ 的估计值随样本数量的改善情况，并与通过数值积分计算得到的真实值进行了比较。

![](img/325742126d3ff007c6c385f4ffb5c3be_58_0.png)

在前一个例子中，我们使用了归一化的提议分布。然而，对于更复杂的分布，我们通常不知道归一化常数（即配分函数）。由于我们处理的是 pdf 的比值，我们将看到，对于未归一化的分布，上述数学仍然成立；此外，我们还将研究一种估计配分函数比值的方法，并讨论 IS 作为估计器的性质。

让我们定义归一化的 PDF $p(x)$ 和 $q(x)$ 如下。

$$p(x) = \frac{1}{Z_p}\tilde{p}(x)\qquad q(x) = \frac{1}{Z_q}\tilde{q}(x)\tag{2.26}$$
