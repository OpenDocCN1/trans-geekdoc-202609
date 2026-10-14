
```
class KNN():
    def __init__(self, K):
        self.K = K

    def euclidean_distance(self, x1, x2):
        dist = 0
        for i in range(len(x1)):
            dist += np.power((x1[i] - x2[i]), 2)
        return np.sqrt(dist)

    def knn_search(self, X_train, y_train, Q):
        y_pred = np.empty(Q.shape[0])

        for i, query in enumerate(Q):
            idx = np.argsort([self.euclidean_distance(
                query, x) for x in X_train])[:self.K]
            knn_labels = y_train[idx]
            y_pred[i] = np.mean(knn_labels)
        return y_pred

if __name__ == "__main__":

    plt.close('all')

    #iris dataset
    iris = datasets.load_iris()
    X = iris.data[:, :2]
    y = iris.target

    X_train, X_test, y_train, y_test = train_test_split(X, y,
        test_size=0.2, random_state=42)

    K = 4
    knn = KNN(K)
    y_pred = knn.knn_search(X_train, y_train, X_test)

    plt.figure(1)
    plt.scatter(X_train[:,0], X_train[:,1], s = 100, marker = 'x', color =
        'r', label = 'data')
    plt.scatter(X_test[:,0], X_test[:,1], s = 100, marker = 'o', color =
        'b', label = 'query')
    plt.title('K Nearest Neighbors (K=%d)'% K)
    plt.legend()
    plt.xlabel('X1')
    plt.ylabel('X2')
    plt.grid(True)
    plt.show()
```

- 获取查询点的 K 个最近邻
- 计算 KNN 训练标签的平均值
- 提取 KNN 训练标签

在高维空间中寻找精确的最近邻通常在计算上不可行，因此存在近似方法。存在两类近似方法：一类是将空间划分为区域，例如在快速近似最近邻库 FLANN 中实现的 k-d 树，另一类是基于哈希的方法，例如局部敏感哈希 LSH。在下一节中，我们将讨论一种不同类型的函数回归。

## 6.5 高斯过程回归

高斯过程 GPs 定义了在观察到数据后可以更新为后验的函数先验（参见 C. E. Rasmussen 和 C. K. I. Williams 的《Gaussian Processes for Machine Learning》，The MIT Press，2006）。在监督设置中，函数在数据点 x_i 与目标值 y_i 之间给出映射：y_i = f(x_i)。高斯过程在给定数据 p(f|x, y) 的情况下推断函数分布，然后用它对新数据进行预测。GP 假设函数在有限且任意选择的点 x_1, ..., x_n 上定义，使得 p(f(x_1), ..., f(x_n)) 是联合高斯，均值为 μ(x)，协方差为 Σ(x)，其中 Σ_ij = κ(x_i, x_j)，κ 是正定核函数。通过高斯过程回归可以解决的一个例子是基于观测测量预测 CO₂ 水平。在代码清单 6.4 中，我们将假设正弦模型和径向基函数核。

考虑一个简单的回归问题。

$f(x) = x^T w \quad y = f(x) + \epsilon \quad \epsilon \sim N\left(0, \sigma_n^2\right)$
(6.12)

假设噪声独立同分布，我们可以写下以下似然函数。

$p(y|X, w) = \prod_{i=1}^n p(y_i|x_i, w) = \prod_{i=1}^n \frac{1}{\sqrt{2\pi}\sigma_n} \exp\left\{ -\frac{(y_i - x_i^T w)^2}{2\sigma_n^2} \right\}$
$\sim N\left(Xw, \sigma_n^2 I\right)$
(6.13)

在贝叶斯框架中，我们需要对参数指定先验：w ~ N(0, Σ_p)。仅写出依赖于权重的似然和先验项，我们得到以下方程。

$p(w|X, y) \propto \exp\left\{ -\frac{1}{2\sigma_n^2} \|y - Xw\|^2 \right\} \exp\left\{ -\frac{1}{2} w^T \Sigma_p^{-1} w \right\}$
$\propto \exp\left\{ -\frac{1}{2} (w - \tilde{w}) \left( \frac{1}{\sigma_n^2} X X^T + \Sigma_p^{-1} \right) (w - \tilde{w}) \right\}$
$\sim N\left( \frac{1}{\sigma_n^2} A^{-1} X y, A^{-1} \right)$
(6.14)

这里，我们假设以下。

$$A = \sigma_n^{-2} X X^T + \Sigma_p^{-1}\tag{6.15}$$

因此，我们对参数 $w$ 具有闭式后验分布。要使用该方程进行预测，我们需要求逆大小为 $p \times p$ 的矩阵 $A$。

假设观测无噪声，我们希望预测函数输出 $y^* = f(x^*)$，其中 $x^*$ 是我们的测试数据。考虑以下联合 GP 分布。

$$\begin{pmatrix} f \\ f_* \end{pmatrix} \sim N\left(\begin{pmatrix} \mu \\ \mu_* \end{pmatrix}, \begin{pmatrix} K & K_* \\ K_*^T & K_{**} \end{pmatrix}\right)\tag{6.16}$$

