
## 7.6. Adagrad 随机梯度下降优化（Adagrad）

**定义 7.6.1**（Adagrad 随机梯度下降优化方法）。设 $\boldsymbol{d} \in \mathbb{N}$，$(\gamma_n)_{n \in \mathbb{N}} \subseteq [0, \infty)$，$(J_n)_{n \in \mathbb{N}} \subseteq \mathbb{N}$，$\varepsilon \in (0, \infty)$，设 $(\Omega, \mathcal{F}, \mathbb{P})$ 为一个概率空间，设 $(\mathcal{S}, \boldsymbol{S})$ 为一个可测空间，设 $\xi: \Omega \to \mathbb{R}^{\boldsymbol{d}}$ 为一个随机变量，对于每个 $n \in \mathbb{N}$，$j \in \{1, 2, \ldots, J_n\}$，设 $X_{n,j}: \Omega \to \mathcal{S}$ 为一个随机变量，并且设 $\ell = (\ell(\theta, x))_{(\theta, x) \in \mathbb{R}^{\boldsymbol{d}} \times \mathcal{S}}: \mathbb{R}^{\boldsymbol{d}} \times \mathcal{S} \to \mathbb{R}$ 和 $\boldsymbol{g} = (\boldsymbol{g}_1, \ldots, \boldsymbol{g}_{\boldsymbol{d}}): \mathbb{R}^{\boldsymbol{d}} \times \mathcal{S} \to \mathbb{R}^{\boldsymbol{d}}$ 满足对于所有属于 $\{V \subseteq \mathbb{R}^{\boldsymbol{d}}: V \text{ 是开集的}\}$ 的 $U$，$x \in \mathcal{S}$，以及满足 $(U \ni \psi \mapsto \ell(\psi, x) \in \mathbb{R}) \in C^1(U, \mathbb{R})$ 的 $\theta \in U$，有

$$\boldsymbol{g}(\theta, x) = (\nabla_{\theta} \ell)(\theta, x). \tag{7.137}$$

那么，我们称 $\Theta$ 是关于损失函数 $\ell$、广义梯度 $\boldsymbol{g}$、学习率 $(\gamma_n)_{n \in \mathbb{N}}$、批量大小 $(J_n)_{n \in \mathbb{N}}$、正则化因子 $\varepsilon$、初始值 $\xi$ 以及数据 $(X_{n,j})_{(n, j) \in \{(k, l) \in \mathbb{N}^2: l \leq J_k\}}$ 在 $((\Omega, \mathcal{F}, \mathbb{P}), (\mathcal{S}, \boldsymbol{S}))$ 上的 Adagrad 随机梯度下降过程（当且仅当 $\Theta = (\Theta^{(1)}, \ldots, \Theta^{(\boldsymbol{d})}): \mathbb{N}_0 \times \Omega \to \mathbb{R}^{\boldsymbol{d}}$ 是从 $\mathbb{N}_0 \times \Omega$ 到 $\mathbb{R}^{\boldsymbol{d}}$ 的函数，且满足对于所有 $n \in \mathbb{N}$，$i \in \{1, 2, \ldots, \boldsymbol{d}\}$，都有 $\Theta_0 = \xi$ 且

$$\Theta_n^{(i)} = \Theta_{n-1}^{(i)} - \gamma_n \left( \varepsilon + \left[ \sum_{k=1}^{n} \left( \frac{1}{J_k} \sum_{j=1}^{J_k} \boldsymbol{g}_{i, j}(\Theta_{k-1}, X_{k, j}) \right)^2 \right]^{1/2 - 1} \right) \left[ \frac{1}{J_n} \sum_{j=1}^{J_n} \boldsymbol{g}_{i, j}(\Theta_{n-1}, X_{n, j}) \right]. \tag{7.138}$$

上述定义 7.6.1 中描述的 Adagrad 随机梯度下降优化方法的 PyTorch 实现见源码 7.7。上述定义 7.6.1 中描述的 Adagrad 随机梯度下降优化方法也可在 PyTorch 中以内置优化器 `torch.optim.Adagrad` 的形式获得（在实际应用中，通常更推荐使用内置优化器而非从头开始实现）。

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
lr = 0.02
eps = 1e-10

sum_sq_grad = [p.clone().detach().fill_(eps) for p in net.parameters()]

for n in range(N):
    indices = torch.randint(0, M, (J,))

    x = X[indices]
    y = Y[indices]

    net.zero_grad()

    loss_val = loss(net(x), y)
    loss_val.backward()

    with torch.no_grad():
        for a, p in zip(sum_sq_grad, net.parameters()):
            a.add_(p.grad * p.grad)
            p.sub_(lr * a.rsqrt() * p.grad)

    if n % 1000 == 0:
        with torch.no_grad():
            x = torch.rand((1000, 1)) * 4 * np.pi - 2 * np.pi
            y = torch.sin(x)
            loss_val = loss(net(x), y)
            print(f"Iteration: {n+1}, Loss: {loss_val}")
