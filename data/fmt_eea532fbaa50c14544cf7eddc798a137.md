
### 55
`initial_loss = (u0 - phi(x)).square().mean()`

57
# 使用自动
# 微分计算偏导数
`u = N(torch.hstack((t, x1, x2)))`
`ones = torch.ones_like(u)`
`u_t = grad(u, t, ones, create_graph=True)[0]`
`u_x1 = grad(u, x1, ones, create_graph=True)[0]`
`u_x2 = grad(u, x2, ones, create_graph=True)[0]`
`ones = torch.ones_like(u_x1)`
`u_xx1 = grad(u_x1, x1, ones, create_graph=True)[0]`
`u_x2x2 = grad(u_x2, x2, ones, create_graph=True)[0]`

68
# 计算偏微分方程（PDE）的损失
`Laplace = u_x1x1 + u_x2x2`
`pde_loss = (u_t - (0.005 * Laplace + u - u**3)).square().mean()`

72
# 计算总损失并执行梯度步骤
`loss = initial_loss + pde_loss`
`loss.backward()`
`optimizer.step()`

### 绘制不同时间点的解

`mesh = 128`
`a, b = -3, 3`
`gs = GridSpec(2, 4, width_ratios=[1, 1, 1, 0.05])`
`fig = plt.figure(figsize=(16, 10), dpi=300)`
`x, y = torch.meshgrid(`
`torch.linspace(a, b, mesh),`
`torch.linspace(a, b, mesh),`
`indexing="xy"`
`)`
`x = x.reshape((mesh * mesh, 1)).to(dev)`
`y = y.reshape((mesh * mesh, 1)).to(dev)`

`for i in range(6):`
`t = torch.full((mesh * mesh, 1), i * T / 5).to(dev)`
`z = N(torch.cat((t, x, y), 1))`
`z = z.detach().cpu().numpy().reshape((mesh, mesh))`
`ax = fig.add_subplot(gs[i // 3, i % 3])`
`ax.set_title(f"t = {i * T / 5}")`
`ax.imshow(`
`z, cmap="viridis", extent=[a, b, a, b], vmin=-1.2, vmax=1.2`
`)`

# 在图表中添加颜色条
`norm = plt.Normalize(vmin=-1.2, vmax=1.2)`
`sm = ScalarMappable(cmap="viridis", norm=norm)`
`cax = fig.add_subplot(gs[:, 3])`
`fig.colorbar(sm, cax=cax, orientation="vertical")`
`fig.savefig("../plots/pinn.pdf", bbox_inches="tight")`

源码 16.1 (`code/pinn.py`)：使用 `PyTorch` 实现的 PINN 方法简单实现，用于计算函数 $u \in C^{1,2}([0,3] \times \mathbb{R}^{2}, \mathbb{R})$ 的近似值，该函数满足对于所有 $t \in [0,2]$，$x \in \mathbb{R}^{2}$，有 $(\frac{\partial u}{\partial t})(t, x) = \frac{1}{200}(\Delta_{x}u)(t, x) + u(t, x) - [u(t, x)]^{3}$ 且 $u(0, x) = \sin(\|x\|_{2}^{2})$（参见定义 3.3.4）。该代码生成的绘图如图 16.1 所示。

## 16.4 DGMs 的实现

在下述源码 16.2 中，我们展示了 DGM 的一个简单实现，如上文第 16.2 节所述，用于寻找二维 Allen–Cahn 型半线性热方程解的近似值 $u \in C^{1,2}([0,3] \times \mathbb{R}^{2})$

$$(\frac{\partial u}{\partial t})(t, x) = \frac{1}{200}(\Delta_{x}u)(t, x) + u(t, x) - [u(t, x)]^{3} \tag{16.20}$$

其中对于 $t \in [0,3]$，$x = (x_{1}, x_{2}) \in \mathbb{R}^{2}$，初始条件为 $u(0, x) = \sin(x_{1})\sin(x_{2})$。正如 Sgrignolo & Spiliopoulos [379] 最初提议的那样，该实现在每个训练步骤中选取随机变量 $(\mathcal{T}, \mathcal{X})$ 的 256 个实现组成的批次，其中 $\mathcal{T}$ 在 $[0,3]$ 上均匀分布，$\mathcal{X}$ 在 $\mathbb{R}^{2}$ 上正态分布，均值为 $\mathbb{R}^{2}$ 中的 $0$，协方差为 $4I_{2} \in \mathbb{R}^{2 \times 2}$（参见定义 1.5.5）。与源码 16.1 中的 PINN 实现类似，它训练一个具有 4 个隐藏层的全连接前馈人工神经网络（每个隐藏层包含 50

