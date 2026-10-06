
## 5.4.1 模糊梯度下降算法

上述 GDOA 可用于以下情况求解 FSE（图 5.1）。

![Figure 5.1 Flow chart of the proposed fuzzy gradient descent optimization algorithm](img/PBHE0650-05-f01.jpg)

图 5.1 所提的模糊梯度下降优化算法流程图

### 情况 1

在 (5.9) 中，系数矩阵的元素表示为三角形模糊数（TFNs）。元素 `\widetilde{\mathcal{m}}_{\mathit{ij}}` 定义为 `[\mathcal{m}_{L_{\mathit{ij}}},\mathcal{m}_{N_{\mathit{ij}}},\mathcal{m}_{R_{\mathit{ij}}}]`，而右侧向量为 `\mathcal{Y}_j` 且保持确值（crisp）。

FSLE 情况 1 的矩阵表示可以写如下：

```latex
(5.19)
\begin{bmatrix}
\left\lbrack {\widetilde{\mathcal{m}}_{L_{11}},\widetilde{\mathcal{m}}_{N_{11}},\widetilde{\mathcal{m}}_{R_{11}}} \right\rbrack & \left\lbrack {\widetilde{\mathcal{m}}_{L_{12}},\widetilde{\mathcal{m}}_{N_{12}},\widetilde{\mathcal{m}}_{R_{12}}} \right\rbrack & \cdots & \left\lbrack {\widetilde{\mathcal{m}}_{L_{1n}},\widetilde{\mathcal{m}}_{N_{1n}},\widetilde{\mathcal{m}}_{R_{1n}}} \right\rbrack \\
\left\lbrack {\widetilde{\mathcal{m}}_{L_{21}},\widetilde{\mathcal{m}}_{N_{21}},\widetilde{\mathcal{m}}_{R_{21}}} \right\rbrack & \left\lbrack {\widetilde{\mathcal{m}}_{L_{22}},\widetilde{\mathcal{m}}_{N_{22}},\widetilde{\mathcal{m}}_{R_{22}}} \right\rbrack & \cdots & \left\lbrack {\widetilde{\mathcal{m}}_{L_{1n}},\widetilde{\mathcal{m}}_{N_{1n}},\widetilde{\mathcal{m}}_{R_{1n}}} \right\rbrack \\
\vdots & \vdots & \ddots & \vdots \\
\left\lbrack {\widetilde{\mathcal{m}}_{L_{n1}},\widetilde{\mathcal{m}}_{N_{n1}},\widetilde{\mathcal{m}}_{R_{11}}} \right\rbrack & \left\lbrack {\widetilde{\mathcal{m}}_{L_{n2}},\widetilde{\mathcal{m}}_{N_{n2}},\widetilde{\mathcal{m}}_{R_{n2}}} \right\rbrack & \cdots & \left\lbrack {\widetilde{\mathcal{m}}_{L_{\mathit{nn}}},\widetilde{\mathcal{m}}_{N_{\mathit{nn}}},\widetilde{\mathcal{m}}_{R_{\mathit{nn}}}} \right\rbrack
\end{bmatrix}
\begin{bmatrix}
\left\lbrack {\widetilde{x}_{L_{1}},\widetilde{x}_{N_{1}},\widetilde{x}_{R_{1}}} \right\rbrack \\
\left\lbrack {\widetilde{x}_{L_{2}},\widetilde{x}_{N_{2}},\widetilde{x}_{R_{2}}} \right\rbrack \\
\vdots \\
\left\lbrack {\widetilde{x}_{L_{n}},\widetilde{x}_{N_{n}},\widetilde{x}_{R_{n}}} \right\rbrack
\end{bmatrix}
=
\begin{bmatrix}
b_{1} \\
b_{2} \\
\vdots \\
b_{n}
\end{bmatrix}.
```

### 情况 2

在 (5.9) 中，具有 TFN 值的右侧向量表示为 `\widetilde{\mathcal{Y}}_j`，且同样定义为 `[b_{L_{\mathit{ij}}},b_{N_{\mathit{ij}}},b_{R_{\mathit{ij}}}]`，而左侧向量的系数保持为 `\widetilde{\mathcal{m}}_{\mathit{ij}}` 且为确值，其矩阵表示如情况 2 所示。

```latex
(5.20)
\begin{bmatrix}
\mathcal{m}_{11} & \mathcal{m}_{12} & \cdots & \mathcal{m}_{1n} \\
\mathcal{m}_{21} & \mathcal{m}_{22} & \cdots & \mathcal{m}_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
\mathcal{m}_{n1} & \mathcal{m}_{n2} & \cdots & \mathcal{m}_{\mathit{nn}}
\end{bmatrix}
\begin{bmatrix}
\left\lbrack {\widetilde{x}_{L_{1}},\widetilde{x}_{N_{1}},\widetilde{x}_{R_{1}}} \right\rbrack \\
\left\lbrack {\widetilde{x}_{L_{2}},\widetilde{x}_{N_{2}},\widetilde{x}_{R_{2}}} \right\rbrack \\
\vdots \\
\left\lbrack {\widetilde{x}_{L_{n}},\widetilde{x}_{N_{n}},\widetilde{x}_{R_{n}}} \right\rbrack
\end{bmatrix}
=
\begin{bmatrix}
\left\lbrack {\widetilde{b}_{L_{1}},\widetilde{b}_{N_{1}},\widetilde{b}_{R_{1}}} \right\rbrack \\
\left\lbrack {\widetilde{b}_{L_{2}},\widetilde{b}_{N_{2}},\widetilde{b}_{R_{2}}} \right\rbrack \\
\vdots \\
\left\lbrack {\widetilde{b}_{L_{n}},\widetilde{b}_{N_{n}},\widetilde{b}_{R_{n}}} \right\rbrack
\end{bmatrix}
```

