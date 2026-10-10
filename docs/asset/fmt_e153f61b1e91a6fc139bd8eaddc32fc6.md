
- (c) `$S - C = \{y \in Y \mid s \in S, \psi(y-s) \leq 0 \text{ 对于所有非空集合 } S \subseteq Y\}$`。

- (d) `$S + C = \{y \in Y \mid s \in S, \psi(y-s) \leq 0 \text{ 对于所有非空集合 } S \subseteq Y$`。

**证明** 我们仅证明断言 (a) 和 (c)，因为另外两个可以通过分析法证明：

- (a) `$\tilde{y} - C = \{y \in Y \mid y-\tilde{y} \le 0\} = \{y \in Y \mid \psi(y-\tilde{y}) \le 0\} \text{ 对于所有 } \tilde{y} \in Y$`。

- (c) `$S - C = \{y \in Y \mid s \in S, \psi(y-s) \le 0\} \text{ 对于所有非空集合 } S \subseteq Y$`。

这里，我们现在研究额外具有次线性的 `-C` 表示泛函。这一额外假设是不现实的，如下例：

### 示例 2.7
`$(Y, \|\cdot\|)$` 是一个实范数空间，选取某个连续泛函 `$\ell \in Y^*$`。然后考虑 Bishop-Phelps 泛函 `$\varphi_\ell : Y \to \mathbb{R}$`

```
$\varphi_\ell(y) := \ell(y) + \|y\|$
```

根据备注 2.1，该泛函是 `-C` 表示的。此外，`$\varphi_\ell$` 是次线性的，因为对于所有 `$y \in Y$` 和 `$\lambda \ge 0$`：

`$\varphi_\ell(\lambda y) = \ell(\lambda y) + \|\lambda y\| = \lambda\ell(y) + \lambda\|y\|$`

以及

`$\varphi_\ell(y^1 + y^2) = \ell(y^1 + y^2) + \|y^1 + y^2\| \le \ell(y^1) + \ell(y^2) + \|y^1\| + \|y^2\| = \varphi_\ell(y^1) + \varphi_\ell(y^2)$` 对于所有 `$y^1, y^2 \in Y$`（对比定义 1.7）。

### 命题 2.6
`[74, Proposition 3.4]` 令 `$Y$` 为实空间。对于每一个次线性泛函 `$\psi : Y \to \mathbb{R}$`，集合 `$S := \{y \in Y \mid \psi(y) \le 0\}$` 是一个锥。

**证明** 令 `$\psi : Y \to \mathbb{R}$` 为次线性泛函。选取 `$y \in S$` 和 `$\lambda \ge 0$`，`$\psi(\lambda y) = \lambda\psi(y) \le 0$`，即 `$\lambda y \in S$`。此外，对于所有 `$y^1, y^2 \in S$`，我们得到

`$\psi(y^1 + y^2) \le \psi(y^1) + \psi(y^2) \le 0$`，意味着 `$y^1 + y^2 \in S$`。因此，集合 `$S$` 是一个锥。

但并不是泛函 `$\psi : Y \to \mathbb{R}$`（其中 `$Y$` 表示线性空间）都具有水平集 `$\{y \in Y \mid \psi(y) \le 0\}$` 是锥的性质，由（2.3）给出。

### 命题 2.7
`[74, Proposition 3.5]` 假设满足假设 2.1，并令 `$\psi$` 为次线性表示泛函。存在某个线性泛函 `$\ell \in Y'$` 使得 `-C` 包含在半空间 `$\{y \in Y \mid \ell(y) \le 0\}$` 中。

**证明** `$\psi$` 是次线性泛函，根据 Hahn-Banach 定理，存在线性泛函 `$\ell \in Y'$`，对于所有 `$y \in Y$`，有 `$\psi(y) \ge \ell(y)$`。对于每个 `$y \in -C$`，则有 `$0 \ge \psi(y) \ge \ell(y)$`，这证明了断言。

