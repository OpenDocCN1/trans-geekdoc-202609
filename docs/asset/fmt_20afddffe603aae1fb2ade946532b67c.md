
```python
import numpy as np
from scipy.sparse import coo_matrix
import matplotlib.pyplot as plt

np.random.seed(42)

class HMM():
    def __init__(self, d=3, k=2, n=10000):
        self.d = d
        self.k = k
        self.n = n

        self.A = np.zeros((k,k))
        self.E = np.zeros((k,d))
        self.s = np.zeros(k)

        self.x = np.zeros(self.n)

    def normalize_mat(self, X, dim=1):
        z = np.sum(X, axis=dim)
        Xnorm = X/z.reshape(-1,1)
        return Xnorm

    def normalize_vec(self, v):
        z = sum(v)
        u = v / z
        return u, z

    def init_hmm(self):

        #initialize matrices at random
        self.A = self.normalize_mat(np.random.rand(self.k,self.k))
        self.E = self.normalize_mat(np.random.rand(self.k,self.d))
        self.s, _ = self.normalize_vec(np.random.rand(self.k))

        #generate markov observations
        z = np.random.choice(self.k, size=1, p=self.s)
        self.x[0] = np.random.choice(self.d, size=1, p=self.E[z,:].ravel())
        for i in range(1, self.n):
            z = np.random.choice(self.k, size=1, p=self.A[z,:].ravel())
            self.x[i] = np.random.choice(self.d, size=1,
                p=self.E[z,:].ravel())
        #end for

    def forward_backward(self):

        #construct sparse matrix X of emission indicators
        data = np.ones(self.n)
        row = self.x
        col = np.arange(self.n)
        X = coo_matrix((data, (row, col)), shape=(self.d, self.n))

        M = self.E * X

        At = np.transpose(self.A)
        c = np.zeros(self.n)  #normalization constants
        alpha = np.zeros((self.k, self.n))  #alpha = p(z_t = j | x_{1:T})
        alpha[:,0], c[0] = self.normalize_vec(self.s * M[:,0])
        for t in range(1, self.n):
            alpha[:,t], c[t] = self.normalize_vec(np
                .dot(At, alpha[:,t-1]) * M[:,t])
        #end for

        beta = np.ones((self.k, self.n))
        for t in range(self.n-2, 0, -1):
            beta[:,t] = np.dot(self.A, beta[:,t+1] * M[:,t+1])/c[t+1]
        #end for
        gamma = alpha * beta

        return gamma, alpha, beta, c

    def viterbi(self):

        #construct sparse matrix X of emission indicators
        data = np.ones(self.n)
        row = self.x
        col = np.arange(self.n)
        X = coo_matrix((data, (row, col)), shape=(self.d, self.n))

        #log scale for numerical stability
        s = np.log(self.s)
        A = np.log(self.A)
        M = np.log(self.E * X)

        Z = np.zeros((self.k, self.n))
        Z[:,0] = np.arange(self.k)
        v = s + M[:,0]
        for t in range(1, self.n):
            Av = A + v.reshape(-1,1)
            v = np.max(Av, axis=0)
            idx = np.argmax(Av, axis=0)
            v = v.reshape(-1,1) + M[:,t].reshape(-1,1)
            Z = Z[idx,:]
            Z[:,t] = np.arange(self.k)
        #end for
        llh = np.max(v)
        idx = np.argmax(v)
        z = Z[idx,:]

        return z, llh


if __name__ == "__main__":

    hmm = HMM()
    hmm.init_hmm()

    gamma, alpha, beta, c = hmm.forward_backward()
    z, llh = hmm.viterbi()
```

数据维度；隐状态维度；数据点数量；发射矩阵；转移矩阵；初始状态向量；发射观测值

