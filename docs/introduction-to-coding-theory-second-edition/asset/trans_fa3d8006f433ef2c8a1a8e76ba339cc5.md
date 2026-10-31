
## 23.3 tms-网

tms-网由 Niederreiter [157] 定义，基于 Sobol [195] 的早期工作，在数值积分的拟蒙特卡洛方法背景下提出。从一开始就注意到与组合结构的密切联系，并由 Lawrence [131]、Mullen 和 Schmid [155, 180] 等人进一步探索。我们的描述受 Rosenbloom 和 Tsfasman [177] 的启发。最好从技术描述开始，因为与正交表的密切联系将变得显而易见。

设 Ω = Ω^(T,s) 为 T s 个元素的集合，划分为 s 个块 B_i，i = 1,2,...,s，其中 B_i = {ω_1^(i),...,ω_T^(i)}。每个块都带有全序：

ω_1^(i) < ω_2^(i) < ... < ω_T^(i).

这使得 Ω 具有偏序集的结构，是 s 个全序集（链）的并集，每个包含 T 个点。我们将 Ω 视为 T s 维向量空间 𝔽_q^(T,s) 的基。Ω 中的理想是关于前驱封闭的元素集合。反理想是关于后继封闭的子集，等价于理想的补集。

将元素 x = (x_j^(i)) ∈ 𝔽_q^(T,s)，i = 1,...,s；j = 1,...,T 视为具有 T 行 s 列的矩阵。Rosenbloom-Tsfasman 度量定义如下：如果在每个块中，前导零消失，则剩余单元的数量为权重 ρ(x)。x 与 y 之间的距离则为 ρ(x−y)。子空间 𝒞 ⊆ 𝔽_q^(T,s) 的最小权重（最小距离）是其非零成员权重中的最小值。

线性子空间（码）𝒞 ⊆ 𝔽_q^(T,s) 的强度为 k = k(𝒞)，如果 k 是使得从 𝒞 到任意大小为 k 的理想的投影满射的最大值。我们也称这样的子空间为有序正交表（OOA），它是 q 线性的，具有长度 s、深度 T、维数 m = dim(𝒞) 和强度 k。关于对称双线性形式定义对偶

⟨x,y⟩ = Σ_{i=1}^s x_1^(i) y_T^(i) + x_2^(i) y_{T-1}^(i) + ... + x_T^(i) y_1^(i).

这些概念由线性码对偶原理的以下推广所证实。

### 23.1 定理. 设 𝒞 ⊆ 𝔽_q^(T,s) 为线性子空间（码）。则

ρ(𝒞^⊥) = k(𝒞) + 1.

将 𝔽_q^(T,s) 连同这些对偶、强度和距离的概念称为 NRT 空间，是 Niederreiter-Rosenbloom-Tsfasman 空间的简称。注意，在 T = 1 的情况下，我们得到编码理论中熟悉的 Hamming 空间。

为了理解在数值积分拟蒙特卡洛方法中的应用，将 x ∈ 𝔽_q^{(T,s)} 解释为 s 维单位立方体中的点，通过将固定 i 的 x_j^{(i)} 读作介于 0 和 1 之间的实数的 q 进制展开的前 T 位数字。例如，点 1 1 1 0 在 𝔽_2^{(3,4)} 中映射到点 (3/8, 1/4, 1/4, 5/8) ∈ [0,1)^4。这也促使了块内部的分层排序。

目标是在 s 维欧几里得空间的单位立方体 [0,1)^s 中构造点集，在某种意义上几乎均匀分布。粗略地说，蒙特卡洛方法的思想是随机选择这组点，而拟蒙特卡洛则试图通过确定性选择达到甚至超过随机选择的性能。

NRT 空间中强度为 k 的码对应于 s 维单位立方体中的点集，几乎均匀分布：我们控制 q 进制展开中的前 k 位数字。这就是为什么 tms-网是该理论中最重要的对象。按定义，线性 (t,m,s)_q-网等价于强度为 k 的 m 维码 𝒞 ⊆ 𝔽_q^{(k,s)}，其中 t = m − k。

由于 NRT 空间是 Hamming 空间的推广，且深度为 1 的 NRT 空间与 Hamming 空间相同，因此将编码理论的方法推广是一个自然的策略。这是在 [177] 以及其他各种论文中采用的观点。参见 [27] 中 Gilbert-Varshamov 界和 (u, u+v) 构造的推广以及有用的参考文献。中心参数是强度。这就是为什么 tms-网应被视为线性正交表的推广。有时采用对偶观点并利用 NRT 空间中的距离是有益的。例如，这发生在 (u, u+v) 构造的证明中。

一个自然的问题是网可嵌入性：给定强度为 k、长度为 s 的 m 维线性正交表（若 s > m，则为 [s, s−m, k+1]_q 码的对偶），是否可能构造一个在深度为 k 的 NRT 空间中强度为 k 的 m 维 OOA（等价地，一个 tms-网），其投影到给定的 OA？Gilbert-Varshamov 类型的结果仅基于参数的数值就对该问题给出了肯定的答案。相反，获得显式构造是可取的。BCH 码的一些显式嵌入见于 [21, 79]。