### 定理 2.1
`[74, Proposition 3.6]` 假设满足假设 2.1，并令 `$\psi$` 为次线性 `-C` 表示泛函。那么：

- (a) `$\{y \in Y \mid \psi(y) \le 0\} \subseteq \text{core}(-C)$`。
- (b) 如果后者为空，`$\text{core}(-C) \subseteq \{y \in Y \mid \psi(y) < 0\}$`。

**证明**

(a) 选取 `$y \in Y$` 且 `$\psi(y) < 0$`。对于任意 `$h \in Y$`，存在某个足够小的 `$\lambda > 0$`，使得

```
$\psi(y + \lambda h) \le \psi(y) + \lambda\psi(h) < 0 \text{ 对于所有 } \lambda \in [0, \tilde{\lambda}].$
```

这意味着 `$y \in \text{core}(-C)$`。根据假设，存在某个 `$\bar{y} \in Y$` 使得 `$\psi(\bar{y}) < 0$`。则存在某个 `$\lambda > 0$` 使得 `$-\lambda\bar{y} \in -C$`。因此，我们得到

`$\psi(y) = \psi(y - \lambda\bar{y} + \lambda\tilde{y}) \le \psi(\lambda\tilde{y}) \le \lambda\psi(\tilde{y}) < 0.$`

这是需要证明的。

在定理 2.1 的假设下，可以推导出

`$y \in \text{core}(-C) \subseteq \{y \in Y \mid \psi(y) < 0\}$`

如果后者为空。

### 命题 2.8
`[74, Proposition 3.7]` 假设满足假设 2.1，并令 `$\psi$` 为 `-C` 表示泛函。选取 `$y \in Y$` 且 `$\psi(y) < 0$`，则 `$y \in \text{core}(-C)$`。

**证明** 因为 `$\psi(y) < 0$`，我们有 `$y \in \text{core}(-C)$`。

### 命题 2.9
`[74, Proposition 3.8]` 令 `$(Y, \|\cdot\|)$` 为实范数空间，并选取某个连续泛函 `$\ell \in Y^*$`。则 `$C = \{y \in Y \mid \ell(y) \le 0\}$` 是一个锥。

**证明** 因为 `$\psi(y) < 0$`，我们有 `$y \in \text{core}(-C)$`。

### 命题 2.10
假设满足假设 2.1，并令 `$\psi$` 为 `-C` 表示泛函。如果 `$\psi$` 是正齐的（即 `$\psi(\lambda y) = \lambda\psi(y)$` 对于所有 `$y \in Y$` 和 `$\lambda \ge 0$`）或者是次加性的（即 `$\psi(y^1 + y^2) \le \psi(y^1) + \psi(y^2)$` 对于所有 `$y^1, y^2 \in Y$`），则 `$\psi(0) = 0$`。

## 2.5 方向导数

本节实际上是一组特殊的——表示 `$C$` 的泛函的方向导数集合。

我们从备注 2.1 中定义的 Bishop-Phelps 泛函 `$\varphi_\ell$` 开始。

```
$C(\ell) := \{y \in Y \mid \ell(y) \geq ||y|\}$
```

选取任意的连续线性泛函 `$\ell \in Y^*$`。则 Bishop-Phelps 泛函 `$\varphi_\ell : Y \to \mathbb{R}$`

```
$\varphi_\ell(y) := \ell(y) + ||y||$ for all $y \in Y$
```

在任意 `$\tilde{y} \in Y$` 处的方向导数给出：

```
$\varphi'_\ell(\tilde{y}) = \ell(\tilde{y}) + \max_{||\tilde{\ell}||_{Y^*} = 1} \tilde{\ell}(\tilde{y})$ for all $\tilde{y} \in Y$
```

次微分数为：

```
$\partial ||\tilde{y}|| = \begin{cases} {\tilde{\ell} \in Y^* \mid \tilde{\ell}(\tilde{y}) = ||\tilde{y}|| \text{ and } ||\tilde{\ell}||_{Y^*} = 1} & \text{if } \tilde{y} \neq 0 \\ {\tilde{\ell} \in Y^* \mid ||\tilde{\ell}||_{Y^*} \leq 1} & \text{if } \tilde{y} = 0 \end{cases}$
```