![](img/dec290f673e6357c31893c67b579ffe1_516_0.png)

图 16.1 (`plots/pinn.pdf`)：函数 $[-3, 3]^{2} \ni x \mapsto U(t, x) \in \mathbb{R}$ 的绘图，其中 $t \in \{0, 0.6, 1.2, 1.8, 2.4, 3\}$，且 $U \in C([0,3] \times \mathbb{R}^{2}, \mathbb{R})$ 是函数 $u \in C^{1, 2}([0, 3] \times \mathbb{R}^{2}, \mathbb{R})$ 的近似值，该函数满足对于所有 $t \in [0, 3], x \in \mathbb{R}^{2}$ 有 $(\frac{\partial u}{\partial t})(t, x) = \frac{1}{200}(\Delta_{x}u)(t, x) + u(t, x) - [u(t, x)]^{3}$ 且 $u(0, x) = \sin(\|x\|_{2}^{2})$，通过源码 16.1 中实现的 PINN 方法计算得到（参见定义 3.3.4）。

个神经元，每层）并使用参数为 1 的 swish 激活函数（参见第 1.2.8 节）。训练使用 Adam SGD 优化方法进行（参见第 7.9 节）。在 30000 步训练后得到的解 $u$ 的近似值绘图如图 16.2 所示。

```python
import torch
import matplotlib.pyplot as plt
from torch.autograd import grad
from matplotlib.gridspec import GridSpec
from matplotlib.cm import ScalarMappable
```

`dev = torch.device("cuda:0" if torch.cuda.is_available() else "cpu")`
`T = 3.0` # 时间范围

# 初始值
`def phi(x):`
`return x.sin().prod(axis=1, keepdims=True)`

`torch.manual_seed(0)`

# 我们使用一个具有 4 个隐藏层的网络，每层 50 个神经元，
# 并使用 Swish 激活函数（在 PyTorch 中称为 SiLU）
`N = torch.nn.Sequential(`
`torch.nn.Linear(3, 50), torch.nn.SiLU(),`
`torch.nn.Linear(50, 50), torch.nn.SiLU(),`
`torch.nn.Linear(50, 50), torch.nn.SiLU(),`
`torch.nn.Linear(50, 50), torch.nn.SiLU(),`
`torch.nn.Linear(50, 1),`
`).to(dev)`

`optimizer = torch.optim.Adam(N.parameters(), lr=3e-4)`
`J = 256` # 批次大小

`for i in range(30000):`
# 选择随机批次训练样本
`x = torch.rand(J, 2).to(dev) * 2`
`t = torch.rand(J, 1).to(dev) * T`
`x1 = x[:, 0:1]`
`x2 = x[:, 1:2]`
`x1.requires_grad_()`
`x2.requires_grad_()`
`t.requires_grad_()`
`optimizer.zero_grad()`
# 设 u 为人工神经网络的实现函数，计算
# 批次中每个 x 对应的 u(0, x)
`u0 = N(torch.hstack((torch.zeros_like(t), x)))`
# 计算初始条件的损失
`initial_loss = (u0 - phi(x)).square().mean()`

# 使用自动
# 微分计算偏导数
`u = N(torch.hstack((t, x1, x2)))`
`ones = torch.ones_like(u)`
`u_t = grad(u, t, ones, create_graph=True)[0]`
`u_x1 = grad(u, x1, ones, create_graph=True)[0]`
`u_x2 = grad(u, x2, ones, create_graph=True)[0]`
`ones = torch.ones_like(u_x1)`
`u_xx1 = grad(u_x1, x1, ones, create_graph=True)[0]`
`u_xx2 = grad(u_x2, x2, ones, create_graph=True)[0]`

# 计算偏微分方程（PDE）的损失
`Laplace = u_xx1 + u_xx2`
`pde_loss = (u_t - (0.005 * Laplace + u - u**3)).square().mean()`

