
$$f(x) = \sum_{\rho=1}^{\infty} a_{\rho}\phi_{\rho}(x), \quad f'(x) = \sum_{\rho=1}^{\infty} a_{\rho}\phi_{\rho}(x), \quad (f,f')_{\mathcal{H}} = \sum_{\rho=1}^{\infty} \frac{a_{\rho}a_{\rho}'}{\lambda_{\rho}}. (100)$$

对于任何位于核特征基张空间内的目标函数 $f^*$，核岭回归估计器的均方泛化误差为：

$$\mathcal{E}(\lambda, \{x_v\}) = \int (d^d x) (f(x) - f^*(x))^2 = \sum_{\rho=1}^{\infty} |a_{\rho}(\lambda, \{x_v\}) - c_{\rho}|^2. (101)$$

其中 $c_{\rho}$ 表示目标函数 $f^*$ 的第 $\rho$ 个系数，$a_{\rho}$ 是估计器的系数，$f$ 取决于岭参数 $\lambda$ 和训练集 $\{x_v\}_{v=1,...,P}$。请注意，根据定义，由于 $f$ 属于 $\mathcal{H}$，因此 $\sum_{\rho}|a_{\rho}|^2/\lambda_{\rho} < \infty$，而 $c_{\rho}$ 可以取任何值。

[BCP20; CBP21] 的作者基于统计物理的复制方法，找到了一个关于训练集实现上 $\{\hat{f}_x\}$ 上平均均方误差的启发式表达式，其形式如下：

$$\mathcal{E}(\lambda, P) = \partial_{\lambda} \left( \frac{k_{\lambda}(P)}{P} \right) \sum_{P} (\lambda_{\rho} + k_{\lambda}(P))^2 |c_{\rho}|^2, \quad 102$$

其中 $(P)$ 满足：

$$\frac{k_{\lambda}(P)}{P} = \lambda + \frac{1}{P} \sum_{\rho} \frac{\lambda_{\rho} k_{\lambda}(P)/P}{\lambda_{\rho} + k_{\lambda}(P)/P}, \quad 103$$

简之，复制方法的工作如下 [MPV87b]：首先定义能量函数 $E(f)$ 为方程 97 中的参数，然后赋予概率分布 $P(f) = Z^{-\beta E(f)}$，其中 $Z$ 是归一化常数且 $\beta=0$。随着 $\beta \to \infty$，概率分布 $P(f)$ 集中在方程 97 最小问题的解上，即可以将方程 101 右侧的 $f$ 替换为 $\beta$ 的平均值，然后在计算后取极限 $\beta \to \infty$ 以恢复泛化误差。这种简化源于 $f$ 被替换为其特征分解，能量函数 $E(f)$ 变为系数 $c_{\rho}$ 的二次函数。然后，在特征函数 $\phi_{\rho}(x)$ 关于 $x$ 的一阶和二阶矩假设下，方程 101 中的所有平均值都简化为高斯积分。从数学上讲，$k_{\lambda}(P)/P$ 与大 $P$ 极限下 Gram 矩阵 $K_{p}/P$ 的 Stieltjes 变换 [PB20] 相关。直上看，它起到了阈值的作用：对于 $\lambda_{\rho} \gg k_{\lambda}(P)/P$ 的 $\rho$，误差的数学贡献为 0；对于 $\lambda_{\rho} \ll k_{\lambda}(P)/P$ 的 $\rho$，贡献为 $\mathbb{E}[|c_{\rho}|^2]$。这等同于说算法预测器 $f(x)$ 只捕捉了特征值大于 $k_{\lambda}(P)/P$ 的特征函数。这种图实际上可以用于在无岭情况下通过方程 102 和方程 103 的渐近行为来探索学习曲线 $\beta$。随后，假设核和目标函数具有幂律谱，其中 $\lambda_{\rho} \sim \rho^{-a}$ 且 $\mathbb{E}[|c_{\rho}|^2] \sim \rho^{-b}$，满足 $2a > b-1$。首先，使用 Euler-Maclaurin 公式将方程 103 中的和近似积分。然后，用渐近极限替换积分内部的特征值。[BCP20; CBP21] 中考虑的风险与方程 97 差了一个 $1/P$ 的因子。当 $P \to \infty$ 时，$\lambda_P = A\rho^{-a}, \kappa_0(P)/P \to 0$，这两个操作导致了渐近独立于 $P$ 的误差：

$$\frac{\kappa_0(P)}{P} = \frac{\kappa_0(1)}{P} \int_0^{\infty} \frac{d\rho}{A\rho^{-a} + \kappa_0(P)/\rho} + \mathcal{O}(1) \quad 104$$

$$\frac{\kappa_0(P)}{P} = \frac{\kappa_0(1)}{P} \left( \frac{\kappa_0(\rho)}{\rho} \right) \int_0^{\infty} \frac{d\sigma}{\sigma^{a-1} A^2}{1 + \sigma} + \mathcal{O}(1)$$

其中右侧通过变量 $\sigma = \kappa_0(\rho)/P$。由于 $\sigma$ 的积分是有限且独立于 $P$，我们得到 $\kappa_0(P)/P = O(P^{-a})$。同样，我们发现模式无关的前因子 $\kappa_0(P)/P|_{\lambda=0} = \mathcal{O}(1)$。结果是，我们得到某些 $P$ 无关的前因子：

$$\mathcal{E}(P) \sim \sum_{\rho} \frac{\rho^{-2a}}{(A\rho^{-a} + P\rho^{-a})^2} |c_{\rho}|^2. \quad 105$$

遵循阈值 $\kappa_0(P)/P \sim P^{-a}$ 的直观论，将方程 105 中的和分为 $\lambda_{\rho} \gg \kappa_0(P)/P$、$\lambda_{\rho} \sim \kappa_0(P)/P$ 和 $\lambda_{\rho} \ll \kappa_0(P)$ 三个扇区：

$$\mathcal{E}(P) \sim \sum_{\rho \ll P} \frac{\rho^{-2a}}{(A\rho^{-a})^2} |c_{\rho}|^2 + \sum_{\rho \sim P} |c_{\rho}|^2 + \sum_{\rho \gg P} |c_{\rho}|^2. \quad 106$$

最后，通过注意到根据我们对 $|c_{\rho}|^2$ 衰减的假设，rho \ll P$ 的和是 $P$ 的低阶项，而另外两个和可以合并，得到了方程 28。

### A.2 卷积和局部连接网络的 NTK

本节首先回顾单层全连接网络的 NTK 计算 [CO9]。

**定义 A.2.1（单层 FCN）。** 有 $H$ 个神经元的单层全连接网络定义如下：

$$f^{FCN}(\mathbf{x}) = \frac{1}{\sqrt{H}} \sum_{h=1}^{H} a_h \sigma(\mathbf{w}_h^T\mathbf{x} + b_h), \quad 107$$

其中 $\mathbf{x} \in \mathbb{R}^d$ 是输入，$H$ 是宽度，$\sigma$ 是非线性激活函数，$\{\mathbf{w}_h \in \mathbb{R}^d\}_{h=1}^H$ 和 $\{\mathbf{b}_h \in \mathbb{R}\}_{h=1}^H$ 是网络的参数。将方程 107 代入得

$$K^{FC}_{NTK,N}(\mathbf{x},\mathbf{y};\theta) = \frac{1}{H} \sum_{h=1}^{H} \sigma'(\mathbf{w}_h^T\mathbf{x} + b_h)\sigma'(\mathbf{w}_h^T\mathbf{y} + b_h) + a_h^2\sigma'^2(\mathbf{w}_h^T\mathbf{x} + b_h)\sigma'(\mathbf{w}_h^T\mathbf{y} + b_h), \quad 108$$

其中 $\sigma'$ 表示 $\sigma$ 对其参数的导数。如果所有参数都独立从标准正态分布初始化，$K_{NTK,N}^{FC}(\mathbf{x}, \mathbf{y}; \boldsymbol{\theta})$ 是一个随机特征核，它在 $H \to \infty$ 极限下收敛于：

$$K_{NTK}^{FC}(\mathbf{x}, \mathbf{y}) = \mathbb{E}_{\mathbf{w}}[\sigma'(\mathbf{x}^T\mathbf{w})\sigma'(\mathbf{y}^T\mathbf{w})] + \mathbb{E}_a[a^2]\mathbb{E}_{\mathbf{w}}[\sigma'(\mathbf{x}^T\mathbf{w})\sigma'(\mathbf{y}^T\mathbf{w}) (\mathbf{x}^T\mathbf{y}+1)]$$

当 $\sigma$ 为 ReLU 激活函数时，可以使用反余核的技术 [Cs09] 精确计算期望：

$$K_{NTK}^{FC}(\mathbf{x}, \mathbf{y}) = \frac{1}{2\pi}\sqrt{\|\mathbf{x}\|^2+1}\sqrt{\|\mathbf{y}\|^2+1}\sin(\varphi)(\pi-\varphi) + \frac{1}{2\pi}(\mathbf{x}^T\mathbf{y}+1)(\pi-\varphi),$$

其中 $\varphi$ 表示角

$$\varphi = \arccos\left(\frac{\mathbf{x}^T\mathbf{y}+1}{\sqrt{\|\mathbf{x}\|^2+1}\sqrt{\|\mathbf{y}\|^2+1}}\right)$$

注意，在第 2.3 节中，对于 ReLU 网络，$K_{x}^{FC}(\mathbf{x})$ 在 $\mathbf{x}=\mathbf{y}$ 处显示尖峰。

### 引理 2.1 的证明

证明。将方程 29 代入方程 31：

$$K_{NTK,N,x}^{CN}(\mathbf{x}, \mathbf{y}; \boldsymbol{\theta}) = \frac{1}{|\mathcal{P}|^2}\sum_{i,j\in\mathcal{P}}\frac{1}{H}\sum_{h=1}^H(\sigma'(\mathbf{w}_h^T\mathbf{x}+b_h)\sigma'(\mathbf{w}_h^T\mathbf{y}+b_h) + a_i^2\sigma'(\mathbf{w}_i^T\mathbf{x}+b_i)\sigma'(\mathbf{w}_j^T\mathbf{y}+b_j)(\mathbf{x}^T\mathbf{y}+1))$$

在上一行中，补丁之和的单项是方程 108 得到的随机特征核 $K_{NTK,N}^{FC}$ 作用于 s 维输入，即 $\mathbf{x}$ 和 $\mathbf{y}$ 的补丁。

$$K_{NTK,N}^{FC}(\mathbf{x}, \mathbf{y}) = \frac{1}{|\mathcal{P}|^2}\sum_{i,j\in\mathcal{P}}K_{NTK,N}^{FC}(\mathbf{x}, \mathbf{y}).$$

如果所有参数都独立从标准正态分布初始化，方程 113 的 $H \to \infty$ 极限产生方程 32。

## A.3 卷积核与局部核的 Mercer 分解

### 引理 2.3.2 的证明

将方程 30 代入方程 31，

```
$K_{\text{NTK},N}^{\text{LC}}(\mathbf{x}_i, \mathbf{y}_j; \theta) = \frac{1}{|P|} \sum_{l \in P} \left( \frac{1}{H} \sum_{h=1}^{H} \sigma(\mathbf{w}_h^T\mathbf{x}_i + b_{h,l})\sigma(\mathbf{w}_h^T\mathbf{y}_j + b_{h,l}) \\ + \alpha_{h,l}^2 \sigma'(\mathbf{w}_h^T\mathbf{x}_i + b_{h,l})\sigma'(\mathbf{w}_h^T\mathbf{y}_j + b_{h,l})(\mathbf{x}_i^T\mathbf{y}_j + 1)\right).$
```

在上行中，对所有块（patches）的单行求和项是作用于 s 维输入（即 x 和 y 的块）的方程 108 中得到的随机特征核 $K_{\text{NTK},N}^{\text{FC}}$。因此，

```
$K_{\text{NTK},N}^{\text{LC}}(\mathbf{x}_i, \mathbf{y}_j; \theta) = \frac{1}{|P|} \sum_{l \in P} K_{\text{NTK},N}^{\text{FC}}(\mathbf{x}_i, \mathbf{y}_j).$
```

如果所有参数都独立从标准正态分布初始化，则在 $H \to \infty$ 的极限下恢复方程 33。

## A.3 卷积核与局部核的 Mercer 分解

在本节中，我们证明引理 2.3.3 和引理 2.3.4 中引入的特征分解，然后将它们扩展到重叠块核（参考 A.3.1）。我们将输入空间中两个（复）函数 $f$ 和 $g$ 之间的标量积定义为

```
$\langle f, g \rangle = \int_d p(d^dx)f(\mathbf{x})g(\mathbf{x}).$
```

### 引理 2.3.3 的证明

我们首先证明特征函数的正交性。通过如方程 38 中将 $d$ 维特征函数 $\Phi_\rho$ 写为组成核的 $s$ 维特征函数 $\phi_\rho$，对于 $\rho, \sigma \neq 1$，

```
$\langle \Phi_\rho, \Phi_\sigma \rangle = \frac{s}{d} \sum_{i \in P} \int p(d^dx)\phi_\rho(\mathbf{x}_i)\phi_\sigma(\mathbf{x}_j).$
```

将块求和中 $i$ 和 $j$ 重合的项与其他项分离，由于块是不重叠的，右侧（RHS）可以写为

```
$\frac{s}{d} \sum_{i \in P} \int p(d^dx)\phi_\rho(\mathbf{x}_i)\phi_\sigma(\mathbf{x}_i) + \sum_{i\neq j \in P} \int p(d^dx)\phi_\rho(\mathbf{x}_i)\phi_\sigma(\mathbf{x}_j).$
```

根据特征函数 $\Phi_\rho$ 的正交性，第一个积分仅当 $\rho = \sigma$ 时不为零且等于 1，而根据假设 $i$，对于所有的 $\rho > 1$，p^{(s)}(d^dx)\Phi_\rho(x) = 0$，因此第二个积分始终为 0。因此，

```
$$\Phi_\rho\Phi_{\sigma} = \delta_{\rho,\sigma}. \quad (119)$$
```

当 $\rho = 1$ 且 $\sigma \neq 1$ 时，根据假设 $i$，$\int p(d^4x)\Phi_1(x)\Phi_\rho(x) = 0$，即 $\Phi_1 = 1$ 且对于所有 $\rho > 1$，$\int p^{(s)}(d^4x)\Phi_\rho(x) = 0$。最后，如果 $\rho = 1$，$\int p(d^4x)\Phi_1(x) = 1$。然后我们证明方程 38 中定义的特征函数和特征值满足核实验。对于 $\rho = 1$，

```
$$\int p(d^4y)K^{CN}(\mathbf{x},y) = \int p(d^4y)\sum_{i,j\in P} \frac{s^2}{d_i^2} C(x_i,y_j) = \frac{s^2}{d^2} \sum_{i,j\in P} \lambda_1 = \Lambda_1, \quad (120)$$
```

其中我们使用了假设 $i$ 中的 $\int p^{(s)}(d^4y)C(\mathbf{x},y) = \lambda_1$。对于 $\rho > 1$，

```
$$\int p(d^4y)K^{CN}(\mathbf{x},y)\Phi_\rho(y) = \int p(d^4y)\sum_{i,j\in P} \frac{s^2}{d_i^2} C(x_i,y_j)\sqrt{\frac{s}{d^2}} \sum_{i\in P} \Phi_\rho(y). \quad (121)$$
```

将对 $l$ 的求和分为 $l=j$ 的项和剩余项，右侧写为

```
$$\frac{s^2}{d^2} \sum_{i,j\in P} \left( \int p(d^4y)C(x_i,y_j)\sqrt{\frac{s}{d^2}} \Phi_\rho(j) \right) + \sum_{i\neq j \in P} \int p(d^4y)C(x_i,y_j)\sqrt{\frac{s}{d^2}} \Phi_\rho(y). \quad (122)$$
```

使用假设 $i$，第三个积分始终为 0，因此

```
$$\int p(d^4y)K^{CN}(\mathbf{x},y)\Phi_\rho(y) = \frac{s^2}{d^2} \sum_{i,j\in P} \Lambda_\rho\sqrt{\frac{s}{d^2}} \Phi_\rho(x) = \Lambda_\rho\Phi_\rho(x). \quad (123)$$
```