在训练集中建立界定清晰的簇，并提升分类性能。单侧选择（OSS）方法从多数类 `E` 中选取一个有代表性的子集，并将其与所有少数类样本 `S_min` 组成的集合合并，构成 `N = {E ∪ S_min}`。进一步处理缩减后的集合 `N`，以移除所有多数类 Tomek 链接。让我们使用 `imbalanced-learn` 库来实验 Tomek 链接欠采样。

## 清单 7.3 Tomek 链接算法

```python
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

from sklearn.model_selection import train_test_split
from sklearn.utils import shuffle
from imblearn.under_sampling import TomekLinks

rng = np.random.RandomState(42)

def main():
    n_samples_1 = 500
    n_samples_2 = 50
    X_syn = np.r_[1.5 * rng.randn(n_samples_1, 2), 0.5 * rng.randn(n_samples_2, 2) + [2, 2]]
    y_syn = np.array([0] * (n_samples_1) + [1] * (n_samples_2))
    X_syn, y_syn = shuffle(X_syn, y_syn)
    X_syn_train, X_syn_test, y_syn_train, y_syn_test = train_test_split(X_syn, y_syn)

    tl = TomekLinks(sampling_strategy='auto')
    X_resampled, y_resampled = tl.fit_resample(X_syn, y_syn)
    idx_resampled = tl.sample_indices_
    idx_samples_removed = np.setdiff1d(np.arange(X_syn.shape[0]), idx_resampled)

    fig = plt.figure()
    ax = fig.add_subplot(1, 1, 1)

    idx_class_0 = y_resampled == 0
    plt.scatter(X_resampled[idx_class_0, 0], X_resampled[idx_class_0, 1], alpha=.8, label='Class #0')
    plt.scatter(X_resampled[-idx_class_0, 0], X_resampled[-idx_class_0, 1], alpha=.8, label='Class #1')
    plt.scatter(X_syn[idx_samples_removed, 0], X_syn[idx_samples_removed, 1], alpha=.8, label='Removed samples')
    plt.title('Undersampling: Tomek links')
    plt.legend()
    plt.show()

if __name__ == "__main__":
    main()
```

图 7.6 显示了由此产生的输出。因此，我们可以看到，移除不想要的类重叠可以增强决策边界的稳健性，并提高分类精度。

![](img/325742126d3ff007c6c385f4ffb5c3be_156_0.png)

**图 7.6** Tomek 链接算法，展示了分类边界处被移除的若干样本

### 7.2.2 过采样策略

过采样方法将数据追加到原始数据集的少数类中，如图 7.7 所示。*随机过采样*只是将数据点均匀随机地添加到少数类中。*合成少数类过采样技术*（SMOTE）通过寻找特征空间中的 *K* 个最近邻，并沿着连接任意 *K* 个少数类最近邻的线段生成新的数据点，从而产生合成样本。合成样本的生成方式如下：取当前考虑的特征向量（样本）与其最近邻之间的差值，将该差值乘以一个 0 到 1 之间的随机数，再加到当前考虑的特征向量上，从而用一个新的数据点扩充数据集。

![](img/325742126d3ff007c6c385f4ffb5c3be_156_1.png)

**图 7.7** 过采样策略

自适应合成采样（ADASYN）根据少数类样本的学习难易程度，对不同样本使用加权分布：越难学习的少数类样本，就会生成越多的合成数据。因此，ADASYN 方法在两个方面改善了对不平衡数据集的学习：减少类别不平衡引入的偏差，并自适应地将分类决策边界向困难样本偏移。让我们使用 `imbalanced-learn` 库来实验 SMOTE 过采样。

## 清单 7.4 SMOTE 算法

