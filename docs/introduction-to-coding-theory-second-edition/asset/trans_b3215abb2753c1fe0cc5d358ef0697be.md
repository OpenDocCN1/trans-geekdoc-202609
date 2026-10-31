
at most s weight numbers of D(I) are in doubt (the others are = 0), and the first s weight numbers of C(I) are known (they are 1, 0, ..., 0). It follows from Proposition 23.9 that the weight distribution of C(I) and of D(I) is uniquely determined, independent of the choice of T.

至多有 s 个 D(I) 的权数存疑（其余为 = 0），而 C(I) 的前 s 个权数已知（它们为 1, 0, ..., 0）。由命题 23.9 可知，C(I) 和 D(I) 的权分布是唯一确定的，与 T 的选择无关。

This shows that the coordinates with entry = 0 of the weight i vectors of C⊥ form a t design. It follows that the complements of those sets (block size n − i) form a t-design as well. In the binary case, these designs are simple by construction. In cases where q > 2 one has to add an additional assumption in order to obtain simple designs. It has to be guaranteed that different codewords having the same support are necessarily scalar multiples of one another.

这表明 C⊥ 的权为 i 的向量中 entry = 0 的坐标构成一个 t 设计。由此可知这些集合的补集（块大小为 n − i）也构成一个 t 设计。在二元情形下，这些设计由构造即为单的。当 q > 2 时，需要增加额外假设才能得到单设计。必须保证具有相同支集的不同码字必然是彼此的标量倍数。

A similar proof works for the weight d words in C. This design is obviously simple.

类似的证明对 C 中的权为 d 的字也适用。该设计显然是单的。

The Assmus-Mattson theorem is from Assmus and Mattson [3], where it was used to construct new 5-designs. More 5-designs were derived in Pless [166] from a class of ternary codes. As an example, the fact that the octads of the large Witt design, the words of weight 8 in the Golay code [24, 12, 8]2, form a 5-design follows also from the Assmus-Mattson theorem.

Assmus-Mattson 定理来自 Assmus 和 Mattson [3]，其中它被用来构造新的 5 设计。Pless [166] 从一类三元码中推导出更多 5 设计。例如，大 Witt 设计的八元组，即 Golay 码 [24, 12, 8]₂ 中权为 8 的字构成 5 设计这一事实，也可由 Assmus-Mattson 定理得出。

As there were no 5-homogeneous permutation groups underlying these 5-designs derived from codes, it became clear that the link from permutation groups to designs was not as tight as one could have suspected.

由于这些由码导出的 5 设计背后没有 5-齐次置换群，很明显置换群与设计之间的联系并没有人们所怀疑的那样紧密。

The next step was taken with the help of computer results. The first simple 6-designs were constructed by Magliveras-Leavitt [144]. The method was to start from groups PGL2(q) in their 3-transitive action on the q + 1 points of the projective line PG(1, q) and construct t designs with t > 3 as unions of orbits. This led to 6 − (33, 8, 36) designs in [144], to 6 − (14, 7, 4) designs in Kreher-Radziiszowski [127] and to some more explicit examples of simple t designs for high t.

下一步借助计算机结果取得进展。第一个单 6 设计由 Magliveras-Leavitt [144] 构造。方法是先从群 PGL2(q) 在其对射影线 PG(1, q) 的 q + 1 个点上的 3-传递作用出发，将 t 设计（t > 3）构造为轨道的并。这导致了 [144] 中的 6-(33, 8, 36) 设计，Kreher-Radziiszowski [127] 中的 6-(14, 7, 4) 设计，以及一些 t 较高的单 t 设计的更明确例子。

The last step was taken by Luc Teirlinck, who, in [206, 207], used a purely combinatorial machinery to construct simple t designs for every t. An important open question is the existence of Steiner systems S(t, k, v) for t > 5. No example is known.

最后一步由 Luc Teirlinck 完成，他在 [206, 207] 中使用纯组合机器构造了对每个 t 的单 t 设计。一个重要开放问题是 Steiner 系统 S(t, k, v) 在 t > 5 时的存在性。尚无已知例子。

## 23.7 Nonlinear codes

## 23.7 非线性码

We encountered many nonlinear codes along the way. The additive codes of Chapter 18 are nonlinear but it could be objected that they are not very serious about their nonlinearity. A similar phenomenon is represented by the so-called Z4 linear binary codes. More precisely, one should speak of images under the Gray map of Z4 linear codes. The only nonlinear element in their construction is the Gray map. This gives rise to several families of very good binary codes which in many respects behave like linear codes. The single most famous of the Z₄ linear binary codes is the Nordstrom-Robinson code 𝒩ℛ. In Section 16.5 we described it precisely from this Z₄-linear point of view.

