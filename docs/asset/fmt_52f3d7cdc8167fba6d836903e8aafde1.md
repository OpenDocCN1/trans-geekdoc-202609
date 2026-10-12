
```python
def convert(image):
    image = image.astype(np.float64)
    yuvimg = np.empty(image.shape)
    if False:
        yuvimg[:,:,0] = image[:,:,0]*0.5+image[:,:,1]*0.2+ image[:,:,2]*0.3
        yuvimg[:,:,1] = image[:,:,1]*0.5
        yuvimg[:,:,2] = image[:,:,1]*0.1+ image[:,:,2]*0.7
    else:
        for y in range(image.shape[0]):
            for x in range(image.shape[1]):
                rgb = image[y, x]
                yuvimg[y, x][0] = rgb[0]*0.5+rgb[1]*0.2+rgb[2]*0.3
                yuvimg[y, x][1] = rgb[1]*0.5
                yuvimg[y, x][2] = rgb[1]*0.1+rgb[2]*0.7
            
    return yuvimg.astype(np.uint8)

img = convert(image)
plt.imshow(img)
plt.show() 
```

![](img/file104.png "fig:")  

**图 5-4 处理图像的每个像素**

使用 `numpy` 函数（如 `invert()`）来转换图像颜色：

```python
img = np.invert(image)
plt.imshow(img)
plt.show() 
```

![](img/file105.png "fig:")  

**图 5-5 反转图像颜色**

`skimage` 的不同模块（如 `util`、`transform` 等）提供了用于图像不同变换的函数，例如使用 `util` 的 `random_noise()` 函数向图像添加噪声：

```python
from skimage import util
img = util.random_noise(image)
plt.imshow(img)
plt.show()
```

![](img/file106.png "fig:")  

**图 5-6 添加噪声**

可以使用 `transform` 的 `rotate()` 旋转图像：

```python
from skimage import transform
img = transform.rotate(image, 30)
plt.imshow(img)
plt.show()
```

![](img/file107.png "fig:")  

**图 5-7 旋转图像**

改变图像强度的对比度：

```python
from skimage import exposure
v_min, v_max = np.percentile(image, (18, 89.8))
img = exposure.rescale_intensity(image, in_range=(v_min, v_max))
plt.imshow(img)
plt.show()
```

![](img/file108.png "fig:")  

**图 5-8 改变对比度**

改变图像的曝光度：

```python
# gamma 和 gain 参数在 0 和 1 之间
img = exposure.adjust_gamma(image, gamma=0.4, gain=0.9)
plt.imshow(img)
plt.show()
```

![](img/file109.png "fig:")  

**图 5-9 改变曝光度**

```python
img = exposure.adjust_log(image)
plt.imshow(img)
plt.show()
```

![](img/file110.png "fig:")  

**图 5-10 对数变换**

将具有多个颜色通道的彩色图像转换为单通道灰度图像（黑白图像）：

```python
from skimage import color
img = color.rgb2gray(image)
print(img.shape)
plt.imshow(img,cmap='gray')
plt.show()
```

(403, 544)

![](img/file111.png "fig:")  

**图 5-11 彩色图像转换为灰度图像**

您还可以使用许多其他 Python 包来处理图像等数据，例如 `scipy` 的图像处理模块 `ndimage` 来处理图像，如模糊图像：

```python
from scipy import ndimage
img = ndimage.uniform_filter(image, size=(11, 11, 1))
plt.imshow(img)
plt.show()
```

![](img/file112.png "fig:")  

**图 5-12 模糊图像**

与图像数据一样，可以对文本、语音等其他数据进行各种数据增强，并可以使用各种公共数据处理包来提高数据处理的效率。

通过数据增强，数据总量可以增加数倍，这有助于减少过拟合。虽然增强后的数据与原始数据相关，但它避免了获取全新数据的成本。

## 5.1.2 归一化

与简单回归一样，绝对值过大的数据会导致神经网络的数值计算溢出，梯度下降算法会变得非常缓慢，并且不同尺度的特征对算法有不同的影响，这会导致“特征偏差”，从而使训练算法难以约束。因此，在训练神经网络之前，应对未归一化的数据进行归一化。通常对每个特征单独归一化，即对于每个特征 `x[i]`，计算该特征在训练集中的均值 `x[i]_mean` 和标准差 `x[i]_std`，然后使用均值和标准差将所有样本的该特征归一化到接近 0 的较小范围内，例如 `[0, 1]` 或 `[-0.5, 0.5]` 或 `[-1, 1]`，通常使用以下公式进行归一化：

$$\frac{x_{i} - x_{i\_mean}}{x_{i\_std}}$$

此规范化过程可以通过以下 Python 代码实现：

```python
X -= np.mean(X, axis=0) 
X /= np.std(X, axis=0)
```

