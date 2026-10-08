
且令 $\pmb{\mathfrak{L}}: C^{1,2}([0,T] \times \mathbb{R}^{d}, \mathbb{R}) \rightarrow [0, \infty)$ 满足对于所有 $v = (v(t,x))_{(t,x) \in [0,T] \times \mathbb{R}^{d}} \in C^{1,2}([0,T] \times \mathbb{R}^{d}, \mathbb{R})$，有

$$\pmb{\mathfrak{L}}(v) = \mathbb{E}[|v(0, \mathcal{X}) - g(\mathcal{X})|^{2} + |\big(\tfrac{\partial v}{\partial t}\big)(\mathcal{T}, \mathcal{X}) - (\Delta_{x}v)(\mathcal{T}, \mathcal{X}) - f(v(\mathcal{T}, \mathcal{X}))|^{2}]. \tag{16.12}$$

注意到定理 16.1.1 保证未知函数 $u$ 满足

$$\pmb{\mathfrak{L}}(u) = 0 \tag{16.13}$$

因此它是与 (16.12) 相关的优化问题的一个最小化点。受此启发，我们旨在通过计算函数 $\pmb{\mathfrak{L}}: C^{1,2}([0,T] \times \mathbb{R}^{d}, \mathbb{R}) \rightarrow [0, \infty]$ 的近似最小化点来寻找 $u$ 的近似值。由于其无穷维性，该优化问题目前尚不适用于数值计算。

为此，在第二步中，我们将这个有限维随机优化问题简化为涉及 *ANNs* 的有限维随机优化问题。具体而言，设 $a: \mathbb{R} \rightarrow \mathbb{R}$ 是可微的，设 $h \in \mathbb{N}$，$l_{1}, l_{2}, \ldots, l_{h}$，$\mathfrak{d} \in \mathbb{N}$ 满足 $\mathfrak{d} = l_{1}(d+2) + [\sum_{k=2}^{h}l_{k}(l_{k-1} + 1)] + l_{h} + 1$，且设 $\mathcal{L}: \mathbb{R}^{\mathfrak{d}} \rightarrow [0, \infty)$ 满足对于所有 $\theta \in \mathbb{R}^{\mathfrak{d}}$，有

$$\begin{align*} \mathcal{L}(\theta) &= \pmb{\mathfrak{L}}\big(\mathcal{N}^{\theta, d+1}_{\mathfrak{A}_{a, l_{1}}, \mathfrak{A}_{a, l_{2}}, \ldots, \mathfrak{A}_{a, l_{h}}, \operatorname{id}_{\mathbb{R}}}\big) \\ &= \mathbb{E}\Big[\big|\mathcal{N}^{\theta, d+1}_{\mathfrak{A}_{a, l_{1}}, \mathfrak{A}_{a, l_{2}}, \ldots, \mathfrak{A}_{a, l_{h}}, \operatorname{id}_{\mathbb{R}}}(0, \mathcal{X}) - g(\mathcal{X})\big|^{2} \\ &\quad+ \big(\tfrac{\partial \mathcal{N}^{\theta, d+1}_{\mathfrak{A}_{a, l_{1}}, \mathfrak{A}_{a, l_{2}}, \ldots, \mathfrak{A}_{a, l_{h}}, \operatorname{id}_{\mathbb{R}}}}{\partial t}(\mathcal{T}, \mathcal{X}) - (\Delta_{x}\mathcal{N}^{\theta, d+1}_{\mathfrak{A}_{a, l_{1}}, \mathfrak{A}_{a, l_{2}}, \ldots, \mathfrak{A}_{a, l_{h}}, \operatorname{id}_{\mathbb{R}}})(\mathcal{T}, \mathcal{X}) \ &\quad- f\big(\mathcal{N}^{\theta, d+1}_{\mathfrak{A}_{a, l_{1}}, \mathfrak{A}_{a, l_{2}}, \ldots, \mathfrak{A}_{a, l_{h}}, \operatorname{id}_{\mathbb{R}}}(\mathcal{T}, \mathcal{X})\big)\big)^{2}\Big] \tag{16.14} \end{align*}$$

(参见定义 1.1.3 和 1.2.1)。我们现在可以通过计算函数 $\mathcal{L}$ 的近似最小化点 $\vartheta \in \mathbb{R}^{\mathfrak{d}}$，并利用与该近似最小化点相关联的 *ANN* 的实现 $\mathcal{N}^{\vartheta, d+1}_{\mathfrak{A}_{a, l_{1}}, \mathfrak{A}_{a, l_{2}}, \ldots, \mathfrak{A}_{a, l_{h}}, \operatorname{id}_{\mathbb{R}}}$ 作为 $\pmb{\mathfrak{L}}$ 的近似最小化点，从而计算出函数 $\pmb{\mathfrak{L}}$ 的近似最小化点。