就界而言，Martin 和 Stinson [146] 将正交表的 Rao 界推广到 tms-网。Martin [145] 最终也成功地推广了线性规划界。线性码的代数几何构造可以推广到 tms-网是一个重要的见解；参见 Niederreiter 和 Xing [158, 159]。

## 一个网嵌入

我们给出二元 BCH 码的网嵌入的一个例子。对于任意自然数 $r$，设 $q = 2^r$ 并从长度为 $s = q + 1$ 的二元 BCH 码开始，其中 $A = \{0,1\}$ 为指数的定义集。这里我们使用第 13 章中发展的理论。由于 $A$ 的 Galois 闭包包含区间 $\{-2, -1, 0, 1, 2\}$，相应的 BCH 码具有参数 $[2^r + 1, 2^r - 2r, 6]_2$，由 BCH 界给出。换句话说，向量集合 $(w,1) \in \mathbb{F}_2^{2r+1}$，其中 $w$ 在 $F = \mathbb{F}_{q^2}$ 中遍历 $s$ 次单位根，是 5-独立的。这里我们将 $w \in F$ 视为 $\mathbb{F}_2^{2r}$ 的元素。网嵌入的思想是使用 $(w,1)$ 作为块 $B_w$ 的第一个元素，并寻找第二个、……第五个元素，使得在 $\mathbb{F}_2^{(5,s)}$ 中得到强度为 5 的族。我们尚未能够构造此网嵌入。然而，在引入一个额外坐标后，我们确实得到了一个网嵌入。

### 23.2 定义. 设 $W$ 为 $F = \mathbb{F}_{q^2}$ 的阶为 $s = q + 1$ 的子群。选取 $\alpha \in \mathbb{F}_q \setminus \mathbb{F}_2$ 使得 $\alpha^2 + 1$ 不是形如 $w' + 1/w'$ 的数，其中 $w' \in W$。对每个 $w \in W$，定义块 $X(w)$ 如下：