如果所有特征的值大致在同一范围内，也可以对所有特征进行统一标准化，即使用训练集中所有数据的所有特征计算一个统一的均值 `x_mean` 和标准差 `x_std`，然后用这个相同的均值和标准差对所有数据特征进行归一化。例如，对于使用单字节正整数表示图像像素颜色值的图像，因为这些值都在 `[0, 255]` 范围内变化，因此可以直接将图像除以 255，将这些图像像素值转换为 `[0, 1]`，而无需专门为每个特征计算均值和方差。

需要注意的是，验证集和测试集中的样本不能单独归一化，否则这些集合中的样本与训练集中的样本不使用相同的归一化标准，因此用训练好的模型预测它们就没有意义。也就是说，在对验证集或测试集中的样本进行预测时，使用与训练集相同的归一化参数（均值和标准差）对验证或测试样本进行归一化。

## 5.1.3 特征工程

对于原始数据样本，某些特征可能与机器学习无关，且特征通常不是独立的，而是相关的。这些相互关联的原始数据特征在机器学习过程中会相互制约，使得学习算法难以收敛。

特征工程是从原始数据中发现和提取有助于机器学习的良好特征。特征工程是传统机器学习中最基础的关键问题之一。不同领域通常会使用一些特定于该领域的人工特征方法。特征工程通常包括许多具体技术，如数据预处理（如数据归一化）、数据降维、特征选择、人工特征设计和特征学习。

### 1. 数据降维与主成分分析

数据降维是将高维数据转换为低维表示。一个样本可能有大量原始特征。如果用较少的特征来表示样本，可以提高机器学习算法的效率。就像数据压缩一样，压缩后的数据保留了原始数据的固有信息，但对压缩数据的处理（如数据传输）比对原始数据的处理更高效。

主成分分析（PCA）是机器学习中一种经典的数据降维技术。它将数据表示为主轴的线性组合，可以消除数据特征的相关性，然后用少量的主轴来表示原始数据，从而降低数据的维度，即特征的数量。例如，一个 `256*256` 像素的彩色人脸图像需要 `256*256*3 = 196608` 个数值表示，即其维度为 196608，而一个人脸图像可以用 23 个主轴的线性组合来表示，可保留原始图像 97% 的信息，因此一个人脸只需要 23 个数值。

对于以下二维平面的数据点，每个数据点由 2 个坐标表示：

#### PCA 与白化

```python
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline
# Generate random sample points near the line y=2x+1
np.random.seed(1)

pts = 25
x = np.random.randn(pts,1)          # Randomly sample some x coordinates
y = x+2
y = y+ np.random.randn(pts,1)*0.2   # Give Y random noise

plt.plot(x,y,'o')
plt.xlabel('x')
plt.ylabel('y')
plt.axis('equal')
plt.show()
```

![](img/file113.png "fig:")  

**图 5-13 在直线 y=2x+1 附近随机采样的二维平面数据点**

将每个点的坐标视为一个矩阵，所有点坐标可以放入矩阵 `X` 中并显示前 3 个坐标点：

```python
X = np.stack((x.flatten(), y.flatten()), axis=-1)
print(X.shape)
print(X[:3])
```

(25, 2)  

[[ 1.62434536 3.48759979]  

 [-0.61175641 1.36366554]  

 [-0.52817175 1.28467436]]

PCA 可用于降维，使每个点仅有一个数值，而不是用 2 个数值表示。PCA 方法的第一步是将每个维度（轴）的分量中心化，即每个维度的分量减去该维度所有分量的均值：

```python
X -= np.mean(X, axis = 0) 
print(X[:3])
plt.plot(X[:,0],X[:,1],'o')
plt.axis('equal')
plt.show()
```

[[ 1.63707525 1.50798964]  

 [-0.59902653 -0.61594461]  

 [-0.51544186 -0.69493579]]

![](img/file114.png "fig:")  

**图 5-14 数据中心化，即数据每个维度（特征）的分量减去该维度所有分量的均值，使每个特征以 0 为中心点**

如果有一个由一组三维坐标点组成的矩阵 `A`，每一行代表一个坐标点的三个坐标：

$$

A = \begin{pmatrix} 1 & 3 & 2 \\ -4 & 2 & 6 \\ 2 & 6 & 4 \\ -3 & 0 & 1 \end{pmatrix}

$$

即 `A` 有 4 个样本，每个样本有 3 个特征（x, y, z 坐标）。这些样本的特征之间是否相关？`A` 的相关矩阵（协方差矩阵），`A^T A`，表示数据集不同特征之间的相关程度。

$$

A^T A = \begin{pmatrix} 1 & -4 & 2 & -3 \\ 3 & 2 & 6 & 0 \\ 2 & 6 & 4 & 1 \end{pmatrix} \begin{pmatrix} 1 & 3 & 2 \\ -4 & 2 & 6 \\ 2 & 6 & 4 \\ -3 & 0 & 1 \end{pmatrix} = \begin{pmatrix} 30 & 7 & -17 \\ 7 & 49 & 42 \\ -17 & 42 & 57 \end{pmatrix}

$$

计算代码如下：