### 情况 3

在 (5.9) 中，系数矩阵和右侧向量的元素均为 TFNs。情况 3 的矩阵表示所示：

```latex
(5.21)
\begin{bmatrix}
\left\lbrack {\widetilde{\mathcal{m}}_{L_{11}},\widetilde{\mathcal{m}}_{N_{11}},\widetilde{\mathcal{m}}_{R_{11}}} \right\rbrack & \left\lbrack {\widetilde{\mathcal{m}}_{L_{12}},\widetilde{\mathcal{m}}_{N_{12}},\widetilde{\mathcal{m}}_{R_{12}}} \right\rbrack & \cdots & \left\lbrack {\widetilde{\mathcal{m}}_{L_{1n}},\widetilde{\mathcal{m}}_{N_{1n}},\widetilde{\mathcal{m}}_{R_{1n}}} \right\rbrack \\
\left\lbrack {\widetilde{\mathcal{m}}_{L_{21}},\widetilde{\mathcal{m}}_{N_{21}},\widetilde{\mathcal{m}}_{R_{21}}} \right\rbrack & \left\lbrack {\widetilde{\mathcal{m}}_{L_{22}},\widetilde{\mathcal{m}}_{N_{22}},\widetilde{\mathcal{m}}_{R_{22}}} \right\rbrack & \cdots & \left\lbrack {\widetilde{\mathcal{m}}_{L_{1n}},\widetilde{\mathcal{m}}_{N_{1n}},\widetilde{\mathcal{m}}_{R_{1n}}} \right\rbrack \\
\vdots & \vdots & \ddots & \vdots \\
\left\lbrack {\widetilde{\mathcal{m}}_{L_{n1}},\widetilde{\mathcal{m}}_{N_{n1}},\widetilde{\mathcal{m}}_{R_{11}}} \right\rbrack & \left\lbrack {\widetilde{\mathcal{m}}_{L_{n2}},\widetilde{\mathcal{m}}_{N_{n2}},\widetilde{\mathcal{m}}_{R_{n2}}} \right\rbrack & \cdots & \left\lbrack {\widetilde{\mathcal{m}}_{L_{\mathit{nn}}},\widetilde{\mathcal{m}}_{N_{\mathit{nn}}},\widetilde{\mathcal{m}}_{R_{\mathit{nn}}}} \right\rbrack
\end{bmatrix}
\begin{bmatrix}
\left\lbrack {\widetilde{x}_{L_{1}},\widetilde{x}_{N_{1}},\widetilde{x}_{R_{1}}} \right\rbrack \\
\left\lbrack {\widetilde{x}_{L_{2}},\widetilde{x}_{N_{2}},\widetilde{x}_{R_{2}}} \right\rbrack \\
\vdots \\
\left\lbrack {\widetilde{x}_{L_{n}},\widetilde{x}_{N_{n}},\widetilde{x}_{R_{n}}} \right\rbrack
\end{bmatrix}
=
\begin{bmatrix}
\left\lbrack {\widetilde{b}_{L_{1}},\widetilde{b}_{N_{1}},\widetilde{b}_{R_{1}}} \right\rbrack \\
\left\lbrack {\widetilde{b}_{L_{2}},\widetilde{b}_{N_{2}},\widetilde{b}_{R_{2}}} \right\rbrack \\
\vdots \\
\left\lbrack {\widetilde{b}_{L_{n}},\widetilde{b}_{N_{n}},\widetilde{b}_{R_{n}}} \right\rbrack
\end{bmatrix}
```

其中系数矩阵的元素 `\widetilde{\mathcal{m}}_{\mathit{ij}}` = `[\mathcal{m}_{L_{\mathit{ij}}},\mathcal{m}_{N_{\mathit{ij}}},\mathcal{m}_{R_{\mathit{ij}}}]` 是 TFNs。

**定义 1** 对于使用 TFN 的梯度下降法，场变量必须具有收敛到所得 TFN 中心和宽度的特性。

由于我们的系统处理模糊性，我们得到了一个 FSE。因此，为了解决 FSE，我们针对 FSE 扩展了梯度下降法。所提出的针对 TFN 的基于梯度的技术已被证明是收敛的。根据定义 1，我们必须首先证明 TFN 的中心值表现出收敛性，然后建立 TFN 宽度收敛的证明。

**定理 1** 如果 `M` 是实数且 SPDM，那么求解 `\widetilde{M}\widetilde{X}_k = \widetilde{\mathcal{Y}}` 等于最小化二次函数 `f(x_k) = \frac{1}{2}\widetilde{X}_k^T\widetilde{M}\widetilde{X}_k - \widetilde{X}_k^T\widetilde{\mathcal{Y}}`。

***证明***

二次函数 `f(x_k) = \frac{1}{2}\widetilde{X}_k^T\widetilde{M}\widetilde{X}_k - \widetilde{X}_k^T\widetilde{\mathcal{Y}}`。

此外，`f(\widetilde{X}_k)` 的最小值通过取上述 FSDA 得到。

考虑近似解 `\widetilde{X}_k`。
