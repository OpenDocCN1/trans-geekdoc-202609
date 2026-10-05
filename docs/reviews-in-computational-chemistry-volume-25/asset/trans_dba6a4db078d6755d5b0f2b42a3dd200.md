

## 自旋密度密度泛函理论 207

现在引入了自旋相关的算符。外部电势可以是作用于双分量旋旋的算符 $\hat{V}_{ext}$。交换相关电势的定义如方程[27]所示，尽管 $E_{xc}$ 现在是自旋密度矩阵的泛函 $E_{xc} = E_{xc}[\rho_{\alpha\beta}]$。交换相关电势为

```
$V_{xc}^{\alpha\beta}(\vec{r}) = \frac{\delta E_{xc}[\rho_{\alpha\beta}]}{\delta \rho_{\alpha\beta}(\vec{r})} \quad [40]$
```

该电势通常用虚构的交换相关磁场 $B_{xc}$表示：

```
$V_{xc}^{\alpha\beta}(\vec{r}) = \frac{\delta E_{xc}}{\delta n(\vec{r})}I - B_{xc}(\vec{r}) \cdot \sigma \quad [41]$
```

```
$B_{xc}(\vec{r}) = - \frac{\delta E_{xc}}{\delta m(\vec{r})} \quad [42]$
```

Kohn-Sham 密顿量为

```
$$\hat{H}_{KS}[\rho_{\alpha\beta}] = \hat{T} + \hat{V}_{ext} + \hat{V}_H[n]I + \hat{V}_{xc}[\rho_{\alpha\beta}] \quad [43]$
```

对应的 Kohn-Sham 方程变为：

```
$$\hat{H}_{KS}[\rho_{\alpha\beta}]|\Psi_j = \varepsilon_j|\Psi_j \quad [44]$
```

即：

```
$$\sum_{\beta} \left( -\frac{\nabla^2}{2}\delta_{\alpha\beta} + V_{KS}^{\alpha\beta}(\vec{r}) \right) \Psi_{\beta}(\vec{r}) = \varepsilon_i \Psi_{xc}(\vec{r}) \quad [45]$$
```

其中 Kohn-Sham 有效电势为：

```
$V_{KS}^{\alpha\beta}(\vec{r}) = V_{ext}^{\alpha\beta}(\vec{r}) + \delta_{\alpha\beta} \frac{n(\vec{r}')}{|\vec{r}-\vec{r}'|} d^3r' + V_{xc}^{\alpha\beta}(\vec{r}) \quad [46]$
```

在大多数感兴趣的情况下，自旋密度 $n(\vec{r})$ 是共线的；磁化密度 $m(\vec{r})$ 的方向在系统占据的空间内是相同的；按照惯例，将其识别为 z 方向。如果外部电势是对角线，则哈密顿量也是对角线，这允许人们将旋旋的自旋 $\uparrow$ 和 $\downarrow$ 分量分离，并得到两个

## 208 过渡元素原子簇的磁学性质

方程组。这种方法被称为自旋极化计算。自旋极化程度定义为 $\xi = (n_+ - n_-)/n$，范围从 0 到 1。当 $\xi = 1$ 时，我们得到一个完全极化的系统；当 $\xi = 0$ 时，系统未极化。这种方法足以处理在某些固体中发现的铁磁或反铁磁有序。$^{31,32}$ 在铁磁和反铁磁有序中，自旋磁矩指向相同的方向（$\uparrow\uparrow\uparrow \dots$），而在反铁磁有序中，晶格点上的自旋 $\uparrow$ 磁矩周围相邻晶格点是相反方向的自旋 $\downarrow$，反之亦然。

## 局部自旋密度近似 (LSDA)

与非自旋极化情况一样，自旋极化方法的主要问题源于我们对交换相关能量泛函 $E_{xc}[\rho_{\alpha\beta}]$ 的认知有限，该泛函是未。然而，对于完全极化的相互作用电子气体，$E_{xc}[\rho_{\beta}]$ 是已知的，即 $n(\vec{r}) = n_-(\vec{r}) = 0$（当然，对于非均匀电子气体，$n_+(\vec{r}) = n/2$，见上文）。因此，von Barth 和 Hedin 为部分极化电子气体的每个电子能量提出了插值公式（z 轴作为自旋量子化方向）：

```
$e_{xc}(n,\xi) = e_{xc}^c(n) + [e_{xc}^F(n)]f(\xi) \quad [47]$
```

其中函数 $f(\xi)$ 给出交换能量的自旋依赖性：

```
$f(\xi) = \frac{1}{2}(2^{1/3}-1)^{-1}\{(1+\xi)^{4/3} + (1-\xi)^{4/3} - 2\} \quad [48]$
```

