
```python
X = np.array([[1.,2.],[3.,4.],[5.,6.]])  # 每行对应一个样本

Z2 = forward_propagation(X, parameters)
print(Z2)
```

```
[[-1.36253581e-04 4.87491807e-04 -2.47960226e-05]
     [-1.64985210e-04 1.01574088e-03 -5.99877659e-05]
     [-1.96135525e-04 1.54048069e-03 -9.36558871e-05]]
```

前向计算函数输出属于每个类别的得分 `Z`，得分可以通过 `softmax()` 函数转换为属于每个类别的概率，然后结合真实目标值计算多分类交叉熵损失。函数 `softmax_cross_entropy()` 和函数 `softmax_cross_entropy_reg()` 根据输出得分值 `Z` 和真实值 `y` 计算交叉熵损失，其中包含正则项损失（`reg` 为正则项系数）。

```python
def softmax(Z):
    exp_Z = np.exp(Z-np.max(Z,axis=1,keepdims=True))
    return exp_Z/np.sum(exp_Z,axis=1,keepdims=True)

def softmax_cross_entropy(Z, y, onehot=False):
    m = len(Z)
    F = softmax(Z)
    if onehot:
        loss = -np.sum(y*np.log(F))/m
    else:
        y.flatten()
        log_Fy = -np.log(F[range(m),y])        
        loss = np.sum(log_Fy) / m
    return loss

def softmax_cross_entropy_reg(Z, Y, parameters,onehot=False,reg=1e-3):
    W1 = parameters[0]  
    W2 = parameters[2]
    L  = softmax_cross_entropy(Z,y,onehot)+ reg*(np.sum(W1**2)+np.sum(W2**2))    
    assert(isinstance(L, float))    
    return L
```

```python
y = np.array([2,0,1])             # 每行对应一个样本
softmax_crossentropy_loss(Z2,y,parameters)
```

```
1.098427770814438
```

通常希望神经网络能通过输入一组数据 `X` 和对应的目标值 `y` 来计算损失函数值。因此，将前向计算和单独的交叉熵损失计算函数结合起来：

```python
def compute_loss_reg(f,loss,X, Y, parameters,reg=1e-3):
    Z2 = f(X,parameters)
    return loss(Z2,y,parameters,reg)
```

测试此函数：

```
reg = 1e-3
compute_loss_reg(forward_propagation, softmax_cross_entropy_reg, X, y, parameters, reg)
```

```
1.098427770814438
```

定义一个返回计算出的损失函数对象的函数 `f()`，并将其和模型参数传递给第 2.4 节中的通用数值梯度计算函数，以计算神经网络的数值梯度。

```
import util

def f():
    return compute_loss_reg(forward_propagation,
                            softmax_cross_entropy_reg, X, y, parameters, reg)

num_grads = util.numerical_gradient(f, parameters)
print(num_grads[0])
print(num_grads[3])
```

```
[[ 0.00956814 -0.00773283  0.00375128  0.00506506]
 [ 0.00950714 -0.00774762  0.00379433  0.0050036 ]]
[[-0.00014298  0.00025054 -0.00010756]]
```

现在我们可以修改之前的梯度下降法来训练神经网络模型：

```
def max_abs(grads):
    return max([np.max(np.abs(grad)) for grad in grads])

def gradient_descent_ANN(f, X, y, parameters, reg=0., alpha=0.01,
                         iterations=100, gamma=0.8, epsilon=1e-8):
    losses = []
    for i in range(0, iterations):
        loss = f()
        grads = util.numerical_gradient(f, parameters)
        if max_abs(grads) < epsilon:
            print("gradient is small enough!")
            print("iterated num is :", i)
            break
        for param, grad in zip(parameters, grads):
            param -= alpha * grad

        losses.append(loss)
    return parameters, losses
```

现在再次测试之前的螺旋数据集：

```
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline

np.random.seed(100)

def gen_spiral_dataset(N=100, D=2, K=3):
    X = np.zeros((N*K, D))  # data matrix (each row = single example)
    y = np.zeros(N*K, dtype='uint8')  # class labels
    for j in range(K):
        ix = range(N*j, N*(j+1))
        r = np.linspace(0.0, 1, N)  # radius
        t = np.linspace(j*4, (j+1)*4, N) + np.random.randn(N)*0.2  # theta
        X[ix] = np.c_[r*np.sin(t), r*np.cos(t)]
        y[ix] = j
    return X, y

N = 100  # number of points per class
D = 2    # dimensionality
K = 3    # number of classes

X_spiral, y_spiral = gen_spiral_dataset()
# lets visualize the data:
plt.scatter(X_spiral[:, 0], X_spiral[:, 1], c=y_spiral, s=40, cmap=plt.cm.Spectral)
plt.show()
```

