
因此可以看出，高维空间中的内积与低维空间中内积的 `d=2` 次幂相同。这是问题的关键；每当需要高维度的内积时，就无需利用特征映射。该结果只需在低维中将内积提高到 `d` 次幂即可得到，从而确定高维内积。
更一般地，核方法将希尔伯特空间 `H[L]`=`R^(n)` 中两个向量的点积映射到另一个希尔伯特空间 `H[H]`=`R[m]` 中两个相关向量的点积。当 `n`=`m` 时，出现线性核。在这种情况下，`K(v,w)`=`<v, w>`，且对于 `R` 中的 `a`，`<a v+u, w>`=`a` `<v, w>`+`<u, w>`。类似地，`<v, a w+u>`=`a` `<v, w>`+`<v, u>`。由于它是线性的，核为 `K(v,w)`=`v’w` 且特征映射 `Φ(v)`=`v`。该情况下的 Gram 矩阵是一个 `n` by `n` 矩阵，其条目由 `R^(n)` 中的向量的内积组成，具体而言对于 `R^(n)` 中的 {`v[1]`, …, `v[n]`}；则 `G` 中条目 `G[ij]` 等于 `<v[i], v[j]>`。

### 示例 1.11
再次考虑载体集合 `H[L]`=`R²`，其中向量 `v`=`(v[1] v[2])′`=`(2 3)′`，且 `w`=`(w[1] w[2])′`=`(4 –1)`。假设 `H[L]`=`H[H]` 且特征映射 `Φ` 为恒等映射；则 `v` 和 `w` 的 Gram 矩阵一般给出，并且再次使用 `v` 和 `w` 的实际元组值，`G`=
```
\begin{array}{l}
{\left| \left\langle v,v \right\rangle\quad\left\langle v,w \right\rangle \right| = \left| 13 5 \right|}
\left. \left| \left\langle w,v \right\rangle\left\langle w,w \right\rangle \right|\mspace{21mu} \middle| 5 17 \middle| .# \right.
\end{array}
```
![Equation](Images/F000199si21.png)
当 `m` 大于 `n` 时，`m`=`n^(d)`；则 `R^(n)` 中的点积提高到正整数幂 `d` 后，将等于 `R^(m)` 中的点积。这称为多项式核方法或核技巧。这里，定义域空间 `R^(n)` 中的向量 `v` 和 `w` 为 `v`=`(v[1] v[2]…v[n])′` 和 `w`=`(w[1] w[2]…w[n])′`。映射函数 `Φ`: `R^(n)` → `R^(m)` 取向量例如定义域中的 `v` 的所有 `n` 个元组，并形成所有可能的 `d` 次齐次单项式。在形成这些单项式时，定义域向量中的元组需以不同顺序重复。这些不同的单项式随后成为 `R^(m)` 中相关向量的元组；也就是说，由 `v` 的元组形成的单项式成为 `Φ(v)` 中的元组。就元组而言，这是一种非线性映射。如果执行此过程，则 `m`=`n^(d)`。此外，核 `k` 满足 `k(v,w)`=`<Φ(v), Φ(w)>`=`(<v, w>)^(d)`。通过在高维空间中取内积可以看出这一结果：
```
\left\langle {\Phi\left( v \right),\Phi\left( w \right)} \right\rangle = {\sum\limits_{\mathit{j}1}}\cdots{\sum\limits_{\mathit{jd}}{v_{\mathit{j}1}\cdots v_{\mathit{jd}} \cdot w_{\mathit{j}1}\cdots w_{\text{jd},}}} = {\sum\limits_{\mathit{j}1}{v_{\mathit{j1}} \cdot w_{\mathit{j1}}\cdots}}{\sum\limits_{\mathit{jd}}{v_{\mathit{jd}} \cdot w_{\text{jd},}}} = \left\lbrack {\sum\limits_{\mathit{j}}{v_{\mathit{j}} \cdot w_{\mathit{j}}}} \right\rbrack^{d} = \left\langle {v,w} \right\rangle^{d}
```
![Equation](Images/F000199si22.png).

