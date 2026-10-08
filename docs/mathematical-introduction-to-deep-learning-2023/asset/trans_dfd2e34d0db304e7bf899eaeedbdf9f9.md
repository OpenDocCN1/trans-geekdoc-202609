
(iii) 对于所有的 $n \in \{1, 2, \dots, \mathcal{L}(\Phi)\}$，均有

$\mathcal{W}_{n,\Phi} \in \mathbb{R}^{\mathbb{D}_{n}(\Phi) \times \mathbb{D}_{n-1}(\Phi)} \quad \text{ 且 } \quad \mathcal{B}_{n,\Phi} \in \mathbb{R}^{\mathbb{D}_{n}(\Phi)}.$

*引理 1.3.3 的证明。* 注意，假设

$\Phi \in \mathbf{N} = \bigcup_{L \in \mathbf{N}} (\cup_{(l_{0}, l_{1}, \dots, l_{L}) \in \mathbf{N}^{L+1}} (\textbf{\bigotimes}_{k=1}^{L} (\mathbb{R}^{l_{k} \times l_{k-1}} \times \mathbb{R}^{l_{k}})))$

保证了存在 $L \in \mathbb{N}$ 以及 $l_{0}, l_{1}, \dots, l_{L} \in \mathbb{N}$，使得

$\Phi \in \textbf{\bigotimes}_{k=1}^{L} (\mathbb{R}^{l_{k} \times l_{k-1}} \times \mathbb{R}^{l_{k}}).$

注意到 (1.85)、(1.78) 和 (1.79) 意味着

$\mathcal{L}(\Phi) = L, \quad \mathcal{I}(\Phi) = l_{0} = \mathbb{D}_{0}(\Phi), \quad \text{ 且 } \quad \mathcal{O}(\Phi) = l_{L} = \mathbb{D}_{L}(\Phi).$

这表明

$\mathcal{D}(\Phi) = (l_{0}, l_{1}, \dots, l_{L}) \in \mathbf{N}^{L+1} = \mathbf{N}^{\mathcal{L}(\Phi)+1}.$

接下来注意，(1.85)、(1.79) 和 (1.81) 保证了对于所有的 $n \in \{1, 2, \dots, \mathcal{L}(\Phi)\}$，均有

$\mathcal{W}_{n,\Phi} \in \mathbb{R}^{l_{n} \times l_{n-1}} = \mathbb{R}^{\mathbb{D}_{n}(\Phi) \times \mathbb{D}_{n-1}(\Phi)} \quad \text{ 且 } \quad \mathcal{B}_{n,\Phi} \in \mathbb{R}^{l_{n}} = \mathbb{R}^{\mathbb{D}_{n}(\Phi)}.$

引理 1.3.3 的证明至此完成。

### 1.3.2 全连接前馈神经网络的实现

**定义 1.3.4**（全连接前馈神经网络的实现）。*设* $\Phi \in \mathbf{N}$ *且设* $a\colon \mathbb{R} \rightarrow \mathbb{R}$ *为一个函数（参见定义 1.3.1）。则我们用*

$\mathcal{R}_{a}^{\mathbf{N}}(\Phi)\colon \mathbb{R}^{\mathcal{I}(\Phi)} \rightarrow \mathbb{R}^{\mathcal{O}(\Phi)}$

*表示满足对所有* $x_{0} \in \mathbb{R}^{\mathbb{D}_{0}(\Phi)}$， $x_{1} \in \mathbb{R}^{\mathbb{D}_{1}(\Phi)}$， $\dots$， $x_{\mathcal{L}(\Phi)} \in \mathbb{R}^{\mathbb{D}_{\mathcal{L}(\Phi)}(\Phi)}$ *且*

$\forall k \in \{1, 2, \dots, \mathcal{L}(\Phi)\}\colon x_{k} = \mathfrak{M}_{a}^{1, \mathbb{D}_{1}(\Phi)(k)+\operatorname{id}_{\mathbb{N}^{\mathcal{L}(\Phi)+1}}(k), \mathbb{D}_{k}(\Phi)}(\mathcal{W}_{k,\Phi}x_{k-1}+\mathcal{B}_{k,\Phi})$

**练习 1.3.1。** 设

$\Phi = ((W_{1}, B_{1}), (W_{2}, B_{2}), (W_{3}, B_{3})) \in (\mathbb{R}^{2 \times 1} \times \mathbb{R}^{2}) \times (\mathbb{R}^{3 \times 2} \times \mathbb{R}^{3}) \times (\mathbb{R}^{1 \times 3} \times \mathbb{R}^{1})$  (1.92)

满足

$W_{1} = \begin{pmatrix} 1 \\ 2 \end{pmatrix} , B_{1} = \begin{pmatrix} 3 \\ 4 \end{pmatrix} , W_{2} = \begin{pmatrix} -1 & 2 \\ 3 & -4 \\ -5 & 6 \end{pmatrix} , B_{2} = \begin{pmatrix} 0 \\ 0 \\ 0 \end{pmatrix} .$  (1.93)

