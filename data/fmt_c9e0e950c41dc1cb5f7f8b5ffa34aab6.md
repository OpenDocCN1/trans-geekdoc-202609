
```python
from Layers import *
from im2row import *

class Conv_fast:
    def __init__(self, in_channels, out_channels, kernel_size, stride=1, padding=0):
        super().__init__()
        self.C = in_channels
        self.F = out_channels
        self.kH = kernel_size
        self.kW = kernel_size
        self.S = stride
        self.P = padding
        # filters 是一个三维数组，维度为 (num_filters, self.K, self.K)
        # 也可以使用 Xavier 初始化。
        # self.K = np.random.randn(self.F, self.C, self.kH, self.kW) #/(self.K*self.K)
        self.K = np.random.normal(0, 1, (self.F, self.C, self.kH, self.kW))
        self.b = np.zeros((1, self.F))  # ,1))
        self.params = [self.K, self.b]
        self.grads = [np.zeros_like(self.K), np.zeros_like(self.b)]
        self.X = None
        self.reset_parameters()

    def reset_parameters(self):
        kaiming_uniform(self.K, a=math.sqrt(5))
        if self.b is not None:
            # fan_in, _ = calculate_fan_in_and_fan_out(self.K)
            fan_in = self.C
            bound = 1 / math.sqrt(fan_in)
            self.b[:] = np.random.uniform(-bound, bound, (self.b.shape))

    def forward(self, X):
        # 转换为多通道
        self.X = X
        if len(X.shape) == 1:
            X = X.reshape(X.shape[0], 1, 1, 1)
        elif len(X.shape) == 2:
            X = X.reshape(X.shape[0], X.shape[1], 1, 1)
        self.N, self.H, self.W = X.shape[0], X.shape[2], X.shape[3]
        S, P, kH, kW = self.S, self.P, self.kH, self.kW
        self.oH = (self.H - kH + 2 * P) // S + 1
        self.oW = (self.W - kW + 2 * P) // S + 1
        X_shape = (self.N, self.C, self.H, self.W)
        self.X_row = im2row_indices(X, self.kH, self.kW, S=self.S, P=self.P)
        K_col = self.K.reshape(self.F, -1).transpose()
        Z_row = self.X_row @ K_col + self.b  # W_row @ self.X_row + self.b
        Z = Z_row.reshape(self.N, self.oH, self.oW, -1)
        Z = Z.transpose(0, 3, 1, 2)
        return Z

    def __call__(self, x):
        return self.forward(x)

    def backward(self, dZ):
        if len(dZ.shape) <= 2:
            dZ = dZ.reshape(dZ.shape[0], -1, self.oH, self.oW)
        K = self.K
        # 将 dZ 展平为与 Z_row 形状相同的矩阵
        F = dZ.shape[1]  # 将 (N,F,oH,oW) 转换为 (N,oH,oW,F)
        assert F == self.F
        dZ_row = dZ.transpose(0, 2, 3, 1).reshape(-1, F)
        # 计算损失函数关于卷积核参数的梯度
        dK_col = np.dot(self.X_row.T, dZ_row)  # X_row.T @ dZ_row
        dK_col = dK_col.transpose(1, 0)  # 将 F 通道轴从 axis=1 移至 axis=0
        dK = dK_col.reshape(self.K.shape)
        db = np.sum(dZ, axis=(0, 2, 3))
        db = db.reshape(-1, F)
        # 计算损失函数关于卷积层输入的梯度
        K_col = K.reshape(K.shape[0], -1).transpose()  # 展平
        dX_row = np.dot(dZ_row, K_col.T)
        X_shape = (self.N, self.C, self.H, self.W)
        dX = row2im_indices(dX_row, X_shape, self.kH, self.kW, S=self.S, P=self.P)
        dX = dX.reshape(self.X.shape)
        self.grads[0] += dK
        self.grads[1] += db
        return dX

    # -------- 添加正则项的梯度 -----
    def reg_grad(self, reg):
        self.grads[0] += 2 * reg * self.K

    def reg_loss(self, reg):
        return reg * np.sum(self.K**2)

    def reg_loss_grad(self, reg):
        self.grads[0] += 2 * reg * self.K
        return reg * np.sum(self.K**2)
```

