
给定两个实值变量 $(x, y)$，既可以将它们视为二维空间中的矢量量 $[x, y]^T$，也可以将它们描述为一个复变量 $z = x + jy$，其中 $j^2 := -1$。采用后一种方法的好处是可以利用复数域 $\mathbb{C}$ 中可用的运算，即乘法和除法。此类运算的存在极大地便利了代数操作。回顾一下，在矢量空间中并未定义此类运算。^([^(19)](#fn19))

假设我们有一个复值（输出）随机变量

$$y := y_r + jy_i \tag{4.13}$$

和一个复值（输入）随机矢量

$$\mathbf{x} = \mathbf{x}_r + j\mathbf{x}_i. \tag{4.14}$$

量 $y_r, y_i, \mathbf{x}_r$ 和 $\mathbf{x}_i$ 均为实值随机变量/矢量。目标是计算一个由复值参数矢量 $\boldsymbol{\theta} = \boldsymbol{\theta}_r + j\boldsymbol{\theta}_i \in \mathbb{C}^l$ 定义的线性估计器，以最小化相应的 MSE，

$$\mathbb{E}[|e|^2] := \mathbb{E}[ee^*] = \mathbb{E}[|y - \boldsymbol{\theta}^H \mathbf{x}|^2]. \tag{4.15}$$

观察公式 [(4.15)](#Chp004_119-175_B978044329238500010X.xhtml#deq24)，不难发现，在复变量的情况下，两个复值随机变量之间的内积运算应定义为 $\mathbb{E}[xy^*]$，以保证由内积隐含的范数 $\| x \| = \sqrt{\mathbb{E}[xx^*]}$ 是一个有效量。应用与之前相同的正交条件，我们重新推导出如公式 [(4.11)](#Chp004_119-175_B978044329238500010X.xhtml#deq17) 所示的正规方程，

$$\boldsymbol{\Sigma}_x \boldsymbol{\theta}^* = \mathbf{p},$$