$W_{3} = \begin{pmatrix} -1 & 1 & -1 \end{pmatrix} , \text{且} B_{3} = \begin{pmatrix} -4 \end{pmatrix} .$  (1.94)

证明或反驳以下陈述：成立

$(\mathcal{R}_{c}^{\text{N}}(\Phi))(-1) = 0$  (1.95)

（参见定义 1.2.4 和 1.3.4）。

**练习 1.3.2。** 设 $a$ 为标准逻辑激活函数（参见定义 1.2.18）。证明或反驳以下陈述：存在 $\Phi \in \mathbf{N}$ 使得

$\mathcal{R}_{\text{tanh}}^{\mathbf{N}}(\Phi) = a$  (1.96)

（参见定义 1.2.25, 1.3.1, 和 1.3.4）。

```python
import torch
import torch.nn as nn
import torch.nn.functional as F

# To define a neural network, we define a class that inherits from
# torch.nn.Module
class FullyConnectedANN(nn.Module):
    def __init__(self):
        super().__init__()
        # In the constructor, we define the weights and biases.
        # Wrapping the tensors in torch.nn.Parameter objects tells
        # PyTorch that these are parameters that should be
        # optimized during training.
        self.W1 = nn.Parameter(
            torch.Tensor([[1, 0], [0, -1], [-2, 2]])
        )
        self.B1 = nn.Parameter(torch.Tensor([0, 2, -1]))
        self.W2 = nn.Parameter(torch.Tensor([[1, -2, 3]]))
        self.B2 = nn.Parameter(torch.Tensor([1]))

        # The realization function of the network
    def forward(self, x0):
        x1 = F.relu(self.W1 @ x0 + self.B1)
        x2 = self.W2 @ x1 + self.B2
        return x2

model = FullyConnectedANN()

x0 = torch.Tensor([1, 2])
# Print the output of the realization function for input x0
print(model.forward(x0))

# As a consequence of inheriting from torch.nn.Module we can just
# "call" the model itself (which will call the forward method
# implicitly)
print(model(x0))

# Wrapping a tensor in a Parameter object and assigning it to an
# instance variable of the Module makes PyTorch register it as a
# parameter. We can access all parameters via the parameters
# method.
for p in model.parameters():
    print(p)
```