### 梯度测试

同样，可以使用梯度测试来检查该卷积层的代码是否正确：

```python
import util

np.random.seed(1)
N, C, H, W = 4, 3, 5, 5
F, kH, kW = 6, 3, 3
oH, oW = 3, 3
x = np.random.randn(N, C, H, W)
y = np.random.randn(N, F, oH, oW)
conv = Conv_fast(C, F, kH, 1, 0)
f = conv.forward(x)
loss, do = util.mse_loss_grad(f, y)
dx = conv.backward(do)

def loss_f():
    f = conv.forward(x)
    loss, do = util.mse_loss_grad(f, y)
    return loss

dW_num = util.numerical_gradient(loss_f, conv.params[0], 1e-6)
diff_error = lambda x, y: np.max(np.abs(x - y) / (np.maximum(1e-8, np.abs(x) + np.abs(y))))
print(diff_error(conv.grads[0], dW_num))
# print("dW", conv.grads[0][:2])
# print("dW_num", dW_num[:2])
```

```
4.198542114313848e-07
```

### 与非加速卷积的时间对比

为了比较快速卷积与之前非加速卷积的时间效率，使用与之前相同的卷积神经网络对 MNIST 手写数字识别问题进行训练：

```python
from Layers import *

import time

np.random.seed(0)

# N,C,H,W = 64,256,64,64
# F,kH= 128,5
N,C,H,W = 128,16,64,64
F,kH= 32,5

x = np.random.randn(N,C,H,W)
oH = H-kH+1
do = np.random.randn(N,F,oH,oH)

start = time.time()
conv = Conv(C,F,kH)
f = conv(x)
conv.backward(do)
done = time.time()
elapsed = done - start
print(elapsed)

start = time.time()
conv = Conv_fast(C,F,kH)
f = conv(x)
conv.backward(do)
done = time.time()
elapsed = done - start
print(elapsed)
```

```
476.4419822692871
29.02124047279358
```

原始卷积耗时 476 秒，而快速卷积仅需 29 秒。

将之前用于 MNIST 手写数字分类的卷积神经网络中的卷积替换为快速卷积，并观察时间效率：

```python
import pickle, gzip, urllib.request, json
import numpy as np
import os.path

if not os.path.isfile("mnist.pkl.gz"):
    # 加载数据集
    urllib.request.urlretrieve("http://deeplearning.net/data/mnist/mnist.pkl.gz", "mnist.pkl.gz")

with gzip.open('mnist.pkl.gz', 'rb') as f:
    train_set, valid_set, test_set = pickle.load(f, encoding='latin1')

train_X, train_y = train_set
print(train_X.shape)
train_X = train_X.reshape((train_X.shape[0],1,28,28))
print(train_X.shape)
```

```
(50000, 784)
(50000, 1, 28, 28)
```

定义一个卷积神经网络并对其进行训练：

```python
import train
from NeuralNetwork import *
import time

np.random.seed(1)

nn = NeuralNetwork()
nn.add_layer(Conv_fast(1,2,5,1,0))
nn.add_layer(Pool((2,2,2)))
nn.add_layer(Conv_fast(2,4,5,1,0))
nn.add_layer(Pool((2,2,2)))
nn.add_layer(Dense(64, 100))
nn.add_layer(Relu())
nn.add_layer(Dense(100, 10))

learning_rate = 1e-3 #1e-1
momentum = 0.9
optimizer = train.SGD(nn.parameters(), learning_rate, momentum)

epochs = 1
batch_size = 64
reg = 1e-3
print_n = 100

start = time.time()
X, y = train_X, train_y
losses = train.train_nn(nn, X, y, optimizer, util.cross_entropy_grad_loss, epochs, batch_size, reg, print_n)
done = time.time()
elapsed = done - start
print(elapsed)
print(np.mean(nn.predict(X) == y))
```