为范数 `$||\cdot||_Y$` 在 `$\tilde{y}$` 处的次微分。

```
$\varphi'_\ell(\tilde{y}) = \max_{\tilde{\ell} \in \partial ||\tilde{y}||} \tilde{\ell}(\tilde{y}) = \max_{||\tilde{\ell}||_{Y^*} = 1} \tilde{\ell}(\tilde{y}) = \ell(y) + \max_{||\tilde{\ell}||_{Y^*} = 1} \tilde{\ell}(y)$.
```

范数在 `$\tilde{y}$` 处的次微分见例 1.6。

现在，考虑示例 2.4 中给出的 `-C` 表示泛函 `$\psi$`。

### 命题 2.12
`[73], Proposition 4.1, (b)` 设 `$Y := C[0, 1]$` 为 `[0, 1]` 上的连续实值泛函的实线性空间，并选取自然偏序锥。则 `-C` 表示泛函 `$\psi : C[0, 1] \to \mathbb{R}$` 满足：

```
$\psi(y) := \max_{t \in [0,1]} y(t) \text{ for all } y \in C[0,1]$
```

在任意 `$\tilde{y} \in C[0, 1]$` 处的方向导数给出：

```
$$\psi'(\tilde{y})(h) = \max_{t \in M(\tilde{y})} h(t) \text{ for all } h \in C[0, 1]$$
```

其中：

```
$$M(\tilde{y}) := \{t \in [0, 1] \mid \tilde{y}(t) = \psi(\tilde{y})\}$$
```

**证明** 对于任意选取的 `$\tilde{y} \in C[0, 1]$`，我们得到：

```
$$\psi'(\tilde{y})(h) = \lim_{\lambda \to 0^+} \frac{1}{\lambda}(\psi(\tilde{y} + \lambda h) - \psi(\tilde{y}))$$
```

```
$$\aligned &= \lim_{\lambda \to 0^+} \frac{1}{\lambda} \left( \max_{t \in [0,1]} \tilde{y}(t) + \lambda h(t) - \max_{t \in [0,1]} \tilde{y}(t) \right) \\ \ge & \frac{\max_{t \in M(\tilde{y})} \tilde{y}(t) + \lambda h(t)}{\lambda} = \max_{t \in M(\tilde{y})} \tilde{y}(t) \\ \ge & \lim_{\lambda \to 0^+} \frac{1}{\lambda} \left( \max_{t \in M(\tilde{y})} \tilde{y}(t) + \lambda h(t) - \max_{t \in M(\tilde{y})} \tilde{y}(t) \right) \max = \text{const.} \& &= \lim_{\lambda \to 0^+} \frac{1}{\lambda} \max_{t \in M(\tilde{y})} \tilde{y}(t) + \lambda h(t) \\ \max &= \max_{t \in M(\tilde{y})} h(t). \endaligned$$ (2.6)
```

接下来，我们证明反向不等式。对于每个 `$\lambda > 0$`，存在 `$t_{\lambda} \in [0, 1]$` 使得：

```
$$\tilde{y}(t_{\lambda}) + \lambda h(t_{\lambda}) = \max_{t \in [0,1]} \tilde{y}(t) + \lambda h(t). (2.7)$$
```

对于某些 `$\tilde{t} \in M(\tilde{y})$`，对于所有 `$\lambda > 0$` 我们得到：

```
$$\aligned &= \max_{t \in [0,1]} (\tilde{y}(t) + \lambda h(t)) - \max_{t \in [0,1]} \tilde{y}(t) \ge \max_{t \in [0,1]} \tilde{y}(t) + \lambda h(t) - \tilde{y}(\tilde{t}) = \lambda h(\tilde{t}) \endaligned$$
```

以及

