

# 198 ■ 机器学习简要介绍

```python
import numpy as np
import matplotlib.pyplot as plt
import tensorflow as tf
from sklearn.decomposition import PCA
import skimage.util

# 加载数据
(x, train, y, test) = tf.keras.datasets.mnist.load_data()

# 将数据限制为数字子集并显示示例
k = 25
data, label = train[k], y[np.random.choice(train.shape[0], k)]
montage = skimage.util.montage(data)
plt.imshow(montage, cmap='Gray')
ax = plt.figure()
ax.get_axes()[0].set_ticks([])
ax.get_axes()[0].set_yticks([])

# 将图像重塑为数组
train = np.reshape(data, (data.shape[0], 
    data.shape[1]*data.shape[2]))

# 初始化主成分分析
ncomp = 3
pca = PCA(n_components=ncomp)
subspace = pca.transform(train)

# 找到主成分并将数据转换到此
# 显示数据点
colors = [(1,0,0), (0,1,0), (0,0,1), (1,1,0), (0,1,1)]
fig = plt.figure()
if ncomp == 2:
    for i in range(0,k):
        plt.scatter(X[data.label == i], Y[data.label == i],
                    facecolor='none', edgecolors=colors[i],
                    s=10)
else:
    ax = plt.figure(projection='3d')
    for i in range(0,k):
        ax.scatter(X[data.label == i], Y[data.label == i], Z[data.label == i],
                    facecolors='none', edgecolors=colors[i],
                    s=10)
plt.show()

# 重构示例
rec = pca.inverse_transform(subspace[choice])
rec_digits = rec.reshape(data.shape[1], data.shape[2])
montage = skimage.util.montage(rec_digits)
plt.imshow(montage, cmap='Gray')
ax = plt.figure()
ax.get_axes()[0].set_ticks([])
ax.get_axes()[0].set_yticks([])
```

列表 7.1：使用 Python 进行 PCA 数字分类。对于 MATLAB，请访问 https://github.com/ACFaul/Dimensionality-Reduction-Matlab。

![](img/c6c76bf52016db7e78a5e30d4766ef81_227_0.png)

(a) 原图。

(b) 使用两个主成分的重构。

(c) 使用三个主成分的重构。

![](img/c6c76bf52016db7e78a5e30d4766ef81_227_1.png)

(d) 两个主成分跨子空间中的样本位置。

(e) 三个主成分跨子空间中的样本位置。

图 7.4：四个数字的 PCA。

而其在主子空间上的投影由分解的前 $K$ 项给出

```
$$\sum_{d=1}^K(\mathbf{v}_n^T \mathbf{w}_d)\mathbf{w}_d.$$
```

因此，样本与其投影之间的平方距离是分解中剩余 $D - K$ 项的长度：

```
$|\sum_{d=K+1}^D(\mathbf{v}_n^T \mathbf{w}_d)\|^2 = \left(\sum_{d=K+1}^D(\mathbf{v}_n^T \mathbf{w}_d)\right)^T(\sum_{d=K+1}^D(\mathbf{v}_n^T \mathbf{w}_d))$
```

其中 $\mathbf{w}_1, \dots, \mathbf{w}_D$ 是正交的。

对所有样本求和并除以 $N$ 得到将表示限制在主子空间时，样本移动的平均平方距离：

```
\sum_{n=1}^N \sum_{d=K+1}^D (v_n^T w_d)^2 = \sum_{d=K+1}^D w_d^2 \left( \frac{1}{N} \sum_{n=1}^N v_n^T v_n \right)
= \sum_{d=K+1}^D w_d^T (S + \mu\mu^T) w_d
\= \sum_{d=K+1}^D \lambda_d d + \sum_{d=K+1}^D (\mu^T w_d)^2
```

这里我们使用公式 (2.10) 作为协方差矩阵的另一种计算方法。第一部分是 $\Sigma$ 的 $D - K$ 个最小特征值的和，而第二部分是均值与其投影之间的平方距离。当更多的特征向量作为主成分时，样本与其投影之间的平均平方距离变得越小。这意味着重构变得更加准确。我们将在第 8.8 节介绍主成分回归时再次讨论这一点。

$\Sigma$ 的特征值和特征向量可以用于数据的白化（whitening）或球化（sphering）技术。这会将数据转换到一个不同的特征空间，在该空间中样本的均值为零且协方差矩阵为单位矩阵。如果特征的测量量级不同或变异性很大，这可能是必要的。然而，在此类变换之后，主成分分析以及任何依赖于协方差矩阵不同特征向量的技术将不再适用。白化后，变换后的 $v_n$ 值为：

```
v_n = \Lambda^{-1/2}W^T(x_n - \mu)
```

其中 $W$ 是由特征向量 $w_d$ 形成的正交矩阵，$\Lambda^{-1/2}$ 是对角线上有 $\lambda_d$ 的矩阵。如果 $\Sigma$ 无零，则这是良定义的，在样本不同且 $N > D$ 时如此。另一方面，变换后数据的协方差矩阵为：

```
\sum_{n=1}^N v_n v_n^T = \sum_{n=1}^N \Lambda^{-1/2}W^T(x_n - \mu)(x_n - \mu)^T W\Lambda^{-1/2}
```

这一切依赖于寻找特征值和特征向量的稳定高效的方法。Faul (2016) 描述了一些示例。保持这些特性是重要的。

