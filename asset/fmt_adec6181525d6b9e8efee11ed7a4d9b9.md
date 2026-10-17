
(a) 该结论的证明遵循命题 2.12 的对于。对于选取的 $\tilde{A}, H \in \mathbb{S}^n$，我们有：

$$\psi'(\tilde{A})(H) = \lim_{\lambda \to 0^+} \frac{1}{\lambda}(\psi(\tilde{A} + \lambda H) - \psi(\tilde{A}))$$

$$= \lim_{\lambda \to 0^+} \frac{1}{\lambda} \left( \max_{\|x\|_2=1} x^\top(\tilde{A} + \lambda H)x - \max_{\|x\|_2=1} x^\top \tilde{A} \right)$$

$$\ge \max_{x \in X(\tilde{A})} x^\top(\tilde{A} + \lambda H)x = \max_{x \in X(\tilde{A})} x^\top \tilde{A}x \quad \text{on } X(\tilde{A})$$

$$\ge \lim_{\lambda \to 0^+} \max_{x \in X(\tilde{A})} x^\top \tilde{A}x + \lambda x^\top HX - x^\top \tilde{A}$$

$$= \max_{x \in X(\tilde{A})} x^\top HX. \quad (2.9)$$

对于反向不等式的证明，选取任意的 $\lambda > 0$。存在 $\|x_\lambda\|_2 = 1$ 的 $x_\lambda$ 使得：

$$x_\lambda^\top(\tilde{A} + \lambda H) = \max_{\|x\|_2=1} x^\top(\tilde{A} + \lambda H)x.$$

对于任意 $x \in X(\tilde{A})$ 我们得到：

$$\max_{\|x\|_2=1} x^\top(\tilde{A} + \lambda H)x - \max_{\|x\|_2=1} x^\top \tilde{A}x \ge \max_{\|x\|_2=1} x^\top(\tilde{A} + \lambda H)x - \tilde{A}x$$

42 - 泛函数的表示

不等式 (2.9) 和 (2.10) 意味着该断言。

(b) 该证明遵循部分 (a)。对于任意选择的 $\bar{A}, H \in \mathbb{S}^n$，有

```
$$\psi'(\bar{A})(H) = \lim_{\lambda \to 0^+} \frac{1}{\lambda}(\psi(\bar{A} + \lambda H))
= \lim_{\lambda \to 0^+} \frac{1}{\lambda} \left( \max_{x \in \mathbb{R}_+^n \|x\|_2=1} x^{\mathrm{T}}(\bar{A} + \lambda H) - \max_{x \in \mathbb{R}_+^n \|x\|_2=1} x^{\mathrm{T}}\bar{A} \right)\\\geq \max_{x \in X(\bar{A})} x^{\mathrm{T}}(\bar{A} + \lambda H)\\
= \max_{x \in X(\bar{A})} x^{\mathrm{T}}\bar{A} \quad \text{on } X(\bar{A})$\
\geq \lim_{\lambda \to 0^+} \frac{1}{\lambda} x^{\mathrm{T}}\bar{A} + \lambda x^{\mathrm{T}}Hx\\
= \max x^{\mathrm{T}}Hx. \qquad (2.11)$$
```

对于逆不等式的证明，选择任意的 $\lambda > 0$。存在某些 $x_{\lambda} \in \mathbb{R}_+^n$ 使得 $\|x_{\lambda}\|_2=1$，满足

```
$x_{\lambda}^{\mathrm{T}}(\bar{A} + \lambda H) = \max_{x \in \mathbb{R}_+^n \|x\|_2=1} x^{\mathrm{T}}$
```

对于任意的 $\tilde{x} \in X(\bar{A})$，我们得到

```
$x^{\mathrm{T}}(\bar{A} + \lambda H) - \max_{x \in \mathbb{R}_+^n \|x\|_2=1} x^{\mathrm{T}}\bar{A} \geq \tilde{x}^{\mathrm{T}}(\bar{A} + \lambda H) - \tilde{x}^{\mathrm{T}}\bar{A}$
```

```
$= \lambda\tilde{x}^{\mathrm{T}}H\tilde{x} \quad \text{for all } \lambda > 0,$
```

并且对于

```
$x^{\mathrm{T}}(\bar{A} + \lambda H) - \max_{x \in \mathbb{R}_+^n \|x\|_2=1} x^{\mathrm{T}}\bar{A}$
```

```
$$\geq \max_{x \in \mathbb{R}_+^n \|x\|_2=1} x^{\mathrm{T}}\bar{A} + \lambda \max_{x \in \mathbb{R}_+^n \|x\|_2=1} x^{\mathrm{T}}Hx - \max_{x \in \mathbb{R}_+^n \|x\|_2=1} x^{\mathrm{T}}\bar{A}$$
```

```
$= \lambda \max_{x \in \mathbb{R}_+^n \|x\|_2=1} x^{\mathrm{T}}Hx \quad \text{for all } \lambda > 0,$
```

