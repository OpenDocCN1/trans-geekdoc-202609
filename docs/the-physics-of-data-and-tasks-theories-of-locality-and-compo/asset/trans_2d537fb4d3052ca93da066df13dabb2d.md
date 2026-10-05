

## A.3 卷积核与局部核的 Mercer 分解

### 引理 2.3.2 的证明

将方程 30 代入方程 31，

```
$K_{\text{NTK},N}^{\text{LC}}(\mathbf{x}_i, \mathbf{y}_j; \theta) = \frac{1}{|P|} \sum_{l \in P} \left( \frac{1}{H} \sum_{h=1}^{H} \sigma(\mathbf{w}_h^T\mathbf{x}_i + b_{h,l})\sigma(\mathbf{w}_h^T\mathbf{y}_j + b_{h,l}) \\ + \alpha_{h,l}^2 \sigma'(\mathbf{w}_h^T\mathbf{x}_i + b_{h,l})\sigma'(\mathbf{w}_h^T\mathbf{y}_j + b_{h,l})(\mathbf{x}_i^T\mathbf{y}_j + 1)\right).$
```

在上行中，对所有块（patches）的单行求和项是作用于 s 维输入（即 x 和 y 的块）的方程 108 中得到的随机特征核 $K_{\text{NTK},N}^{\text{FC}}$。因此，