```
[ 1, 1] loss: 2.383
[ 101, 1] loss: 2.316
[ 201, 1] loss: 2.283
[ 301, 1] loss: 2.160
[ 401, 1] loss: 1.675
[ 501, 1] loss: 1.091
[ 601, 1] loss: 0.514
[ 701, 1] loss: 0.659
690.5078177452087
0.83894
```

```python
import matplotlib.pyplot as plt
%matplotlib inline
plt.plot(losses)
```

## 6.5 典型卷积神经网络结构

1989 年，卷积神经网络结构（CNN）的发明者 Yann LeCun 利用反向传播（BP）算法训练多层神经网络以识别手写邮政编码。所用的神经网络于 1994 年被称为 LeNet。虽然该论文并未提及卷积或卷积神经网络，仅指出使用 5×5 的相邻区域作为感受野。1998 年，LeCun 提出了著名的 LeNet-5 神经网络，标志着卷积神经网络的真正诞生。由于当时硬件条件的限制，卷积神经网络的训练极其消耗机器资源和时间。因此，CNN 网络模型并未普及。

直到 2012 年，Alex Krizhevsky 利用 GPU 实现了一个名为 AlexNet 的深度卷积神经网络，并赢得了 ImageNet 图像识别竞赛的冠军，以深度卷积神经网络为代表的深度学习才开始迅速发展。随后，提出了各种神经网络结构，如 VGG、GoogLeNet、ResNet、Inception 等。

### 6.5.1 LeNet-5

图 6-55 展示了 LeNet-5 的网络结构。一张 32×32×1 的图像经过六个步长为 1、填充为 0 的 5×5 卷积核，生成 6 个尺寸为 28×28 的输出特征图；随后通过跨度为 2、大小为 2 的平均池化操作，生成六个 14×14 的特征图，即图像的长宽减半。接着通过 16 个步长为 1、填充为 0 的 5×5 卷积核，生成 16 个尺寸为 10×10 的输出特征图。再通过跨度为 2、大小为 2 的平均池化操作，生成 16 个 5×5 的特征图。

![](img/file138.png "fig:")  

图 6-55 LeNet 网络结构

随后是全连接层，拥有 120 个神经元，每个神经元接收来自上一层 16 个 5×5 特征图（图像）共 400 个特征值，每个神经元产生一个输出值，120 个神经元生成一个由 120 个输出组成的一维向量，输出给下一个拥有 84 个神经元的全连接层。拥有 84 个神经元的全连接层将其 84 个输出送入最终的输出层，若进行 10 分类，输出层将包含 10 个神经元，每个神经元输出样本属于对应类别的得分。这 10 个分类可通过 softmax 函数计算多类交叉熵损失并结合真实目标值来训练神经网络模型。

LeNet-5 是卷积神经网络的经典结构。它采用“先卷积后池化”的模式，从多通道输入生成多通道输出并减小图像尺寸。如上例所示，单通道 32×32×1 经过一系列“卷积-池化”变换，最终生成 16 个 5×5 的特征图，最后再经过若干全连接层产生最终输出。

### 6.5.2 AlexNet

AlexNet 是 Alex Krizhevsky 等人提出的一种 CNN 网络结构。它在 2012 年 ImageNet 图像分类竞赛中获得第一名，瞬间将 top-5 错误率降低了 10 个百分点以上。作者利用 CUDA GPU 实现了并行神经网络训练算法，使得在合理时间内训练深度神经网络成为可能。其网络结构如图 6-56 所示。

![](img/file139.png "fig:")  

图 6-56 AlexNet 网络结构
