
4. 若 `I` ⊆ `W` ⊆ `Q`，则 `DM`(`I, Q`) ≥ `DM`(`I, W`) 且 `DM`(`I, Q`) ≥ `DM`(`W, Q`)。

## 针对图像模糊集的建议距离度量

本节介绍一种新的 PF 距离度量并提供其可靠性的证据。设 `I` = {`m[z]`, `s[I]`(`m[z]`), `g[I]`(`m[z]`), `e[I]`(`m[z]`) | `m[z]` ∈ `K`} 和 `W` = {`m[z]`, `s[W]`(`m[z]`), `g[W]`(`m[z]`), `e[W]`(`m[z]`) | `m[z]` ∈ `K`} 为两个 `PFS`，则 `PFS` 的建议距离度量如下给出：

### 定义 3.1
设 `K` = {`m[1]`, `m[2]`, …, `m[q]`} 为有限全集。对于 `I`, `W` ∈ `PFS`(`K`)，我们定义距离度量 `D*` 为

(3.1)

$$D^{\*}(I,W) = \\frac{1}{q}\\sum\\limits\_{z = 1}^{q}\\left\\lbrack \\frac{\\begin{array}{l} {2\\left( {\\left| {s\_{I}\\left( m\_{z} \\right) - s\_{W}\\left( m\_{z} \\right)} \\right| + \\left| {e\_{I}\\left( m\_{z} \\right) - e\_{W}\\left( m\_{z} \\right)} \\right| + \\left| {g\_{I}\\left( m\_{z} \\right) - g\_{W}\\left( m\_{z} \\right)} \\right| +} \\right.} \\\\ \\left. \\left| {\\kappa\_{I}\\left( m\_{z} \\right) - \\kappa\_{W}\\left( m\_{z} \\right)} \\right| \\right) \\\\ \\end{array}}{\\begin{array}{l} {4 + \\left| {s\_{I}\\left( m\_{z} \\right) - s\_{W}\\left( m\_{z} \\right)} \\right| + \\left| {e\_{I}\\left( m\_{z} \\right) - e\_{W}\\left( m\_{z} \\right)} \\right| + \\left| {g\_{I}\\left( m\_{z} \\right) - g\_{W}\\left( m\_{z} \\right)} \\right| +} \\\\ \\left| {\\kappa\_{I}\\left( m\_{z} \\right) - \\kappa\_{W}\\left( m\_{z} \\right)} \\right| \\\\ \\end{array}} \\right\\rbrack$$

### 定理 3.2
度量 `D*` 满足以下特征：
1. 0 ≤ `D*`(`I,W`) ≤ 1.
2. `D*`(`I,W`) = `D*`(`W,I`)
3. `D*`(`I,I`) = 0.
4. 若 `I` ⊆ `W` ⊆ `Q`，则 `D*`(`I,Q`) ≥ `D*`(`I,W`) 且 `D*`(`I,Q`) ≥ `D*`(`W,Q`)。

**证明。**
1. 对于 `I`, `W` ∈ `PFS`(`K`)，显然有 0 ≤ |`s[I]`−`s[W]`|, |`g[I]`−`g[W]`|, |`e[I]`−`e[W]`|, |`κ[I]`−`κ[W]`| ≤ 1。
这意味着 0 ≤ |`s[I]`−`s[W]`| + |`g[I]`−`g[W]`| + |`e[I]`−`e[W]`| + |`κ[I]`−`κ[W]`| ≤ 4。这意味着