在途中我们遇到了许多非线性码。第 18 章的加性码是非线性的，但可以反驳说它们对非线性并不太认真。所谓的 Z4 线性二元码代表了类似的现象。更准确地说，应该谈论 Z4 线性码在 Gray 映射下的像。它们构造中唯一的非线性元素是 Gray 映射。这产生了几个在许多方面表现得像线性码的非常好的二元码家族。Z₄ 线性二元码中最著名的是 Nordstrom-Robinson 码 𝒩ℛ。在第 16.5 节中我们已从这一 Z₄-线性观点精确地描述了它。

It was first constructed when Robinson gave an introductory talk on coding theory for high school students, where he used as an illustration the open problem of the existence of a (15, 256, 5)₂ (equivalent to (16, 256, 6)₂). The corresponding linear codes cannot exist; see Exercise 16.5.4. Nordstrom was one of the students. He picked up the challenge and succeeded in constructing the code.

它最初是在 Robinson 为高中生做编码理论入门讲座时构造的，其中他以 (15, 256, 5)₂（等价于 (16, 256, 6)₂）存在的公开问题作为例证。相应的线性码不可能存在；参见练习 16.5.4。Nordstrom 是学生之一。他接受了挑战并成功构造了该码。

The Nordstrom-Robinson code can be seen from various different angles. It is a member of two families of Z₄ linear binary codes, the Kerdock codes and the Preparata codes. It is also closely related to the Reed-Muller codes and to Galois geometries, in particular quadratic forms. We start from a description of the Reed-Muller codes and the Kerdock codes from a geometric point of view.

Nordstrom-Robinson 码可以从各种不同的角度来看。它是两个 Z₄ 线性二元码族的成员，Kerdock 码和 Preparata 码。它也与 Reed-Muller 码和伽罗瓦几何密切相关，特别是二次型。我们从几何观点出发描述 Reed-Muller 码和 Kerdock 码。

## Reed-Muller codes and Kerdock codes

## Reed-Muller 码和 Kerdock 码

We constructed the Reed-Muller codes ℛℳ(a, r) using the (u, u + v) construction in Exercise 5.2.9 of Section 5.2, and as lengthened primitive cyclic codes in Section 14.1. Recall that ℛℳ(a, r) is a [2ʳ, Σᵢ₌₀ᵃ (r choose i), 2ʳ⁻ᵃ]₂ code. In this section we want to get a better understanding from a different point of view.

我们使用第 5.2 节练习 5.2.9 中的 (u, u + v) 构造，以及第 14.1 节中的延拓本原循环码构造了 Reed-Muller 码 ℛℳ(a, r)。Recall ℛℳ(a, r) 是一个 [2ʳ, Σᵢ₌₀ᵃ (r choose i), 2ʳ⁻ᵃ]₂ 码。本节我们想从不同观点获得更好的理解。

### 23.11 Definition.

### 23.11 定义。

The set ℱᵣ of all mappings f : 𝔽₂ʳ ⟶ 𝔽₂ is a binary vector space of dimension 2ʳ. Here addition is defined by (f + g)(x) = f(x) + g(x). A basis consists of the characteristic functions χₐ for a ∈ 𝔽₂ʳ defined by χₐ(a) = 1, χₐ(b) = 0 for b ≠ a.

所有映射 f : 𝔽₂ʳ ⟶ 𝔽₂ 的集合 ℱᵣ 是一个维数为 2ʳ 的二元向量空间。这里加法定义为 (f + g)(x) = f(x) + g(x)。一个基由特征函数 χₐ 组成，a ∈ 𝔽₂ʳ 定义为 χₐ(a) = 1，χₐ(b) = 0 当 b ≠ a。

This is one way of representing 𝔽₂^q, where q = 2ʳ. Each polynomial in r variables x₁, x₂, …, xᵣ with coefficients in 𝔽₂ describes an element of ℱᵣ. Exponents higher than 1 of xᵢ are not needed, as xᵢ and xᵢ² describe the same mapping on 𝔽₂. So we can restrict to monomials, which are products of different xᵢ. Such a monomial is described by a subset of the index set {1, 2, …, r}. For example, the subset {1, 2, 4} describes the monomial x₁x₂x₄. As simple as that. How many different such polynomials are there? The set {1, 2, …, r} has q = 2ʳ subsets, so this is the number of different monomials of that type. In order to show that these monomials form a basis of ℱᵣ, it suffices to represent the characteristic functions χₐ in terms of polynomials.

