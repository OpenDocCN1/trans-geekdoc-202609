
in the tangent space is

$\mathrm{D}(a,\, b) = \sqrt{\sum_{i, j=1}^{n} g_{i,j}(a)(a_i - b_i)(a_j - b_j)} \ . \tag{1.2}$

Therefore, in Lie group machine learning, the basic steps of the learning algorithm based on geodesic distance can be summarised as follows.

**Algorithm 1.13:** Geodesic distance algorithm of Lie group machine learning

**Initialisation:** $(X,\tau)$ is a topological space, $x \in X$  
**Input:** Sample point $a$  
**Output:** The distance between all points in the coordinate neighbourhood of $a$ and $a$

1. Generate the neighbourhood $U_a$ of the sample point $a$.
2. Analyse the neighbourhood information of $a$ in the sample set of points to take an automorphism under the invariant inner product $g_{i,j}(a)$, and calculate the value of $g_{i,j}(a)$.
3. Substitute the resulting value $g_{i,j}(a)$ into Equation (1.2) to calculate the distance between each point in $U_a$ and $a$.
4. Output all values of distance (the smaller the distance, the closer the result to be learned)

# 1.5 Axiom hypothesis of Lie group machine learning [2, 3, 5]

This section focuses on the axiom hypothesis of Lie group machine learning.

**Hypothesis 1.1.** Lie group machine learning generalisation ability hypothesis axiom including 1), 2), and 3):

1. Let $G$ be a Lie group, and for any Lie sub-algebra $h$ of Lie algebra $g$ of $G$, there exists a unique connected Lie subgroup $H$ of $G$, such that the following graphs are interchangeable.

$$
    \begin{gathered}
        \eta \subset g \\
        \exp \downarrow \quad \downarrow \exp \\
        H \subset G
    \end{gathered}
$$

2. Let $V$ be an $n$-dimensional linear space, and let $G$ be a Lie subgroup of GL(V). If

$$(g(x), g(y)) = (x, y)\forall x, y \in V \ , \ g \in G \ ,$$

then the inner product $(x, y)$ in $V$ is called unchanged under $G$.

3. Set the left and right invariant Riemannian structures with a total volume of 1 in the compact connected Lie group $G$, where $f$ is any central function on it. Then, we have the following Weyl integral formula

$$\int_G f(g) dg = \frac{1}{|W|} \int_T f(t)\,|Q(t)|^2\, dt \tag{1.3}$$

where |W| represents the number of elements in W. When $t = \exp H$ ($H \in \eta$), $Q(t)$ can be denoted as

$$Q(\exp H) = \sum_{\sigma \in W} \operatorname{sign}(\sigma)e^{2i\chi(\alpha(\delta),H)} \ \ (1.4)$$

where $\delta$ is half of the sum of the roots of $C^\circ$, i.e.,

$$\delta = \frac{1}{2} \sum_{\alpha \in \Delta^1(G)} \alpha \ .$$

Proof. First, we prove axiom 1). Let $X_1, X_2, \ldots, X_m$ be any set of bases from vector subspace $h$. We regard them as the left invariant vector field on $G$. Then, every tangent space of point $g$ on $G$ can be expanded into a subspace, i.e., $D(g) = \operatorname{span}\langle X_1(g), \ldots, X_m(g)\rangle$, where $X_n(g)$ denotes the value of vector field $X_n$ at point $g$. In the tangent space of each point, taking an $m$-dimensional space is called an $m$-dimensional distribution on $G$, which can be regarded as a high-dimensional promotion of the vector field. Therefore, all $X_n$ ($1 \leq i \leq m$) are left invariant, i.e., $d_x (X_n(g)) = X_n(ag)$. The distribution $D$ expanded by them is left invariant, i.e., $d_x (D(g)) = D(ag)$. Moreover, $\eta = \operatorname{span}\langle X_1(g), \ldots, X_m(g)\rangle$ is a Lie sub-algebra; hence, $[X_n, X_t]$ ($1 \leq i, j \leq m$) can always use the linear combination of $X_1, X_2, \ldots, X_m$ for representation. This shows that the above distributions $D$ satisfies the integrable conditions in the Frobenius theorem. Hence, there is a unique maximum integral submanifold corresponding to $D$, which is represented by unit element $e$, denoted by $H$.