在方程[47] 中，$e_{xc}^c(n)$ 和 $e_{xc}^F(n)$ 是未极化（顺磁）和完全极化（铁磁）电子气体的交换相关密度。von Barth 和 Hedin 方便地参数化了 $e_{xc}^c(n)$ 和 $e_{xc}^F(n)$。对于 $e_{xc}(n,\xi)$，还提出了其他插值方法用于构建 LSDA：

```
$E_{xc}[\rho_{\alpha\beta}] = \int n(\vec{r})e_{xc}(n(\vec{r}),\xi(\vec{r}))d^3r \quad [49]$
```

```
$V_{xc}^c(\vec{r}) = -\frac{\delta E_{xc}[\rho_{\alpha\beta}]}{\delta n(\vec{r})} \quad [50]$
```

## 非共线自旋密度泛函理论 209

与无限制 Hartree-Fock 方法一样，LSDA 允许不同的自旋取向。LSDA 简化了交换但也包含了库仑相关。

## 非共线自旋密度泛函理论

在许多感兴趣的系统中，自旋密度是共线的；即磁化矢量 $\vec{m}$ 的方向在空间任意处都是相同的。然而，在其他系统中$\vec{m}$ 的方向随空间变化，著名的例子是铁的 $\gamma$ 相$^{34}$。在低对称性或无序系统中很容易出现非共线磁构型$^{35,36}$。固体进行了允许非共线磁结构的广义 LSDA 计算$^{37–39}$。簇的非共线形式是较新的$^{40,41}$，并以 LSDA 为基础。当使用交换相关泛函时，核心思想是由 von Barth 和 Hedin 引入的。可以将系统体积分成若干个小盒子，并考虑每个小盒子内的电子形成自旋极化气体，其密度为 $n_{\uparrow}(\vec{r})$ 和 $n_{\downarrow}(\vec{r})$，即 $\vec{r}$ 处自旋密度矩阵 $\rho_{\alpha\beta}$ 的两个实正特征值。在每一点，可以使用局部坐标系使得 z 轴与局部自旋方向对齐。通过这种方法，我们可以使用 LSDA 交换相关泛函并在局部对角系中计算交换电势。这种策略提供了一种局部磁化密度近似，其本质与 LSDA 相似。在 LSDA 中，通过假设系统局部表现为自旋极化气体来计算交换电势。

## 210 过渡元素原子簇的磁学性质

## 非共线自旋密度泛函理论

（此处为原文重复内容，根据要求跳过翻译）$\vec{m}$ 的方向随空间变化，著名的例子是铁的 $\gamma$ 相$^{34}$。在低对称性或无序系统中很容易出现非共线磁构型$^{35,36}$。固体进行了允许非共线磁结构的广义 LSDA 计算$^{37–39}$。簇的非共线形式是较新的$^{40,41}$，并以 LSDA 为基础。当使用交换相关泛函时，核心思想是由 von Barth 和 Hedin 引入的。可以将系统体积分成若干个小盒子，并考虑每个小盒子内的电子形成自旋极化气体，其密度为 $n_{\uparrow}(\vec{r})$ 和 $n_{\downarrow}(\vec{r})$，即 $\vec{r}$ 处自旋密度矩阵 $\rho_{\alpha\beta}$ 的两个实正特征值。在每一点，可以使用局部坐标系使得 z 轴与局部自旋方向对齐。通过这种方法，我们可以使用 LSDA 交换相关泛函并在局部对角系中计算交换电势。这种策略提供了一种局部磁化密度近似，其本质与 LSDA 相似。在 LSDA 中，通过假设系统局部表现为自旋极化气体来计算交换电势。

$U^+(\tilde{r})$ 是 $U(\tilde{r})$ 的伴随（或厄米特共轭）。局部旋转角 $\theta(\tilde{r})$ 和 $\phi(\tilde{r})$（磁化矢量的方位角和极角）通过方程[52] 矩阵中非对角元素为零的要求计算得出。

```
$U(\tilde{r}) = \begin{pmatrix} \cos(\theta/2)e^{-i\phi/2} & -\sin(\theta/2)e^{-i\phi/2} \\ -\sin(\theta/2)e^{i\phi/2} & \cos(\theta/2)e^{i\phi/2} \end{pmatrix}$
```
（注：矩阵的 OCR 是碎片化的，根据上下文和提供的文本流进行了重建）：

这导致了 $2 \times 2$ 厄米矩阵形式的交换相关电势：

```
$V_{xc}(\tilde{r}) = \frac{1}{2}(V_{sc}^{\uparrow}(\tilde{r}) + V_{sc}^{\downarrow}(\tilde{r}))\mathbf{I} + \frac{1}{2}(V_{sc}^{\uparrow}(\tilde{r}) - V_{sc}^{\downarrow}(\tilde{r}))\boldsymbol{\sigma} \cdot d(\tilde{r}) \quad [55]$
```

$d(r)$ 是磁化 $m(r)$ 方向的单位矢量。方程[55]中第二项的存在有效地耦合了自旋 $\uparrow$ 和 $\downarrow$ 分量。

