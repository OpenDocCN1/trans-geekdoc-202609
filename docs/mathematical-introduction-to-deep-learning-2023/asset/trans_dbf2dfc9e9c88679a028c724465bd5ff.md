

```python
delta = 0.9
eps = 1e-10

moments = [p.clone().detach().zero_() for p in net.parameters()]
Delta = [p.clone().detach().zero_() for p in net.parameters()]

for n in range(N):
    indices = torch.randint(0, M, (j,))

    x = X[indices]
    y = Y[indices]

    net.zero_grad()

    loss_val = loss(net(x), y)
    loss_val.backward()

    with torch.no_grad():
        for m, D, p in zip(moments, Delta, net.parameters()):
            m.mul_(beta)
            m.add_((1 - beta) * p.grad * p.grad)
            inc = ((eps + D) / (eps + m)).sqrt() * p.grad
            p.sub_(inc)
            D.mul_(delta)
            D.add_((1 - delta) * inc * inc)

    if n % 1000 == 0:
        with torch.no_grad():
            x = torch.rand((1000, 1)) * 4 * np.pi - 2 * np.pi
            y = torch.sin(x)
            loss_val = loss(net(x), y)
            print(f"Iteration: {n+1}, Loss: {loss_val}")
```

源代码 7.10 (code/optimization_methods/adadelta.py)：使用 PyTorch 实现 Adadelta SGD 优化方法的 Python 代码

## 7.9 自适应矩估计 SGD 优化（Adam）

在本节中，我们介绍第 6.8 节中 Adam GD 优化方法的随机版本（参见 Kingma & Ba [247]）。

定义 7.9.1 (Adam SGD 优化方法). 设 $n \in \mathbb{N}$，$(\gamma_n)_{n\in\mathbb{N}} \subseteq [0, \infty)$，$(J_n)_{n\in\mathbb{N}} \subseteq \mathbb{N}$，$(\alpha_n)_{n\in\mathbb{N}} \subseteq [0, 1]$，$(\beta_n)_{n\in\mathbb{N}} \subseteq [0, 1]$，$\varepsilon \in (0, \infty)$ 满足

$$ \max\{\alpha_1, \beta_1\} < 1, \tag{7.152} $$

设 $(\Omega, \mathcal{F}, \mathbb{P})$ 为概率空间，设 $(S, \mathcal{S})$ 为可测空间，设 $\xi: \Omega \rightarrow \mathbb{R}^{\mathcal{D}}$ 为随机变量，对于每个 $n \in \mathbb{N}, j \in \{1, 2, \ldots, J_n\}$，设 $X_{n,j}: \Omega \rightarrow S$ 为随机变量，并且设 $\ell = (\ell(\theta, x))_{(\theta, x) \in \mathbb{R}^{\mathcal{D}} \times S}: \mathbb{R}^{\mathcal{D}} \times S \rightarrow \mathbb{R}$ 和 $\boldsymbol{\mathcal{Q}} = (\boldsymbol{q}_1, \ldots, \boldsymbol{q}_{\mathcal{D}}): \mathbb{R}^{\mathcal{D}} \times S \rightarrow \mathbb{R}^{\mathcal{D}}$ 满足对于所有 $U \in \{V \subseteq \mathbb{R}^{\mathcal{D}}: V \text{ 是开集}\}$，$x \in S$，$\theta \in U$ 且 $(U \ni \partial \ni \ell(\partial, x) \in \mathbb{R}) \in C^1(U, \mathbb{R})$，有

$$ \mathcal{Q}(\theta, x) = \left(\nabla_{q^\ell}\theta\right) \ell(\theta, x). \tag{7.153} $$

