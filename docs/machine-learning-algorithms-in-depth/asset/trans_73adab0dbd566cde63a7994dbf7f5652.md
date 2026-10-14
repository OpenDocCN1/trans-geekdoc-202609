
## 2.6 Metropolis-Hastings 采样

让我们来看一种更通用的 MCMC 算法，用于从分布中采样。我们的目标是构建一条马尔可夫链，使其平稳分布等于我们的目标分布 p(x)。目标分布 p(x) 是我们感兴趣从中抽取样本的分布（通常是后验 p(θ|x) 或密度函数 p(θ)）。

Metropolis-Hastings (MH) 算法的基本思想是：根据提议分布 q(x′|x) 从当前状态 x 提议一个移动到新状态 x′，然后根据 MH 比率决定接受或拒绝该提议状态，该比率确保满足细致平衡条件，如公式 2.18 所示。

p(x′) q(x|x′) = p(x) q(x′|x)  (2.18)

细致平衡方程表明，从状态 x 转移出去的概率等于转移到状态 x 的概率。为了推导 MH 比率，暂时假设上述细致平衡方程不成立，那么必然存在一个修正因子 r(x′|x) 使得两边相等，求解该因子得到如下 MH 比率。

p(x′) q(x|x′) = r(x′|x) p(x) q(x′|x)

r(x′|x) = min[ 1, p(x′) q(x|x′) / p(x) q(x′|x) ]  (2.19)

我们可以将 Metropolis-Hastings 算法总结如图 2.13 所示。

- 从提议分布中采样
- 1: 随机初始化 x₀
- 2: for k = 0, 1, 2, … do
- 3:   提议一个新状态 x′ ~ q(x′|xₖ)
- 4:   计算 metropolis-hastings 比率：
- 5:   r(x′|x) = min[ 1, p(x′)q(x|x′) / p(x)q(x′|x) ]
- 6:   令 xₖ₊₁ = { x′，概率为 r(x′|x) ← 接受样本
                   xₖ，概率为 1 − r(x′|x) ← 拒绝样本 }
- 7: end for

图 2.13 Metropolis-Hastings 伪代码

让我们针对多变量高斯混合目标分布和高斯提议分布来实现 MH 算法。

p(x) = Σₖ₌₁ᴷ π(k) N(x; μₖ, Σₖ)
q(x′|x) = N(x′|x, Σ)  (2.20)

让我们查看代码清单 2.5。`mh_gauss` 类包含：`target_pdf` 函数，定义目标分布（本例中为高斯混合 p(x)）；`proposal_pdf` 函数，定义提议分布（一个多元正态分布）；以及 `sample` 函数，它根据前一个状态 x_k 从提议 q(x′|x) 中采样一个新状态，计算 Metropolis-Hastings 比率，并以概率 r(x′|x) 接受新样本或以概率 1 − r(x′|x) 拒绝样本。

### 清单 2.5 Metropolis-Hastings 采样

```
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
            x_curr = self.mh_samples[i,:]
```

目标参数：
p(x) = \sum_k pi(k) N(x; mu_k, Sigma_k)

提议参数：
q(x) = N(x; mu, Sigma)

采样链参数

目标概率密度函数：p(x) = \sum_k pi(k) N(x; mu_k,Sigma_k)

提议概率密度函数：
q(x) = N(x; mu, Sigma)

从提议分布中抽取初始样本。

```
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

```
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

从图 2.14 可以看出，MH 样本非常接近真实的两个二维高斯混合分布，其均值分别为 μ1 = [4,0]，μ2 = [−4,0]；协方差分别为 Σ_1 = [[2,1],[1,1]] 和 Σ_2 = [[1,0],[0,1]]；混合比例为 π = [0.4,0.6]。

请注意，我们可以自由选择任何提议分布 q(x'|x)，这使方法非常灵活。一个好的提议选择将带来较高的样本接受率。

![](img/325742126d3ff007c6c385f4ffb5c3be_55_0.png)

图 2.14 多元高斯混合的 Metropolis-Hastings 采样

在我们的实现中，我们选择了一个以当前状态为中心的对称高斯分布，如公式 2.21 所示。

$q(x'|x) = \mathcal{N}(x'|x, \Sigma)$

(2.21)

这被称为随机游走 Metropolis 算法。如果我们使用形如 $q(x'|x) = q(x')$ 的提议分布，即新状态独立于旧状态，就得到了独立采样器，它类似于我们下一节将要讨论的重要性采样。

另外，注意计算 MH 比率时，我们不需要知道分布的归一化常数 $Z$，因为比率中的 $Z$ 会相互抵消。MH 算法与 Gibbs 采样之间存在联系：Gibbs 算法的接受比率始终为 1。

## 2.7 重要性采样

重要性采样（IS）是一种蒙特卡洛算法，用于估计如下形式的积分。

$E[f(x)] = \int p(x) f(x) dx$

(2.22)

重要性采样背后的思想是在感兴趣的区域（即 p(x) 和 |f(x)| 都较大的区域）抽取样本。重要性采样通过从一个更易采样的提议分布 q(x) 中抽取样本来工作。因此，我们可以通过从提议分布 q(x) 中抽取样本并使用蒙特卡洛积分来计算 f(x) 关于目标分布 p(x) 的期望值。

E[f(x)] = ∫ f(x) p(x)/q(x) q(x) dx ≈ 1/N Σ_{i=1}^N w(x_i) f(x_i)，其中 x_i ~ q(x)  (2.23)

在公式 2.23 中，我们将重要性权重定义为 w(x) = p(x) / q(x)。让我们看一个例子，其中我们使用重要性采样来近似 f(x) = 2 sin(πx/1.5), x ≥ 0 的期望值。我们需要对由非整数自由度（DoF）参数 k 参数化的未归一化 χ 分布求期望。

p(x) ~ x^{(k-1)} exp{ -x²/2 }, x ≥ 0  (2.24)

我们将使用一个更易采样的提议分布 q(x)：

q(x) ~ N(x; 0.8, 1.5)  (2.25)

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

我们的 `importance_sampler` 类包含一个名为 `sample` 的函数，该函数将样本数 N 作为输入。在 `sample` 函数内部，我们遍历样本数，对于每次迭代，我们从提议分布 q(x) 中采样，并将重要性权重计算为目标分布 p(x) 与提议分布 q(x) 之比。最后，我们通过使用重要性权重对感兴趣的函数 f(x) 进行加权，对所有样本求和并除以 N 来计算蒙特卡洛积分。让我们查看以下代码清单，它包含了所有细节。

