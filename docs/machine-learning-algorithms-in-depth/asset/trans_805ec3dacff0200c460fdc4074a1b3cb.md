

我们可以使用以下学习率调度，它满足方程 5.27 中的条件。

$$
\sum_{k=1}^{\infty} \eta_k = \infty
$$
$$
\sum_{k=1}^{\infty} \eta_k^2 < \infty \tag{5.27}
$$

我们可以使用以下学习率调度，它满足方程 5.27 中的条件。

$$
\eta_k = (\tau_0 + k)^{-\kappa} \tag{5.28}
$$

这里，\(\tau_0 \ge 0\) 减缓算法的早期迭代，而 \(\kappa \in (0.5, 1]\) 控制旧值被遗忘的速率。为了计算最陡下降方向 \(g_k\)，我们需要对损失函数 \(\text{NLL}(\theta)\) 求导。

$$
\frac{d}{d\theta}\log p(D|\theta) = \sum_{i=1}^{n}\left[y_i\frac{d}{d\theta}\log\sigma\left(\theta^T x_i\right) + (1-y_i)\frac{d}{d\theta}\log\left(1-\sigma\left(\theta^T x_i\right)\right)\right]
$$
$$
= \sum_{i=1}^{n}\left[y_i\frac{\sigma\left(\theta^T x_i\right)\left(1-\sigma\left(\theta^T x_i\right)\right)}{\sigma\left(\theta^T x_i\right)}x_i + (1-y_i)\frac{\sigma\left(\theta^T x_i\right)\left(1-\sigma\left(\theta^T x_i\right)\right)}{1-\sigma\left(\theta^T x_i\right)}(-x_i)\right]
$$
$$
= \sum_{i=1}^{n}\left[y_i x_i\left(1-\sigma\left(\theta^T x_i\right)\right)-(1-y_i)x_i\sigma\left(\theta^T x_i\right)\right]
$$
$$
= \sum_{i=1}^{n}\left[y_i-\sigma\left(\theta^T x_i\right)\right]x_i
$$
$$
= \sum_{i=1}^{n}\left[y_i-\mu_i\right]x_i = -X^T(\mu - y) \tag{5.29}
$$

在方程 5.29 中，我们使用了事实 \(d/dx\,\sigma(x) = (1-\sigma(x))\sigma(x)\) 以及伯努利分布的均值 \(\mu_i = \sigma(\theta^T x_i)\)。请注意，有许多自动微分库可以避免手工推导梯度。此外，我们可以添加正则化来控制参数规模。我们的正则化目标和梯度如下。

$$
\min_{\theta}\text{Loss}(\theta) = \min_{\theta}\left[\text{NLL}(\theta) + \lambda\theta^T\theta\right]
$$
$$
g_k = X^T(\mu - y) + 2\lambda\theta \tag{5.30}
$$

我们现在准备为逻辑回归实现 SGD。让我们从图 5.10 所示的以下伪代码开始。

```text
1: class sgdlr
2: function lr_objective(θ, X, y, λ)
3: μ_i = sigmoid(θ^T X_i)
4: cost = - Σ_{i=1}^n [y_i log μ_i + (1 - y_i) log (1 - μ_i)] + λ θ^T θ
5: grad = X^T (μ - y) + 2λ θ ← Computes the gradient
6: return cost, grad
7: function fit(X, y):
8: η_i = (τ + i)^{-κ} ← Sets the learning rate
9: for i = 1, 2, … num_iter
10:   cost, grad = lr_objective(θ, X, y, λ)
11:   θ = θ - η_i grad ← Updates the theta
12: end for
13: return θ
14: function predict(X, θ):
15: ŷ = sigmoid (θ^T X) ← Makes a prediction
16: return ŷ
```

**Figure 5.10** 逻辑回归算法伪代码

sgdlr 类包含三个主要函数：lr_objective、fit 和 predict。在 lr_objective 函数中，我们计算正则化目标函数和目标的梯度，如文中所述。在 fit 函数中，我们首先设置学习率，并且在每次迭代中，我们沿着与梯度相反的方向更新 theta 参数。最后，在 predict 函数中，我们基于测试数据对标签进行二元预测。在下面的代码列表中，我们使用合成高斯混合数据集来训练逻辑回归模型。