$X_1(w) = (w,1,0),\; X_2(w) = (\alpha w,0,1),\; X_3(w) = (\mathbf{0},1,1),$
$X_4(w) = (\mathbf{0},0,1)$ and $X_5(w) = X_1(w')$

for some $w' \neq w$.

选择 $\alpha$ 的原因将在证明中变得明显。我们必须证明，任何由五个向量 $X_i(w) \in \mathbb{F}_2^{2r+2}$ 组成的族 $F$ 都是线性无关的，前提是 $F$ 由某个第一个块的前 $n_1$ 个向量、某个其他块的前 $n_2$ 个向量等组成，其中 $n_1 + n_2 + \cdots = 5$。将 $n_i$ 排序使得 $n_1 \ge n_2 \ge \cdots$ 并称 $(n_1,n_2,\ldots)$ 为族 $F$ 的类型。可能的类型为

$(1,1,1,1,1),\; (2,1,1,1),\; (2,2,1),\; (3,1,1),\; (3,2),\; (4,1),\; (5)$.

由于我们选择 BCH 码作为起点，类型 $(1,1,1,1,1)$ 是独立的。最后一个坐标表明类型 $(2,1,1,1)$ 也是独立的。此外，根据 $X_5(w)$ 的选择，类型 $(5)$ 归约为类型 $(4,1)$。只需证明类型为 $(2,2,1)$ 到 $(4,1)$ 的族是独立的。

- Type $(2,2,1)$

Assume there is a linear combination of

$(\alpha w_1,0,1),\; (\alpha w_2,0,1),\; (w_1,1,0),\; (w_2,1,0),\; (w_3,1,0)$

with coefficients $\lambda_1,\ldots,\lambda_5$. As type $(2,1,1,1)$ has been considered already, we can assume $\lambda_1 = \lambda_2 = 1$. The middle coordinate shows $\lambda_3 + \lambda_4 + \lambda_5 = 0$. Assume at first $\lambda_5 = 0$. Clearly $\lambda_3 = \lambda_4 = 1$. The first coordinate section yields

the contradiction $w_1 = w_2$. We can therefore assume $\lambda_3 = \lambda_5 = 1$, $\lambda_4 = 0$. The equation is

$(\alpha + 1)w_1 + \alpha w_2 + w_3 = 0.$

Multiplication by $w_1^{-1}$ shows that we can assume $w_1 = 1$. We have $\alpha + 1 = \alpha w_2 + w_3$. Raising to power $q$ yields $\alpha + 1 = \alpha / w_2 + 1 / w_3$, after multiplication $\alpha^2 + 1 = \alpha^2 + 1 + \alpha (w_2 / w_3 + w_3 / w_2)$. Let $x = w_2 / w_3$. Then $1 \neq x \in W$ and $x + 1/x = 0$. This yields the contradiction $x^2 = 1$, hence $x = 1$.

- 类型 $(2,2,1)$

假设存在

$(\alpha w_1,0,1),\; (\alpha w_2,0,1),\; (w_1,1,0),\; (w_2,1,0),\; (w_3,1,0)$

的线性组合，系数为 $\lambda_1,\ldots,\lambda_5$。由于类型 $(2,1,1,1)$ 已被考虑，我们可以假设 $\lambda_1 = \lambda_2 = 1$。中间坐标表明 $\lambda_3 + \lambda_4 + \lambda_5 = 0$。首先假设 $\lambda_5 = 0$。显然 $\lambda_3 = \lambda_4 = 1$。第一坐标部分给出

矛盾 $w_1 = w_2$。因此我们可以假设 $\lambda_3 = \lambda_5 = 1$，$\lambda_4 = 0$。方程为

$(\alpha + 1)w_1 + \alpha w_2 + w_3 = 0.$

乘以 $w_1^{-1}$ 表明我们可以假设 $w_1 = 1$。我们有 $\alpha + 1 = \alpha w_2 + w_3$。求 $q$ 次幂得到 $\alpha + 1 = \alpha / w_2 + 1 / w_3$，乘法后 $\alpha^2 + 1 = \alpha^2 + 1 + \alpha (w_2 / w_3 + w_3 / w_2)$。令 $x = w_2 / w_3$。则 $1 \neq x \in W$ 且 $x + 1/x = 0$。这导致矛盾 $x^2 = 1$，故 $x = 1$。

- Type (3,2)

The first coordinate section shows that there is no nontrivial linear combination of

$(\mathbf{0},1,1)$, $(\alpha w_1,0,1)$, $(\alpha w_2,0,1)$, $(w_1,1,0)$, $(w_2,1,0)$.

- 类型 (3,2)

第一坐标部分表明不存在

$(\mathbf{0},1,1)$, $(\alpha w_1,0,1)$, $(\alpha w_2,0,1)$, $(w_1,1,0)$, $(w_2,1,0)$.

的非平凡线性组合。

- Type (3,1,1)

Consider a linear combination of

$(\mathbf{0},1,1)$, $(\alpha w_1,0,1)$, $(w_1,1,0)$, $(w_2,1,0)$, $(w_3,1,0)$.

Clearly $\lambda_1 = 1$. The last coordinate shows $\lambda_2 = 1$. The first coordinate section shows $\lambda_4 = \lambda_5 = 1$. The middle coordinate yields $\lambda_3 = 1$. We have $(\alpha + 1)w_1 = w_2 + w_3$. As before, we can assume $w_1 = 1$. Raising to power $q + 1$, we obtain $(\alpha + 1)^2 = w_2 / w_3 + w_3 / w_2$. Let $x = w_2 / w_3$. By choice of $\alpha$ a contradiction is reached.

- 类型 (3,1,1)

考虑

$(\mathbf{0},1,1)$, $(\alpha w_1,0,1)$, $(w_1,1,0)$, $(w_2,1,0)$, $(w_3,1,0)$.

的线性组合。

显然 $\lambda_1 = 1$。最后一个坐标表明 $\lambda_2 = 1$。第一坐标部分表明 $\lambda_4 = \lambda_5 = 1$。中间坐标给出 $\lambda_3 = 1$。我们有 $(\alpha + 1)w_1 = w_2 + w_3$。如前所述，我们可以假设 $w_1 = 1$。求 $q + 1$ 次幂，得到 $(\alpha + 1)^2 = w_2 / w_3 + w_3 / w_2$。令 $x = w_2 / w_3$。根据 $\alpha$ 的选择得到矛盾。

Type (4,1) is easy to check.

类型 (4,1) 易于检验。

In order to complete the proof, it remains to show that $\alpha$ can be chosen as required in Definition 23.2. This is left to the reader; see Exercise 23.3.1.

为了完成证明，还需证明 $\alpha$ 可以按定义 23.2 所要求的方式选取。这留给读者；参见练习 23.3.1。

We have shown that there is a $(2r + 2)$-dimensional subspace of $\mathbb{F}_2^{(s,s)}$ of strength 5. In the tms terminology this is a linear $(2r - 3, 2r + 2, 2^r + 1)_2$ net. It gives us a set of $2^{2r+2}$ points in the unit cube $[0,1)^s$, which in some technical sense are uniformly distributed. The quality of the distribution is measured by the strength $m - t$, which in our case is 5.

我们已证明 $\mathbb{F}_2^{(s,s)}$ 中存在一个 $(2r + 2)$ 维子空间，强度为 5。在 tms 术语中，这是一个线性 $(2r - 3, 2r + 2, 2^r + 1)_2$ 网。它给出了单位立方体 $[0,1)^s$ 中 $2^{2r+2}$ 个点的集合，在某种技术意义上是均匀分布的。分布的质量由强度 $m - t$ 衡量，在我们的情况下为 5。

## 练习 23.3

**23.3.1.** *Prove that $\alpha$ can be chosen as required in Definition 23.2.*

**23.3.1.** *证明 $\alpha$ 可以按定义 23.2 所要求的方式选取。*
