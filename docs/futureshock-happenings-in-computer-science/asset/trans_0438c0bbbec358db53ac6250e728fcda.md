
m ∈ ℕ, 且 σ·τ ∈ T（τ 可以为空）。这里，σ 结束于蓝色点，对应于记号 36 中的 v_n。蓝色点之前的绿色点对应于 ∧_{i<n, s_i+1=∨} v_i 中的合取项。蓝色点之前的红色点对应于 ∧_{i<n, s_i+1=∨} v̄_i 中的合取项。蓝色点之后的红色点对应于 ∧_{i≤m} v̄_i 中的合取项。

## Example 38.

回顾示例 10 中的约定和记号。按记号 36 定义的所有 σ ∈ T 的 σ||_T 的简化值可以如 图 7.13 所示描绘。

![](img/35d43ba1274e18d0f2f189e6392aa2e3_152_0.png)

## Figure 7.13

## Lemma 39.

设有一个布尔 ℳ-嵌入 𝔈、一个 |T| > 1 的 𝔈-分级树 T 以及 T 的一个非空成员 σ。设 i = ρ_T^{-1}(σ)。设 ν 使得 σ 以 (∨,ν) 或 (∧,ν) 结尾。对所有 ℳ ∈ 𝔈(ρ_T(i+1)) \ 𝔈(ρ_T(i-1))，ℳ ∈ 𝔈(ρ_T(i)) 当且仅当 ℳ ∈ 𝔈(ν)。

证明。若 𝔈(ρ_T(i+1)) = 𝔈(ρ_T(i-1))，则结果是显然的，故假设并非如此。证明按 𝔈-分级树的规模进行归纳。结果对规模为 2 的 𝔈-分级树是显然的。设 k ≥ 2，并假设结果对规模介于 2 和 k 之间的所有 𝔈-分级树成立。设 T 是一个规模为 k+1 的 𝔈-分级树。设 σ ∈ T 且 𝔈-分级树 T' 满足 T = T' ∪ {σ}。设 σ' ∈ T' 使得 σ 的形式为 σ'·((∧,ν)) 或 σ'·((∨,ν))。我们依次考虑两种情况。设 i = ρ_{T'}^{-1}(σ')。注意 σ' 非空，故可写成 σ' = ((𝔛_0, v_0),..., (𝔛_n, v_n))，n ∈ ℕ，且 i < |T'|。

### Case 1 σ = σ'·((∧,ν)).

