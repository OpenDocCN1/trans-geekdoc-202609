
### Algorithm 1.8: Judge open cover

**Initialisation:** $A$ is a subset of $X$, $U = \{U_\alpha\}_{\alpha \in A}$ is a subset cluster of $X$

**Input:** $A, U$

**Output:** $\{0, 1\}$

```text
procedure OPENCOVER(A, U)
    if not (A ⊂ ⋃_α U_α) then return 0;
    for ∀ U_α do
        if OPENSET(U_α) ≤ 0 then return 0; // U_α is not an open set of topological space X
    end for
    return 1;
end OPENCOVER
```

### Algorithm 1.9: Judge differential manifold

**Initialisation:** $M$ is a manifold with $n$ dimensions, $V = \{(U_\alpha, \varphi_\alpha) : \alpha \in I\}$ is a subset of a coordinate card in $M$

**Input:** $M$

**Output:** $\{0, 1\}$

```text
procedure DIFFMANI(M)
    if DIFFMANI(M) ≤ 0 then return 0;
    for ∀ α ∈ I do
        if OPENCOVER(M, U_α) ≤ 0 then return 0; // U_α is not an open cover of M
    end for
    for ∀ V_a, V_b ∈ V do
        if ASSOCIATE(V_a, V_b) ≤ 0 then return 0; // V_a, V_b are not related to C^r
        if MAXIMUM(V) ≤ 0 then return 0; // V is not maximum
    end for
    return 1;
end DIFFMANI
```

Now, we can give the specific definition of a Lie group.

**Definition 1.16.** Suppose that $G$ is a non-empty set satisfying the following conditions:
- $G$ is a group;
- $G$ is a differential manifold;
- The operations of the group are differentiable, i.e., the mapping $(g_1, g_2) \mapsto g_1g_2^{-1}$ from $G \times G$ to $G$ is a differentiable mapping.

Then, $G$ is a Lie group.

According to the definition of a Lie group, we know that a Lie group is not only a group but also a differential manifold. In general, a manifold is the extension of the concept of a point, line, surface, or various high-dimensional continuous spaces. All observed data in the field of machine learning can be connected with a point, line, surface or other structures. Thus, a Lie group can be used to represent data in the field of machine learning. Through the geometric and algebraic representation of a Lie group for data, we can provide a qualitative description from the geometric point of view and a quantitative description from the algebraic point of view. Through this learning approach for many-to-many expressions, it is possible to find a natural way to solve many problems.

### Algorithm 1.10: Judge Lie group

**Initialisation:** $G$ is a non-empty set

**Input:** $G$

**Output:** $\{0, 1\}$

```text
procedure LIEGROUP(G)
    if GROUP(G) ≤ 0 then return 0; // G is not a group
    if DIFFMANI(G) ≤ 0 then return 0; // G is not a differential manifold
    if DIFFERENTIAL(G) then
        return 1; // operation of G is differentiable
    else
        return 0;
    end if
end LIEGROUP
```

Based on the above preparation as well as the extensive experience of physicists and chemists who have used Lie groups, the extension of Lie groups to machine learning can be regarded as the discovery of the laws of data implication from the perspective of machine learning applied to data analysis. Experts in physics, chemistry, and other areas use the Lie group as a tool to solve problems, which is also implicit in the field of machine learning, where experts can adopt such a vision to find deep data solutions. For further details, readers may refer to the relevant physical and chemical literature. We now give the definition of Lie group machine learning.

**Definition 1.17.** Lie group machine learning: In general, $G$ is used to represent the input space and $M$ is used to represent the output field. Let $G \subseteq \mathbb{R}^D, M \subseteq \mathbb{R}^d, D > d$. Then, the definition of Lie group $G$ for the mapping $\varphi$ on $M$ is as follows:

$\varphi: G \times M \rightarrow M$
$g, x \rightarrow \varphi(g, x)$