### 2.5 方向导数

对于某些 $\alpha \ge 0$，我们得出

```
$$\max_{x \in \mathbb{R}^n \|x\|_2=1} x^{\mathsf{T}}(\tilde{A} + \lambda H)x - \max_{x \in \mathbb{R}^n \|x\|_2=1} x^{\mathsf{T}}\tilde{A} \le \lambda \alpha \text{ for all } \lambda > 0.$$$
```

因此，我们有

```
$$\lim_{\lambda \to 0_+} x^{\mathsf{T}}(\tilde{A} + \lambda H)x_{\lambda} = \max_{x \in \mathbb{R}^n \|x\|_2=1} x^{\mathsf{T}}\tilde{A}.$$
```

所以，存在一个正数序列 $(\lambda_k)_{k \in \mathbb{N}}$ 收敛于 0，且 $\lim_{k \to \infty} x_{\lambda_k} = \tilde{x} \in X(\tilde{A})$。我们得出

```
$$\Psi'(\tilde{A})(H) = \lim_{k \to \infty} \frac{1}{\lambda_k} \max_{x \in \mathbb{R}^n \|x\|_2=1} x^{\mathsf{T}}(\tilde{A} + \lambda_k H)x - \max_{x \in \mathbb{R}^n \|x\|_2=1} x^{\mathsf{T}}\tilde{A} \\
\ge x_{\lambda_k}^{\mathsf{T}}(\tilde{A} + \lambda_k H)x_{\lambda_k} \\
\ge \lambda_k x_{\lambda_k}^{\mathsf{T}}H x_{\lambda_k} \\
= \lim_{k \to \infty} \frac{1}{\lambda_k} (x_{\lambda_k}^{\mathsf{T}}\tilde{A}x_{\lambda_k} + \lambda_k x_{\lambda_k}^{\mathsf{T}}H x_{\lambda_k}) \\
= \tilde{x}^{\mathsf{T}}H\tilde{x} \\
\le \max_{x \in X(\tilde{A})} x^{\mathsf{T}}Hx. \quad (2.12)$$
```

不等式 (2.11) 和 (2.12) 意味着该断言。

**备注 2.4** [73, 4.2] 如果在命题2 (a) 中矩阵 $\tilde{A} \in \mathcal{S}^n$ 的最大特征是单的，那么对应的特征向量 $\tilde{x}$ 是唯一的，且集合 $X(\tilde{A})$ 包含该向量。在这种特殊情况下，方向导数为

```
$$\Psi'(\tilde{A})(H) = \tilde{x}^{\mathsf{T}}H\tilde{x} \quad \text{for all } H \in \mathcal{S}^n.$$
```

如果 $\tilde{A}$ 的最大特征是重特征，则集合 $X(\tilde{A})$ 是 $\mathbb{S}^n$ 中一个由 $\tilde{A}$ 的特征向量所张成的二维子空间内的一个圆。设 $\tilde{x}^1$ 和 $\tilde{x}^2$ 为 $\tilde{A}$ 的最大特征值的正交特征向量。那么该子空间由 $\tilde{x}^1$ 和 $\tilde{x}^2$ 张成，我们有

```
$$X(\tilde{A}) = \{\alpha\tilde{x}^1 + \beta\tilde{x}^2 \mid \alpha, \beta \in \mathbb{R} \text{ and } \|\alpha\tilde{x}^1 + \beta\tilde{x}^2\|_2 = 1\}.$$
```

在这种特殊情况下，方向导数为

```
$$\Psi'(\tilde{A})(H) = \max_{\alpha,\beta \in \mathbb{R}} (\alpha\tilde{x}^1 + \beta\tilde{x}^2)^{\mathsf{T}} H (\alpha\tilde{x}^1 + \beta\tilde{x}^2) \quad \text{for all } H \in \mathcal{S}^n.$$
```

这个两个变量的极大化很容易解决。最后，我们考虑空间 $\mathbb{R}^m$。

**命题 2.14** [72, 8.3] 设 $\tilde{Y} := \mathbb{R}^m$（$m \in \mathbb{N}$）且选择 $C := \mathbb{R}^m_+$。那么表示 $-C$ 的泛函数 $\psi : \mathbb{R}^m \to \mathbb{R}$

```
$$\psi(y) = \max(y_1, \dots, y_m) \quad \text{for all } y = (y_1, \dots, y_m) \in \mathbb{R}^m$$
```

在任意 $\tilde{y} \in \mathbb{R}^m$ 处的方向导数为

```
$$\Psi'(\tilde{y})(h) = \max_{i \in I(\tilde{Y})} h_i \quad \text{for all } h = (h_1, \dots, h_m) \in \mathbb{R}^m$$
```

其中

```
$$I(\tilde{Y}) := \{i \in \{1, \dots, m\} \mid \tilde{y}_i = \psi(\tilde{y})\}.$$
```