源码 1.15 (code/fc-ann-manual.py)：用于在 PYTORCH 中实现全连接前馈 ANN 的 PYTHON 代码。此处创建的模型代表全连接前馈 ANN $(((\begin{pmatrix}1 & 0 \\ 0 & -1 \\ -2 & 2\end{pmatrix}, (\begin{pmatrix}0 \\ 2 \\ -1\end{pmatrix})), ((\begin{pmatrix}1 & -2 & 3\end{pmatrix}, (\begin{pmatrix}1\end{pmatrix}))) \in (\mathbb{R}^{3 \times 2} \times \mathbb{R}^{3}) \times (\mathbb{R}^{1 \times 3} \times \mathbb{R}^{1}) \subseteq \mathbf{N}$，在隐藏层之后使用 ReLU 激活函数。

```python
import torch
import torch.nn as nn

class FullyConnectedANN(nn.Module):
    def __init__(self):
        super().__init__()
        # Define the layers of the network in terms of Modules.
        # nn.Linear(3, 20) represents an affine function defined
        # by a 20x3 weight matrix and a 20-dimensional bias vector.
        self.affine1 = nn.Linear(3, 20)
        # The torch.nn.ReLU class simply wraps the
        # torch.nn.functional.relu function as a Module.
        self.activation1 = nn.ReLU()
        self.affine2 = nn.Linear(20, 30)
        self.activation2 = nn.ReLU()
        self.affine3 = nn.Linear(30, 1)

    def forward(self, x0):
        x1 = self.activation1(self.affine1(x0))
        x2 = self.activation2(self.affine2(x1))
        x3 = self.affine3(x2)
        return x3

model = FullyConnectedANN()

x0 = torch.Tensor([1, 2, 3])
print(model(x0))

# Assigning a Module to an instance variable of a Module registers
# all of the former's parameters as parameters of the latter
for p in model.parameters():
    print(p)
```

源码 1.16 (code/fc-ann.py)：用于在 PYTORCH 中实现全连接前馈 ANN 的 PYTHON 代码。此处实现的模型代表一个具有两个隐藏层的全连接前馈 ANN，输入层有 3 个神经元，第一个隐藏层有 20 个神经元，第二个隐藏层有 30 个神经元，输出层有 1 个神经元。与源码 1.15 不同，此代码使用 torch.nn.Linear 类来表示仿射变换。

```python
import torch
import torch.nn as nn

# A Module whose forward method is simply a composition of Modules
# can be represented using the torch.nn.Sequential class
model = nn.Sequential(
    nn.Linear(3, 20),
    nn.ReLU(),
    nn.Linear(20, 30),
    nn.ReLU(),
    nn.Linear(30, 1),
)

# Prints a summary of the model architecture
print(model)

x0 = torch.Tensor([1, 2, 3])
print(model(x0))
```

源码 1.17 (code/fc-ann2.py)：用于在 PyTorch 中创建全连接前馈 ANN 的 PYTHON 代码。这创建了与源码 1.16 相同的模型，但使用 torch.nn.Sequential 类而不是定义新的 torch.nn.Module 子类。

### 1.3.3 关于与向量化描述的联系

**定义 1.3.5**（全连接前馈 ANN 从结构化描述到向量化描述的转换）。我们用 $T: \mathbf{N} \rightarrow \bigcup_{n \in \mathbb{N}} \mathbb{R}^{n}$ 表示满足对所有 $\Phi \in \mathbf{N}$， $k \in \{1, 2, \dots, \mathcal{L}(\Phi)\}$， $d \in \mathbb{N}$， $\theta = (\theta_{1}, \theta_{2}, \dots, \theta_{d}) \in \mathbb{R}^{d}$ 且 $T(\Phi) = \theta$ 的函数，使得

$d = \mathcal{P}(\Phi), \quad B_{k,\Phi} = \left( \begin{array}{c} \theta_{\sum_{i=1}^{k-1} l_{i}(l_{i-1}+1)+l_{k}l_{k-1}+1} \\ \theta_{\sum_{i=1}^{k-1} l_{i}(l_{i-1}+1)+l_{k}l_{k-1}+2} \\ \theta_{\sum_{i=1}^{k-1} l_{i}(l_{i-1}+1)+l_{k}l_{k-1}+3} \\ \vdots \\ \theta_{\sum_{i=1}^{k-1} l_{i}(l_{i-1}+1)+l_{k}l_{k-1}+l_{k}} \end{array} \right), \quad \text{且} \quad \mathcal{W}_{k,\Phi} = \left( \begin{array}{cccc} \theta_{\sum_{i=1}^{k-1} l_{i}(l_{i-1}+1)+1} & \theta_{\sum_{i=1}^{k-1} l_{i}(l_{i-1}+1)+2} & \dots & \theta_{\sum_{i=1}^{k-1} l_{i}(l_{i-1}+1)+l_{k-1}} \\ \theta_{\sum_{i=1}^{k-1} l_{i}(l_{i-1}+1)+l_{k-1}+1} & \theta_{\sum_{i=1}^{k-1} l_{i}(l_{i-1}+1)+l_{k-1}+2} & \dots & \theta_{\sum_{i=1}^{k-1} l_{i}(l_{i-1}+1)+2l_{k-1}} \\ \theta_{\sum_{i=1}^{k-1} l_{i}(l_{i-1}+1)+2l_{k-1}+1} & \theta_{\sum_{i=1}^{k-1} l_{i}(l_{i-1}+1)+2l_{k-1}+2} & \dots & \theta_{\sum_{i=1}^{k-1} l_{i}(l_{i-1}+1)+3l_{k-1}} \\ \vdots & \vdots & \ddots & \vdots \\ \theta_{\sum_{i=1}^{k-1} l_{i}(l_{i-1}+1)+(l_{k}-1)l_{k-1}+1} & \theta_{\sum_{i=1}^{k-1} l_{i}(l_{i-1}+1)+(l_{k}-1)l_{k-1}+2} & \dots & \theta_{\sum_{i=1}^{k-1} l_{i}(l_{i-1}+1)+l_{k}l_{k-1}} \end{array} \right)$  (1.97)

（参见定义 1.3.1）。

**引理 1.3.6。** 设 $\Phi \in (\mathbb{R}^{3 \times 3} \times \mathbb{R}^{3}) \times (\mathbb{R}^{2 \times 3} \times \mathbb{R}^{2})$ 满足

$\Phi = \left( \left( \left( \begin{array}{ccc} 1 & 2 & 3 \\ 4 & 5 & 6 \\ 7 & 8 & 9 \end{array} \right), \left( \begin{array}{c} 10 \\ 11 \\ 12 \end{array} \right) \right), \left( \left( \begin{array}{ccc} 13 & 14 & 15 \\ 16 & 17 & 18 \end{array} \right), \left( \begin{array}{c} 19 \\ 20 \end{array} \right) \right) \right).$  (1.98)

则 $T(\Phi) = (1, 2, 3, \dots, 19, 20) \in \mathbb{R}^{20}$。

*引理 1.3.6 的证明。* 注意，(1.97) 建立了 (1.98)。引理 1.3.6 的证明至此完成。 $\square$

**引理 1.3.7。** 设 $a, b \in \mathbb{N}$， $W = (W_{ij})_{(i,j) \in \{1,2,\dots,a\} \times \{1,2,\dots,b\}} \in \mathbb{R}^{a \times b}$， $B = (B_{1}, B_{2}, \dots, B_{a}) \in \mathbb{R}^{a}$。则

$T(((W, B))) = (W_{1,1}, W_{1,2}, \dots, W_{1,b}, W_{2,1}, W_{2,2}, \dots, W_{2,b}, \dots, W_{a,1}, W_{a,2}, \dots, W_{a,b}, B_{1}, B_{2}, \dots, B_{a})$  (1.99)

（参见定义 1.3.5）。

