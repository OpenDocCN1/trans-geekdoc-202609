
根据梯度计算公式，很容易编写损失函数关于 `W` 的梯度计算代码。在下面的代码中，假设 `X` 代表多样本的数据特征矩阵，`y` 代表目标值向量，`reg` 是正则化参数 `λ`，`loss_softmax()` 和 `gradient_softmax()` 分别计算损失函数的损失和关于 `W` 的梯度：

```python
# def loss_gradient(W,X,y,lambda_):
def gradient_softmax(W,X,y,reg):
    m = len(X)
    Z = np.dot(X,W)
    
    I_i = np.zeros_like(Z)
    I_i[np.arange(len(Z)),y] = 1
    F = softmax(Z)
    # F = np.exp(Z) / np.exp(Z).sum(axis=-1,keepdims=True)
    grad = (1 / m) * np.dot(X.T, F - I_i)      # Z.shape[0]
    grad = grad + 2*reg*W
    return grad

def loss_softmax(W,X,y,reg):
    m = len(X)
    Z = np.dot(X,W) 
    Z_i_y_i = Z[np.arange(len(Z)),y]
    negtive_log_prob = - Z_i_y_i + np.log(np.sum(np.exp(Z),axis=-1))
    loss = np.mean(negtive_log_prob) + reg*np.sum(W*W)
    return loss  
```

使用以下数据测试函数：

```python
X = np.array([[2,3],[4,5]])        # 每行对应一个样本，每个样本 2 个特征
y = np.array([2,1])                # 类别数为 3
W = np.array([[0.1,0.2,0.3],[0.4,0.2,0.8]])    # 2x3 矩阵

reg = 0.2

print(gradient_softmax(W,X,y,reg))
print(loss_softmax(W,X,y,reg))
```

```
[[ 0.30213245 -1.75779321  1.69566076]
 [ 0.5254108  -2.19194012  2.22652932]]
2.086304963628266
```

如果每个样本的目标值用独热向量表示，且 `y` 代表由多样本目标值组成的矩阵，则下面的 `loss_softmax_onehot()` 和 `gradient_softmax_onehot()` 计算损失函数的损失和关于 `W` 的梯度：

```python
def gradient_softmax_onehot(W,X,y,reg):
    m = len(X)               # 样本数
    nC = W.shape[1]          # 类别数
    # y_one_hot = np.eye(nC)[y[:,0]]
    y_one_hot = y
    
    # y_mat = oneHotIt(y)      # 接下来将整数类别编码转换为独热表示
    Z = np.dot(X,W)           # Z 是加权和
    F = softmax(Z)            # F 是概率矩阵
    grad = (1 / m) * np.dot(X.T, (F - y_one_hot)) + 2*reg*W  # 计算该损失的梯度
    return grad  # 原文为 grade，推测为笔误已修正

def loss_softmax_onehot(W,X,y,reg):
    m = len(X) # 首先获取训练样本数
    nC = W.shape[1]
    # y_one_hot = np.eye(nC)[y[:,0]]
    y_one_hot = y
    
    # y_mat = oneHotIt(y)          # 将整数类别编码转换为独热向量形式
    Z = np.dot(X,W)               # Z 是加权和
    F = softmax(Z)                # F 是概率矩阵
    loss = (-1 / m) * np.sum(y_one_hot * np.log(F)) + (reg)*np.sum(W*W)
    return loss
```

```python
X = np.array([[2,3],[4,5]])          # 每行对应一个样本，每个样本 2 个特征
y = np.array([[0,0,1],[0,1,0]])      # 类别数为 3
W = np.array([[0.1,0.2,0.3],[0.4,0.2,0.8]])  # 2x3 矩阵

reg = 0.2
print(gradient_softmax_onehot(W,X,y,reg))
print(loss_softmax_onehot(W,X,y,reg))
```

```
[[ 0.30213245 -1.75779321  1.69566076]
 [ 0.5254108  -2.19194012  2.22652932]]
2.0863049636282662
```

### 3.6.7 Softmax 回归的梯度下降法实现

基于此的梯度下降算法代码如下：

```python
def gradient_descent_softmax(w,X, y, reg=0., alpha=0.01, iterations=100, gamma=0.8, epsilon=1e-8):
    X = np.hstack((np.ones((X.shape[0], 1), dtype=X.dtype), X))  # 增加一列特征 1 
    v = np.zeros_like(w)
    # losses = []
    w_history = [] 
    for i in range(0, iterations):
        gradient = gradient_softmax(w, X, y, reg)
        if np.max(np.abs(gradient)) < epsilon:
            print("gradient is small enough!")
            print("iterated num is :", i)
            break            
        
        w = w - (alpha * gradient)
        # v = gamma*v + alpha* gradient
        # w = w - v
        # losses.append(loss)
        w_history.append(w)
    return w_history
```

对于一组样本 (`X`,`y`)，以下辅助函数计算历史纪录 `w_history` 中每个模型参数对应的模型损失：

### 3.6.8 螺旋数据集的 Softmax 回归

在之前的三类螺旋数据集上训练 Softmax 回归模型：

```python
def compute_loss_history(w_history, X, y, reg=0., OneHot=False):
    loss_history = []
    X = np.hstack((np.ones((X.shape[0], 1), dtype=X.dtype), X))
    if OneHot:
        for w in w_history:
            loss_history.append(loss_softmax_onthot(w, X, y, reg))
    else:
        for w in w_history:
            loss_history.append(loss_softmax(w, X, y, reg))
    return loss_history
```