此推导的第三步也是最后一步，是通过 *SGD* 类型的优化方法来近似计算 $\mathcal{L}$ 的这样一个近似最小化点。我们现在简述普通 *SGD* 优化方法的情况（参见定义 7.2.1）。设 $\xi \in \mathbb{R}^{\mathfrak{d}}$，$J \in \mathbb{N}$，$(\gamma_{n})_{n \in \mathbb{N}} \subseteq [0, \infty)$，对于每个 $n \in \mathbb{N}$，$j \in \{1,2,\ldots,J\}$，设 $\mathfrak{T}_{n,j}: \Omega \rightarrow [0,T]$ 和 $\mathfrak{X}_{n,j}: \Omega \rightarrow \mathbb{R}^{d}$ 为随机变量，假设对于所有 $n \in \mathbb{N}$，$j \in \{1,2,\ldots,J\}$，$A \in \mathcal{B}([0,T])$，$B \in \mathcal{B}(\mathbb{R}^{d})$，有

$$\mathbb{P}(\mathcal{T} \in A) = \mathbb{P}(\mathfrak{T}_{n,j} \in A) \quad \text{且} \quad \mathbb{P}(\mathcal{X} \in B) = \mathbb{P}(\mathfrak{X}_{n,j} \in B), \tag{16.15}$$

设 $\mathscr{L}: \mathbb{R}^{\mathfrak{d}} \times [0, T] \times \mathbb{R}^{d} \rightarrow \mathbb{R}$ 满足对于所有 $\theta \in \mathbb{R}^{\mathfrak{d}}$，$t \in [0, T]$，$x \in \mathbb{R}^{d}$，有