Now, we prove that $H$ is a connected subgroup. Let $h$ be any element in $H$. For the left invariant of $D$, obviously, $l_x^{-1} \cdot H = h^{-1} \cdot H$ is a maximum integral submanifold of $D$. By definition, $e \in h^{-1} \cdot H$, i.e., $h^{-1} \cdot H$ passes point $e$. Owing to the uniqueness of the maximum integral submanifold, $h^{-1} \cdot H = H$. If $h$ is arbitrary, then

$$H^{-1} \cdot H = \bigcup_{h \in H} h^{-1} \cdot H = h \ .$$

This proves that $H$ is a connected subgroup. 2) omitted.

3) Proof: We prove it in the following steps. (1) From the analysis of the orbital geometry of $\operatorname{Ad}$ (accompanying transformation) on $G$, we know that $T$ is a public geodesic submanifold and is orthogonal to each conjugate class. Moreover, $C_0 \approx T/W \approx G/\operatorname{Ad}$ is a good basic domain on which we take any two points $t_1$ and $t_2$ such that their distance in $D_0$ is the shortest distance of the conjugate class in $G$, referred to as the orbital distance.

(2) For any given inner point $t \in C_0$, its orbit type is $G/T$. For any given boundary point $t \in \partial C_0 = D_0 \setminus C_0$, its number of orbits is always less than $\dim G/T$. Therefore, it is not difficult to see the collection of non-$G/T$ orbit types, i.e.,

$$G(\partial D_0) = \bigcup_{x \in \partial D_0} G(x) \ .$$

In other words, when we perform integration on $G$, the above subset can be omitted, and we only need to calculate on $G(C_0)$.

(3) Let $t$ be a moving point on $C_0$, $m = \operatorname{dim} G/T = \operatorname{dim} G - \operatorname{dim} T$. Then, $G(t)$ is a $G/T$-type orbit and its $m$-dimensional volume is a function whose domain is $C_0$. We call it the (main) orbital volume function and denote it by $v(t)$. Since each orbit $G(t)$ is the same $G/T$-type homogeneous Riemannian space, its volume ratio is equal to the ratio of its volume elements. We can take a benchmark of $G/T$ homogeneous Riemannian space. For each $G/T$-type orbit $G(t)$, the coset $g \cdot t$ mapped to $g(t)$ is a homogeneous Riemannian space between the $G$-isometric mapping $E$

$$E: G/T \rightarrow G(t), \quad g \cdot t \mapsto g(t) = gtg^{-1} \ .$$

Then, the ratio of the volume element of the above is the Jacobi determinant of the above mapping $E_t$, i.e., the object of the volume function $v(t)$ can be calculated by

$$v(t) = c \cdot \operatorname{det}(dE_{t|_{0}}) \ . \tag{1.5}$$

where $c$ is an undetermined proportional constant and $dE_{t|_{0}}$ is the linear mapping of the base point on the tangent space.

$$\operatorname{d}E_{t|_{0}}: \oplus_{a \in \Delta^{+}} R_{(t,a)}^{2} \rightarrow \mathfrak{J}_{0}(G(t)) \ . \tag{1.6}$$

(4) Since $E_t$ is $G$-isomorphic, $dE_{t|_{0}}$ is a $T$-norm (because the base point is a fixed point under the effect of $T$). Thus, $dE_{t|_{0}}$ can be decomposed into linear straight sums of the following two-dimensional $T$-invariant subspace

$$dE_{t|_{0}, a}: R_{(t,a)}^{2} \rightarrow \mathfrak{J}_{0}(G_{0}(t)) \ . \tag{1.7}$$

Hence, we can use the following formula to calculate $\operatorname{det}(dE_{t|_{0}})$, i.e.,

$$\operatorname{det}(dE_{t|_{0}}) = \prod_{a \in \Delta^{+}} \operatorname{det}(dE_{t|_{0}}, a) \ . \tag{1.8}$$

However, $\operatorname{det}(dE_{t|_{0}})$ is proportional to the $S^2$-type (main) orbit volume function in $Ga/Ta \equiv \widehat{G}_{a} \equiv S^{3}$. In other words, we can use the diagram

![](img/456a7a56403cbb2b5f1a261793529a51_34_0.png)

to put the calculation of $\operatorname{det}(dE_{t|_{0,a}})$ into the $S^2$-type volume function in $\widehat{G}_{a}$ ($\widehat{G}_{a}$ is an isomorphism with $S^{3}$ or SO(3); hence, $\widehat{G}_{a}$ has the same volume elements as $S^{3}$ and we thus see $\widehat{G}_{a}$ as $S^{3}$ in the above problem). Then, we get