```
$K_{\text{NTK},N}^{\text{LC}}(\mathbf{x}_i, \mathbf{y}_j; \theta) = \frac{1}{|P|} \sum_{l \in P} K_{\text{NTK},N}^{\text{FC}}(\mathbf{x}_i, \mathbf{y}_j).
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

## A.3 卷积核与局部核的 Mercer 分解

最后，我们从 $\mathcal{K}^{CN}$ 的定义证明方程 37 的展开

```
$\mathcal{K}^{CN}(x,y) = \frac{s^2}{d^2} \sum_{i,j\in P} C(x_i,y_j) \quad (124)$
= \frac{s^2}{d^2} \sum_{i,j\in P} \Lambda_{ij} \phi_p(x)\phi_p(y) = \lambda_1 \frac{s^2}{d} \sum_{i\in P} \phi_1(x)\phi_1(y) + \sum_{\rho > 1} \Lambda_\rho \left( \sqrt{\frac{s}{d}} \sum_{i\in P} \Phi_\rho(x) \right) \left( \sqrt{\frac{s}{d}} \sum_{j\in P} \Phi_\rho(y) \right) = \sum_{\rho} \Lambda_\rho \Phi_\rho(x)\Phi_\rho(y).$
```

### 引理 2.34 的证明

我们再次证明 $d$ 维特征函数 $\Phi_{\rho,j}$ 关于组成核的 $s$ 维特征函数 $\phi_\rho$ 的正交性，如方程 40，对于 $\rho, \sigma \neq 1$，

```
$$\Phi_{\rho,i}(x), \Phi_{\sigma,j}(y) = \int p(d^dx)\Phi_{\rho,i}(x)\Phi_{\sigma,j}(y) = \delta_{\rho,\sigma}\delta_{i,j}, \quad (125)$$
```

当 $i=j$ 时根据特征函数 $\Phi_\rho$ 的正交性以及假设 $i$，对于所有的 $\rho > 1$，$\int p^{(s)}(d^dx)\phi_\rho(x)=0$；当 $i \neq j$ 时。此外，如果 $\Phi_1(x)=1$，则 $\int p(d^dx)\Phi_{\sigma,i}(x)=0$ 且 $\int p(d^dx)\Phi_1(x)=1$。然后我们证明方程 40 中定义的特征函数和特征值满足核特征问题。对于 $\rho=1$，

```
$$\int p(d^dx)\mathcal{K}^{LC}(x,y) = \int p(d^dx)\sum_{i \in P} \frac{s}{d} \lambda_1 = \frac{s}{d} \sum_{i \in P} \lambda_1 = \Lambda_1, \quad (126)$$
```

其中我们使用了假设 $i$ 中的 $\int p^{(s)}(d^sy)C(x,y)=\lambda_1$。对于 $\rho > 1$，

```
$$\int p(d^dx)\mathcal{K}^{LC}(x,y)\Phi_\rho(y) = \int p(d^dx)\sum_{j \in P} \frac{s}{d} C(x_j,y_j)\Phi_\rho(y_j). \quad (127)$$
```

将对 $j$ 的求和分为 $j=i$ 的项和剩余项，右侧可以写为

```
$$\frac{s}{d} \int p(d^dy_i)C(x_i,y_i)\Phi_\rho(y_i) + \frac{s}{d} \sum_{j \neq i \in P} \int p(d^dy_j)C(x_j,y_j)\Phi_\rho(y_j). \quad (128)$$
```

## 附录：局部性克服了维度灾咒

使用假设 $i$，第三个积分始终为 0，因此

```
$$\int p(d^dy)\mathcal{K}^{CN}(\mathbf{x},\mathbf{y}) = \sum_{i \in \mathcal{P}} \lambda_i \Phi_{d,i}(\mathbf{x}) = \lambda_i \Phi_{d,i}(\mathbf{x}). \quad (129)$$
```

最后，我们从 $K^{LC}$ 证明方程 37 的展开

```
$$\mathcal{K}^{LC}(\mathbf{x},\mathbf{y}) = \sum_{i \in P} \frac{s}{d} \lambda_1 \quad (130)$$
$$\frac{s^2}{d^2} \sum_{i,j\in P} \Lambda_{ij} \phi_p(x)\phi_p(y) = \lambda_1 \frac{s^2}{d} \sum_{i\in P} \phi_1(x)\phi_1(y) + \sum_{\rho > 1} \Lambda_\rho \left( \sqrt{\frac{s}{d}} \sum_{i\in P} \Phi_\rho(x) \right) \left( \sqrt{\frac{s}{d}} \sum_{j\in P} \Phi_\rho(y) \right) = \sum_{\rho} \Lambda_\rho \Phi_\rho(x)\Phi_\rho(y). \quad (131)$$
```

## A.3.1 重叠块卷积核的谱

在本节中，引理 2.3.3 和引理 2.3.4 扩展到具有重叠块的核，其中 $\mathcal{P}=\{1,\dots,d\}$ 且 $|\mathcal{P}|=d$。这种扩展需要额外的假设，如下所示：

- i) $d$ 维测度 $p^{(d)}(d^d\mathbf{x})$ 在 $d$ 维环面上是均匀的；
- ii) 组成核 $\mathcal{C}(\mathbf{x},\mathbf{y})$ 是平移不变、同性的且周期的，

```
$$\mathcal{C}(\mathbf{x},\mathbf{y}) = c(|||\mathbf{x}-\mathbf{y}||\), c(|||\mathbf{x}-\mathbf{y}+\mathbf{n}||\)=c(|||\mathbf{x}-\mathbf{y}||\) \forall \mathbf{n} \in \mathbb{Z}^d. \quad (134)$$
```

假设 (i) 和 (ii) 意味着 $\mathcal{C}(\mathbf{x},\mathbf{y})$ 在傅里叶空间中对角化，即用 $k$ 表示 $s$ 维波波数

```
$$\c(\mathbf{x}-\mathbf{y}) = \sum_{k=2:n \in \mathbb{Z}^d} \lambda_k \Phi_k(\mathbf{x})\overline{\Phi_k(\mathbf{y})} = \sum_{k=2:n \in \mathbb{Z}^d} \lambda_k e^{i\mathbf{k}^T\mathbf{x}}, \quad (135)$$
```

且特征值 $\lambda_k$ 取决于 $k$ 的模，$\mathbf{k}=\sqrt{\mathbf{k}^T\mathbf{k}}$。让我们引入以下定义，首先回习 $\mathbf{x}$ 的 $s$ 维路径 $x_i$ 是从 $x_i$ 开始的连续子序列

```
$$\mathbf{x} = (x_1,x_2,\dots,x_d) \Rightarrow \mathbf{x}_i = (x_i,x_{i+1},\dots,x_{i+s-1}), \quad (136)$$
```

并且输入是“包裹”的，即我们识别 $x_{nd}$ 与 $x_d$，对于所有的 $n \in \mathbb{Z}$。

