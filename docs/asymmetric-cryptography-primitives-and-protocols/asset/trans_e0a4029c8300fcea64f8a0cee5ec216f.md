

# 定义 11.7（算术电路可满足性）

设 `\mathbb{F}` 为有限域，`C : \mathbb{F}^{\ell_{in}} \times \mathbb{F}^{\ell_{wit}} \to \mathbb{F}^{\ell_{out}}` 为一个算术电路。算术电路可满足性关系 `R_C : (\mathbb{F}^{\ell_{in}} \times \mathbb{F}^{\ell_{out}}) \times \mathbb{F}^{\ell_{wit}} \to \{true, false\}` 是这样一种关系：输入元组 `((\vec{x}, \vec{y}), \vec{w})` 时，若 `C(\vec{x}, \vec{w}) = \vec{y}` 则返回 `true`，否则返回 `false`。

## 11.6.2. 二次算术程序

我们介绍 Gennaro 等人 (2013) 引入的 QAP 概念。

### 定义 11.8（QAP (Gennaro 等人, 2013)）

QAP 是一个元组 `(\mathbb{F}, n, m, \ell, v(X), \vec{a}(X), \vec{b}(X), \vec{c}(X))`，其中 `\mathbb{F}` 是有限域，`n, m, \ell \in \mathbb{N}` 为正整数，`v(X)` 是一个 `n` 次多项式，`\vec{a}(X), \vec{b}(X), \vec{c}(X)` 是三个包含 `m` 个次数 `< n` 的多项式的向量。QAP 关系 `R_{QAP} : \mathbb{F}^\ell \times \mathbb{F}^{m-\ell-1} \to \{true, false\}` 是一种二元关系，输入 `(\vec{x}, \vec{w})` 时，当且仅当满足以下条件返回 `true`：

```
\sum_{j=1}^m z_j a_j(X) \cdot \sum_{j=1}^m z_j b_j(X) - \sum_{j=1}^m z_j c_j(X) = h(X) v(X)
```

其中 `\vec{z} := (1, \vec{x}, \vec{w})`。

Gennaro 等人 (2013) 证明了如何用 QAP 编码算术电路可满足性。下文我们将陈述并证明他们的结果，我们认为这是一个将电路检查算术化的很好的例子。

### 定理 11.3

设 `C : \mathbb{F}^{\ell_{in}} \times \mathbb{F}^{\ell_{wit}} \to \mathbb{F}^{\ell_{out}}` 为一个包含 `N` 个乘法门的算术电路，`R_C` 为其关联的算术电路可满足性关系。则存在一个 QAP 关系 `R_{QAP} := (\mathbb{F}, n, m, \ell, v(X), \vec{a}(X), \vec{b}(X), \vec{c}(X))`，其中 `n = \ell_{out} + N`，`m = \ell_{in} + \ell_{out} + N + 1` 且 `\ell = \ell_{in} + \ell_{out}`，使得：

```
R_C((\vec{x}, \vec{y}), \vec{w}) = R_{QAP}(\vec{x}, (\vec{y}, \vec{w}))
```

#### 证明

在证明中，我们展示如何从电路 `C` 构造一个 QAP。通过其构造可以看出，QAP 关系表达的语言与 `R_C` 相同，即它接受的 `(\vec{x}, \vec{y}) \in \mathbb{F}^{\ell_{in}} \times \mathbb{F}^{\ell_{out}}` 的集合与电路 `C` 相同。

思路是通过验证是否存在一个对所有输入、输出和乘法门的赋值且该赋值与电路一致，来检查电路的可满足性。更准确地说，由于输入和输出是公开的，我们需要证明存在内部门的有效赋值。设 `\vec{w}' \in \mathbb{F}^N` 为包含此类赋值的向量，并定义 `\vec{z} := (1, \vec{x}, \vec{y}, \vec{w}') \in \mathbb{F}^m` 为包含输入、输出和内部门的值（以及常数 1）的向量。

令 `m = \ell_{in} + \ell_{out} + N + 1` 和 `\ell = \ell_{in} + \ell_{out} + 1`，如定理所述，并将集合 `[m]` 划分为三个集合：`I_{in} = \{2, ..., \ell_{in} + 1\}`，`I_{out} = \{\ell_{in} + 2, ..., \ell\}` 和 `I_{mid} = \{\ell + 1, ..., m\}`。

直观上，我们用 `I_{mid}` 中的整数标记电路 `C` 的所有 `N` 个乘法门，用 `I_{in}`（分别 `I_{out}`）中的整数标记 `\ell_{in}`（分别 `\ell_{out}`）个输入（分别输出）门。

然后，所有乘法门的一致性可以通过以下方式检查：

```
\forall j \in I_{mid}: \langle \vec{a}^j, \vec{z} \rangle \cdot \langle \vec{b}^j, \vec{z} \rangle = \langle \vec{c}^j, \vec{z} \rangle
```

其中，对于每个 `j \in I_{mid}`，`\vec{a}^j, \vec{b}^j` 是表达第 `j` 个乘法门左、右输入线的线性子电路的适当向量。

接下来，我们为公开输出添加约束：

```
\forall j \in I_{out}: z_j = \langle \vec{a}^j, \vec{z} \rangle
```

其中每个 `\vec{a}^j` 的支撑集仅在 `I_{mid}` 上。由于 `z_1 = 1`，这些约束检查 `z_j = \langle \vec{a}^j, \vec{z} \rangle`，确保每个公开输出 `z[j]` 在乘法门的输出上通过由向量 `\vec{a}^j` 表达的线性子电路计算后正确获得。我们注意到，对于每个输出门都是乘法门的电路，这组约束可以省略。

