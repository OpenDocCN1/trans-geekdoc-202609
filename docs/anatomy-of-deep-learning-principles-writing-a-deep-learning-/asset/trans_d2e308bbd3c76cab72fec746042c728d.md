

# 卷积层的反向传播推导与实现

## 一维卷积扩展到二维多通道

同理，一维数据的卷积可以扩展到多输入输出通道的二维数据卷积的反向推导。如图 6-39 所示，为单输入通道和单输出通道的梯度求解示意图。

**图 6-39**  
$z_{00} = x_{00}w_{00}+x_{01}w_{01}+x_{10}w_{10}+x_{11}w_{11}$，其关于 $w_{00}, w_{01}, w_{10}, w_{11}$ 的梯度分别为 $x_{00}, x_{01}, x_{10}, x_{11}$，其关于 $x_{00}, x_{01}, x_{10}, x_{11}$ 的梯度分别为 $w_{00}, w_{01}, w_{10}, w_{11}$。

$$
\frac{\partial L}{\partial ww} = \sum_{ij}\frac{\partial L}{\partial z_{ij}}\frac{\partial z_{ij}}{\partial ww}
$$

其中 $z_{ij}$ 是以 $x_{ij}$ 为起始的窗口 $xx[i:i+K_h, j:j+K_w]$ 与卷积核 $WW$ 的加权和，即 $z_{ij} = xx[i:i+K_h, j:j+K_w] \cdot ww$，且

$$
\frac{\partial z_{ij}}{\partial w_{u,v}} = x_{i+u, j+v}
$$

因此，将 $\frac{\partial z_{ij}}{\partial ww}$ 写成与 $ww$ 形状相同的矩阵：

$$
\frac{\partial z_{ij}}{\partial ww} = xx[i:i+K_h, j:j+K_w]
$$

例如，上图中 $\frac{\partial z_{00}}{\partial ww}$ 为：

$$
\frac{\partial z_{00}}{\partial ww} = xx[0:0+2, 0:0+2] = \begin{bmatrix} x_{00} & x_{01} \\ x_{10} & x_{11} \end{bmatrix}
$$

故

$$
\frac{\partial L}{\partial ww} = \sum_{ij}\frac{\partial L}{\partial z_{ij}} xx[i:i+K_h, j:j+K_w]
$$

同理，因为 $\frac{\partial z_{ij}}{\partial b} = 1$，所以：

$$
\frac{\partial L}{\partial b} = \sum_{ij}\frac{\partial L}{\partial z_{ij}}\frac{\partial z_{ij}}{\partial b} = \sum_{ij}\frac{\partial L}{\partial z_{ij}}
$$

因为

$$
\frac{\partial L}{\partial xx} = \sum_{ij}\frac{\partial L}{\partial z_{ij}}\frac{\partial z_{ij}}{\partial xx}
$$

且 $z_{ij} = xx[i:i+K_h, j:j+K_w] \cdot ww$ 仅依赖于数据窗口 $xx[i:i+K_h, j:j+K_w]$，并且：

$$
\frac{\partial z_{ij}}{\partial x_{i+u, j+v}} = w_{u,v}
$$

因此：

$$
\frac{\partial z_{ij}}{\partial xx}[i:i+K_h, j:j+K_w] = ww
$$

例如，上式中 $\frac{\partial z_{ij}}{\partial xx}$ 的窗口 $[i:i+2, j:j+2]$ 为：

$$
\frac{\partial z_{ij}}{\partial xx}[i:i+2, j:j+2] = ww = \begin{bmatrix} w_{00} & w_{01} \\ w_{10} & w_{11} \end{bmatrix}
$$

因此，只需将 $\frac{\partial L}{\partial z_{ij}}\frac{\partial z_{ij}}{\partial xx} = \frac{\partial L}{\partial z_{ij}}w$ 加到 $\frac{\partial L}{\partial xx}$ 对应的窗口 $[i:i+K_h, j:j+K_w]$ 上，即：

$$
\frac{\partial L}{\partial xx}[i:i+K_h, j:j+K_w] += \frac{\partial L}{\partial z_{ij}}ww
$$

## 带填充和步长的卷积

对于带填充和步长的卷积，在进行反向推导前，也需要先填充 $xx$，然后根据步长找到 $z_{ij}$ 对应的数据窗口，即按以下公式计算 $L$ 关于 $ww$、$xx$ 的梯度（偏导数）：