**证明** 该证明遵循命题 2.12 的证明。对于任意的 $\tilde{y}, h \in \mathbb{R}^m$，我们得到

```
$$\Psi'(\tilde{y})(h) = \lim_{\lambda \to 0^+} \frac{1}{\lambda} (\Psi(\tilde{y} + \lambda h) - \Psi(\tilde{y}))\\
= \lim_{\lambda \to 0^+} \frac{1}{\lambda} (\max_{1 \le i \le m} \{\tilde{y}_i + \lambda h_i\} - \max_{1 \le i \le m} \{\tilde{y}_i\})\\
= \lim_{\lambda \to 0^+} \frac{1}{\lambda} (\max_{i \in I(\tilde{Y})} \{\tilde{y}_i + \lambda h_i\} - \max_{i \in I(\tilde{Y})} \{\tilde{y}_i\})$$$$
```

对于足够小的 $\lambda > 0$，我们有

```
$$\max_{1 \le i \le m} \{\tilde{y}_i + \lambda h_i\} = \max_{i \in I(\tilde{Y})} \{\tilde{y}_i + \lambda h_i\}$$
```

因为对于 $j \notin I(\tilde{Y})$，即 $\tilde{y}_j < \max_{1 \le i \le m} \{\tilde{y}_i\}$，存在某些 $\varepsilon > 0 使得

```
$$\tilde{y}_j + \lambda h_j \le \tilde{y}_j + \varepsilon < \max_{1 \le i \le m} \{\tilde{y}_i\}$$
```

并且

```
$$\tilde{y}_j + \lambda h_j < \max_{1 \le i \le m} \{\tilde{y}_i + \lambda h_i\}.$$$$
```

### 2.6 次微分

因此，我们得出

```
$$\psi'(\bar{y})(h) = \lim_{\lambda \to 0_+} \lambda \left( \max_{i \in R(Y)} \{\bar{y}_i + \lambda h_i\} - \max_{i \in R(Y)} \{\bar{y}_i\} \right) = \text{const}\\
= \lim_{\lambda \to 0_+} \lambda \max_{i \in R(Y)} \{\bar{y}_i + \lambda h_i - \bar{y}_i\\
= \lim_{\lambda \to 0_+} \max_{i \in R(Y)} [\lambda h_i]\\
= \max_{i \in R(Y)} \{h_i\},$$$$
```

这证明了该断言。

结合示例 2.2 注意，惩罚泛函数 $\eta : \mathbb{R}^m \to \mathbb{R}^+$

$\eta(y) := \sum_{i=1}^m (\max(0, y_i))^2 \quad \text{for all } y = (y_1, \dots, y_m)$

### 2.6 -C 表示泛函

根据备注 2.3 (a)，这意味着对于每一个 $n \in \mathbb{N}$，有

$-\ell_n(c) = \ell_n(-c) \leq \psi(-c) \leq 0$ 对于所有 $c \in C$。

因此，我们得到

$$\tilde{\ell}(c) = \lim_{n \to \infty, n \geq 0} \lambda_n(c) \geq 0 \text{ 对于所有 } c \in C,$$$$

即 $\tilde{\ell} \in C^*$。

我们讨论一个非常简单的例子。

**示例 2.8 ([74, 示例 3.2])** 对于 $\mathbb{R}^2$ 中的锥 $C := \mathbb{R}_+^2$，众周知 $C$ 与其对偶锥 $C^*$ 重合，即 $C$ 是自对的。对于表示 $-C$ 的泛函 $\psi: \mathbb{R}^2 \to \mathbb{R}$

$$\psi(y) := \max\{y_1, y_2\} \text{ 对于所有 } y = (y_1, y_2) \in \mathbb{R}^2,$$$$

我们得到次微分

$$\partial\psi(0_{\mathbb{R}^2}) = \{\ell \in \mathbb{R}^2 \mid \psi(y) \geq \ell^T y \forall y \in \mathbb{R}^2\}$$

$= \{(\ell_1, \ell_2) \in \mathbb{R}^2 \mid \max\{y_1, y_2\} \geq \ell_1 y_1 + \ell_2 y_2 \forall (y_1, y_2) \in \mathbb{R}^2\}.$$

通过简单的计算，我们发现不等式

$$\max\{y_1, y_2\} \geq \ell_1 y_1 + \ell_2 y_2 \text{ 对于所有 } (y_1, y_2) \in \mathbb{R}^2$$

等价于条件 $(\ell_1, \ell_2) \in \text{conv} \{ \begin{pmatrix} 0 \\ 1 \end{pmatrix} \}$，即

$ $cone(\partial\psi(0_{\mathbb{R}^2})) = \text{conv} \{ \begin{pmatrix} 0 \\ 1 \end{pmatrix} \} = \mathbb{R}_+^+ = C^*$。

这个例子表明，定理 2.2 断言中的包含关系也可以是等式。

最后，我们将注意力转向 Bishop-Phelps 锥，它的处理非常简单。