```python
X_spiral, y_spiral = gen_spiral_dataset()
X = X_spiral
y = y_spiral

alpha = 1e-0
iterations = 200
reg = 1e-3

w = np.zeros([X.shape[1] + 1, len(np.unique(y))])
w_history = gradient_descent_softmax(w, X, y, reg, alpha, iterations)
w = w_history[-1]
print("w: ", w)
loss_history = compute_loss_history(w_history, X, y, reg)
print(loss_history[:-1:len(loss_history)//10])
plt.plot(loss_history, color='r')
```

```
w: [[-0.05432759  0.00909428  0.04523331]
 [ 1.33458061  1.00350822 -2.33808883]
 [-2.34741204  2.66497338 -0.31756134]]
[1.0676120053842029, 0.8282060256848282, 0.7842866954902825, 0.7712475770990912, 0.7664708448591956, 0.7645211840017035, 0.7636739840781024, 0.7632912248183761, 0.7631138695802607, 0.763030293277599]
```

![](img/file78.png)

**图 3-43 训练损失曲线**

以下函数可计算训练好的模型在一批数据 (`X`, `y`) 上的预测准确率：

```python
def getAccuracy(w, X, y):
    X = np.hstack((np.ones((X.shape[0], 1), dtype=X.dtype), X))
    probs = softmax(np.dot(X, w))
    predicts = np.argmax(probs, axis=1)
    accuracy = sum(predicts == y) / (float(len(y)))
    return accuracy
```

使用 `getAccuracy()` 计算刚才数据集上训练好的 Softmax 模型的预测准确率。

```python
getAccuracy(w, X_spiral, y_spiral)
```

```
0.5366666666666666
```

以下代码绘制该问题 Softmax 模型的分类边界：

```python
# plot the resulting classifier
h = 0.02
x_min, x_max = X[:, 0].min() - 1, X[:, 0].max() + 1
y_min, y_max = X[:, 1].min() - 1, X[:, 1].max() + 1
xx, yy = np.meshgrid(np.arange(x_min, x_max, h),
                     np.arange(y_min, y_max, h))

Z = np.dot(np.c_[np.ones(xx.size), xx.ravel(), yy.ravel()], w)
Z = np.argmax(Z, axis=1)
Z = Z.reshape(xx.shape)
fig = plt.figure()
plt.contourf(xx, yy, Z, cmap=plt.cm.Spectral, alpha=0.3)
plt.scatter(X[:, 0], X[:, 1], c=y, s=40, cmap=plt.cm.Spectral)
plt.xlim(xx.min(), xx.max())
plt.ylim(yy.min(), yy.max())
# fig.savefig('spiral_linear.png')
```

```
(-1.908218802050246, 1.9517811979497575)
```

![](img/file79.png)

**图 3-44 三类数据点集的分类**

可以看出，Softmax 回归本质上仍是一个线性函数模型，图中的分割线均为直线。难以对数据进行非线性分割。模型的准确率为 `0.5366666666666666`。

## 3.7 批量梯度下降与随机梯度下降

### 3.7.1 MNIST 手写数字集

MNIST 手写数字训练集是一些手写数字的图像，每张图像都是一个手写数字。样本数据集中有 0,1,...,9 这 10 个数字的图像。所以这是一个 10 分类问题。

以下代码读取 MNIST 手写数字训练集：

```python
import pickle, gzip, urllib.request, json
import numpy as np
import os.path

if not os.path.isfile("mnist.pkl.gz"):
    # Load the dataset
    urllib.request.urlretrieve("http://deeplearning.net/data/mnist/mnist.pkl.gz", "mnist.pkl.gz")

with gzip.open('mnist.pkl.gz', 'rb') as f:
    train_set, valid_set, test_set = pickle.load(f, encoding='latin1')

train_X, train_y = train_set
valid_X, valid_y = valid_set
test_X, test_y = test_set  # Fixed: was valid_set in original
print(train_X.shape, train_y.shape)
print(valid_X.shape, valid_y.shape)
print(test_X.shape, test_y.shape)
print(train_X.dtype, train_y.dtype)
print(train_X[9][300], train_y[9])
print(np.min(train_y), np.max(train_y))
```

```
(50000, 784) (50000,)
(10000, 784) (10000,)
(10000, 784) (10000,)
float32 int64
0.98828125 4
0 9
```

训练集有 50,000 个样本，验证集和测试集各有 10,000 个样本。图像的每个像素值都是 float 类型的实数，取值范围是 `[0, 1]` 之间的实数，表示每个像素的灰度强度，标签值表示图像对应的数字分类，用 0, 1, 2, ..., 9 表示。

以下代码可视化其中一张图像：

```python
import matplotlib.pyplot as plt
%matplotlib inline
digit = train_X[9].reshape(28, 28)
plt.subplot(1, 2, 1)
plt.imshow(digit)
plt.colorbar()
plt.subplot(1, 2, 2)
plt.imshow(digit, cmap='gray')
plt.colorbar()
plt.show()
```

![](img/file80.png "fig:")

**图 3-44 来自 Mnist 数据集的手写数字图像**

继续输出该样本中的少量像素值（数据特征）。

```python
print(train_X.shape)
print(train_X[9][200:250])
```

```
(50000, 784)
[0. 0. 0. 0. 0. 0.
 0. 0. 0. 0. 0. 0.
 0. 0. 0. 0. 0.75 0.984375
 0.73046875 0. 0. 0. 0. 0.
 0. 0. 0. 0. 0. 0.
 0. 0. 0. 0. 0. 0.
 0.2421875 0.72265625 0.0703125 0. 0. 0.
 0. 0.34765625 0.921875 0.84765625 0.18359375 0.
 0. 0.]
```

### 3.7.2 使用部分训练样本训练逻辑回归

训练集中的样本数量达到 50,000 个。使用整个训练集的样本进行训练，每次计算需要大量的资源和时间。为了提高训练效率，可以取出部分数据，例如使用 `batch=500` 个样本进行训练：