### 示例 1.12
在此示例中，设 `n=2` 且 `d=3`。对于 `R²` 中的 `v`=`(v[1] v[2])′`，`Φ(v)` = (`v[1]³ v[2]³ v[1]² v[2] v[1] v[2]² v[2] v[1]² v[2] v[1]² v[1] v[2] v[1] v[2] v[1] v[2]`) , ![Equation](Images/F000199si23.png) 是一个 `R⁸` 中的向量。若 `w`=`(w[1] w[2])'`，则三次齐次多项式可以填满 `Φ(w)` 的八个元组，就像它对 `Φ(v)` 所做的那样。假设已完成，则形成：
```
\begin{matrix}
{\left\langle {\Phi\left( v \right),\Phi\left( w \right)} \right\rangle = {\sum\limits_{\mathit{j}1}}\cdots{\sum\limits_{\mathit{jd}}{v_{\mathit{j}1}\cdots v_{\mathit{jd}} \cdot w_{\mathit{j}1}\cdots w_{\mathit{jd}}}} = {\sum\limits_{\mathit{j}1}{\sum\limits_{\mathit{j}2}{\sum\limits_{\mathit{j}3}{v_{\mathit{j}1}v_{\mathit{j}2}v_{\mathit{j}3}w_{\mathit{j}1}w_{\mathit{j}2}w_{\mathit{j}3}}}}}
{= {\sum\limits_{\mathit{j}1}{v_{\mathit{j}1}w_{\mathit{j}1}}}{\sum\limits_{\mathit{j}2}{v_{\mathit{j}2}w_{\mathit{j}2}}}{\sum\limits_{\mathit{j}3}{v_{\mathit{j}3}w_{\mathit{j}3}}} = {\lbrack{\sum_{j = 1}^{2}{v_{j} \cdot w_{j}}}\\rbrack}^{3} = \left\langle {v,w} \right\rangle^{3} = \left\lbrack {v_{1}w_{1} + v_{2}w_{2}} \right\rbrack^{3}}
{= v_{1}^{3}w_{1}^{3} + v_{2}^{3}w_{2}^{3} + 3v_{1}^{2}v_{2}w_{1}^{2}w_{2} + 3v_{1}v_{2}^{2}w_{1}w_{2}^{2}.#}
\end{matrix}
```
![Equation](Images/F000199si24.png)
使用特征映射 `Φ` 的好处是不使用它。维度为 `n` 的数据可以在维度为 `m`=`n^(d)` 的希尔伯特空间中使用，而无需实际将数据转换到该维度。每当仅需要高维数据的内积时，这都是成立的。这里唯一需要的计算只是求 `<v, w>^(d)`。特征映射和核方法的应用将在后面的章节中给出，同时还将介绍几种特征映射和各种核。

### 1.1.11 R-模
再次，为了利用 MSA 中的深入高级定义，将描述一个向量空间子结构。它称为交换环 `R` 上的单位 R-模，具有幺元。类型与 MSA 向量空间和域描述中的完全相同。因此类型仍为 `SCALAR` 和 `VECTOR`。签名集合也是如此，除了偏操作名 `INV` 在交换幺环中不存在，在环中也不存在。因此，在如 [图 1.1](#Ch001_1-19_B9780443136979000199.xhtml#f0010) 的多值图 中，结果图将被修改。在这种情况下，`INV` 的虚线箭头将被完全移除。
R-模的实际签名集合与向量空间结构相同。因此，R-模的元数序列仍为 `(1, 1, 2(1, 1))`。签名集合如下：
```
\begin{array}{l}
\left. {Binary}{operation}{\left\{ {V - {ADD}} \right\}},V - {ADD}{maps}{VECTOR} \times {VECTOR}\rightarrow{VECTOR} \right.
\left. \quad\quad\quad\quad\quad\quad\quad\left\{ {S - {MULT}} \right\},S - {MULT}{maps}{SCALAR} \times {VECTOR}\rightarrow{VECTOR} \right.
\left. {Unary}{operation}{\left\{ {V - {MINUS}} \right\}},V - {MINUS}{maps}{VECTOR}\rightarrow{VECTOR} \right.
{{Zero} - {ary}{operation}{\left\{ {V - {ZERO}} \right\}},V - {ZERO} = 0.}
\end{array}
```
![Equation](Images/F000199si25.png)
回顾向量空间结构的方程恒等式：`(1)–(8)`，它们对单位 R-模都成立。
请记住，约束 `(1)–(4)` 意味着所描述的结构，即单位 R-模，在向量加法下也是一个阿贝尔群。此外，有时在模的定义中会省略环的交换性。如果是这种情况，则约束 `(5)−(8)` 会相应调整。例如，约束 `(5)` 可能仅写为：`1 · v=v`。`1` 是单侧恒等元。此外，在这种情况下，在定义 `S-MULT` 时必须小心。它只能定义，同时考虑运算顺序。在 MSA 多值图中，使用斜杠标记多值箭头的尾部。在这种类型的图中，斜杠 `/` 用于第一个操作数，双斜杠 `//` 用于 `S-MULT` 的第二个参数。这种符号在描述左模或右模时很重要。当环为域时，所有这些都不重要。

### 示例 1.13