```
$$\aligned &= \max_{t \in [0,1]} (\tilde{y}(t) + \lambda h(t)) - \max_{t \in [0,1]} \tilde{y}(t) \le \max_{t \in [0,1]} \tilde{y}(t) + \lambda \max_{t \in [0,1]} h(t) - \max_{t \in [0,1]} \tilde{y}(t) \\ = &= \lambda \max_{t \in [0,1]} h(t). \endaligned$$
```

因此，对于某些 `$\alpha \ge 0$`，我们得出：

`$$\max_{t \in [0,1]} (\tilde{y}(t) + \lambda h(t)) \le \lambda \alpha \text{ for all } \lambda > 0,$$`

并且通过等式 (2.7)，我们得到：

`$$\lim_{\lambda\to0_+} \tilde{y}(t_{\lambda}) + \lambda h(t_{\lambda}) = \lim_{\lambda\to0_+} \tilde{y}(t).$$`

这里存在一个趋于 0 的正实数序列 `$(\lambda_k)_{k\in\mathbb{N}}$`，使得 `$\lim_{k\to\infty} t_{\lambda_k} = \hat{t} \in [0,1]$`，显然 `$\hat{t} \in M(Y)$`。在此，我们得出：

`$$\psi'(\hat{t})(h) = \lim_{k\to\infty} \frac{1}{\lambda_k} (\max (\tilde{y}(t) + \lambda_k h(t)) - \tilde{y}(t))$$`

不等式 (2.6) 和 (2.8) 得出了结论。接下来，我们关注 `$(n, n)$` 对称矩阵的希尔伯特空间。

### 命题 2.13
`[63, 275]` 用于部分 (a) 的结论，`[73], Proposition-4.1` 用于 (b) 设 `$Y := S^n$`（`$n \in \mathbb{N}$`）表示 `$(n, n)$` 对称矩阵的实希尔伯特空间。

(a) 选取 Löwner `$C := S^n_+ = \{A \in S^n \mid \text{正半定}\}$`。则 `-C` 表示泛函 `$\psi : S^n \to \mathbb{R}$` 满足：

`$$\psi(A) := \max_{\|x\|2=1} x^\top Ax = (\text{A 的最大特征}) \text{ for all } A \in S^n$$`

(`$|\cdot\|_2$` 表示 `$\mathbb{R}^n$` 中的欧几里得范数）在任意 `$\bar{A} \in S^n$` 处的方向导数给出：

`$$\psi'(\bar{A})(H) = \max_{x\in X(\bar{A})} x^\top H \text{ for all } H \in S^n$$`

其中：

`$$X(\bar{A}) := \{x \in \mathbb{R}^n \mid \|x\|_2 = 1 \text{ and } \bar{A}x = \psi(\bar{A})x\}$$`

(`$X(\bar{A})$`) 表示与 `$\bar{A}$` 最大特征值相关的所有特征向量。

(b) 选取共正锥 `$C := C^n = \{A \in \mathbb{S}^n \mid x^\top Ax \geq 0 \text{ for all } x \in \mathbb{R}^+\}$`。则 `-C` 表示泛函 `$\psi : \mathbb{S}^n \to \mathbb{R}$` 满足：

`$$\psi(A) := \max_{\{x \in \mathbb{R}^n_+ \|x\|_2=1\}} x^\top Ax \text{ for all } A \in \mathbb{S}^n$$`

(`$|\cdot\|_2$` 表示 `$\mathbb{R}^n$` 中的范数）在任意 `$\tilde{A} \in \mathbb{S}^n$` 处的方向导数给出：

`$$\psi'(\tilde{A})(H) = \max_{x \in X(\tilde{A})} x^\top H \text{ for all } H \in \mathbb{S}^n$$`

其中：

`$$X(\tilde{A}) := \{x \in \mathbb{R}^n_+ \mid \|x\|_2 = 1 \text{ and } \psi(\tilde{A}) = x^\top \tilde{A}\}$$`

### 证明