```

源码 7.7（*code/optimization_methods/adagrad.py*）：使用 PyTorch 实现 Adagrad 随机梯度下降优化方法的 Python 代码。

## 7.7 均方根反向传播随机梯度下降优化（RMSPROP）

在本节中，我们介绍第 6.6 节中 RMSprop 梯度下降优化方法的随机版本（参见 Hinton 等人 [199]）。

**定义 7.7.1**（RMSprop 随机梯度下降优化方法）。设 $\mathbf{d} \in \mathbb{N}$，$(\gamma_{n})_{n \in \mathbb{N}} \subseteq [0, \infty)$，$(J_{n})_{n \in \mathbb{N}} \subseteq \mathbb{N}$，$(\beta_{n})_{n \in \mathbb{N}} \subseteq [0, 1]$，$\varepsilon \in (0, \infty)$，设 $(\Omega, \mathcal{F}, \mathbb{P})$ 为一个概率空间，设 $(S, \mathcal{S})$ 为一个可测空间，设 $\xi: \Omega \rightarrow \mathbb{R}^{d}$ 为一个随机变量，对于每个 $n \in \mathbb{N}$，$j \in \{ 1, 2, \ldots, J_{n} \}$，设 $X_{n,j}: \Omega \rightarrow S$ 为一个随机变量，并且设 $\ell = (\ell(\theta, x))_{(\theta, x) \in \mathbb{R}^{d} \times S}: \mathbb{R}^{d} \times S \rightarrow \mathbb{R}$ 和 $\mathbf{g} = (\mathbf{g}_{1}, \ldots, \mathbf{g}_{d}): \mathbb{R}^{d} \times S \rightarrow \mathbb{R}^{d}$ 满足对于所有属于 $\{ V \subseteq \mathbb{R}^{d}: V$ 是开集$\}$ 的 $U$，$x \in S$，以及满足 $(U \supset \vartheta \mapsto \mathcal{L}(\vartheta, x) \in \mathbb{R}) \in C^{1}(U, \mathbb{R})$ 的 $\theta \in U$，有

$$\boldsymbol{g}(\theta, x) = (\nabla_{\theta} \mathcal{L})(\theta, x). \tag{7.139}$$

那么，我们称 $\Theta$ 是关于损失函数 $\mathcal{L}$、广义梯度 $\boldsymbol{g}$、学习率 $(\gamma_{n})_{n \in \mathbb{N}}$、批量大小 $(J_{n})_{n \in \mathbb{N}}$、二阶矩衰减因子 $(\beta_{n})_{n \in \mathbb{N}}$、正则化因子 $\varepsilon$、初始值 $\boldsymbol{\xi}$ 以及数据 $(X_{n, j})_{(n, j) \in(\{k, l \in \mathbb{N}: l \leq J_{k}\})}$ 的 RMSprop 随机梯度下降过程，当且仅当存在 $\mathbb{M}=(\mathbb{M}^{(1)}, \ldots, \mathbb{M}^{(\mathbf{d})}): \mathbb{N}_{0} \times \Omega \rightarrow \mathbb{R}^{\mathbf{d}}$，使得 $\Theta=(\Theta^{(1)}, \ldots, \Theta^{(\mathbf{d})}): \mathbb{N}_{0} \times \Omega \rightarrow \mathbb{R}^{\mathbf{d}}$ 是从 $\mathbb{N}_{0} \times \Omega$ 到 $\mathbb{R}^{\mathbf{d}}$ 的函数，并且满足对于所有 $n \in \mathbb{N}$，$i \in\{1,2, \ldots, \mathbf{d}\}$，有

$$\Theta_{0}=\boldsymbol{\xi}, \quad \mathbb{M}_{0}=0, \tag{7.140}$$

$$\mathbb{M}_{n}^{(i)}=\beta_{n} \mathbb{M}_{n-1}^{(i)}+\left(1-\beta_{n}\right)\left[\frac{1}{J_{n}} \sum_{j=1}^{J_{n}} \boldsymbol{g}_{i}\left(\Theta_{n-1}, X_{n, j}\right)\right]^{2}, \tag{7.141}$$

以及

$$\Theta_{n}^{(i)}=\Theta_{n-1}^{(i)}-\frac{\gamma_{n}}{\varepsilon+\left[\mathbb{M}_{n}^{(i)}\right]^{1 / 2}}\left[\frac{1}{J_{n}} \sum_{j=1}^{J_{n}} \boldsymbol{g}_{i}\left(\Theta_{n-1}, X_{n, j}\right)\right]. \tag{7.142}$$

**注 7.7.2.** 在 Hinton 等人 [199] 中，建议将 $0.9 = \beta_{1} = \beta_{2} = \ldots$ 作为定义 7.7.1 中二阶矩衰减因子 $(\beta_{n})_{n \in \mathbb{N}} \subseteq [0,1]$ 的默认值。

上述定义 7.7.1 中描述的 RMSprop 随机梯度下降优化方法的 PyTorch 实现见源码 7.8。上述定义 7.7.1 中描述的 RMSprop 随机梯度下降优化方法也可在 PyTorch 中以内置优化器 `torch.optim.RMSprop` 的形式获得（在实际应用中，通常更推荐使用内置优化器而非从头开始实现）。

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
```

