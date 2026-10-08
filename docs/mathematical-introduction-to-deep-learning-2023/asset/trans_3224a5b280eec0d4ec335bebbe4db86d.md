
40    x = x_data[indices, :]
41    t = t_data[indices, :]
42
43    x1, x2 = x[:, 0:1], x[:, 1:2]
44
45    x1.requires_grad()
46    x2.requires_grad()
47    t.requires_grad()
48
49    optimizer.zero_grad()
50
51    # 设 u 为人工神经网络的实现函数，计算
52    # 批次中每个 x 对应的 u(0, x)
53    u0 = N(torch.hstack((torch.zeros_like(t), x)))
54    # 计算初始条件的损失
55    initial_loss = (u0 - phi(x)).square().mean()
56
57    # 使用自动
58    # 微分计算偏导数
59    u = N(torch.hstack((t, x1, x2)))
60    ones = torch.ones_like(u)
61    u_t = grad(u, t, ones, create_graph=True)[0]
62    u_x1 = grad(u, x1, ones, create_graph=True)[0]
63    u_x2 = grad(u, x2, ones, create_graph=True)[0]
64    ones = torch.ones_like(u_x1)
65    u_xx1 = grad(u_x1, x1, ones, create_graph=True)[0]
66    u_x2x2 = grad(u_x2, x2, ones, create_graph=True)[0]
67
68    # 计算偏微分方程（PDE）的损失
69    Laplace = u_x1x1 + u_x2x2
70    pde_loss = (u_t - (0.005 * Laplace + u - u**3)).square().mean()
71
72    # 计算总损失并执行梯度步骤
73    loss = initial_loss + pde_loss
74    loss.backward()
75    optimizer.step()
76
77    ### 绘制不同时间点的解
78
79    mesh = 128
80    a, b = -3, 3
81
82    gs = GridSpec(2, 4, width_ratios=[1, 1, 1, 0.05])
83    fig = plt.figure(figsize=(16, 10), dpi=300)
84
85    x, y = torch.meshgrid(
86        torch.linspace(a, b, mesh),
87        torch.linspace(a, b, mesh),
88        indexing="xy"
89    )
90    x = x.reshape((mesh * mesh, 1)).to(dev)
91    y = y.reshape((mesh * mesh, 1)).to(dev)
92
93    for i in range(6):
94        t = torch.full((mesh * mesh, 1), i * T / 5).to(dev)
95        z = N(torch.cat((t, x, y), 1))
96        z = z.detach().cpu().numpy().reshape((mesh, mesh))
97
98        ax = fig.add_subplot(gs[i // 3, i % 3])
99        ax.set_title(f"t = {i * T / 5}")
100        ax.imshow(
101            z, cmap="viridis", extent=[a, b, a, b], vmin=-1.2, vmax=1.2
102        )
103
104    # 在图表中添加颜色条
105    norm = plt.Normalize(vmin=-1.2, vmax=1.2)
106    sm = ScalarMappable(cmap="viridis", norm=norm)
107    cax = fig.add_subplot(gs[:, 3])
108    fig.colorbar(sm, cax=cax, orientation="vertical")
109
110    fig.savefig("../plots/pinn.pdf", bbox_inches="tight")

源码 16.1 (code/pinn.py)：使用 PyTorch 实现的 PINN 方法简单实现，用于计算函数 $u \in C^{1,2}([0,3] \times \mathbb{R}^{2}, \mathbb{R})$ 的近似值，该函数满足对于所有 $t \in [0,2]$，$x \in \mathbb{R}^{2}$，有 $(\frac{\partial u}{\partial t})(t, x) = \frac{1}{200}(\Delta_{x}u)(t, x) + u(t, x) - [u(t, x)]^{3}$ 且 $u(0, x) = \sin(\|x\|_{2}^{2})$（参见定义 3.3.4）。该代码生成的绘图如图 16.1 所示。

## 16.4 DGMs 的实现

在下述源码 16.2 中，我们展示了 DGM 的一个简单实现，如上文第 16.2 节所述，用于寻找二维 Allen–Cahn 型半线性热方程解的近似值 $u \in C^{1,2}([0,3] \times \mathbb{R}^{2})$

$$(\frac{\partial u}{\partial t})(t, x) = \frac{1}{200}(\Delta_{x}u)(t, x) + u(t, x) - [u(t, x)]^{3} \tag{16.20}$$

其中对于 $t \in [0,3]$，$x = (x_{1}, x_{2}) \in \mathbb{R}^{2}$，初始条件为 $u(0, x) = \sin(x_{1})\sin(x_{2})$。正如 Sgrignolo & Spiliopoulos [379] 最初提议的那样，该实现在每个训练步骤中选取随机变量 $(\mathcal{T}, \mathcal{X})$ 的 256 个实现组成的批次，其中 $\mathcal{T}$ 在 $[0,3]$ 上均匀分布，$\mathcal{X}$ 在 $\mathbb{R}^{2}$ 上正态分布，均值为 $\mathbb{R}^{2}$ 中的 $0$，协方差为 $4I_{2} \in \mathbb{R}^{2 \times 2}$（参见定义 1.5.5）。与源码 16.1 中的 PINN 实现类似，它训练一个具有 4 个隐藏层的全连接前馈人工神经网络（每个隐藏层包含 50

![](img/dec290f673e6357c31893c67b579ffe1_516_0.png)

图 16.1 (plots/pinn.pdf)：函数 $[-3, 3]^{2} \ni x \mapsto U(t, x) \in \mathbb{R}$ 的绘图，其中 $t \in \{0, 0.6, 1.2, 1.8, 2.4, 3\}$，且 $U \in C([0,3] \times \mathbb{R}^{2}, \mathbb{R})$ 是函数 $u \in C^{1, 2}([0, 3] \times \mathbb{R}^{2}, \mathbb{R})$ 的近似值，该函数满足对于所有 $t \in [0, 3], x \in \mathbb{R}^{2}$ 有 $(\frac{\partial u}{\partial t})(t, x) = \frac{1}{200}(\Delta_{x}u)(t, x) + u(t, x) - [u(t, x)]^{3}$ 且 $u(0, x) = \sin(\|x\|_{2}^{2})$，通过源码 16.1 中实现的 PINN 方法计算得到（参见定义 3.3.4）。

个神经元，每层）并使用参数为 1 的 swish 激活函数（参见第 1.2.8 节）。训练使用 Adam SGD 优化方法进行（参见第 7.9 节）。在 30000 步训练后得到的解 $u$ 的近似值绘图如图 16.2 所示。

1  import torch
2  import matplotlib.pyplot as plt
3  from torch.autograd import grad
4  from matplotlib.gridspec import GridSpec
5  from matplotlib.cm import ScalarMappable
6
7
8  dev = torch.device("cuda:0" if torch.cuda.is_available() else "cpu")
9
10  T = 3.0   # 时间范围
11
12  # 初始值
13  def phi(x):
14      return x.sin().prod(axis=1, keepdims=True)
15
16  torch.manual_seed(0)
17
18  # 我们使用一个具有 4 个隐藏层的网络，每层 50 个神经元，
19  # 并使用 Swish 激活函数（在 PyTorch 中称为 SiLU）
20  N = torch.nn.Sequential(
21      torch.nn.Linear(3, 50), torch.nn.SiLU(),
22      torch.nn.Linear(50, 50), torch.nn.SiLU(),
23      torch.nn.Linear(50, 50), torch.nn.SiLU(),
24      torch.nn.Linear(50, 50), torch.nn.SiLU(),
25      torch.nn.Linear(50, 1),
26  ).to(dev)
27
28  optimizer = torch.optim.Adam(N.parameters(), lr=3e-4)
29
30  J = 256  # 批次大小
31
32  for i in range(30000):
33      # 选择随机批次训练样本
34      x = torch.rand(J, 2).to(dev) * 2
35      t = torch.rand(J, 1).to(dev) * T
36
37      x1 = x[:, 0:1]
38      x2 = x[:, 1:2]
39
40      x1.requires_grad_()
41      x2.requires_grad_()
42      t.requires_grad_()
43
44      optimizer.zero_grad()
45
46      # 设 u 为人工神经网络的实现函数，计算
47      # 批次中每个 x 对应的 u(0, x)
48      u0 = N(torch.hstack((torch.zeros_like(t), x)))
49      # 计算初始条件的损失
50      initial_loss = (u0 - phi(x)).square().mean()
51
52      # 使用自动
53      # 微分计算偏导数
54      u = N(torch.hstack((t, x1, x2)))
55      ones = torch.ones_like(u)
56      u_t = grad(u, t, ones, create_graph=True)[0]
57      u_x1 = grad(u, x1, ones, create_graph=True)[0]
58      u_x2 = grad(u, x2, ones, create_graph=True)[0]
59      ones = torch.ones_like(u_x1)
60      u_xx1 = grad(u_x1, x1, ones, create_graph=True)[0]
61      u_xx2 = grad(u_x2, x2, ones, create_graph=True)[0]
62
63      # 计算偏微分方程（PDE）的损失
64      Laplace = u_xx1 + u_xx2
65      pde_loss = (u_t - (0.005 * Laplace + u - u**3)).square().mean()
66
67      # 计算总损失并执行梯度步骤
68      loss = initial_loss + pde_loss
69      loss.backward()
70      optimizer.step()
71
72      ### 绘制不同时间点的解
73
74      mesh = 128
75      a, b = -torch.pi, torch.pi
76
77      gs = GridSpec(2, 4, width_ratios=[1, 1, 1, 0.05])
78      fig = plt.figure(figsize=(16, 10), dpi=300)
79
80      x, y = torch.meshgrid(
81          torch.linspace(a, b, mesh),
82          torch.linspace(a, b, mesh),
83          indexing="xy"
84      )
85      x = x.reshape((mesh * mesh, 1)).to(dev)
86      y = y.reshape((mesh * mesh, 1)).to(dev)
87
88      for i in range(6):
89          t = torch.full((mesh * mesh, 1), i * T / 5).to(dev)
90          z = N(torch.cat((t, x, y), 1))
91          z = z.detach().cpu().numpy().reshape((mesh, mesh))
92
93          ax = fig.add_subplot(gs[i // 3, i % 3])
94          ax.set_title(f"t = {i * T / 5}")
95          ax.imshow(
96              z, cmap="viridis", extent=[a, b, a, b], vmin=-1.2, vmax=1.2
97          )
98
99      # 在图表中添加颜色条
100     norm = plt.Normalize(vmin=-1.2, vmax=1.2)
101     sm = ScalarMappable(cmap="viridis", norm=norm)
102     cax = fig.add_subplot(gs[:, 3])
103     fig.colorbar(sm, cax=cax, orientation="vertical")
104
105     fig.savefig("../plots/dgm.pdf", bbox_inches="tight")