![](img/file92.png)

```
X = X_spiral
y = y_spiral
n_x, n_h, n_o = 2, 5, 3
parameters = initialize_parameters(n_x, n_h, n_o)
alpha = 1e-0
iterations = 1000
lambda_ = 1e-3
parameters, losses = gradient_descent_ANN(f, X, y, parameters, lambda_, alpha, iterations)
for param in parameters:
    print(param)
print(losses[:-1:len(losses)//10])
plt.plot(losses, color='r')
```

```
W1 [[ 3.38138518  0.61426967 -4.03084148  4.58725647 -3.51525488]
     [ 1.71779295  4.22070297 -0.02482012 -2.94531953 -1.70138925]]
b1 [[-0.22738705  2.46255351 -1.6012184   0.13971558  1.93803839]]
W2 [[ 3.02107406 -0.56140685 -2.45577033]
     [-3.6239263   1.24139541  2.38094385]
     [ 0.1104459  -2.84775015  2.73785532]
     [ 0.32970362 -3.41827375  3.08718502]
     [ 2.15366321 -3.60902121  1.45391142]]
b2 [[ 2.05837167 -0.0169156  -2.04145607]]
[0.3952037360037423, 0.3830253864421071, 0.37822677209963196, 0.3757042519269851]
```

![](img/file93.png)

**图 4-22. 三分类神经网络在螺旋数据集上的损失曲线**

以下函数通过将预测结果与目标值比较，计算模型在样本集 (`X`, `y`) 上的预测准确率：

```
def getAccuracy(X, y, parameters):
    predicts = forward_propagation(X, parameters)
    predicts = np.argmax(predicts, axis=1)
    accuracy = sum(predicts == y) / (float(len(y)))
    return accuracy
```

```
getAccuracy(X, y, parameters)
```

```
0.9433333333333334
```

模型在训练集上的预测准确率达到了 0.943，而原始 Softmax 回归模型的预测准确率仅为 0.516。使用与之前类似的代码再次绘制决策区域：

```
# plot the resulting classifier
h = 0.02
x_min, x_max = X[:, 0].min() - 1, X[:, 0].max() + 1
y_min, y_max = X[:, 1].min() - 1, X[:, 1].max() + 1
xx, yy = np.meshgrid(np.arange(x_min, x_max, h),
                     np.arange(y_min, y_max, h))

XX = np.c_[xx.ravel(), yy.ravel()]
Z = forward_propagation(XX, parameters)
Z = np.argmax(Z, axis=1)
Z = Z.reshape(xx.shape)
fig = plt.figure()
plt.contourf(xx, yy, Z, cmap=plt.cm.Spectral, alpha=0.3)
plt.scatter(X[:, 0], X[:, 1], c=y, s=40, cmap=plt.cm.Spectral)
plt.xlim(xx.min(), xx.max())
plt.ylim(yy.min(), yy.max())
# fig.savefig('spiral_linear.png')
```

(-1.9355521912329907, 1.8444478087670126)

![](img/file94.png)

**图 4-23 神经网络函数三分类的决策区域**

可以看出，两层神经网络模型的决策曲线不再是直线，而是可以是任意弯曲的曲线。

### 4.1.8 深度学习

自神经网络发明以来，神经网络经历了一个辉煌、沉默、复兴的曲折发展过程……

直到 2012 年，加拿大大学的团队在 ImageNet 比赛中获胜，神经网络模型再次大放异彩，使用了 6 层卷积神经网络。现代神经网络的成功主要归功于高性能并行计算硬件和大规模数据。

特别是高性能 GPU，尤其是 Nvidia 的 CUDA GPU，可以执行数据密集型大规模并行计算。

## 4.2 反向推导