# 计算总损失并执行梯度步骤
`loss = initial_loss + pde_loss`
`loss.backward()`
`optimizer.step()`

### 绘制不同时间点的解

`mesh = 128`
`a, b = -torch.pi, torch.pi`
`gs = GridSpec(2, 4, width_ratios=[1, 1, 1, 0.05])`
`fig = plt.figure(figsize=(16, 10), dpi=300)`
`x, y = torch.meshgrid(`
`torch.linspace(a, b, mesh),`
`torch.linspace(a, b, mesh),`
`indexing="xy"`
`)`
`x = x.reshape((mesh * mesh, 1)).to(dev)`
`y = y.reshape((mesh * mesh, 1)).to(dev)`

`for i in range(6):`
`t = torch.full((mesh * mesh, 1), i * T / 5).to(dev)`
`z = N(torch.cat((t, x, y), 1))`
`z = z.detach().cpu().numpy().reshape((mesh, mesh))`
`ax = fig.add_subplot(gs[i // 3, i % 3])`
`ax.set_title(f"t = {i * T / 5}")`
`ax.imshow(`
`z, cmap="viridis", extent=[a, b, a, b], vmin=-1.2, vmax=1.2`
`)`

# 在图表中添加颜色条
`norm = plt.Normalize(vmin=-1.2, vmax=1.2)`
`sm = ScalarMappable(cmap="viridis", norm=norm)`
`cax = fig.add_subplot(gs[:, 3])`
`fig.colorbar(sm, cax=cax, orientation="vertical")`
`fig.savefig("../plots/dgm.pdf", bbox_inches="tight")`
```

源代码 16.2 (`code/dgm.py`)：使用 `PyTorch` 实现的一种简单深伽辽金方法，用于计算函数 $u \in C^{1,2}([0,3] \times \mathbb{R}^{2}, \mathbb{R})$ 的近似值，该函数满足对于所有 $t \in [0,3]$ 和 $x = (x_{1},x_{2}) \in \mathbb{R}^{2}$，$(\frac{\partial u}{\partial t})(t,x) = \frac{1}{200}(\Delta_{x}u)(t,x) + u(t,x) - [u(t,x)]^{3}$ 且 $u(0,x) = \sin(x_{1})\sin(x_{2})$。此代码生成的图像如图 16.2 所示。

![](img/dec290f673e6357c31893c67b579ffe1_519_0.png)

图 16.2 (`plots/dgm.pdf`)：函数 $[-\pi,\pi]^{2} \ni x \mapsto U(t,x) \in \mathbb{R}$ 的图像，其中 $t \in \{0,0.6,1.2,1.8,2.4,3\}$，且 $U \in C([0,3] \times \mathbb{R}^{2}, \mathbb{R})$ 是函数 $u \in C^{1,2}([0,3] \times \mathbb{R}^{2}, \mathbb{R})$ 的近似值，该函数通过源代码 16.2 计算，满足对于所有 $t \in [0,3]$ 和 $x = (x_{1},x_{2}) \in \mathbb{R}^{2}$，$u(0,x) = \sin(x_{1})\sin(x_{2})$ 且 $(\frac{\partial u}{\partial t})(t,x) = \frac{1}{200}(\Delta_{x}u)(t,x) + u(t,x) - [u(t,x)]^{3}$。

## 第 17 章

## 深科尔莫哥洛夫方法 (DKMs)

第 16 章介绍的 **PINNs** 和 **DGMs** 一方面在构建相关随机优化问题的过程中未能充分利用底层 *PDE* 的大量结构，因此作为 *PDE* 的通用深度学习方法具有广泛适用性的关键优势。另一方面，在某种程度上利用所考虑的 *PDE* 问题特定结构的 *PDE* 深度学习方法通常能产生更精确的近似值（参见例如 Beck 等人 [24] 及其中的参考文献）。特别是，文献中存在若干深度学习方法，它们在构建随机优化问题的过程中利用了 *PDE* 本身允许随机表示这一特性。文献中有很多基于 *PDE* 的此类随机公式化的深度学习方法，因此与随机分析以及费曼–卡奇型公式有着密切的联系（参见例如 [20, 119, 145, 187, 207, 336] 及其中的参考文献）。