$$\operatorname{det}(dE_{t} |_{0,a}) = c' \cdot \sin^{2}\pi(a,H) \tag{1.10}$$

where $H$ satisfies $t = \exp H$ (note that the positive root of $S^{3}$ is $2\Theta$). By integrating formulas (1), (4), and (5), we get

$$v(\exp H) = c^{\prime\prime} \cdot \sin^{2}\pi(a,H) = c \cdot [\widehat{Q}(\exp H)]^{2} \tag{1.11}$$

where $\widehat{Q}(\exp H) = \prod_{a \in \Delta^{+}} (e^{\pi i(a,H)} - e^{-\pi i(a,H)})$.

(5) Finally, we will prove that $\tilde{Q}(\exp H)$ in the above formula is equal to $Q(\exp H)$ in $(*)$. It is proved as follows: Let $\{a_1, \ldots, a_k\}$ be the simple root system for the Weyl room $C_0$. Then, according to the definition of reflection symmetry, we get $ra_i(a_i) = -a_i$, which is equivalent to the two half-space positive and negative sides divided by $\langle a_i\rangle^\bot$, and it naturally corresponds to the other root $a$. When divided by $\langle a_i\rangle^\bot$, the two selected half-space positive and negative sides have no effect. Hence, the next $\Delta^+ \setminus \{a_i\}$ still becomes $\Delta^+ \setminus \{a_i\}$, and we have

$$ra_i(\Delta^+) = (\Delta^+ \setminus \{a_i\}) \cup \{-a_i\} \quad (1 \leq i \leq k) \ . \tag{1.12}$$

Let $\delta = 1/2 \sum_{a \in \Delta^+} a$; according to (1.12), $ra_i(\delta) = \delta - a_i$, and $r_a (\zeta) = \zeta - 2\langle \zeta, a\rangle / \langle a, a\rangle a$, we get

$$r_a \left( \delta \right) = \delta - \frac{2\langle \delta, a_i\rangle}{\langle a_i, a_i\rangle}a_i, \quad 1 \leq i \leq k \ .$$

Hence,

$$\frac{2\langle \delta, a_i\rangle}{\langle a_i, a_i\rangle} = 1 \tag{1.13}$$

Moreover, according to the expression of $\tilde{Q}(\exp H)$ and formula (1.12), we can infer that

$$\tilde{Q}(\exp r_a(H)) = (-1) \cdot \tilde{Q}(\exp H) \ . \tag{1.14}$$

As a result, for the effect of $W$, $\tilde{Q}(\exp H)$ is an odd function, i.e.,

$$\tilde{Q}(\exp \sigma(H)) = \operatorname{sign}(\sigma) \cdot \tilde{Q}(\exp H), \quad \sigma \in W \tag{1.15}$$

where $\operatorname{sign}(\sigma)$ is the sign of $\sigma$ for the determinant of the orthogonal transform on $h$.

There is a dominant item in the expansion $\tilde{Q}(\exp H)$. From (1.15), we can see that all the items $\operatorname{sign}(\sigma) \cdot e^{2 \pi i \langle \sigma(\delta), H \rangle}$ should be included in the expansion of $\tilde{Q}(\exp H)$. Moreover, it is not difficult to prove from (1.13) that it cannot not contain other items in the expansion, so it can only be

$$\tilde{Q}(\exp H) = Q(\exp H) \ .$$

(6) Let $f$ be a central function defined on $G$. When seeking $G$ the integral $\int_G f(g) dg$, we first take the product along the $G$-orbit. Since $f$ is equal on each $G$-orbit $G(t)$, we have

$$
\begin{gather*}
\int_G f(g) dg = \int_{C_0} f(t) \nu(t) dt = \frac{1}{|W|}\int_T f(t) \nu(t) dt \\
= \frac{1}{|W|}\int_T f(t) |Q(t)|^2 \ dt \ ,
\end{gather*} \tag{1.16}
$$

where $C_0$ is an undetermined constant, and $|W|$ is the order of $W$ ($T$ is separated into $|W|$ pieces of Weyl rooms). Then, substitute $f(g) = 1$ into (1.16); it is easy to determine that the above-mentioned constant must be 1. $\square$