$$
\frac{\partial L}{\partial ww} = \sum_{ij}\frac{\partial L}{\partial z_{ij}} xx[i \ast S:i \ast S + K_h, j \ast S:j \ast S + K_w]
$$

$$
\frac{\partial L}{\partial b} = \sum_{ij}\frac{\partial L}{\partial z_{ij}}
$$

$$
\frac{\partial L}{\partial xx}[i \ast S:i \ast S + K_h, j \ast S:j \ast S + K_w] += \frac{\partial L}{\partial z_{ij}}ww
$$

以上是单通道输入和单通道输出的计算公式。对于多通道输入 $xx$，卷积核的权重张量 $ww$ 此时对应 3D 卷积核，梯度计算公式类似，只是多了一个颜色通道：

$$
\frac{\partial L}{\partial ww} = \sum_{ij}\frac{\partial L}{\partial z_{ij}} xx[:, i \ast S:i \ast S + K_h, j \ast S:j \ast S + K_w]
$$

$$
\frac{\partial L}{\partial xx}[:, i \ast S:i \ast S + K_h, j \ast S:j \ast S + K_w] += \frac{\partial L}{\partial z_{ij}}ww
$$

如果是多通道输出，将上述公式中的 $ww$ 替换为对应每个输出通道 $f$ 的权重张量 $ww^{(f)}$，但因为 $xx$ 对每个输出通道特征图 $zz^{(f)}$ 都有贡献，所以所有 $zz^{(f)}$ 关于 $xx$ 的梯度应当累加，即：

$$
\frac{\partial L}{\partial xx}[:, i \ast S:i \ast S + K_h, j \ast S:j \ast S + K_w] += \sum_{f}(\frac{\partial L}{\partial z_{ij}^{f}} ww^{f})
$$

$$
\frac{\partial L}{\partial ww^{f}} = \sum_{ij}\frac{\partial L}{\partial z_{ij}^{f}} xx[:, i \ast S:i \ast S + K_h, j \ast S:j \ast S + K_w]
$$

$$
\frac{\partial L}{\partial b^{f}} = \sum_{ij}\frac{\partial L}{\partial z_{ij}^{f}}
$$

如果有多个样本，只需将上述每个样本的梯度 $\frac{\partial L}{\partial ww^{f}}, \frac{\partial L}{\partial b^{f}}$ 累加，而各样本的 $xx$ 相互独立，所以 $\frac{\partial L}{\partial xx}$ 不能累加。

## `Conv` 类实现

在之前 `Layer` 类的基础上，以下代码定义了一个表示卷积层的类 `Conv`，用于多样本、多输入通道、多输出通道的卷积前向计算（`forward`）和反向推导（`backward`）。`Conv` 的构造函数接受输入输出通道数和代表卷积操作的卷积核等参数。`forward()` 方法接受多通道输入 `X` 生成卷积多通道输出 `Z`。`backward()` 方法接受来自损失函数的关于卷积层输出 `Z` 的梯度 `dZ`，计算损失函数关于卷积参数（`W`、`b`）和输入 `X` 的梯度。

```python
import numpy as np
import math
from init_weights import *

class Layer:
    def __init__(self):
        self.params = None
        pass

    def forward(self, x):
        raise NotImplementedError

    def backward(self, x, grad):
        raise NotImplementedError

    def reg_grad(self, reg):
        pass

    def reg_loss(self, reg):
        return 0.

    def reg_loss_grad(self, reg):
        return 0

class Conv(Layer):
    def __init__(self, in_channels, out_channels, kernel_size, stride=1, padding=0):
        super().__init__()
        self.C = in_channels
        self.F = out_channels
        self.K = kernel_size
        self.S = stride
        self.P = padding

        # filters is a 3d array with dimensions (num_filters, self.K, self.K)
        # you can also use Xavier Initialization.
        self.W = np.random.randn(self.F, self.C, self.K, self.K)  # /(self.K*self.K)
        self.b = np.random.randn(out_channels,)
        self.params = [self.W, self.b]
        self.grads = [np.zeros_like(self.W), np.zeros_like(self.b)]
        self.X = None
        self.reset_parameters()

    def reset_parameters(self):
        kaiming_uniform(self.W, a=math.sqrt(5))
        if self.b is not None:
            # fan_in, _ = calculate_fan_in_and_fan_out(self.K)
            fan_in = self.C
            bound = 1 / math.sqrt(fan_in)
            self.b[:] = np.random.uniform(-bound, bound, (self.b.shape))

    def forward(self, X):
        self.X = X
```
