
```python
#end while
square_dist[it] = X**2 + Y**2
weights[it] = weight
#end for

mean_square_dist = np.mean(weights * square_dist)/np.mean(weights)
print("mean square dist: ", mean_square_dist)

#generate plots
plt.figure()
for i in range(num_step-1):
    plt.plot(path[i,0], path[i,1], path[i+1,0], path[i+1,1], 'ob')
plt.title('random walk with no overlaps')
plt.xlabel('X')
plt.ylabel('Y')
plt.show()

plt.figure()
sns.displot(square_dist)
plt.xlim(0,np.max(square_dist))
plt.title('square distance of the random walk')
plt.xlabel('square distance (X^2 + Y^2)')
plt.show()

if __name__ == "__main__":
    num_step = 150
    num_iter = 100
    moves = np.array([[0, 1],[0, -1],[-1, 0],[1, 0]])
    rand_walk(num_step, num_iter, moves)
```

- 计算平方扩展
- 用于平均结果的迭代次数
- 随机游走的步数
- 二维移动

图2.10展示了由最后一次迭代生成的自回避随机游走。在二维格点上，长度为n的随机游走共有4^n种可能，而对于较大的n，随机游走能够自回避的可能性非常低。该图还显示了每次随机游走迭代计算得到的平方距离直方图。直方图呈正偏态，表明长距离游走的概率较小。在下一节中，我们将介绍一种流行的采样算法：吉布斯采样。

![](img/325742126d3ff007c6c385f4ffb5c3be_47_0.png)

![](img/325742126d3ff007c6c385f4ffb5c3be_47_1.png)

**图2.10** 自回避随机游走（左）与随机游走平方距离（右）

## 2.5 吉布斯采样

在本节中，我们将介绍一种基本的MCMC算法，称为吉布斯采样。这种采样形式基于这样的思想：从多维分布中一次采样一个变量，并以所有其他变量的最新样本为条件。例如，对于一个d=3维的分布，给定起始样本x^{[k]}，我们按如下方式生成下一个样本x^{[k+1]}。

$$
x_1^{k+1} \sim p\left(x_1|x_2^k, x_3^k\right)
$$
$$
x_2^{k+1} \sim p\left(x_2|x_1^{k+1}, x_3^k\right)
$$
$$
x_3^{k+1} \sim p\left(x_3|x_1^{k+1}, x_2^{k+1}\right)
\tag{2.14}
$$

方程2.14中的分布称为完全条件分布。此外，请注意，朴素吉布斯采样算法是顺序执行的（其步骤数与分布的维度成正比），并且它假设我们可以轻松地从完全条件分布中采样。吉布斯采样算法适用于方程2.14中的完全条件分布易于计算的场景。

完全条件分布易于计算的一个实例是多元高斯分布，其概率密度函数（PDF）定义如下。

$$
\mathcal{N}(x; \mu, \Sigma) = \frac{1}{(2\pi)^{\frac{d}{2}}|\Sigma|^{\frac{1}{2}}} \exp\left[-\frac{1}{2}(x-\mu)^T \Sigma^{-1} (x-\mu)\right]
\tag{2.15}
$$

让我们将高斯向量划分为两个集合x_{1:D} = (x_A, x_B)，其参数如方程2.16所示。

$$
\mu = \begin{pmatrix} \mu_A \\ \mu_B \end{pmatrix}
$$
$$
\Sigma = \begin{pmatrix} \Sigma_{AA} & \Sigma_{AB} \\ \Sigma_{BA} & \Sigma_{BB} \end{pmatrix}
\tag{2.16}
$$

然后，如Christopher M. Bishop所著《模式识别与机器学习》（2006）第2.3节所讨论的，可以证明完全条件分布由方程2.17给出。

$$
p(x_A|x_B) = \mathcal{N}(x_A|\mu_{A|B}, \Sigma_{A|B})
$$
$$
\mu_{A|B} = \mu_A + \Sigma_{AB} \Sigma_{BB}^{-1} (x_B - \mu_B)
$$
$$
\Sigma_{A|B} = \Sigma_{AA} - \Sigma_{AB} \Sigma_{BB}^{-1} \Sigma_{BA}
\tag{2.17}
$$

让我们通过查看图2.11中的伪代码来理解吉布斯采样算法。

```text
1: class gibbs_gauss
2: function gauss_conditional(mu, Sigma, setA, x):
3: setU = set(range(len(mu))) ← Universal set
4: setB = setU\setA
5: x_B, μ_A, μ_B = x[setB], mu[setA], mu[setB]
6: μ_{A|B} = μ_A + Σ_{AB} Σ_{BB}^{-1} (x_B - μ_B)
7: Σ_{A|B} = Σ_{AA} - Σ_{AB} Σ_{BB}^{-1} Σ_{BA}
8: return μ_{A|B}, Σ_{A|B}
9: function sample(mu, Sigma, xinit, num_samples):
10: x = xinit
11: dim = len(mu)
12: for s = 1 to num_samples:
13:   for d = 1 to dim:
14:     μ_{A|B}, Σ_{A|B} = gauss_conditional(mu, Sigma, set(d), x)
15:     x[d] ~ N(x; μ_{A|B}, Σ_{A|B}) ← Gibbs samples
16:   end for
17:   samples[s,:] = x
18: end for
19: return samples
```