神经网络模型的训练需要损失函数关于模型参数的梯度（偏导数）。数值求导法得到的梯度（导数）只是解析梯度（导数）的近似，精度不够。更重要的问题是数值求导需要对每个模型参数施加微小扰动，然后计算整个神经网络的损失。当神经网络规模较大（层数或每层神经元数较多）时，这种前向计算损失函数的开销也相对较大。例如，使用两层神经网络识别手写数字，一个样本是 28 × 28 = 784 个特征，使用批量梯度下降法，每个批次的样本数为 500，如果神经网络中间层有 100 个神经元，输出层有 10 个神经元。神经网络的模型参数数量为 784 × 100 + 100 + 100 × 10 + 10 = 79510，每次参数更新需要 2 次前向计算，总共 2 × 79510 次前向计算，每次计算都需要执行矩阵乘法和加法运算，例如第一层神经元的计算 `X * W^((1))` 是 500 × 784 矩阵与 784 × 100 矩阵的乘法运算。因此，计算量与样本数、每个样本的特征数和神经网络中的神经元数成正比。为每个模型参数计算数值偏导数的过程相互独立，必须独立执行两次前向计算（包括损失函数值的计算）。因此，数值求导的代价非常大，对于深度和大规模神经网络不可行。事实上，在深度学习中，使用 GPU 等并行计算硬件来加速神经网络的前向计算和梯度计算速度。

因此，实际神经网络的训练是通过链式求导法则，计算损失函数关于模型参数的解析梯度（导数）。模型的损失可以沿正向计算，然后从损失关于最终输出值的梯度开始，沿正向计算的反方向，计算每一层模型参数的梯度。

### 4.2.1 正向计算与反向求导

神经网络是由函数运算和复合形成的复杂复合函数。每一层都可以看作是一个多输入多输出的多元向量值函数。上一层的输出作为下一层的输入；也就是说，神经网络可以看作是逐层函数的复合。

函数求导的链式法则告诉我们，导数的计算过程与函数值的计算过程完全相反。例如，变量 `x` 通过函数 `g` 得到函数值 `g(x)`，然后该值进入函数 `h` 得到值 `h(g(x))`。该值持续输入函数 `k`，最终得到输出 `f(x) = k(h(g(x)))`。计算过程如下：

`x → g(x) → h(g(x)) → k(h(g(x))) = f(x)`

`f(x) = k(h(g(x)))` 是通过一系列函数 `g(x)`、`h(g)`、`k(h)` 的函数复合得到的。输入自变量 `x`；计算 `f(x)` 的过程是按照这个复合过程逐步进行，直到得到最终的 `f(x)`。这种“从内到外”依次通过最内层自变量，从一系列中间值得到最终函数值的过程称为**正向计算**。如果将 `g`、`h`、`k` 视为神经网络每一层的函数，这个计算过程就是神经网络从输入层沿着上一层到下一层逐层传播计算的过程。因此，正向计算在神经网络中称为**正向传播**。

根据链式求导法则，计算 `f` 关于 `x` 的最终导数，可以按如下方式计算：

`f'(x) = k'(h) * h'(g) * g'(x)`

即 `f'(x)` 的计算过程被分解为一系列计算：先计算 `f` 关于 `h` 的导数，即 `f'(h) = k'(h)`，再计算 `h` 关于 `g` 的导数，即 `h'(g)`，最后计算 `g` 关于 `x` 的导数 `g'(x)`。如下所示，导数 `f'(x)` 的计算过程与函数值 `f(x)` 的计算过程方向相反，沿函数复合过程的反方向“从外到内”计算；即沿正向方向反向计算步骤：

`f'(h) = k'(h) → f'(g) = k'(h) * h'(g) → f'(x) = k'(h) * h'(g) * g'(x)`

这种反向计算复合函数导数的过程称为**反向求导**。导数 `f'(h)=k'(h)`、`h'(g)`、`g'(x)` 的计算并非相互独立。如果先得到 `f'(h)`，在计算 `f'(g) = f'(h) * h'(g)` 时，就无需重复计算 `f'(h)`。也就是说，如果沿着反向求导的方向，保存了 `f` 关于中间变量（如 `h`）的导数 `f'(h)`，则可以直接乘以 `h'(g)` 得到 `f'(g)`。这避免了在计算 `f'(g)` 时重新计算 `f'(h)`。

如果将 `x` 视为神经网络的输入，`g`、`h` 视为隐藏层和输出层的输出，`f(h) = k(h)` 视为损失函数，则 `f'(h) = k'(h)` 表示损失函数关于神经网络输出 `h` 的梯度（导数）。在 `f'(h)` 的基础上，沿神经网络从输出层到隐藏层的反方向，可以依次计算损失函数关于隐藏层 `g`、输入 `x` 的梯度（导数）。

如果知道损失函数关于每一层输出的梯度，如 `f'(h)`，就可以得到该层模型参数的梯度。例如，假设神经网络某一层的输入为 `x`，其输出 `a = σ(x*w + b) = σ(z)`。如果已知损失函数 `L` 关于 `a` 的导数为 `L'(a)`，则该层模型参数 `w` 的梯度为：