那么我们要说，对于损失函数 $\ell$、广义梯度 $\boldsymbol{q}$、学习率 $(\gamma_n)_{n \in \mathbb{N}}$、批量大小 $(J_n)_{n \in \mathbb{N}}$、动量衰减因子 $(\alpha_n)_{n \in \mathbb{N}}$、二阶矩衰减因子 $(\beta_n)_{n \in \mathbb{N}}$、正则化因子 $\varepsilon \in (0, \infty)$、初始值 $\boldsymbol{\xi}$ 以及数据 $(X_{n,j})_{(n,j) \in \{(k,i) \in \mathbb{N}^2: 1 \leq i < j\}}$，$\Theta$ 是定义在 $(\Omega, \mathcal{F}, \mathbb{P}), (S, \mathcal{S})$ 上的 Adam SGD 过程。（我们说 $\Theta$ 是对于损失函数 $\ell$ 的 Adam SGD 过程，其学习率为 $(\gamma_n)_{n \in \mathbb{N}}$，批量大小为 $(J_n)_{n \in \mathbb{N}}$，动量衰减因子为 $(\alpha_n)_{n \in \mathbb{N}}$，二阶矩衰减因子为 $(\beta_n)_{n \in \mathbb{N}}$，正则化因子为 $\varepsilon \in (0, \infty)$，初始值为 $\boldsymbol{\xi}$，数据为 $(X_{n,j})_{(n,j) \in \{(k,i) \in \mathbb{N}^2: 1 \leq i < j\}}$，当且仅当 $\Theta = (\Theta^{(1)}, \ldots, \Theta^{(\mathcal{D})}): \mathbb{N}_0 \times \Omega \rightarrow \mathbb{R}^{\mathcal{D}}$ 是从 $\mathbb{N}_0 \times \Omega$ 到 $\mathbb{R}^{\mathcal{D}}$ 的函数，且满足存在 $\boldsymbol{m} = (\boldsymbol{m}^{(1)}, \ldots, \boldsymbol{m}^{(\mathcal{D})}): \mathbb{N}_0 \times \Omega \rightarrow \mathbb{R}^{\mathcal{D}}$ 和 $\mathbb{M} = (\mathbb{M}^{(1)}, \ldots, \mathbb{M}^{(\mathcal{D})}): \mathbb{N}_0 \times \Omega \rightarrow \mathbb{R}^{\mathcal{D}}$，使得对于所有 $n \in \mathbb{N}$ 和 $i \in \{1, 2, \ldots, \mathcal{D}\}$，有

$$ \Theta_0 = \boldsymbol{\xi}, \quad \quad \boldsymbol{m}_0 = 0, \quad \quad \mathbb{M}_0 = 0, \tag{7.154} $$

$$ \boldsymbol{m}_n = \alpha_n \boldsymbol{m}_{n-1} + (1 - \alpha_n) \left[ \frac{1}{J_n} \sum_{j=1}^{J_n} \boldsymbol{q}(\Theta_{n-1}, X_{n,j}) \right], \tag{7.155} $$

$$ \mathbb{M}_n^{(i)} = \beta_n \mathbb{M}_{n-1}^{(i)} + (1 - \beta_n) \left[ \frac{1}{J_n} \sum_{j=1}^{J_n} q_i(\Theta_{n-1}, X_{n,j}) \right]^2, \tag{7.156} $$

$$ \text{且} \qquad \Theta_n^{(i)} = \Theta_{n-1}^{(i)} - \gamma_n \left[ \varepsilon + \left[ \frac{\mathbb{M}_n^{(i)}}{(1 - \prod_{\ell=1}^n \beta_\ell)} \right]^{1/2} \right]^{-1} \left[ \frac{\boldsymbol{m}_n^{(i)}}{(1 - \prod_{\ell=1}^n \alpha_\ell)} \right]. \tag{7.157} $$

注 7.9.2. 在 Kingma & Ba [247] 中，建议选择

$$ 0.001 = \gamma_1 = \gamma_2 = \ldots, \quad \quad 0.9 = \alpha_1 = \alpha_2 = \ldots, \quad \quad 0.999 = \beta_1 = \beta_2 = \ldots, \tag{7.158} $$