此时，我们可以将上述所有约束汇总为三个矩阵 `\mathbf{A, B, C} \in \mathbb{F}^{n \times m}` 的形式，定义如下：

```
\mathbf{A} = \begin{bmatrix} \mathbf{I}_{\ell} \\ \mathbf{A}_{mid} \end{bmatrix}, \quad
\mathbf{B} = \begin{bmatrix} \mathbf{0} \\ \mathbf{B}_{mid} \end{bmatrix}, \quad
\mathbf{C} = \begin{bmatrix} \mathbf{0} \\ \mathbf{C}_{mid} \end{bmatrix}
```

其中 `\vec{e}^j \in \mathbb{F}^{1 \times m}` 是 `m \times m` 单位矩阵的第 `j` 行。

可以看出，`C(\vec{x}, \vec{w}) = \vec{y}` 当且仅当

```
(\mathbf{A}\vec{z}) \circ (\mathbf{B}\vec{z}) = \mathbf{C}\vec{z}
```

其中向量 `\vec{z}` 定义如上，即 `(1, \vec{x}, \vec{w})`。上述方程在文献中被称为一阶约束系统 (R1CS)。

为了完成定理的证明，我们展示如何通过插值将上述二次方程组转换为多项式形式。

- 选取 `\mathbb{F}` 中的 `n` 个不同点构建子集 `\mathbb{H} := \{h_1, ..., h_n\} \subset \mathbb{F}`；
- 计算 `v(X) = \prod_{h \in \mathbb{H}} (X - h)`，这是一个在 `\mathbb{H}` 上消失的 `n` 次多项式，即 `\forall h \in \mathbb{H}: v(h) = 0`；
- 对任意 `j \in [m]`，构造 `a_j(X)`（分别 `b_j(X), c_j(X)`）为唯一的一个次数为 `(n - 1)` 的多项式，使得 `\forall i \in [n], a_j(h_i) = A_{i,j}`（分别 `b_j(h_i) = B_{i,j}, c_j(h_i) = C_{i,j}`）。

我们留作练习验证，通过这种多项式 `\vec{a}(X), \vec{b}(X), \vec{c}(X)` 和 `v(X)` 的构造，我们有

```
(\mathbf{A}\vec{z}) \circ (\mathbf{B}\vec{z}) = \mathbf{C}\vec{z}
```

当且仅当

```
\sum_{j=1}^m z_j a_j(X) \cdot \sum_{j=1}^m z_j b_j(X) - \sum_{j=1}^m z_j c_j(X) = h(X) v(X)
```

---

## 11.6.3. 面向 QAP 的代数 NILP

设 `R_{QAP} := (\mathbb{F}, n, m, \ell, v(X), \vec{a}(X), \vec{b}(X), \vec{c}(X))` 为定义 11.8 中的 QAP 关系。下文我们描述一个在 `\mathbb{F}` 上面向 `R_{QAP}` 的 `(n, 2)`-代数 NILP。

该 NILP 抽象了 Parno 等人 (2013) 的 Pinocchio SNARG 构造。这并非目前最高效的 NILP（及 SNARG）；例如，著名的 Groth16 方案 (Groth 2016) 经过更多优化，证明大小近乎最优。尽管如此，Parno 等人 (2013) 背后的技术引出的 NILP 更具直觉性，因此我们出于展示原因更倾向于此构造。

我们首先给出代数 NILP 的完整描述，然后给出直观解释。

- `\mathsf{NILP}(R_{QAP}) \to \vec{q}`：该算法采样 `\vec{s} \leftarrow \mathbb{F}^7` 并返回查询向量 `\vec{q} = \mathsf{enc}(\vec{s})`。

```
\vec{q}(X, Y) = \begin{bmatrix}
1 \\
X \\
Y \\
X^2 \\
XY \\
Y^2 \\
v(X) \\
X v(X)
\end{bmatrix}
```

其次，采样 `\vec{r} \leftarrow \mathbb{F}^{7m + n - 4\ell + 1}` 并返回查询向量 `\vec{q} = \mathsf{enc}(\vec{r})`。

```
\vec{q}(X, Y) = \begin{bmatrix}
\vec{a}(X) \\
\vec{b}(X) \\
\vec{c}(X) \\
\vec{a}(X) \circ \vec{b}(X) \\
\vec{a}(X) Y \\
\vec{b}(X) Y \\
\vec{c}(X) Y \\
v(X) \vec{1}
\end{bmatrix}
```

令 `\vec{h}` 为系数向量 `\vec{h} = (h_0, ..., h_{n-1})`，证明矩阵 `\mathbf{\Pi} \in \mathbb{F}^{8 \times (7m + n - 4\ell + 1)}` 构造如下：

```
\mathbf{\Pi} = \begin{bmatrix}
\mathbf{I}_m & \mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{0} \\
\mathbf{0} & \mathbf{I}_m & \mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{0} \\
\mathbf{0} & \mathbf{0} & \mathbf{I}_m & \mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{0} \\
\mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{I}_m & \mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{0} \\
\mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{I}_m & \mathbf{0} & \mathbf{0} & \mathbf{0} \\
\mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{I}_m & \mathbf{0} & \mathbf{0} \\
\mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{I}_{n-4\ell+1} & \mathbf{0} \\
\mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{0} & \mathbf{I}_{n-4\ell+1}
\end{bmatrix}
```