### Listing 5.3 SGD 逻辑回归

```python
import numpy as np
import matplotlib.pyplot as plt

def generate_data():

    n = 1000
    mu1 = np.array([1,1])
    mu2 = np.array([-1,-1])
    pik = np.array([0.4,0.6])

    X = np.zeros((n,2))
    y = np.zeros((n,1))

    for i in range(1,n):
        u = np.random.rand()
        idx = np.where(u < np.cumsum(pik))[0]

        if (len(idx)==1):
            X[i,:] = np.random.randn(1,2) + mu1
            y[i] = 1
        else:
            X[i,:] = np.random.randn(1,2) + mu2
            y[i] = -1
    return X, y

class sgdlr:

    def __init__(self):

        self.num_iter = 100
        self.lmbda = 1e-9

        self.tau0 = 10
        self.kappa = 1
        self.eta = np.zeros(self.num_iter)

        self.batch_size = 200
        self.eps = np.finfo(float).eps

    def fit(self, X, y):

        theta = np.random.randn(X.shape[1],1)  # <-- Random init

        for i in range(self.num_iter):
            self.eta[i] = (self.tau0 + i)**(-self.kappa)  # Learning rate schedule

        batch_data, batch_labels = self.make_batches(
            X,y,self.batch_size)  # <-- Divides data into batches
        num_batches = batch_data.shape[0]
        num_updates = 0

        J_hist = np.zeros((self.num_iter * num_batches,1))
        t_hist = np.zeros((self.num_iter * num_batches,1))

        for itr in range(self.num_iter):
            for b in range(num_batches):
                Xb = batch_data[b]
                yb = batch_labels[b]

                J_cost, J_grad = self.lr_objective(theta, Xb, yb, self.lmbda)
                theta = theta - self.eta[itr]*(num_batches*J_grad)

                J_hist[num_updates] = J_cost
                t_hist[num_updates] = np.linalg.norm(theta,2)
                num_updates = num_updates + 1
                print("iteration %d, cost: %f" %(itr, J_cost))

        y_pred = 2*(self.sigmoid(X.dot(theta)) > 0.5) - 1
        y_err = np.size(np.where(y_pred - y)[0])/float(y.shape[0])
        print("classification error:", y_err)

        plt.figure()
        plt.plot(t_hist)
        plt.title("LR theta L2 norm")
        plt.xlabel('iterations')
        plt.ylabel('theta L2 norm')
        #plt.savefig('../figures/lrsgd_theta_norm.png')
        plt.show()

        plt.figure()
        plt.plot(self.eta)
        plt.title("LR learning rate")
        plt.xlabel('iterations')
        plt.ylabel('learning rate')
        #plt.savefig('../figures/lrsgd_learning_rate.png')
        plt.show()

        plt.figure()
        x1 = np.linspace(np.min(X[:,0])-1,np.max(X[:, 0])+1,10)
        plt.scatter(X[:,0], X[:,1])
        plt.plot(x1, -(theta[0]/theta[1])*x1)
        plt.title('LR decision boundary')
        plt.grid(True)
        plt.xlabel('X1')
        plt.ylabel('X2')
        #plt.savefig('../figures/lrsgd_clf.png')
        plt.show()

if __name__ == "__main__":
    X, Y = generate_data()
    sgd = sgdlr()
    theta = sgd.fit(X,Y)
```

图 5.11 显示了随着迭代次数增加而下降的损失函数的随机性，以及我们二元逻辑回归学习到的决策边界。

![](img/325742126d3ff007c6c385f4ffb5c3be_112_0.png)

**Figure 5.11** SGD 逻辑回归：代价（左）和决策边界（右）

二元逻辑回归的自然扩展是处理超过 2 个类别的多项逻辑回归。

## 5.5 朴素贝叶斯

本节重点介绍理解、推导和实现朴素贝叶斯算法。算法的基本（朴素）假设是给定类别标签时特征条件独立。这使我们能够将类别条件密度写成一维密度的乘积。

$$
p(x_i|y=c,\theta)=\prod_{j=1}^{D}p(x_{ij}|y=c,\theta_{jc}) \tag{5.31}
$$