这是表示 𝔽₂^q 的一种方法，其中 q = 2ʳ。系数在 𝔽₂ 中的 r 个变量 x₁, x₂, …, xᵣ 的每个多项式都描述了 ℱᵣ 的一个元素。xᵢ 的指数高于 1 是不需要的，因为 xᵢ 和 xᵢ² 在 𝔽₂ 上描述相同的映射。因此我们可以限制为单项式，它们是不同 xᵢ 的乘积。这样的单项式由指标集 {1, 2, …, r} 的一个子集描述。例如，子集 {1, 2, 4} 描述单项式 x₁x₂x₄。就这么简单。有多少个不同的这样的多项式？集合 {1, 2, …, r} 有 q = 2ʳ 个子集，所以这是该类型不同单项式的数量。为了证明这些单项式构成 ℱᵣ 的基，只需用多项式表示特征函数 χₐ 即可。

This is easy to see. In fact,

$\chi_a = \prod_{i=1}^{r} (1 + x_i + a_i).$

这很容易看出。事实上，

$\chi_a = \prod_{i=1}^{r} (1 + x_i + a_i).$

We have proved the following:

我们证明了以下内容：

### 23.12 Theorem.

### 23.12 定理。

Let $V = \mathbb{F}_2^r$. Each mapping $f : V \longrightarrow \mathbb{F}_2$ can be written in a unique way as a polynomial in $r$ variables $x_1, x_2, \dots, x_r$ with coefficients in $\mathbb{F}_2$ such that in each monomial each variable occurs with exponent $\le 1$. This representation of $f$ is known as the algebraic normal form (ANF).

设 $V = \mathbb{F}_2^r$。每个映射 $f : V \longrightarrow \mathbb{F}_2$ 都可以唯一地写成 r 个变量 $x_1, x_2, \dots, x_r$ 的多项式，系数在 $\mathbb{F}_2$ 中，使得每个单项式中每个变量的指数 $\le 1$。f 的这种表示称为代数正规形 (ANF)。

For example, the ANF of the mapping $00 \mapsto 0$, $10 \mapsto 0$, $01 \mapsto 1$, $11 \mapsto 1$ simply is $x_2$, and the ANF of $00 \mapsto 1$, $10 \mapsto 0$, $01 \mapsto 1$, $11 \mapsto 0$ is $x_1 + 1$. The algebraic normal form plays an important role in information transmission and cryptology.

例如，映射 $00 \mapsto 0$, $10 \mapsto 0$, $01 \mapsto 1$, $11 \mapsto 1$ 的 ANF simply 是 $x_2$，而映射 $00 \mapsto 1$, $10 \mapsto 0$, $01 \mapsto 1$, $11 \mapsto 0$ 的 ANF 是 $x_1 + 1$。代数正规形在信息传输和密码学中起着重要作用。

If we want to study the behavior of functions $f \in \mathcal{F}_r$, it is natural to construct a list of all function values. That is, we order the elements of $V$ in some way and consider the $2^r$-tuple $(f(a))_{a \in V}$. This is how functions defined on $V$ are identified with codewords of length $q = 2^r$.

如果我们想研究函数 $f \in \mathcal{F}_r$ 的行为，自然的做法是构造所有函数值的一个列表。也就是说，我们以某种方式排列 V 的元素，并考虑 $2^r$-元组 $(f(a))_{a \in V}$。这就是 V 上定义的函数与长度为 $q = 2^r$ 的码字等同的方式。

### 23.13 Definition.

### 23.13 定义。

Let $V = \mathbb{F}_2^r$ and $f : V \longrightarrow \mathbb{F}_2$. Order the elements of $V$ in some way: $V = \{a_1, \dots, a_q\}$, where $q = 2^r$. Then $L_f = (f(a_1), f(a_2), \dots, f(a_q))$.

设 $V = \mathbb{F}_2^r$ 且 $f : V \longrightarrow \mathbb{F}_2$。以某种方式排列 V 的元素：$V = \{a_1, \dots, a_q\}$，其中 $q = 2^r$。则 $L_f = (f(a_1), f(a_2), \dots, f(a_q))$。

Recall that each $f \in \mathcal{F}_r$ has an algebraic normal form. We consider the degree of this ANF. For low degrees this leads us to familiar objects. If $f$ is homogeneous of degree $2$, then $f$ is a binary quadratic form.

回想一下，每个 $f \in \mathcal{F}_r$ 都有一个代数正规形。我们考虑该 ANF 的次数。对于低次数，这会引出我们熟悉的对象。如果 $f$ 是 2 次齐次的，则 $f$ 是一个二元二次型。

### 23.14 Definition.

