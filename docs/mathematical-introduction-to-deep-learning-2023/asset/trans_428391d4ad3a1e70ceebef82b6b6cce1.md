
16  N = 150000
17
18  loss = nn.MSELoss()
19  lr = 0.001
20  beta = 0.9
21  eps = 1e-10
22
23  moments = [p.clone().detach().zero_() for p in net.parameters()]
24
25  for n in range(N):
26      indices = torch.randint(0, M, (J,))
27
28      x = X[indices]
29      y = Y[indices]
30
31      net.zero_grad()
32
33      loss_val = loss(net(x), y)
34      loss_val.backward()
35
36      with torch.no_grad():
37          for m, p in zip(moments, net.parameters()):
38              m.mul_(beta)
39              m.add_((1 - beta) * p.grad * p.grad)
40              p.sub_(lr * (eps + m).rsqrt() * p.grad)
41
42      if n % 1000 == 0:
43          with torch.no_grad():
44              x = torch.rand((1000, 1)) * 4 * np.pi - 2 * np.pi
45              y = torch.sin(x)
46              loss_val = loss(net(x), y)
47              print(f"Iteration: {n+1}, Loss: {loss_val}")

源码 7.8 (code/optimization_methods/rmsprop.py)：使用 PYTORCH 实现 RMSprop 随机梯度下降（SGD）优化方法的 PYTHON 代码

### 7.7.1 偏差校正的均方根反向传播 SGD 优化

**定义 7.7.3** (偏差校正 RMSprop SGD 优化方法)。设 $\mathfrak{d}\in\mathbb{N}$，$(\gamma_{n})_{n\in\mathbb{N}}\subseteq[0,\infty)$，$(J_{n})_{n\in\mathbb{N}}\subseteq\mathbb{N}$，$(\beta_{n})_{n\in\mathbb{N}}\subseteq[0,1]$，$\varepsilon\in(0,\infty)$ 满足 $\beta_{1}<1$，设 $(\Omega,\mathcal{F},\mathbb{P})$ 为概率空间，设 $(S,\mathcal{S})$ 为可测空间，设 $\xi:\Omega\to\mathbb{R}^{\mathfrak{d}}$ 为随机变量。对于每个 $n\in\mathbb{N}$ 和 $j\in\{1,2,\dots,J_{n}\}$，设 $X_{n,j}:\Omega\to S$ 为随机变量，且设 $\ell=(\ell(\theta,x))_{(\theta,x)\in\mathbb{R}^{\mathfrak{d}}\times S}:\mathbb{R}^{\mathfrak{d}}\times S\to\mathbb{R}$ 和 $\boldsymbol{g}=(\boldsymbol{g}_{1},\dots,\boldsymbol{g}_{\mathfrak{d}}):\mathbb{R}^{\mathfrak{d}}\times S\to\mathbb{R}^{\mathfrak{d}}$ 满足对于所有 $U \in\{V \subseteq \mathbb{R}^{\mathfrak{d}}$: $V$ 是开集$\}$，$x \in S$，以及使得 $(U \cup \varnothing \to \ell(\vartheta, x) \in \mathbb{R}) \in C^{1}(U, \mathbb{R})$ 的 $\vartheta \in U$，有

$$\vartheta^{\prime} \vartheta(\vartheta, x)=(\nabla \ell^{\vartheta^{\prime}})(\vartheta, x) \text{.} \qquad(7.143)$$

则我们称 $\Theta$ 为基于损失函数 $\ell$、广义梯度 $\vartheta^{\prime}$、学习率 $(\gamma_{n})_{n \in \mathbb{N}}$、批量大小 $(J_{n})_{n \in \mathbb{N}}$、二阶矩衰减因子 $(\beta_{n})_{n \in \mathbb{N}}$、正则化因子 $\varepsilon$、初始值 $\xi$ 以及数据 $(X_{n, j})_{(n, j) \in\{k, \ell\} \times \{j: 1 \leq J_{k}\}}$ 的偏差校正 RMSprop **SGD** 过程在 $((\Omega, \mathcal{F}, \mathbb{P}), (S, \mathcal{S}))$ 上（即当且仅当存在从 $\mathbb{N}_{0} \times \Omega$ 到 $\mathbb{R}^{\mathfrak{d}}$ 的函数 $\Theta=(\Theta^{(1)}, \ldots, \Theta^{(\mathfrak{d})}): \mathbb{N}_{0} \times \Omega \rightarrow \mathbb{R}^{\mathfrak{d}}$ 满足存在 $\mathbb{M}=(\mathbb{M}^{(1)}, \ldots, \mathbb{M}^{(\mathfrak{d})}): \mathbb{N}_{0} \times \Omega \rightarrow \mathbb{R}^{\mathfrak{d}}$ 使得对于所有 $n \in \mathbb{N}$ 和 $i \in\{1,2, \ldots, \mathfrak{d}\}$ 均成立时，我们称 $\Theta$ 为基于损失函数 $\ell$、学习率 $(\gamma_{n})_{n \in \mathbb{N}}$、批量大小 $(J_{n})_{n \in \mathbb{N}}$、二阶矩衰减因子 $(\beta_{n})_{n \in \mathbb{N}}$、正则化因子 $\varepsilon$、初始值 $\xi$ 以及数据 $(X_{n, j})_{(n, j) \in\{k, \ell\} \times \{j: 1 \leq J_{k}\}}$ 的偏差校正 RMSprop **SGD** 过程