$$\mathscr{L}(\theta, t, x)=\left|\mathcal{N}^{\theta, d+1}_{\mathfrak{A}_{a, l_{1}}, \mathfrak{A}_{a, l_{2}}, \ldots, \mathfrak{A}_{a, l_{h}}, \operatorname{id}_{\mathbb{R}}}(0, x)-g(x)\right|^{2} +\left(\frac{\partial \mathcal{N}^{\theta, d+1}_{\mathfrak{A}_{a, l_{1}}, \mathfrak{A}_{a, l_{2}}, \ldots, \mathfrak{A}_{a, l_{h}}, \operatorname{id}_{\mathbb{R}}}}{\partial t}(t, x)-\left(\Delta_{x} \mathcal{N}^{\theta, d+1}_{\mathfrak{A}_{a, l_{1}}, \mathfrak{A}_{a, l_{2}}, \ldots, \mathfrak{A}_{a, l_{h}}, \operatorname{id}_{\mathbb{R}}}(t, x) -f\left(\mathcal{N}^{\theta, d+1}_{\mathfrak{A}_{a, l_{1}}, \mathfrak{A}_{a, l_{2}}, \ldots, \mathfrak{A}_{a, l_{h}}, \operatorname{id}_{\mathbb{R}}}(t, x)\right)\right)^{2}, \tag{16.16}$$

且设 $\Theta=(\Theta_{n})_{n \in \mathbb{N}_{0}}: \mathbb{N}_{0} \times \Omega \rightarrow \mathbb{R}^{\mathfrak{d}}$ 满足对于所有 $n \in \mathbb{N}$，有

$$\Theta_{0}=\zeta \quad \text{且} \quad \Theta_{n}=\Theta_{n-1}-\gamma_{n}\left[\frac{1}{J} \sum_{j=1}^{J}\left(\nabla_{\theta} \mathscr{L}\right)\left(\Theta_{n-1}, \mathfrak{T}_{n, j}, \mathfrak{X}_{n, j}\right)\right]. \tag{16.17}$$

最后，PINNs 和 DGMs 的想法是，对于足够大的 $n \in \mathbb{N}$，选择实现 $\mathcal{N}^{\Theta_{n}, d+1}_{\mathfrak{A}_{a, l_{1}}, \mathfrak{A}_{a, l_{2}}, \ldots, \mathfrak{A}_{a, l_{h}}, \operatorname{id}_{\mathbb{R}}}$ 作为 (16.10) 中 PDE 未知解 $u$ 的近似值

$$\mathcal{N}^{\Theta_{n}, d+1}_{\mathfrak{A}_{a, l_{1}}, \mathfrak{A}_{a, l_{2}}, \ldots, \mathfrak{A}_{a, l_{h}}, \operatorname{id}_{\mathbb{R}}} \approx u \quad(16.18)$$

上述推导中的思想和所得到的方案最初是由 Raissi 等人 [347] 作为 PINNs 引入，由 Sirignano 和 Spiliopoulos [379] 作为 DGMs 引入。非常粗略地说，原本形式的 PINNs 和 DGMs 的区别在于随机变量 $(\mathfrak{T}_{n, j}, \mathfrak{X}_{n, j})_{(n, j) \in \mathbb{N} \times\{1,2, \ldots, J\}}$ 的联合分布的选择方式。宽松地说，在 PINNs 的情况下，最初提出的 $(\mathfrak{T}_{n, j}, \mathfrak{X}_{n, j})_{(n, j) \in \mathbb{N} \times\{1,2, \ldots, J\}}$ 的分布将基于对随机变量 $(\mathcal{T}, \mathcal{X})$ 绘制有限数量的样本，然后让随机变量 $(\mathfrak{T}_{n, j}, \mathfrak{X}_{n, j})_{(n, j) \in \mathbb{N} \times\{1,2, \ldots, J\}}$ 在这些样本中随机选取。在 DGMs 的情况下，最初的提议是选择 $(\mathfrak{T}_{n, j}, \mathfrak{X}_{n, j})_{(n, j) \in \mathbb{N} \times\{1,2, \ldots, J\}}$ 独立同分布。使用更复杂的优化方法（例如 Adam SGD 优化方法）的 PINNs 和 DGMs 实现可以在下一节中找到。

## 16.3 PIN 的实现

在下文源代码 16.1 中，我们展示了一个简单的 PINN 方法实现，该方法如上一节 16.2 中所述，用于寻找二维 Allen-Cahn 型半线性热方程的解 $u \in C^{1, 2}([0, 3] \times \mathbb{R}^{2})$ 的近似值

$$\left(\frac{\partial u}{\partial t}\right)(t, x)=\frac{1}{200}(\Delta_{x} u)(t, x)+u(t, x)-\left[u(t, x)\right]^{3} \quad(16.19)$$

其中对于 $t \in[0,3], x \in \mathbb{R}^{2}$，有 $u(0, x)=\sin \left(\|x\|_{2}^{2}\right)$。该实现遵循 Raissi 等人 [347] 中的原始提议，即首先选择随机变量

$(\mathcal{T}, \mathcal{X})$ 的 20000 个实现，其中 $\mathcal{T}$ 在 [0,3] 上服从连续均匀分布，且 $\mathcal{X}$ 在 $\mathbb{R}^{2}$ 上服从均值 $0 \in \mathbb{R}^{2}$ 且协方差 $4 I_{2} \in \mathbb{R}^{2 \times 2}$ 的正态分布（参见定义 1.5.5）。然后训练一个具有 4 个隐藏层（每个隐藏层有 50 个神经元）的全连接前馈 ANN，并使用参数为 1 的 swish 激活函数（参见 1.2.8 节）。训练使用大小为 256 的批次，每个批次从预先选出的随机变量 $(\mathcal{T}, \mathcal{X})$ 的 20000 个实现中选取。训练使用 Adam SGD 优化方法执行（参见 7.9 节）。经过 20000 个训练步骤后得到的解 $u$ 的近似值的绘图显示在图 16.1 中。

```python
import torch
import matplotlib.pyplot as plt
from torch.autograd import grad
from matplotlib.gridspec import GridSpec
from matplotlib.cm import ScalarMappable

dev = torch.device("cuda:0" if torch.cuda.is_available() else "cpu")

T = 3.0   # the time horizon
M = 20000 # the number of training samples

torch.manual_seed(0)

x_data = torch.randn(M, 2).to(dev) * 2
t_data = torch.rand(M, 1).to(dev) * T

# The initial value
def phi(x):
    return x.square().sum(axis=1, keepdims=True).sin()

# We use a network with 4 hidden layers of 50 neurons each and the
# Swish activation function (called SiLU in PyTorch)
N = torch.nn.Sequential(
    torch.nn.Linear(3, 50), torch.nn.SiLU(),
    torch.nn.Linear(50, 50), torch.nn.SiLU(),
    torch.nn.Linear(50, 50), torch.nn.SiLU(),
    torch.nn.Linear(50, 50), torch.nn.SiLU(),
    torch.nn.Linear(50, 1),
).to(dev)

optimizer = torch.optim.Adam(N.parameters(), lr=3e-4)

J = 256   # the batch size

for i in range(20000):
    # Choose a random batch of training samples
    indices = torch.randint(0, M, (J,))
```
