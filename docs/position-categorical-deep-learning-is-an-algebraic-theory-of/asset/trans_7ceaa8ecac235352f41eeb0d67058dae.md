

# 类别深度学习

- 对于所有的 $f, g, h \in \mathcal{M}$，$*f \otimes (g \otimes h) = (f \otimes g) \otimes h$；
- 对于所有的 $f \in \mathcal{M}$，$id \otimes f = f \otimes id$。

**E.2** (Agories，参见 Capucci & Gavranović, 2023)，设 $(\mathcal{M}, \otimes, I, \alpha, \lambda, \rho)$ 为一个单子畴。一个 $\mathcal{M}$-范畴 $C$ 是一个范畴 $C$，连带有一个函子 $\blacktriangleright: \mathcal{M} \times C \to C$ 以及自然同构 $\eta_X : I \blacktriangleright X \cong X$ 和 $\mu_{M,N} : (M \otimes N) \blacktriangleright X \to M \blacktriangleright (N \blacktriangleright X)$，使得：

对于所有的 $M, N, P \in \mathcal{M}$ 和范畴 $C$，以下图表交换：

![](img/92dd63b8e10fefd3f3f227bf65a30b83_18_0.png)

**左单位右单位**。对于所有的 $C$ 和 $M \in \mathcal{M}$，以下图表交换。

![](img/92dd63b8e10fefd3f3f227bf65a30b83_18_1.png)

*备注* E.3. 由于我们可以假设单子畴是严格的，根据 MacLane 的一致性定理，我们也可以假设范畴是严格的（Capucci & Gavranović, 2023, 备注 3.4）。这意味着，对于任何 $\mathcal{M}$-范畴：

- * 单位 $\eta_X$ 是一个等式，即 $I \blacktriangleright X = id_C$ 作为类型为 $C \to C$ 的函子；且

我们将此类范畴称为**严格**（strict）范畴。我们将使用这些来简化叙述和某些定理。

**示例 4**（单子作用）。任何单子畴都会产生一个自作用。