```python
A = np.array([[1,3,2],[-4,2,6],[2,6,4],[-3,0,1]])
print(A)
print("A^TA:\n",np.dot(A.transpose(),A))
```

[[ 1 3 2]  

 [-4 2 6]  

 [ 2 6 4 ]  

 [-3 0 1]]  

A^TA:  

[[ 30 7 -17]  

 [ 7 49 42]  

 [-17 42 57]]

从协方差矩阵的元素值可以看出，x 和 y 之间的相关值为 7，y 和 z 之间的相关值为 42，表明 y 和 z 之间的相关性较大，而 x 和 y 之间的相关性较小。通常，协方差矩阵可以除以样本数量，以减少样本数量对矩阵值的影响。对于上述样本矩阵 `X`，其协方差矩阵计算如下：

```python
cov = np.dot(X.T, X) / X.shape[0] # covariance matrix
```

对协方差矩阵进行 SVD 分解可获得主成分（特征向量）`U`、奇异值（方差，特征值的平方）`S`，奇异值等价于方差，表示发散程度：

```python
U,S,V = np.linalg.svd(cov)
print(U)
print(S)
print(S[0]/(S[0]+S[1]))
```

[[-0.68302064 -0.73039907]  

 [-0.73039907 0.68302064]]  

[2.46815362 0.01168714]  

0.995287139793862

`U` 的每一列代表一个主轴，主轴代表数据变化的主要方向（主轴方向），如图 5-15 所示：

```python
plt.plot(X[:,0],X[:,1],'o')
plt.plot([0,U[0,0]], [0,U[1,0]])
plt.plot([0,U[0,1]], [0,U[1,1]])
plt.axis('equal')
plt.show()
```

![](img/file115.png "fig:")  

**图 5-15 协方差矩阵的 SVD 分解，可获得主成分（特征值）和主成分方向（特征向量）**

`S[0]` 和 `S[1]` 表示数据在主轴方向上的占比，可以看出数据在第一主轴方向上的变化占比较大。通过将数据投影到由主轴 `U` 定义的轴上，数据可以表示为主轴的分量。

```python
Xrot = np.dot(X, U)
print(Xrot[:5])
```

[[-2.21959042 -0.16573019]  

 [ 0.85903285 0.01682553]  

 [0.85963789 -0.09817723]  

 [ 1.53210054 0.01886974]  

 [-1.32424593 0.03607588]]

显示这些主轴分量在主轴上形成的坐标点：

```python
plt.plot(Xrot[:,0],Xrot[:,1],'o')
plt.axis('equal')
plt.show()
```

![](img/file116.png)

**图 5-16 旋转数据使主轴与坐标轴对齐**

将数据转换为主成分的分量表示可以消除新特征之间的相关性，从其协方差矩阵可以看出，代表不同特征的非对角线值变为 0。

```python
print(np.dot(Xrot.transpose(),Xrot))
```

[[6.17038405e+01 9.38138456e-15]  

 [9.38138456e-15 2.92178571e-01]]

用第一主轴的坐标来表示这些样本，数据损失近乎 `(1-0.995287139793862)*100% = 0.472%`，几乎可以忽略不计。这种将数据样本表示为少数主轴的线性组合的方式称为**数据降维**。对于本例，样本数据的维度可以从特征数 2 降低到特征数 1，达到减少样本特征数量的目的。

```python
Xrot_reduced = np.dot(X, U[:,:1]) # Xrot_reduced become a [N x 1] array
print(Xrot_reduced[:3])
plt.plot(Xrot_reduced[:],[0]*pts,'o')
plt.axis('equal')
plt.show()
```

[[-2.21959042]  

 [ 0.85903285]  

 [0.85963789]]

![](img/file117.png "fig:")  

**图 5-17 数据降维：将数据样本表示为少数主轴的线性组合**

投影并降维后的数据可以反投影到原始数据的主轴上。

```python
X_temp = np.c_[Xrot_reduced, np.zeros(pts) ]
reProjX = np.dot(X_temp, U.transpose())  
plt.plot(reProjX[:,0],reProjX[:,1],'o')
plt.axis('equal')
plt.show()
```

![](img/file118.png "fig:")  

**图 5-18 投影并降维后的数据反投影到原始数据的主轴上，保留了原始数据的主要特征**

可以看出，降维后的数据仍保留了原始数据的主要信息。

#### 2. 白化

数据样本可能有多个特征，这些特征的方差可能差异很大，即不同特征的发散程度不同，导致不同特征对机器学习算法的影响不同。特征之间往往存在相关性，具有相关性的不同特征会对机器学习产生相互制约的影响。这就像一个人被拉向不同方向而不知所措。

白化操作是指降低样本特征的相关性，并使这些特征具有相同的方差。将特征除以其标准差可以达到使特征具有相同方差的目的，而 PCA 投影可以消除特征间的相关性。因此，白化通常是这两种技术的结合，即先进行 PCA 特征投影以消除特征相关性，再将每个特征除以其特征方差。结合 PCA 的白化操作称为 PCA 白化。