以及 $10^{-8} = \varepsilon$ 作为定义 7.9.1 中 $(\gamma_n)_{n \in \mathbb{N}} \subseteq [0, \infty)$，$(\alpha_n)_{n \in \mathbb{N}} \subseteq [0, 1]$，$(\beta_n)_{n \in \mathbb{N}} \subseteq [0, 1]$，$\varepsilon \in (0, \infty)$ 的默认值。

定义 7.9.1 中描述的 Adam SGD 优化方法在 PyTorch 中的实现见源代码 7.11。定义 7.9.1 中描述的 Adam SGD 优化方法也可以在 PyTorch 中以内置的 torch.optim.Adam 优化器的形式使用（对于实际应用而言，使用内置优化器通常比从头实现更受青睐）。

```python
import torch
import torch.nn as nn
import numpy as np

net = nn.Sequential(
    nn.Linear(1, 200), nn.ReLU(), nn.Linear(200, 1)
)

M = 1000

X = torch.rand((M, 1)) * 4 * np.pi - 2 * np.pi
Y = torch.sin(X)

J = 64

N = 150000

loss = nn.MSELoss()
lr = 0.0001
alpha = 0.9
beta = 0.999
eps = 1e-8
adj = 1.
adj2 = 1.

m = [p.clone().detach().zero_() for p in net.parameters()]
MM = [p.clone().detach().zero_() for p in net.parameters()]

for n in range(N):
    indices = torch.randint(0, M, (J,))

    x = X[indices]
    y = Y[indices]

    net.zero_grad()

    loss_val = loss(net(x), y)
    loss_val.backward()

    with torch.no_grad():
        adj *= alpha
        adj2 *= beta
        for m_p, M_p, p in zip(m, MM, net.parameters()):
            m_p.mul_(alpha)
            m_p.add_((1 - alpha) * p.grad)
            M_p.mul_(beta)
            M_p.add_((1 - beta) * p.grad * p.grad)
            p.sub_(lr * m_p / ((1 - adj) * (eps + (M_p / (1 - adj2)).sqrt() )))

    if n % 1000 == 0:
        with torch.no_grad():
            x = torch.rand((1000, 1)) * 4 * np.pi - 2 * np.pi
            y = torch.sin(x)
            loss_val = loss(net(x), y)
            print(f"Iteration: {n+1}, Loss: {loss_val}")
```

源代码 7.11 (code/optimization_methods/adam.py)：使用 PyTorch 实现 Adam SGD 优化方法的 Python 代码。

虽然源代码 7.11 以及本章迄今为止展示的其他源代码主要用于通过提供示例实现来说明本章中引入的各种优化方法的定义，但在源代码 7.12 中，我们展示了如何使用 PyTorch 的内置功能来解决实际的机器学习问题。该代码在一个包含 3 个卷积层和 2 个全连接层（每个隐藏层后跟一个 ReLU 激活函数）的神经网络上，基于 MNIST 数据集（在 Bottou et al. [47] 中介绍，包含 28 × 28 像素的 0 到 9 手写数字灰度图像及其相应标签，是文献中训练机器学习系统最常用的基准之一）进行训练。源代码 7.12 使用交叉熵损失函数和 Adam SGD 优化方法，并输出一个图表，展示训练过程中训练集和未用于训练的测试集上的平均损失变化，以及模型预测准确率的变化，见图 7.4。

```python
import torch
import torchvision.datasets as datasets
import torchvision.transforms as transforms
import torch.nn as nn
import torch.utils.data as data
import torch.optim as optim
import matplotlib.pyplot as plt
from matplotlib.ticker import ScalarFormatter, NullFormatter

# We use the GPU if available. Otherwise, we use the CPU.
device = torch.device(
    "cuda" if torch.cuda.is_available() else "cpu"
)

# We fix a random seed. This is not necessary for training a
# neural network, but we use it here to ensure that the same
# plot is created on every run.
torch.manual_seed(0)

# The torch.utils.data.Dataset class is an abstraction for a
# collection of instances that has a length and can be indexed
```