$$0 \\leq \\left\\lbrack \\frac{2\\left( {\\left| {s\_{I}\\left( m\_{z} \\right) - s\_{W}\\left( m\_{z} \\right)} \\right| + \\left| {e\_{I}\\left( m\_{z} \\right) - e\_{W}\\left( m\_{z} \\right)} \\right| + \\left| {g\_{I}\\left( m\_{z} \\right) - g\_{W}\\left( m\_{z} \\right)} \\right| + \\left| {\\kappa\_{I}\\left( m\_{z} \\right) - \\kappa\_{W}\\left( m\_{z} \\right)} \\right|} \\right)}{4 + \\left| {s\_{I}\\left( m\_{z} \\right) - s\_{W}\\left( m\_{z} \\right)} \\right| + \\left| {e\_{I}\\left( m\_{z} \\right) - e\_{W}\\left( m\_{z} \\right)} \\right| + \\left| {g\_{I}\\left( m\_{z} \\right) - g\_{W}\\left( m\_{z} \\right)} \\right| + \\left| {\\kappa\_{I}\\left( m\_{z} \\right) - \\kappa\_{W}\\left( m\_{z} \\right)} \\right|} \\right\\rbrack \\leq 1.$$

对两边求和可得 0 ≤ `D*`(`I,W`) ≤ 1。
2. 显然。
3. 显然。
4. 考虑 `I`, `W`, `Q` ∈ `PFS`(`K`)，使得 `I` ⊆ `W` ⊆ `Q`，则 `s[I]`(`m[z]`) ≤ `s[W]`(`m[z]`) ≤ `s[Q]`(`m[z]`)，`g[I]`(`m[z]`) ≤ `g[W]`(`m[z]`) ≤ `g[Q]`(`m[z]`)，`e[I]`(`m[z]`) ≥ `e[W]`(`m[z]`) ≥ `e[Q]`(`m[z]`)。

于是，我们有

$$\\begin{array}{l} {\\left| {s\_{I}\\left( m\_{z} \\right) - s\_{W}\\left( m\_{z} \\right)} \\right| \\leq \\left| {s\_{I}\\left( m\_{z} \\right) - s\_{Q}\\left( m\_{z} \\right)} \\right|,\\left| {s\_{W}\\left( m\_{z} \\right) - s\_{Q}\\left( m\_{z} \\right)} \\right| \\leq \\left| {s\_{I}\\left( m\_{z} \\right) - s\_{Q}\\left( m\_{z} \\right)} \\right|,} \\\\ \\left. \\left| {g\_{I}\\left( m\_{z} \\right) - g\_{W}\\left( m\_{z} \\right)} \\right| \\leq g\_{I}\\left( m\_{z} \\right) - g\_{Q}\\left( m\_{z} \\right) \\middle| , \\middle| g\_{W}\\left( m\_{z} \\right) - g\_{Q}\\left( m\_{z} \\right) \\middle| \\leq \\middle| g\_{I}\\left( m\_{z} \\right) - g\_{Q}\\left( m\_{z} \\right) \\mid \\text{,} \\right. \\\\ {\\left| {e\_{I}\\left( m\_{z} \\right) - e\_{W}\\left( m\_{z} \\right)} \\right| \\leq \\left| {e\_{I}\\left( m\_{z} \\right) - e\_{Q}\\left( m\_{z} \\right)} \\right|,\\left| {e\_{W}\\left( m\_{z} \\right) - e\_{Q}\\left( m\_{z} \\right)} \\right| \\leq \\left| {e\_{I}\\left( m\_{z} \\right) - e\_{Q}\\left( m\_{z} \\right)} \\right|.} \\\\ \\left. \\left| {\\kappa\_{I}\\left( m\_{z} \\right) - \\kappa\_{W}\\left( m\_{z} \\right)} \\right| \\leq \\kappa\_{I}\\left( m\_{z} \\right) - \\kappa\_{Q}\\left( m\_{z} \\right) \\middle| , \\middle| \\kappa\_{W}\\left( m\_{z} \\right) - \\kappa\_{Q}\\left( m\_{z} \\right)\\left| {\\leq \\kappa\_{I}\\left( m\_{z} \\right) - \\kappa\_{Q}\\left( m\_{z} \\right)} \\right|.\\ \\right. \\\\ \\end{array}$$