### 23.14 定义。

The Reed-Muller code $\mathcal{R}\mathcal{M}(a, r)$ has as codewords the $L_f$, where $f \in \mathcal{F}_a$ varies over the mappings whose algebraic normal form has degree $\le a$. As addition of polynomials does not increase the degree, $\mathcal{R}\mathcal{M}(a, r)$ is a linear code. Its length is by definition $q = 2^r$. The number of monomials of degree $i$ is $\binom{r}{i}$. This shows that $\mathcal{R}\mathcal{M}(a, r)$ has dimension $\sum_{i=0}^{a} \binom{r}{i}$. Clearly, $\mathcal{R}\mathcal{M}(0, r)$ is the repetition code.

Reed-Muller 码 $\mathcal{R}\mathcal{M}(a, r)$ 的码字为 $L_f$，其中 $f \in \mathcal{F}_a$ 在代数正规形次数 $\le a$ 的映射上变化。由于多项式的加法不会增加次数，$\mathcal{R}\mathcal{M}(a, r)$ 是一个线性码。其长度按定义为 $q = 2^r$。次数为 $i$ 的单项式个数为 $\binom{r}{i}$。这表明 $\mathcal{R}\mathcal{M}(a, r)$ 的维数为 $\sum_{i=0}^{a} \binom{r}{i}$。显然，$\mathcal{R}\mathcal{M}(0, r)$ 是重复码。

### 23.15 Theorem.

### 23.15 定理。

$\mathcal{R}\mathcal{M}(a, r)$ is a binary linear code of length $2^r$, dimension $\sum_{i=0}^{a} \binom{r}{i}$ and minimum distance $2^{r-a}$.

$\mathcal{R}\mathcal{M}(a, r)$ 是一个长度为 $2^r$、维数为 $\sum_{i=0}^{a} \binom{r}{i}$ 且最小距离为 $2^{r-a}$ 的二元线性码。

### PROOF

### 证明

Only the minimum distance is still in doubt. Let $f \in \mathcal{F}_a$. We can assume by induction that the degree is precisely $a$. Choose a variable which occurs in the ANF, without restriction $x_1$, and write

仅最小距离仍有疑问。设 $f \in \mathcal{F}_a$。我们可通过归纳假设次数恰为 $a$。选取 ANF 中出现的变量，不妨取 $x_1$，并写成

$f(x_1,\dots,x_m)=x_1g(x_2,\dots,x_m)+h(x_2,\dots,x_m)$, where $g$ is not identically zero. View $g,h$ as mappings : $W=\mathbb{F}_2^{r-1}\longrightarrow\mathbb{F}_2$. The elements of $V$ are $(0,b)$ and $(1,b)$, where $b\in W$. We have $f(0,b)=h(b)$ and $f(1,b)=g(b)+h(b)$. Observe that $g$ has degree $\le a-1$. By induction there are at least $2^{(r-1)-(a-1)}=2^{r-a}$ points $b\in W$ such that $g(b)=1$. For each such $b$ we have that either $f(0,b)=1$ or $f(1,b)=1$.

$f(x_1,\dots,x_m)=x_1g(x_2,\dots,x_m)+h(x_2,\dots,x_m)$，其中 $g$ 不恒为零。将 $g,h$ 视为映射：$W=\mathbb{F}_2^{r-1}\longrightarrow\mathbb{F}_2$。V 的元素为 $(0,b)$ 和 $(1,b)$，其中 $b\in W$。我们有 $f(0,b)=h(b)$ 且 $f(1,b)=g(b)+h(b)$。注意 $g$ 的次数 $\le a-1$。由归纳可知，至少有 $2^{(r-1)-(a-1)}=2^{r-a}$ 个点 $b\in W$ 使得 $g(b)=1$。对于每个这样的 $b$，我们有 $f(0,b)=1$ 或 $f(1,b)=1$。

Consider $\mathcal{R}\mathcal{M}(2,r)$. Let $f\in\mathcal{F}_2$ of degree 2. If the constant term is 0, then $f$ is a sum of terms of the form $x_i x_j$ for $i\neq j$ and of linear terms $x_i$. We can write $x_i^2$ instead of $x_i$ and obtain the same mapping $f$. This shows that $f$ simply is a binary quadratic form in dimension $r$. We studied quadratic forms in Chapter 17. The weight $wt(L_f)$ equals the number of vectors $v$ where $f(v)=1$. These representation numbers have been determined.