**图2.11** 吉布斯采样器伪代码

我们的gibbs_gauss类包含两个函数：gauss_conditional和sample。gauss_conditional函数计算任意变量集合setA和setB的条件高斯分布p(x_A|x_B)。setA是函数的输入，而setB通过维度D的通用集合与setA的差集计算得到。回想一下，在吉布斯采样中，我们一次对一个维度进行采样，同时以所有其他维度为条件。换句话说，我们遍历可用维度，并在每次迭代中计算条件分布。这正是sample函数所做的。对于每个样本，我们遍历每个维度，计算高斯条件分布的均值和协方差，然后从中抽取并记录一个样本。我们重复此过程，直到达到最大样本数。让我们看看吉布斯采样算法在从二维高斯分布中采样时的实际应用。

### 代码清单2.4 吉布斯采样

```python
import numpy as np
import matplotlib.pyplot as plt
import itertools
from numpy.linalg import inv
from scipy.stats import multivariate_normal

np.random.seed(42)

class gibbs_gauss:
    def gauss_conditional(self, mu, Sigma, setA, x):
        dim = len(mu)
        setU = set(range(dim))
        setB = setU.difference(setA)
        muA = np.array([mu[item] for item in setA]).reshape(-1,1)
        muB = np.array([mu[item] for item in setB]).reshape(-1,1)
        xB = np.array([x[item] for item in setB]).reshape(-1,1)

        Sigma_AA = []
        for (idx1, idx2) in itertools.product(setA, setA):
            Sigma_AA.append(Sigma[idx1][idx2])
        Sigma_AA = np.array(Sigma_AA).reshape(len(setA),len(setA))

        Sigma_AB = []
        for (idx1, idx2) in itertools.product(setA, setB):
            Sigma_AB.append(Sigma[idx1][idx2])
        Sigma_AB = np.array(Sigma_AB).reshape(len(setA),len(setB))

        Sigma_BB = []
        for (idx1, idx2) in itertools.product(setB, setB):
            Sigma_BB.append(Sigma[idx1][idx2])
        Sigma_BB = np.array(Sigma_BB).reshape(len(setB),len(setB))

        Sigma_BB_inv = inv(Sigma_BB)
        mu_AgivenB = muA + np.matmul(np.matmul(Sigma_AB, Sigma_BB_inv),
        xB - muB)
        Sigma_AgivenB = Sigma_AA - np.matmul(np.matmul(Sigma_AB,
        Sigma_BB_inv), np.transpose(Sigma_AB))

        return mu_AgivenB, Sigma_AgivenB

    def sample(self, mu, Sigma, xinit, num_samples):
        dim = len(mu)
        samples = np.zeros((num_samples, dim))
        x = xinit
        for s in range(num_samples):
            for d in range(dim):
                mu_AgivenB, Sigma_AgivenB = self.gauss_conditional(mu, Sigma,
                set([d]), x)
                x[d] = np.random.normal(mu_AgivenB, np.sqrt(Sigma_AgivenB))
            #end for
            samples[s,:] = np.transpose(x)
        #end for
        return samples

if __name__ == "__main__":

    num_samples = 2000
    mu = [1, 1]
    Sigma = [[2,1], [1,1]]
    xinit = np.random.rand(len(mu),1)
    num_burnin = 1000

    gg = gibbs_gauss()
    gibbs_samples = gg.sample(mu, Sigma, xinit, num_samples)

    scipy_samples = multivariate_normal.rvs(mean=mu,cov=Sigma,size=num_samples,random_state=42)

    plt.figure()
    plt.scatter(gibbs_samples[num_burnin:,0], gibbs_samples[num_burnin:,1],
        label='Gibbs Samples')
    plt.grid(True); plt.legend(); plt.xlim([-4,5])
    plt.title("Gibbs Sampling of Multivariate Gaussian"); plt.xlabel("X1");
    plt.ylabel("X2")
    plt.show()

    plt.figure()
    plt.scatter(scipy_samples[num_burnin:,0], scipy_samples[num_burnin:,1],
        label='Ground Truth  Samples')
    plt.grid(True); plt.legend(); plt.xlim([-4,5])
    plt.title("Ground Truth Samples of Multivariate Gaussian");
    plt.xlabel("X1");
    plt.ylabel("X2")
    plt.show()
```

*计算 P(X_A | X_B = x) = N(mu_{A|B}, Sigma_{A|B})*

从图2.12中，我们可以看到吉布斯样本与由μ = [1, 1]ᵀ和Σ = [[2, 1], [1, 1]]参数化的真实二维高斯分布样本相似。在下一节中，我们将研究一种更通用的MCMC采样算法：Metropolis-Hastings采样。

![](img/325742126d3ff007c6c385f4ffb5c3be_51_0.png)

**图2.12** 多元高斯分布的吉布斯样本

