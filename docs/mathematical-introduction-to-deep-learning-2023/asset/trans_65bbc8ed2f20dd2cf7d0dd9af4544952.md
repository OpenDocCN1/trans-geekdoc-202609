
源代码 7.4 (code/optimization_methods/momentum_sgd.py)：实现带经典动量的 SGD 优化方法的 PyTorch Python 代码

```python
losses = []
print(f"lr = {lr}")

for n in range(N):
    indices = torch.randint(0, M, (J,))

    x = X[indices]
    y = Y[indices]

    net.zero_grad()

    loss_val = loss(net(x), y)
    loss_val.backward()

    with torch.no_grad():
        for m, p in zip(momentum, net.parameters()):
            m.mul_(alpha)
            m.add_((1 - alpha) * p.grad)
            p.sub_(lr * m)

    if n % 100 == 0:
        with torch.no_grad():
            x = (torch.rand((1000, 1)) - 0.5) * 4 * np.pi
            y = torch.sin(x)
            loss_val = loss(net(x), y)
            losses.append(loss_val.item())

axs[i].plot(losses, label=f"\\gamma = {lr}$")

axs[i].set_yscale("log")
axs[i].set_ylim([1e-6, 1])
axs[i].set_title(f"\\alpha = {alpha}$")
axs[0].legend()
plt.tight_layout()
plt.savefig("../plots/sgd_momentum.pdf", bbox_inches='tight')
```

## 7.4.1 带偏差校正的经典动量 SGD 优化方法

**定义 7.4.2**（带偏差校正的动量 SGD 优化方法）。设 $d \in \mathbb{N}$，$(\gamma_n)_{n\in\mathbb{N}} \subseteq [0,\infty)$，$(J_n)_{n\in\mathbb{N}} \subseteq \mathbb{N}$，$(\alpha_n)_{n\in\mathbb{N}} \subseteq [0,1]$ 满足 $\alpha_1 < 1$，设 $(\Omega, \mathcal{F}, \mathbb{P})$ 为一个概率空间，设 $(S, \mathcal{S})$ 为一个可测空间，设 $\xi: \Omega \rightarrow \mathbb{R}^{d}$ 为一个随机变量，对于每个 $n \in \mathbb{N}$，$j \in \{1, 2, \dots, J_n\}$，设 $X_{n,j}: \Omega \rightarrow S$ 为一个随机变量，并设 $\mathcal{L} = (\mathcal{L}(\theta, x))_{(\theta, x) \in \mathbb{R}^{d} \times S}: \mathbb{R}^{d} \times S \rightarrow \mathbb{R}$ 和 $\boldsymbol{g} = (\boldsymbol{g}_1, \dots, \boldsymbol{g}_d): \mathbb{R}^{d} \times S \rightarrow \mathbb{R}^{d}$ 满足对于所有 $U \in \{V \subseteq \mathbb{R}^{d}: V \text{ 是开集}\}$，$x \in S$，$\theta \in U$，且 $(U \supseteq \varnothing \mapsto \mathcal{L}(\theta, x) \in \mathbb{R} \text{ 是 } C^1(U, \mathbb{R}))$，有

$$ \boldsymbol{g}(\theta, x) = (\nabla_{\theta}\mathcal{L})(\theta, x). \quad (7.112) $$

则我们称 $\Theta$ 是针对损失函数 $\mathcal{L}$ 及其广义梯度 $\boldsymbol{g}$、学习率 $(\gamma_n)_{n \in \mathbb{N}}$、批量大小 $(J_n)_{n \in \mathbb{N}}$、动量衰减因子 $(\alpha_n)_{n \in \mathbb{N}}$、初始值 $\xi$ 和数据 $(X_{n,j})_{(n,j) \in \{(k,i) \in \mathbb{N}_0^2: i \le J_k\}}$ 在 $((\Omega, \mathcal{F}, \mathbb{P}), (S, \mathcal{S}))$ 上的带偏差校正的动量 **SGD** 过程（当且仅当 $\Phi: \mathbb{N}_0 \rightarrow \Omega \rightarrow \mathbb{R}^{d}$ 是从 $\mathbb{N}_0 \times \Omega$ 到 $\mathbb{R}^{d}$ 的函数，并且满足存在 $\boldsymbol{m}: \mathbb{N}_0 \times \Omega \rightarrow \mathbb{R}^{d}$，使得对于所有 $n \in \mathbb{N}$，有

$$ \Theta_0 = \xi, \quad \boldsymbol{m}_0 = 0, \quad (7.113) $$
$$ \boldsymbol{m}_n = \alpha_n \boldsymbol{m}_{n-1} + (1-\alpha_n) \left[ \frac{1}{J_n} \sum_{j=1}^{J_n} \boldsymbol{g}(\Theta_{n-1}, X_{n,j}) \right], \quad (7.114) $$
$$ \text{且} \quad \Theta_n = \Theta_{n-1} - \frac{\gamma_n \boldsymbol{m}_n}{1 - \prod_{i=1}^{n} \alpha_i}. \quad (7.115) $$

![](img/dec290f673e6357c31893c67b579ffe1_307_0.png)

图 7.3 (plots/sgd_momentum.pdf)：展示动量衰减率和学习率在使用带经典动量的 SGD 优化方法训练人工神经网络（ANN）过程中对损失影响的曲线图