考虑 $\mathcal{R}\mathcal{M}(2,r)$。设 $f\in\mathcal{F}_2$ 的次数为 2。如果常数项为 0，则 $f$ 是形如 $x_i x_j$（$i\neq j$）的项和线性项 $x_i$ 的和。我们可以用 $x_i^2$ 代替 $x_i$ 并得到相同的映射 $f$。这表明 $f$ 只是 $r$ 维的二元二次型。我们在第 17 章研究了二次型。权 $wt(L_f)$ 等于满足 $f(v)=1$ 的向量 $v$ 的个数。这些表示数已被确定。

As we know, the underlying symplectic form is determined by the terms $x_i x_j$ for $i\neq j$. Different choices of quadratic terms $x_i^2$ lead to different quadratic forms belonging to the same symplectic bilinear form. Consider the case when the symplectic form is nondegenerate. Then the quadratic form will automatically be nondegenerate, for every choice of the diagonal terms. This can happen only when $r=2m$ is even. We know the representation numbers of these quadratic forms; see Section 17.2, where we found out the formulas given in Theorems 17.41 and 17.42 for the odd characteristic case are valid in characteristic 2 as well. The numbers are $e_m(0)=2^{2m-1}-2^{m-1},\ e_m(1)=2^{2m-1}+2^{m-1}$ $h_m(0)=2^{2m-1}+2^{m-1},\ h_m(1)=2^{2m-1}-2^{m-1}$.

如我们所知，底层的辛形式由 $i\neq j$ 的项 $x_i x_j$ 决定。二次项 $x_i^2$ 的不同选择会导致属于同一辛双线性形式的不同的二次型。考虑辛形式非退化的情形。则二次型对角项的每一种选择都将自动是非退化的。这只能发生在 $r=2m$ 为偶数时。我们知道这些二次型的表示数；参见第 17.2 节，其中我们发现定理 17.41 和 17.42 中给出的奇特征情形的公式在特征 2 下同样成立。数值为 $e_m(0)=2^{2m-1}-2^{m-1},\ e_m(1)=2^{2m-1}+2^{m-1}$ $h_m(0)=2^{2m-1}+2^{m-1},\ h_m(1)=2^{2m-1}-2^{m-1}$。

Whenever $f$ is elliptic, we have $wt(L_f)=e_m(0),\ wt(L_f+\mathbf{1})=e_m(1)$. If $f$ is hyperbolic, then $wt(L_f)=h_m(0),\ wt(L_f+\mathbf{1})=h_m(1)$. We see that only two different weights occur. Fixing the symplectic form means fixing a coset of $\mathcal{R}\mathcal{M}(1,2m)$ in $\mathcal{R}\mathcal{M}(2,2m)$. Whenever that coset is described by a nondegenerate symplectic form, all codewords for $f$ in that coset will have weights $2^{2m-1}\pm2^{m-1}$.

每当 $f$ 为椭圆时，我们有 $wt(L_f)=e_m(0),\ wt(L_f+\mathbf{1})=e_m(1)$。如果 $f$ 为双曲，则 $wt(L_f)=h_m(0),\ wt(L_f+\mathbf{1})=h_m(1)$。我们看到只有两种不同的权出现。固定辛形式意味着在 $\mathcal{R}\mathcal{M}(2,2m)$ 中固定 $\mathcal{R}\mathcal{M}(1,2m)$ 的一个陪集。每当该陪集由一个非退化辛形式描述时，该陪集中 $f$ 的所有码字权都为 $2^{2m-1}\pm2^{m-1}$。

This leads to the following strategy to construct good codes: find a family of symplectic bilinear forms on $V(2m,2)$ such that, for any two different forms, their difference is nondegenerate. The union of the corresponding cosets of $\mathcal{R}(1,2m)$ in $\mathcal{R}(2,2m)$ will then be a code of minimum distance $2^{2m-1}-2^{m-1}$. How many cosets can we expect in such a set? As we know, each symplectic form on $V(2m,2)$ is determined by a symmetric $(2m,2m)$ matrix with zeroes on the diagonal. How many of those matrices can we find such that the difference between any two is nondegenerate? Certainly the first rows of these

这导致了构造好码的以下策略：在 $V(2m,2)$ 上找到一族辛双线性形式，使得任意两个不同形式之差是非退化的。$\mathcal{R}(2,2m)$ 中 $\mathcal{R}(1,2m)$ 的相应陪集的并集将是一个最小距离为 $2^{2m-1}-2^{m-1}$ 的码。这样的集合中我们期望有多少个陪集？如我们所知，$V(2m,2)$ 上的每个辛形式由一个对角线为零的对称 $(2m,2m)$ 矩阵决定。我们能找到多少个这样的矩阵使得任意两个之差是非退化的？当然这些矩阵的第一行