```python
import seaborn as sns
import matplotlib.pyplot as plt

from sklearn.datasets import make_classification
from sklearn.decomposition import PCA

from imblearn.over_sampling import SMOTE

def plot_resampling(ax, X, y, title):
    c0 = ax.scatter(X[y == 0, 0], X[y == 0, 1], label="Class #0", alpha=0.5)
    c1 = ax.scatter(X[y == 1, 0], X[y == 1, 1], label="Class #1", alpha=0.5)
    ax.set_title(title)
    ax.spines['top'].set_visible(False)
    ax.spines['right'].set_visible(False)
    ax.get_xaxis().tick_bottom()
    ax.get_yaxis().tick_left()
    ax.spines['left'].set_position(('outward', 10))
    ax.spines['bottom'].set_position(('outward', 10))
    ax.set_xlim([-6, 8])
    ax.set_ylim([-6, 6])

    return c0, c1

def main():
    X, y = make_classification(n_classes=2, class_sep=2, weights=[0.3, 0.7],
                               n_informative=3, n_redundant=1, flip_y=0,
                               n_features=20, n_clusters_per_class=1,
                               n_samples=80,
                               random_state=10)  # Generates the dataset

    pca = PCA(n_components=2)
    X_vis = pca.fit_transform(X)  # Fits PCA for visualization

    method = SMOTE()
    X_res, y_res = method.fit_resample(X, y)  # Applies regular SMOTE
    X_res_vis = pca.transform(X_res)

    f, (ax1, ax2) = plt.subplots(1, 2)  # Generates plots
    c0, c1 = plot_resampling(ax1, X_vis, y, 'Original')
    plot_resampling(ax2, X_res_vis, y_res, 'SMOTE')
    ax1.legend((c0, c1), ('Class #0', 'Class #1'))
    plt.tight_layout()
```

```python
plt.show()

if __name__ == "__main__":
    main()
```

在清单7.4中，我们生成了一个包含两个不平衡类别的高维数据集。我们应用常规的SMOTE过采样算法，并拟合一个双成分PCA，以在二维空间中可视化数据。图7.8展示了最终输出。

![](img/325742126d3ff007c6c385f4ffb5c3be_158_0.png)

图7.8 SMOTE算法

因此，我们可以看到SMOTE用合成数据密集地填充了少数类。可以将过采样和欠采样技术结合为一种混合策略。常见的例子包括SMOTE与Tomek链接，或SMOTE与编辑最近邻（ENN）。在类别不平衡数据集上学习的其他方法包括对训练实例加权、为正例和负例引入不同的误分类成本，以及自助采样法。在接下来的章节中，我们将聚焦于监督式机器学习中一个非常重要的原理，它可以减少所需训练样本的数量：主动学习。

#### 7.3 主动学习

主动学习背后的关键思想是，如果允许机器学习算法选择其学习所用的数据，那么它可以用更少的训练标签实现更高的准确率。在许多现代机器学习问题中，主动学习具有充分的动机：未标注数据可能非常丰富，但获取标签的成本很高。主动学习有时被称为查询学习或最优实验设计，因为主动学习者以未标注数据实例的形式提出查询，并由标注专家进行标注。通过这种方式，主动学习者力求使用尽可能少的标注实例来实现高准确率。相关综述可参见Burr Settles所著的《主动学习文献综述》（威斯康星大学麦迪逊分校，计算机科学系，2009年）。

我们关注基于池的采样，该方法假设存在一个较小的标注数据集`L`和一个较大的未标注数据池`U`。根据信息量度量，从池中选择性地抽取查询。基于池的方法对整个未标注数据集合进行排序，以选择最佳查询。因此，对于非常大的数据集，基于流的采样可能更合适，这种采样方式顺序扫描数据并逐个评估查询决策。图7.9展示了一个基于池的主动学习示例，该示例使用逻辑回归（LR）对包含两个平衡类别的合成数据集进行二分类。

![](img/325742126d3ff007c6c385f4ffb5c3be_159_0.png)

图7.9 用于逻辑回归的主动学习

在左侧，我们可以看到逻辑回归决策边界，它是在随机子采样的30个标签上训练的结果，在留出数据上达到了90%的分类准确率。在右侧，我们可以看到逻辑回归决策边界，它是在基于熵的不确定性采样所选择的30个查询上训练的结果。不确定性采样在留出集上达到了更高的分类准确率，为92.5%。

##### 7.3.1 查询策略