带偏差校正的动量 SGD 优化方法在 PyTorch 中的实现见源代码 7.5。

源代码 7.5 (code/optimization_methods/momentum_sgd_bias_adj.py)：实现带偏差校正的动量 SGD 优化方法的 PyTorch Python 代码

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
lr = 0.01
alpha = 0.99
adj = 1

momentum = [p.clone().detach().zero_() for p in net.parameters()]

for n in range(N):
    indices = torch.randint(0, M, (J,))

    x = X[indices]
    y = Y[indices]

    net.zero_grad()

    loss_val = loss(net(x), y)
    loss_val.backward()

    adj *= alpha

    with torch.no_grad():
        for m, p in zip(momentum, net.parameters()):
            m.mul_(alpha)
            m.add_((1-alpha) * p.grad)
            p.sub_(lr * m / (1 - adj))

    if n % 1000 == 0:
        with torch.no_grad():
            x = torch.rand((1000, 1)) * 4 * np.pi - 2 * np.pi
            y = torch.sin(x)
            loss_val = loss(net(x), y)
            print(f"Iteration: {n+1}, Loss: {loss_val}")
```

在本节中，我们介绍第 6.4 节中 Nesterov 加速 GD 优化方法的随机版本（参见 [302, 387]）。

**定义 7.5.1**（Nesterov 加速 SGD 优化方法）。设 $d \in \mathbb{N}$，$(\gamma_n)_{n \in \mathbb{N}} \subseteq [0, \infty)$，$(J_n)_{n \in \mathbb{N}} \subseteq \mathbb{N}$，$(\alpha_n)_{n \in \mathbb{N}} \subseteq [0, 1]$，设 $(\Omega, \mathcal{F}, \mathbb{P})$ 为一个概率空间，设 $(S, \mathcal{S})$ 为一个可测空间，设 $\xi : \Omega \rightarrow \mathbb{R}^{d}$ 为一个随机变量，对于每个 $n \in \mathbb{N}$，$j \in \{1, 2, \ldots, J_n\}$，设 $X_{n, j} : \Omega \rightarrow S$ 为一个随机变量，并设 $\ell = (\ell(\theta, x))_{(\theta, x) \in \mathbb{R}^{d} \times S} : \mathbb{R}^{d} \times S \rightarrow \mathbb{R}$ 和 $\boldsymbol{g} = (\boldsymbol{g}_{1}, \ldots, \boldsymbol{g}_{d}) : \mathbb{R}^{d} \times S \rightarrow \mathbb{R}^{d}$ 满足对于所有 $U \in \{V \subseteq \mathbb{R}^{d} : V \text{ 是开集}\}$，$x \in S$，$\theta \in U$，且 $(U \ni \psi \mapsto \ell(\psi, x) \in \mathbb{R}) \in C^{1}(U, \mathbb{R})$，有

$$ \boldsymbol{g}(\theta, x)=(\nabla_{\theta} \ell)(\theta, x). \quad (7.116) $$

则我们称 $\Theta$ 是针对损失函数 $\ell$ 及其广义梯度 $\boldsymbol{g}$、学习率 $(\gamma_n)_{n \in \mathbb{N}}$、批量大小 $(J_n)_{n \in \mathbb{N}}$、动量衰减因子 $(\alpha_n)_{n \in \mathbb{N}}$、初始值 $\xi$ 和数据 $(X_{n, j})_{(n, j) \in \{(k, i) \in \mathbb{N}_0^2 : i \leq J_k\}}$ 在 $(\Omega, \mathcal{F}, \mathbb{P}), (S, \mathcal{S})$ 上的 Nesterov 加速 SGD 过程，当且仅当 $\Theta : \mathbb{N}_{0} \times \Omega \rightarrow \mathbb{R}^{d}$ 是从 $\mathbb{N}_{0} \times \Omega$ 到 $\mathbb{R}^{d}$ 的函数，并且满足存在 $\mathbf{m} : \mathbb{N}_{0} \times \Omega \rightarrow \mathbb{R}^{d}$，使得对于所有 $n \in \mathbb{N}$，有

$$ \Theta_{0}=\xi,\quad\mathbf{m}_{0}=0, \quad (7.117) $$
$$ \mathbf{m}_{n}=\alpha_{n} \mathbf{m}_{n-1}+\left(1-\alpha_{n}\right)\left[\frac{1}{J_{n}} \sum_{j=1}^{J_{n}} \boldsymbol{g}\left(\Theta_{n-1}-\gamma_{n} \alpha_{n} \mathbf{m}_{n-1}, X_{n, j}\right)\right], \quad (7.118) $$
$$ \text{且} \quad \Theta_{n}=\Theta_{n-1}-\gamma_{n} \mathbf{m}_{n} . \quad (7.119) $$

Nesterov 加速 SGD 优化方法在 PyTorch 中的实现见源代码 7.6。

```python
import torch
import torch.nn as nn
import numpy as np
net = nn.Sequential(nn.Linear(1, 200), nn.ReLU(), nn.Linear(200, 1))
M = 1000
X = torch.rand((M, 1)) * 4 * np.pi - 2 * np.pi
Y = torch.sin(X)
```