It should hold that $\varphi(g_1, \varphi(g_2, x)) = \varphi(g_1 g_2, x), \varphi(e, x) = x$. Then, for any $g \in G$, $M$ is a diffeomorphism exchange

$\varphi_g: M \rightarrow M$
$x \rightarrow \varphi(g, x)$

Mapping set $\{\varphi_g, g \in G\}$ satisfies $\varphi_{g_1} \cdot \varphi_{g_2} = \varphi_{g_1 g_2}, \varphi_e = id_M$. The diagram of Lie group machine learning is shown in Figure 1.2.

Similarly, we can define the right effect of group $G$ on $M$:

$\psi: M \times G \rightarrow M$
$x, g \rightarrow \psi(x, g)$

satisfying $\psi(x, \psi(x, g_1), g_2) = \psi(x, g_1 g_2), \psi(x, e) = x$. The right effect of Lie group machine learning is shown in Figure 1.3.

It is easy to see the diffeomorphism exchange of the right effect from $G$ to $M$:

$\psi_g: M \rightarrow M$
$x \rightarrow \psi(x, g)$

Because a Lie group is an analytic manifold with a group structure, and group operations are analytic, the Lie group machine learning norm can be used to analyse the dimension, compactness, connectivity, nilpotency, subgroup, cosets, quotient groups, quantum groups, and so on. These basic structures serve as the foundation for the design of the Lie group machine learning algorithm [2–4, 8].

![](img/456a7a56403cbb2b5f1a261793529a51_26_0.png)

![](img/456a7a56403cbb2b5f1a261793529a51_26_1.png)

## 1.3 Algebraic model of Lie group machine learning [2, 3, 10]

According to the concept of Lie group machine learning, four different mathematical structures, namely Lie algebras, one-parameter subgroup, left invariant vector field, and left invariant manifold, are defined as a natural correspondence, i.e., Lie algebras $\equiv$ {left invariant vector field} $\equiv$ {left invariant flow} $\equiv$ {one-parameter subgroup}. These mathematical structures serve as the foundation for the study of the Lie algebra root calculation model, decomposition model, and classification model of Lie group root machine learning.

### 1.3.1 Lie algebras

For convenience, suppose that in the Lie group machine learning system, there is an input space $G$. Suppose that the linear space $\mathfrak{g}$ on $G$ has a binary operation $(x, y) \rightarrow [x, y]$ (usually called transposition operation or product), and satisfies the following conditions:

(1) The binary operation is bilinear, i.e.,
$$\left[\lambda x + \mu y, z\right] = \lambda\left[x, z\right] + \mu\left[y, z\right], \forall \lambda, \mu \in G, \forall x, y, z \in \mathfrak{g} \ ;$$

(2) $[x, x] = 0, \forall x \in \mathfrak{g}$;

(3) A Jacobi identity is established, i.e.,
$[x, [y, z]] + [y, [z, x]] + [z, [x, y]] = 0 \forall x, y, z \in \mathfrak{g}$. Then, $\mathfrak{g}$ is a Lie algebra on $G$.

From (1), (2), we obtain $[x, y] = -[y, x], \forall x, y \in \mathfrak{g}$.

### Algorithm 1.11: Judge Lie algebras

**Initialisation:** $\mathfrak{g}$ is a linear space on $G$, $[x, y]$ is a bracket product operation on it

**Input:** $\mathfrak{g}$

**Output:** $\{0, 1\}$

```text
procedure LIEALGEBRA(𝔤)
    for ∀ x, y, z ∈ 𝔤 do
        if [λx + μy, z] != λ[x, z] + μ[y, z] then return 0;
        if [x, x] != 0 then return 0;
        if [x, [y, z]] + [y, [z, x]] + [z, [x, y]] != 0 then return 0;
    end for
    return 1; // If the above three conditions are satisfied, then 𝔤 is a Lie algebra of G
end LIEALGEBRA
```