因此，`D*`(`I, Q`) ≥ `D*`(`I, W`) 且 `D*`(`I, Q`) ≥ `D*`(`W, Q`)。

## 性质

接下来，我们如下定义 PFS 的一种新型加权距离度量，若应用权重向量 `l[z]`，`z` = 1, 2, ..., `q` 使得 ${\\sum\_{z = 1}^{q}l\_{z}} = 1:$

### 定义 3.3
对于给定的 `K` = {`m[1]`, `m[2]`,..., `m[q]` } 和 `I`, `W` ∈ `PFS`(`K`)，加权距离度量 (`D*`)^(`l[z]`):`PFS`(`K`)×`PFS`(`K`)→[0,1] 定义如下：

$$\\left( D^{\*} \\right)^{l\_{z}}(I,W) = {\\sum\_{z = 1}^{q}l\_{z}}\\left\\lbrack \\frac{\\begin{array}{l} {2\\left( {\\left| {s\_{I}\\left( m\_{z} \\right) - s\_{W}\\left( m\_{z} \\right)} \\right| + \\left| {e\_{I}\\left( m\_{z} \\right) - e\_{W}\\left( m\_{z} \\right)} \\right| + \\left| {g\_{I}\\left( m\_{z} \\right) - g\_{W}\\left( m\_{z} \\right)} \\right| +} \\right.} \\\\ \\left. \\left| {\\kappa\_{I}\\left( m\_{z} \\right) - \\kappa\_{W}\\left( m\_{z} \\right)} \\right| \\right) \\\\ \\end{array}}{\\begin{array}{l} {4 + \\left| {s\_{I}\\left( m\_{z} \\right) - s\_{W}\\left( m\_{z} \\right)} \\right| + \\left| {e\_{I}\\left( m\_{z} \\right) - e\_{W}\\left( m\_{z} \\right)} \\right| + \\left| {g\_{I}\\left( m\_{z} \\right) - g\_{W}\\left( m\_{z} \\right)} \\right| +} \\\\ \\left| {\\kappa\_{I}\\left( m\_{z} \\right) - \\kappa\_{W}\\left( m\_{z} \\right)} \\right| \\\\ \\end{array}} \\right\\rbrack$$

### 定理 3.4
(`D*`)^(`I[z]`)(`I`, `W`) 是 `K` = {`m[1]`, `m[2]`, ..., `m[q]` } 中 PFS `I` 与 `W` 之间距离的程度，满足以下特征：
1. 0 ≤ (`D*`)^(`I[z]`) (`I,W`) ≤ 1.
2. (`D*`)^(`I[z]`) (`I,W`) = (`D*`)^(`I[z]`) (`W,I`).
3. (`D*`)^(`I[z]`) (`I,I`) = 0.
4. 若 `I` ⊆ `W` ⊆ `Q`，则 (`D*`)^(`I[z]`) (`I,Q`) ≥ (`D*`)^(`I[z]`) (`I,W`) 且 (`D*`)^(`I[z]`) (`I,Q`) ≥ (`D*`)^(`I[z]`) (`W,Q`)。

**证明。**
本定理的证明与定理 (3.2) 的证明类似，当 $l\_{z} = \\frac{1}{q}$ 时，`z =` 1, 2, …, `q`，则 (`D*`)^`z` (`I, W`) 与 `D*`(`I, W`) 相同。

### 定理 3.5
`D*` 的其他一些性质如下：
1. `D*`(`I, W`) = `D*`(`I^C, W^C`).
2. `D*`(`I, W^C`) = `D*`(`I^C,W`).
3. `D*`(`I, I^C`) = `0` ⇔ `s[I]` = `e[I]`.
4. $\\left. \\frac{3}{2}D^{\*}\\left( {I,I^{C}} \\right) = 1\\Leftrightarrow I \\right.$

**证明。**
1. 我们有