**示例 5**（族范畴）。任何带有拷贝的范畴 $C$ 都有一个作用 $\blacktriangleright: Set \times C \to C$，映射 $(X$

# E.1. 范畴的态射

**定义 6**（强丙单子）。设 $(\mathcal{C}, \blacktriangleright)$ 为一个 $\mathcal{M}$-范畴。$C$ 上的 $(T, \mu, \eta)$ 是**强**的，如果它配备了一个自然变换 $\sigma_{P,A} : P(A) \to T(P(A))$，这是一种强度，使得定义 E.9 中的图表交换。

**示例 7**。对于任何单群 $A$，所有类型的 $A \blacktriangleright : Set \to Set$ 类型对于范畴 (Set, $\times$) 来说都是强的。这包含了来自示例 2.2 的 $G \blacktriangleright : Set \to Set,$^{11}$

**定义 8**（强内算函子）。设 $(\mathcal{C}, \blacktriangleright)$ 为一个 $\mathcal{M}$-范畴。$C$ 上的内算函子 $F$ 是**强**的，如果它配备了一个自然变换 $\sigma_{P,A} : F(A) \to F(P(A))$，这是一种强度，使得定义 E.9 中的 AS1 和 AS2 图表交换。

$^{10}$此的另一个名称是 $\mathcal{M}$-线性态射，在 (Capucci & Gavranović, 2023)

$^{11}$该强度实际上是一个自然同构。

**定义 E.9**（算子范强单子一致性图）。$\mathcal{M}$-范畴 $(\mathcal{C}, \blacktriangleright)$ 范畴 $C$ 上的单子 $(T, \mu, \eta)$ 被称为**强**的，如果它配备了一个自然变换 $\sigma_{P,A} : P \otimes A \to T(P \otimes A$，使得以下图表交换：

**AS1**: 强度与单子单位的兼容性。

**AS2**: 强度与单子乘子的兼容性。![](img/92dd63b8e10fefd3f3f227bf65a30b83_19_0.png)

![](img/92dd63b8e10fefd3f3f227bf65a30b83_19_1.png)

**AS3**: 强度与单子乘法的兼容性。![](img/92dd63b8e10fefd3f3f227bf65a30b83_19_2.png)

![](img/92dd63b8e10fefd3f3f227bf65a30b83_19_3.png)

**示例 E.10**。从示例 2.9 到 2.11 的内函子 H4 和 H7 是强内函子，它们相应的单子也是强的。参见附录。

**示例 E.11**。我们展示了一些相关内函子（左侧）和它们的自由单子（右侧）的强度列表 $\sigma_{P,X}$。对于内函子 $1 + A : Set$，其强度 $\sigma_{P,X} : P \times (1 + A) \to 1 + A \times X$ 给出：
$\sigma_{P,X}(p,inl) = inl(p)$
$\sigma_{P,X}(p,inl) = inl(p,x)$

对于内函子 $A + (-)^2$，其强度 $\sigma_{P,X} : P \times (A + (-)^2) \to A + (P \times X)^2$ 给出：
$\sigma_{P,X}(p,inl) = inl(p)$
$\sigma_{P,X}(p,pair(x,x')) = pair((p,x), (p,x'))$

对于自由单子 $List_{+1}(A) : Set \to Set$，其强度 $\sigma_{P,Z} : P \times List_{+1}(A) \to List_{P \times Z}(A)$ 给出：
$\sigma_{P,Z}(p, Nil) = Nil$
$\sigma_{P,Z}(p, z) = (p,z)$
$\sigma_{P,Z}(p,cons(a,as)) = cons(a, \sigma_{P,Z}(p,as))$

对于自由单子 $Tree(A +-) : Set$，其强度 $\sigma_{P,Z} : P \times Tree(A + Z) \to Tree(A + P \times Z)$ 给出：
$\sigma_{P,Z}(p,Leaf(a)) = Leaf(p,a)$
$\sigma_{P,Z}(p,inl(z)) = Leaf(p,z)$
$\sigma_{P,Z}(p,Node(l,r)) = Node(\sigma_{P,Z}(l), \sigma_{P,Z}(r))$

# F. 代数

范代数的良好参考文献有 (Lack, 2010) 或 Kelly (2005)。后者处理了更一般的丰富范畴概念，2 范畴是一个特例。

# F.1. 单子及其松弛代数

2-单子可以简洁地定义为 Cat-单子（参见 Johnson 等，第 6.5 节）。以下是其定义的展开。

**定义 F.1**（2-单子）。$2-\mathcal{C}$ 上的 2-单子包括：

- $C$ 上的 2-内算函子 $T$；
- 2-自然变换 $\mu : T^2 \Rightarrow T$；
- 2-自然变换 $\eta : \text{id}_C \Rightarrow T$；

使得定义 B.1 中的公理（C-丰富变体）成立。松弛 T 代数 $(A, a, \epsilon_A, \delta_A)$ 其中 $(T, \eta, \mu)$ 是 $C$ 上的 2-单子，$\epsilon_A$ 和 $\delta_A$ 是 $C$ 中的以下 2-态射：

$C$ 的一个对象，$a : T(A) \to A$ 是 $C$ 中的一个态射，

![](img/92dd63b8e10fefd3f3f227bf65a30b83_20_0.png)

满足单位和松弛结合条件（Johnson 等，2026, 6.5.6 和 6.5.7）。

**定义 F.3**（松弛代数态射）。设 $\mathcal{E}$ 为一个 2-范畴，$T$ 为 $\mathcal{E}$ 上的 2-单子，$(A, a, \epsilon_A, \delta_A)$ 和 $(B, b, \epsilon_B, \delta_B)$ 为松弛 T 代数。那么从 $(A, a, \epsilon_A, \delta_A) \to (B, b, \epsilon_B, \delta_B)$ 的 alex 态射是一个对 $(f, \kappa)$，其中 $f : A \to B$ 是 $\mathcal{E}$ 中的一个态射，$\kappa$ 是一个 2-态射，跨越以下

![](img/92dd63b8e10fefd3f3f227bf65a30b83_20_1.png)

使得图表（Johnson 等，6.5.9）交换。

弛代数和松弛代数态射构成了单子范畴 Lax-AlgMnd(T)。

**示例 F.4**（对于 M-模块）。如果 $M$ 是一个单子，可以研究“M-模块”，我们将其定义为配备了 $M^{12}$ 兼容作用的单群，对于 2-单子 $\delta_\epsilon(M) \times -$。事实上，这是任何代数的特例。

**示例 F.5**（作为松弛单群的环）。单子环，或“交叉单群”，用于 (Dudzik et al., 2024) 研究网络中的同步性，可以被描述为 2-单子代数的松弛单群。如果 $A$ 是一个 M-模块，$BA$ 是 $\delta_\epsilon(M) \times -$ 的代数。

G. 2-范畴 Para(C)

**定义 G.1**（para，Curutt 等，2022；Capucci 等，2022）。给定一个单子畴 $(\mathcal{M}, \otimes)$ 和一个 $\mathcal{M}$-范畴 $\mathcal{C}$，让 Para$(\mathcal{C})$ 为 2-范畴：

- 范畴的对象；
- 态射 $X \to Y$ 是对 $(P, f)$，$P$ 是 $M$ 的一个对象，$f : P \blacktriangleright X \to Y$ 是 $C$ 的一个态射。

> 12与 M-作用 A（其中 A 是一个集合）不同，在 M-模块中 A 也配备了单子结构。