- 假设 𝔛_0,...,𝔛_n 均为 ∧，故 i = 1。显然，对所有 ℳ ∈ 𝔈(σ')，ℳ ∈ 𝔈(\widehat{σ'}) 当且仅当 ℳ ∈ 𝔈(ν)。
- 否则，i > 1 且存在非零的 m ≤ n 使得 ((𝔛_m, v_m),..., (𝔛_n, v_n)) 的形式为 ((∨, v_m))·((∧, v_{m+1}),..., (∧, v_n))。设 τ 表示 ((𝔛_0, v_0),..., (𝔛_{m-1}, v_{m-1}))。由命题 32，ρ_{T'}^{-1}(τ) = i - 1。注意 𝔈(v_m ∧ v_{m+1} ∧ ⋯ ∧ v_n ∧ ν) = 𝔈(v_m ∧ v_{m+1} ∧ ⋯ ∧ v_n) ∩ 𝔈(ν)。

设 ℳ ∈ 𝔈(ρ_T'(i+1)) \ 𝔈(ρ_T'(i-1)) 给定。

- 若 ℳ ∈ 𝔈(ν)，则由于 ℳ ∈ 𝔈(\widehat{σ'})，ℳ ∈ 𝔈(\widehat{σ})。
- 若 ℳ ∉ 𝔈(ν)，则由于 ℳ ∉ 𝔈(\widehat{σ'})，ℳ ∉ 𝔈(\widehat{σ})。

### Case 2 σ = σ'·((∨,v)). 存在 m ≤ n 使得 ((𝔛_m, v_m),…,(𝔛_n, v_n)) 的形式为 ((∧, v_m))·((∨, v_{m+1}),…,(∨, v_n))。设 τ 表示 ((𝔛_0, v_0),…,(𝔛_{m-1}, v_{m-1}))。

由推论 34，ρ_T'^{-1}(τ) = i + 1。注意

𝔈(v_m ∨ v_{m+1} ∨ ⋯ ∨ v_n ∨ v) = 𝔈(v_m ∨ v_{m+1} ∨ ⋯ ∨ v_n) ∪ 𝔈(v)。

设 ℳ ∈ 𝔈(ρ_T'(i+1)) \ 𝔈(ρ_T'(i-1)) 给定。

- 若 ℳ ∈ 𝔈(v)，则由于 ℳ ∈ 𝔈(\widehat{σ'})，ℳ ∈ 𝔈(\widehat{σ})。
- 若 ℳ ∉ 𝔈(v)，则由于 ℳ ∉ 𝔈(\widehat{σ'})，ℳ ∉ 𝔈(\widehat{σ})。

由以上所有内容以及结果对 T' 成立的事实，我们借助命题 32 和推论 34 即可容易地推断出结果对 T 成立。

## Proposition 40. 对所有布尔 ℳ-嵌入 𝔈、𝔈-分级树 T 和 σ ∈ T，

𝔈(σ||_T) = 𝔈(\widehat{σ}) \ 𝔈(ρ_T(ρ_T^{-1}(σ) - 1))。

证明。证明按 𝔈-分级树的规模进行归纳。结果对规模为 2 的 𝔈-分级树是显然的。设 k ≥ 2，并假设结果对规模介于 2 和 k 之间的所有 𝔈-分级树成立。设 T 是一个规模为 k + 1 的 𝔈-分级树。设 σ ∈ T 且 𝔈-分级树 T' 满足 T = T' ∪ {σ}。设 σ' ∈ T' 使得 σ 的形式为 σ'·((∧,v)) 或 σ'·((∨,v))。我们依次考虑两种情况。设 i = ρ_{T'}^{-1}(σ')。

### Case 1 σ = σ'·((∧,v)).

- 将 σ' 写成 ((𝔛_0, v_0),…,(𝔛_n, v_n))，n ∈ ℕ，假设 𝔛_0,…,𝔛_n 均为 ∧，故 i = 1。显然，
- 𝔈(σ||_{T'} ∧ v) = 𝔈(\widehat{σ})；
- 𝔈(σ||_{T'} ∧ \bar{v}) = 𝔈(σ') \ 𝔈(\widehat{σ})。

另外，注意

- $\sigma\parallel_T$ 定义为 $\tau\parallel_{T'} \wedge \mathfrak{v}$；
- $\tau\parallel_T$ 定义为 $\tau\parallel_{T'} \wedge \bar{\mathfrak{v}}$。

由以上所有内容以及结果对 $T'$ 成立的事实，我们借助命题 32 和推论 34 即可容易地推断出结果对 $T$ 成立。

## 7.5 NORMAL FORMS

设有一个分级树 $T$ 和 $T$ 的一个成员 $\sigma$。按其定义方式，$\hat{\sigma}$ 可以有 $\vee$s 位于 $\wedge$s 内，$\wedge$s 位于 $\vee$s 内，$\vee$s 位于 $\wedge$s 内……尤其是当 $\sigma$ 更长且有更多“方向变化”时。这与析取或合取范式的扁平结构形成对比，后者将嵌入深度限制为 2（合取内的析取，或合取内的合取）。记号 41 捕捉了将 $\hat{\sigma}$ 转换为析取和合取范式的自然方式。推论 44 刻画了可以表示为形式为 $\hat{\sigma}$ 的公式的析取和合取范式。

## Notation 41.

设有一个分级树 $T$。设 $\mathrm{DNF}(\sigma)$ 和 $\mathrm{CNF}(\sigma)$ 均表示 $\wedge\varnothing$。将 $T$ 的每个非空成员 $\sigma$ 与两个集合族关联如下。

- 将 $\sigma$ 写成
$((\wedge,\mathfrak{v}_0^0),\dots,(\wedge,\mathfrak{v}_0^{p_0}), (\vee,\mathfrak{v}_1),\dots,(\vee,\mathfrak{v}_{n_0}),(\wedge,\mathfrak{v}_1^0),\dots,(\wedge,\mathfrak{v}_1^{p_1}),$
$(\vee,\mathfrak{v}_{n_0+1}),\dots\vee,\mathfrak{v}_{n_0+n_1}),\dots,$
$\dots,(\wedge,\mathfrak{v}_k^0),\dots,(\wedge,\mathfrak{v}_k^{p_k}),(\vee,\mathfrak{v}_{\Sigma_{j<k}n_j+1}),\dots,(\vee,\mathfrak{v}_{\Sigma_{j\le k}n_j}))$
其中 $k,p_0,\dots,p_k,n_k\in\mathbb{N}$ 且 $n_0,\dots,n_{k-1}\in\mathbb{N}\setminus\{0\}$。给定 $i\le\Sigma_{j<k}n_j$，设 $C_i=\{\mathfrak{v}_0^0\}$ 并执行以下操作。
- 对所有 $j\le k$，若 $n_0+\cdots+n_{j-1}\le i$ 则将 $\mathfrak{v}_j^0,\dots,\mathfrak{v}_j^{p_j-1}$ 添加到 $C_i$。
- 若存在唯一的非零 $j<k$ 使得 $n_0+\cdots+n_{j-1}=i$ 则将 $\mathfrak{v}_j^{p_j}$ 添加到 $C_i$。
- 若 $j\le k$ 是最大的满足 $n_0+\cdots+n_j\le i$ 的数，且要么 $j<k$ 要么 $j=k$ 且 $n_k\ne0$，则将 $\mathfrak{v}_{n_0},\dots,\mathfrak{v}_{n_j}$ 添加到 $C_i$。
- 将 $\sigma$ 写成
$((\wedge,\mathfrak{v}_1),\dots,(\wedge,\mathfrak{v}_{p_0}),(\vee,\mathfrak{v}_0^0),\dots,(\vee,\mathfrak{v}_0^{n_0}),$
$(\wedge,\mathfrak{v}_{p_0+1}),\dots,(\wedge,\mathfrak{v}_{p_0+p_1}),(\vee,\mathfrak{v}_1^0),\dots,(\vee,\mathfrak{v}_1^{n_1}),\dots,$
$\dots,(\wedge,\mathfrak{v}_{\Sigma_{j<k}p_j+1}),\dots,(\wedge,\mathfrak{v}_{\Sigma_{j\le k}p_j}),(\vee,\mathfrak{v}_k^1),\dots,(\vee,\mathfrak{v}_k^{n_k}))$
其中 $k,n_k\in\mathbb{N}$ 且 $p_0,\dots,p_k,n_0,\dots,n_{k-1}\in\mathbb{N}\setminus\{0\}$。给定 $0<i\le\Sigma_{j<k}p_j$，设 $D_i=\{\mathfrak{v}_1\}$ 并执行以下操作。
- 对所有 $j\le k$，若 $p_0+\cdots+p_j\le i$ 则将 $\mathfrak{v}_j^0,\dots,\mathfrak{v}_j^{n_j-1}$ 添加到 $D_i$。

- 若存在唯一的 $j \le k$ 使得 $p_0 + \cdots + p_j = i$ 则将 $\mathfrak{v}_j^{n_j}$ 添加到 $D_i$。
- 若 $j \le k$ 是最大的满足 $p_0 + \cdots + p_j \le i$ 的数，则将 $\mathfrak{v}_{p_0}, \dots, \mathfrak{v}_{p_j}$ 添加到 $D_i$。

我们令 DNF$(\sigma)$ 表示 $\bigvee_{i\le\Sigma_{j\le k} n_j} \bigwedge C_i$，并令 CNF$(\sigma)$ 表示 $\bigvee_{1\le i\le\Sigma_{j\le k} p_j} \bigwedge D_i$。

## Proposition 42. 对所有分级树 $T$ 和 $T$ 的成员 $\sigma$，$\hat\sigma$ 等于 DNF$(\sigma)$ 和 CNF$(\sigma)$。

证明。这可通过对 $T$ 的成员长度进行归纳容易验证，利用布尔代数是分配的这一事实。

## Example 43. 图 7.14 和 7.15 表示分级树的一个非空成员 $\sigma$，并说明命题 42 中定义的 DNF$(\sigma)$ 和 CNF$(\sigma)$。

- 图 7.14 说明了 DNF$(\sigma)$ 的值，即 $\bigvee_{i\le\Sigma_{j<k} n_j} \bigwedge C_i$，如记号 41 中所定义。它是 $k = 3$，$p_0 = 2$，$n_0 = 3$，$p_1 = 0$，$n_1 = 1$，$p_2 = 2$，$n_2 = 2$，$p_3 = 0$，且 $n_3 = 0$ 的特例。因此 $\Sigma_{j<k} n_j = 6$。集合 $C_0$ 到 $C_6$ 以 $C_0$ 位于顶部行的中间，$C_6$ 位于右下角的方式表示，按行读取，每行从左到右。对所有 $i \le 6$，$C_i$ 的成员显示为黑色点。

![](img/35d43ba1274e18d0f2f189e6392aa2e3_155_0.png)

Figure 7.14