该模型被称为朴素，因为我们并不期望特征条件独立。然而，即使假设不成立，该模型在许多场景中表现良好。在这里，我们将重点关注用于文档分类的伯努利朴素贝叶斯，其图形模型如图 5.12 所示。请注意阴影节点表示观测变量。

![](img/325742126d3ff007c6c385f4ffb5c3be_113_0.png)

类别条件密度 \(p(x|y=c,\theta)\) 的选择决定了朴素贝叶斯分类器的类型，例如高斯、伯努利或多项式。在本节中，我们重点关注伯努利朴素贝叶斯，因为它在分类文档方面性能很高。

令 \(x_{ij}\) 为伯努利随机变量，表示文档 \(i\in\{1,\dots,N\}\) 中词 \(j\in\{1,\dots,D\}\) 的出现（\(x_{ij}=1\)）或缺失（\(x_{ij}=0\)），由给定类别标签 \(y=c\in\{1,\dots,C\}\) 的 \(\theta_{jc}\) 参数化。此外，令 \(\pi\) 为表示类别标签先验的狄利克雷分布。因此，可学习参数的总数为 \(|\theta|+|\pi|=O(DC)+O(C)=O(DC)\)，其中 \(D\) 为词典大小，\(C\) 为类别数。由于参数数量少，朴素贝叶斯模型对过拟合具有免疫力。

我们可以在方程 5.32 中写下类别条件密度。

$$
p(x|y=c,\theta)=\prod_{i=1}^n\prod_{j=1}^D p(x_{ij}|y=c,\theta_{jc})=\prod_{i=1}^n\prod_{j=1}^D \mathrm{Bernoulli}(x_{ij}|\theta_{jc}) \tag{5.32}
$$

我们可以通过最大化对数似然来推导朴素贝叶斯推理算法。考虑单个文档 \(i\) 中的词 \(x_i\)。

$$
p(x_i,y_i|\theta)=p(y_i|\pi)\prod_{j=1}^D p(x_{ij}|y_i,\theta)
$$
$$
=\prod_{c=1}^C \pi_c^{1[y_i=c]}\prod_{j=1}^D\prod_{c=1}^C p(x_{ij}|\theta_{jc})^{1[y_i=c]} \tag{5.33}
$$

使用朴素贝叶斯假设，我们可以计算对数似然目标。

$$
\log p(D|\theta)=\log\prod_{i=1}^n p(x_i,y_i|\theta)=\sum_{i=1}^n\log p(x_i,y_i|\theta)
$$
$$
=\sum_{c=1}^C N_c\log\pi_c+\sum_{j=1}^D\sum_{c=1}^C\sum_{i:y_i=c}\log p(x_{ij}|\theta_{jc}) \tag{5.34}
$$

请注意这是一个约束优化程序，因为类别标签的概率必须和为一：\(\sum\pi_c=1\)。我们可以通过在目标函数中加入约束并将拉格朗日 \(L(\theta,\lambda)\) 关于模型参数的梯度设为零来使用拉格朗日求解方程 5.34 中的优化问题。

$$
L(\theta,\lambda)=\log p(D|\theta)+\lambda\left(1-\sum_c\pi_c\right) \tag{5.35}
$$

对 \(\pi_c\) 求导，我们得到以下结果。

$$
\frac{d}{d\pi_c}L(\theta,\lambda)=\frac{d}{d\pi_c}\log p(D|\theta)-\lambda=N_c\frac{1}{\pi_c}-\lambda=0 \tag{5.36}
$$

这给出了 \(\pi_c\) 关于 \(\lambda\) 的表达式：\(\pi_c=(1/\lambda)N_c\)。为了解决 \(\lambda\)，我们使用和为一的约束。

$$
\sum_c\pi_c=1\to\sum_c\frac{1}{\lambda}N_c=1\to\lambda=\sum_c N_c \tag{5.37}
$$

将 \(\lambda\) 代回 \(\pi_c\) 的表达式，我们得到 \(\pi_c=N_c/\sum N_c=N_c/N_{tot}\)。同样，我们可以通过将目标关于 \(\theta_{jc}\) 的梯度设为零来计算最优 \(\theta_{jc}\) 参数。