这里，$K = \kappa(X, X)$，$K^* = \kappa(X, X^*)$ 和 $K^{**} = \kappa(X^*, X^*)$，其中 $X$ 是我们的训练数据集，$X^*$ 是我们的测试数据集，$\kappa$ 是核或协方差函数。使用高斯条件化的标准规则，后验具有以下形式。

$$p(f_*|X_*, X, f) \sim N(f_*|\mu_*, \Sigma_*)\\\mu_* = \mu(X_*) + K_*^T K^{-1}(f - \mu(X))\\\Sigma_* = K_{**} - K_*^T K^{-1} K_*\tag{6.17}$$

在代码清单 6.4 中，我们使用方程 6.18 中定义的径向基函数核作为相似性度量。我们现在准备从头实现 GP 回归（见图 6.7）！

```
1: class GPreg:
2: function kernel_func(x, z)
3: Kfn = exp{ -1/(2σ²) ||x - z||² }  ← Radial basis function kernel
4: return Kfn
5: function compute_posterior(X)
6: K = kernel_func(X_train, X_train)
7: Ks = kernel_func(X_train, X_test)
8: Kss = kernel_func(X_test, X_test)
9: μ_post = μ(X_test) + K_s^T K^{-1} (f - μ(X_train))  → Gaussian process posterior
10: Σ_post = K_ss - K_s^T K^{-1} K_s
11: return μ_post, Σ_post
```

图 6.7 高斯过程回归伪代码

代码由 kernel_func 和 compute_posterior 函数组成。kernel_func 返回径向基函数 RBF 核，它衡量两个输入 $x$ 和 $z$ 之间的相似性。在 compute_posterior 函数中，我们首先计算

用于后验均值和协方差方程的成分，然后计算并返回
后验均值和协方差，如文中推导的那样。

### 代码清单 6.4 高斯过程回归

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.spatial.distance import cdist

np.random.seed(42)

class GPReg:

    def __init__(self, X_train, y_train, X_test):

        self.L = 1.0
        self.keps = 1e-8

        self.muFn = self.mean_func(X_test)
        self.Kfn = self.kernel_func(X_test, X_test) + 1e-15*np.eye(
            np.size(X_test))

        self.X_train = X_train
        self.y_train = y_train
        self.X_test = X_test

    def mean_func(self, x):
        muFn = np.zeros(len(x)).reshape(-1,1)
        return muFn

    def kernel_func(self, x, z):
        sq_dist = cdist(x/self.L, z/self.L, 'euclidean')**2
        Kfn = 1.0 * np.exp(-sq_dist/2)
        return Kfn

    def compute_posterior(self):
        K = self.kernel_func(self.X_train, self.X_train)
        Ks = self.kernel_func(self.X_train, self.X_test)
        Kss = self.kernel_func(self.X_test, self.X_test) + self.keps*np.eye(np.size(self.X_test))
        Ki = np.linalg.inv(K)  <--- O(N_train^3)

        postMu = self.mean_func(self.X_test) + np.dot(np.transpose(Ks),
            np.dot(Ki, (self.y_train - self.mean_func(self.X_train))))
        postCov = Kss - np.dot(np.transpose(Ks), np.dot(Ki, Ks))

        self.muFn = postMu
        self.Kfn = postCov

        return None
```

```
def generate_plots(self, X, num_samples=3):
    plt.figure()
    for i in range(num_samples):
        fs = self.gauss_sample(1)
        plt.plot(X, fs, '-k')
        #plt.plot(self.X_train, self.y_train, 'xk')
    mu = self.muFn.ravel()
    S2 = np.diag(self.Kfn)
    plt.fill_between(np.concatenate([X, X[::-1]]), np.concatenate([mu - 2*np.sqrt(S2), (mu + 2*np.sqrt(S2))[::-1]]), alpha=0.2, fc='b')
    plt.show()

def gauss_sample(self, n):
    A = np.linalg.cholesky(self.Kfn)
    Z = np.random.normal(loc=0, scale=1, size=(len(self.muFn),n))
    S = np.dot(A,Z) + self.muFn
    return S

def main():
    # generate noise-less training data
    X_train = np.array([-4, -3, -2, -1, 1])
    X_train = X_train.reshape(-1,1)
    y_train = np.sin(X_train)
    # generate test data
    X_test = np.linspace(-5, 5, 50)
    X_test = X_test.reshape(-1,1)
    gp = GPreg(X_train, y_train, X_test)
    gp.generate_plots(X_test,3)
    gp.compute_posterior()
    gp.generate_plots(X_test,3)

if __name__ == "__main__":
    main()
```

图 6.8 显示了从 GP 先验（左）和在无噪声观测情况下观察到五个数据点后从 GP 后验（右）随机绘制的三个函数。阴影区域对应于均值周围两倍标准差（95% 置信区域）。我们可以看到模型完美地插值训练数据，并且预测不确定性随着远离观测数据而增加。

由于我们的算法是在输入空间的内积方面定义的，它可以通过用 k(x, x') 替换内积而提升到特征空间；这通常被称为核技巧。