$$\Theta_{0} \equiv \xi \text{, } \mathbb{M}_{0} \equiv 0 \text{,} \qquad \qquad \qquad(7.144)$$

$$\mathbb{M}_{n}^{(i)} = \beta_{n} \mathbb{M}_{n-1}^{(i)} + \left(1 - \beta_{n}\right)\left[\frac{1}{J_{n}} \sum_{j = 1}^{J_{n}} \vartheta_{i}(\Theta_{n-1}, X_{n, j})\right]^{2} \text{,} \qquad \qquad(7.145)$$

并且 $\Theta_{n}^{(i)} = \Theta_{n-1}^{(i)} - \gamma_{n}\left[\varepsilon + \left[\left(\frac{\mathbb{M}_{n}^{(i)}}{(1 - \prod_{l = 1}^{n} \beta_{l})}\right)\right]^{1/2}\right]^{-1}\left[\frac{1}{J_{n}} \sum_{j = 1}^{J_{n}} \vartheta_{i}(\Theta_{n-1}, X_{n, j})\right]$ 。 $\qquad(7.146)$

上述**定义 7.7.3**中描述的偏差校正 RMSprop **SGD** 优化方法在 **PYTORCH** 中的实现见**源码 7.9**。

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
lr = 0.001
beta = 0.9
eps = 1e-10
adj = 1
```

23  moments = [p.clone().detach().zero_() for p in net.parameters()]
24
25  for n in range(N):
26      indices = torch.randint(0, M, (J,))
27
28      x = X[indices]
29      y = Y[indices]
30
31      net.zero_grad()
32
33      loss_val = loss(net(x), y)
34      loss_val.backward()
35
36      with torch.no_grad():
37          adj *= beta
38          for m, p in zip(moments, net.parameters()):
39              m.mul_(beta)
40              m.add_((1 - beta) * p.grad * p.grad)
41              p.sub_(lr * (eps + (m / (1 - adj)).sqrt().reciprocal()
42                  * p.grad)
43
44          if n % 1000 == 0:
45              with torch.no_grad():
46                  x = torch.rand((1000, 1)) * 4 * np.pi - 2 * np.pi
47                  y = torch.sin(x)
48                  loss_val = loss(net(x), y)
49                  print(f"Iteration: {n+1}, Loss: {loss_val}")

源码 7.9 (code/optimization_methods/rmsprop_bias_adj.py)：使用 PyTorch 实现偏差校正 RMSprop SGD 优化方法的 PYTHON 代码

# 7.8 Adadelta SGD 优化

在本节中，我们介绍第 6.7 节（参见 Zeiler [429]）中 Adadelta 梯度下降（GD）优化方法的随机版本。

**定义 7.8.1** (Adadelta SGD 优化方法)。设 $\vartheta \in \mathbb{N}$，$(J_n)_{n \in \mathbb{N}} \subseteq \mathbb{N}$，$(\beta_n)_{n \in \mathbb{N}} \subseteq [0, 1]$，$(\delta_n)_{n \in \mathbb{N}} \subseteq [0, 1]$，$\varepsilon \in (0, \infty)$，设 $(\Omega, \mathcal{F}, \mathbb{P})$ 为概率空间，设 $(S, \mathcal{S})$ 为可测空间，设 $\xi: \Omega \rightarrow \mathbb{R}^p$ 为随机变量。对于每个 $n \in \mathbb{N}$ 和 $j \in \{1, 2, \dots, J_n\}$，设 $X_{n,j}: \Omega \rightarrow S$ 为随机变量，且设 $\ell = (\ell(\theta, x))_{(\theta, x) \in \mathbb{R}^p \times S}: \mathbb{R}^p \times S \rightarrow \mathbb{R}$ 和 $\boldsymbol{g} = (\boldsymbol{g}_1, \dots, \boldsymbol{g}_q): \mathbb{R}^p \times S \rightarrow \mathbb{R}^q$ 满足对于所有 $U \in \{V \subseteq \mathbb{R}^p: V$ 是开集\}，$x \in S$，以及使得 $(U \ni \vartheta \mapsto \ell(\vartheta, x) \in \mathbb{R}) \in C^1(U, \mathbb{R})$ 的 $\theta \in U$，有

$$\boldsymbol{g}(\theta, x) = (\nabla_{\theta} \ell^i)(\theta, x). \tag{7.147}$$

则我们称 $\Theta$ 为基于损失函数 $\ell$、广义梯度 $\boldsymbol{\mathcal{G}}$、批量大小 $(J_n)_{n \in \mathbb{N}}$、二阶矩衰减因子 $(\beta_n)_{n \in \mathbb{N}}$、delta 衰减因子 $(\delta_n)_{n \in \mathbb{N}}$、正则化因子 $\varepsilon$、初始值 $\boldsymbol{\xi}$ 以及数据 $(\boldsymbol{X}_{n,j})_{(n, j) \in \{\kappa_0\} \in \mathbb{N}^2: 1 \leq j \leq J_k}$ 的 *Adadelta SGD* 过程在 $(\Omega, \mathcal{F}, \mathbb{P}), (S, \mathcal{S})$ 上（即当且仅当存在从 $\mathbb{N}_0 \times \Omega$ 到 $\mathbb{R}^3$ 的函数 $\Theta = (\Theta^{(1)}, \ldots, \Theta^{(3)}): \mathbb{N}_0 \times \Omega \to \mathbb{R}^3$ 满足存在 $\mathbb{M} = (\mathbb{M}^{(1)}, \ldots, \mathbb{M}^{(3)}): \mathbb{N}_0 \times \Omega \to \mathbb{R}^3$ 和 $\Delta = (\Delta^{(1)}, \ldots, \Delta^{(3)}): \mathbb{N}_0 \times \Omega \to \mathbb{R}^3$ 使得对于所有 $n \in \mathbb{N}$ 和 $i \in \{1, 2, \ldots, \boldsymbol{d}\}$ 均成立时，我们称 $\Theta$ 为基于损失函数 $\ell$、批量大小 $(J_n)_{n \in \mathbb{N}}$、二阶矩衰减因子 $(\beta_n)_{n \in \mathbb{N}}$、delta 衰减因子 $(\delta_n)_{n \in \mathbb{N}}$、正则化因子 $\varepsilon$、初始值 $\boldsymbol{\xi}$ 以及数据 $(\boldsymbol{X}_{n,j})_{(n, j) \in \{\kappa_0\} \in \mathbb{N}^2: 1 \leq j \leq J_k}$ 的 *Adadelta SGD* 过程

$\Theta_0 = \boldsymbol{\xi}, \quad \mathbb{M}_0 = 0, \quad \Delta_0 = 0, \qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad (7.148)$

$\mathbb{M}_n^{(i)} = \beta_n \mathbb{M}_{n-1}^{(i)} + (1 - \beta_n) \left[ \frac{1}{J_n} \sum_{j=1}^{J_n} \boldsymbol{\mathcal{G}}_i(\Theta_{n-1}, \boldsymbol{X}_{n,j}) \right]^2, \qquad\qquad (7.149)$

$\Theta_n^{(i)} = \Theta_{n-1}^{(i)} - \left( \frac{\varepsilon + \Delta_{n-1}^{(i)}}{\varepsilon + \mathbb{M}_n^{(i)}} \right)^{1/2} \left[ \frac{1}{J_n} \sum_{j=1}^{J_n} \boldsymbol{\mathcal{G}}_i(\Theta_{n-1}, \boldsymbol{X}_{n,j}) \right], \qquad (7.150)$

并且 $\qquad \Delta_n^{(i)} = \delta_n \Delta_{n-1}^{(i)} + (1 - \delta_n) |\Theta_n^{(i)} - \Theta_{n-1}^{(i)}|^2. \qquad\qquad\qquad\qquad\qquad\qquad\qquad (7.151)$

上述*定义 7.8.1*中描述的 Adadelta *SGD* 优化方法在 PyTorch 中的实现见*源码 7.10*。上述*定义 7.8.1*中描述的 *Adadelta SGD* 优化方法也可以在 PyTorch 中以内置的 *torch.optim.Adadelta* 优化器的形式获得（在实际应用中，通常优先于从零开始实现）。

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
beta = 0.9
```

