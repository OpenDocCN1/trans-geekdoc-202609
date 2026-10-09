
![](img/456a7a56403cbb2b5f1a261793529a51_39_0.png)

**Fig. 1.6:** The extension of $r$.

Let $s$ and $M$ be the central symmetry of the point of $r(b-\varepsilon)$. Then, $r$ and $s \cdot r$ have convergence at a length of $2\varepsilon$. This also means that $r$ can extend to at least a length of $b-a-2\varepsilon$ (as shown in Figure 1.6). This also means that any geodesic can always extend indefinitely. Therefore, according to the Hopf–Rinow theorem, $M$ is complete.

(2) Let $p, q$ be any two points on $M$. From the completeness of $M$, there is the shortest geodesic section $r: [0, d(p, q)] \rightarrow M$ that links $p, q$ and makes $r(0) = p, r(d(p, q)) = q$. Let $s$ be the centre symmetry of $M$ for the point $r(1/2(p, q))$ on $M$. Obviously, we have

$$s(p)=q, s(q)=p \ .$$

Hence, the effect of $G(M)$ on $M$ can be delivered. This means that $M$ is homogeneous.

(3) Let $K$ be a fixed grouping of subgroups to make a certain set of base points $P_0 \in M$, where $O(n)$ is the conservative transformation group of $T M_{p_0}$. It is not difficult to see that each element in $K$ is uniquely determined by its induction of conservative transformation on $T M_{p_0}$. Thus,

$$
\begin{aligned}
K & \rightarrow O(n) \\
k & \rightarrow d k|_{p_0}
\end{aligned}
$$

is an isomorphism, and the ‘image’ of $K$ is a closed subgroup of $O(n)$. Thus, $K$ is a compact subgroup of $G(M)$ and a Lie group.

(4) Let $\gamma: R \rightarrow M$ be a geodesic (its parameter is the arc length) in $M$. We temporarily use $s_t$ to denote the central symmetry of $M$ for point $\gamma(t)$. Let $X(t),\ t \in [t_1, t_2]$ be the definition of a parallel vector field on $\gamma\ (\left[2t_1-t_2, t_1\right])$. Then,

$$s_{t_1} X(t) = X'(2t_1 - t)$$

is the definition of a parallel vector field on $\gamma\ (\left[2t_1-t_2, t_1\right])$, and

$$X'(t_1) = s_{t_1} X(t_1) = -X(t_1) \ ,$$

as shown in Figure 1.7.

![](img/456a7a56403cbb2b5f1a261793529a51_40_0.png)

**Fig. 1.7**: Parallel vector field.

Thus,

$$
\begin{aligned}
s_{t_1} &= X(t_2) - X'(2t_1 - t_2) \\
&= Y(t_1, 2t_1 - t_2)(-X(t_1)) \\
&= Y(t_1, 2t_1 - t_2) \cdot Y(t_2, t_1)(-X(t_2)) \\
&= -Y(t_2, 2t_1 - t_2)X(t_2) \ .
\end{aligned}
$$

In other words, under the centrosymmetric $s_{t_1}$, the two tangent vectors $X(t_2)$ and $X'(2t_1-t_2)$ correspond to each other, and their relationship is reversed after the parallel movement along $Y(t_{2},2t_{1}-t_{2})$. Thus, two such symmetrical combinations of centres

$$\phi_{Y}(t_1)=s_{t_1/2}\cdot s_0\ t_1\in R$$

is a conformity change that satisfies the following two conditions

$$
\begin{cases}
\phi_{Y}(t_1)\cdot Y(t_2)=Y(t_1+t_2)\\
d(\phi_{Y}(t_1)|_{TM_{Y(t_2)}})=Y(t_2,t_1+t_2)
\end{cases}\ t_1,t_2\in R\ .
$$

From the above, it is not difficult to see that $\phi_{Y}(t_1)\cdot\phi_{Y}(t_1')$ and $\phi_{Y}(t_1+t_1')$ both are conformity changes satisfying the following conditions

$$
\begin{cases}
\varphi_{Y}(t_1+t_1')Y(t_2)=Y(t_1+t_1'+t_2) \ ,\\
d(\varphi_{Y}(t_1)\cdot\varphi_{Y}(t_1'))|_{TM_{Y(t_2)}})=Y(t_2,t_1+t_1'+t_2) \ ,
\end{cases}
$$

$$
\begin{cases}
\varphi_{Y}(t_1+t_1')Y(t_2)=Y(t_1+t_1'+t_2)\\
d(\varphi_{Y}(t_1+t_1'))|_{TM_{Y(t_2)}})=Y(t_2,t_1+t_1'+t_2)\ .
\end{cases}
$$

Thus,

$$\varphi_{Y}(t_1)\varphi_{Y}(t_1')=\varphi_{Y}(t_1+t_1')\ .$$

In other words, $\varphi_{Y}: R \rightarrow (M)$ is a one-parameter subgroup found in 4.

**2.** Let $M$ be a symmetric space, $P_{0}$ be an arbitrarily determined basis point, $S_{0}$ be the centre symmetry of $M$ for the base point $P_{0}$, $G(M)$ be the conserved transformation group of $M$, and $K$ be the preservative group to fix $P_{0}$. Then,

1.  $M \cong G(M)/K$, where $K$ is a compact Lie group;
2.  $\sigma: G(M) \rightarrow G(M)$ is defined as $\sigma(g)=$

$S_{0}gS_{0}, \forall g \in G(M)$; then, $\sigma$ is a dual automorphism of $G(M)$;

3.  Let $F(\sigma)$ be a fixed point subset of $\sigma$, i.e., $F(\sigma) = \{g \in G(M) | \sigma(g) = g\}$, and let $F^{0}(\sigma)$ be the unit connected area of $F(\sigma)$; then, $F(\sigma)$ and $F^{0}(\sigma)$ are a closed subgroup of $G(M)$, and $F^{0}(\sigma) \subseteq K \subseteq F(\sigma)$;
4.  Let $g$ and $k$ be the Lie algebras of $G(M)$ and $K$, respectively; then, $g = k \oplus p$, $k = \text{ker}(d\sigma - id)$, $P = \text{ker}(d\sigma + id)$;
5.  For any given $X \in P$, $r(t) = \exp X(P_{0})$ is a geodesic passing through $P_{0}$ in $M$, and $\exp tX = \Phi_{r}(t)$ ($\Phi_{r}(t)$ is a one-parameter subgroup of $G(M)$).

**Proof.**

1.  $G(M)$ is a transferable transform Lie group affecting $M$, where $K$ is a closed sub-group of $O(n)$ on the of induction of $TM_{p_{0}}$. Hence, $K$ is a compact Lie group, and we have $M \cong G(M)/K$. Moreover, $\forall g \in G(M)$, $\forall \hat{g} \in G(M)$, $\sigma(g) = s_{0}\hat{g}s_{0}$; hence, it is clear that $G(M)$ is a pair of automorphisms. Therefore, its fixed-point subset $F(\sigma)$ is a closed subgroup, and its unit connected area $F^{0}(\sigma)$ is also a closed subgroup.

2.  Let $i: K \to O(n)$ be defined by $i(k) = d{k|}_{p_{0}}$, $k \in K$. It is a natural isomorphism mapping, and

    $$i(S_{0}) = -id \in O(n) \ .$$

    Thus, for any given $k \in K$, there always is

    $$i \left(S_{0}kS_{0}\right) = (-id) \ t(k) \ (-id) = t(k)$$

    i.e., $s_{0}ks_{0} = k$, $K \subseteq F(\sigma)$. Moreover, let $\exp tX$ be a one-parameter subgroup satisfying $s_{0} \left(\exp tX\right) s_{0} = \exp tX$ in $G(M)$, i.e., $\left(\exp tX\right) \cdot s_{0} \cdot \exp \left(-tX\right) = s_{0}$, $\forall t \in R$; then, $s_{0} \left(\exp tX \cdot p_{0}\right) = \left(\exp tX\right) \cdot s_{0} \cdot \exp \left(-tX\right) \exp \left(-tX\right) \cdot p_{0} = \exp tX \cdot p_{0}$, $\forall t \in R$. In other words, $[\exp tX \cdot p_{0}; \forall t \in R]$ is a fixed point subset including $p_{0}$ of $s_{0}$, while point $p_{0}$ is an isolated fixed point of $s_{0}$. Thus,

    $$\exp tX \cdot p_{0} = p_{0}, \forall t \in R \ ,$$

    i.e., $\exp tX \in K$. This proves that $F^{0}(\sigma) \subseteq K$.

3.  According to the assumption and 1) above, $d\sigma : g \to g$ is a pair of automorphisms of $g$. Thus,

    $$g = k \oplus p, \quad k = \text{ker}(d\sigma - id), \quad p = \text{ker}(d\sigma + id)$$

    where 2) proves that $k$ is a Lie algebra of $K$ (i.e., $F^{0}(\sigma)$). Moreover, for the characteristic of $X \in p$, $\exp tX$ is $s_{0} \left(\exp tX\right) s_{0} = \exp \left(-tX\right)$.

    Let $X_{0}$ be the tangent vector of curve $\{\exp tX(p_{0}); t \in R\}$ at point $p_{0}$ on $M$, and $\gamma$ be the geodesic at the starting velocity vector of $X_{0}$. Then, $\phi_{\gamma}(t) = s_{i} \cdot s_{0}$ obviously is a one-parameter subgroup of $G(M)$ because

    $$
    \begin{aligned}
    s_{0}\phi_{\gamma}(t) &= s_{0} \left(S_{\frac{t}{2}} \cdot s_{0}\right) = s_{0} \cdot S_{\frac{t}{2}} \\
    &= \varphi_{\gamma}(t)^{-1} = \varphi_{\gamma}(-t) \ ,
    \end{aligned}
    $$

    thus, $\exp tX = \varphi_{\gamma}(t)$, $\gamma(t) = \exp tX(p_{0})$.

This axiom implies that the close relationship among the dual space, the Lie group, and the Lie algebras, can be regarded as a particular Lie group and Lie algebras.

## **Hypothesis 1.2.** Division of independence hypothesis of Lie group machine learning.

1.  Let $\mathfrak{g}$ be a real Lie algebra and $\sigma$ be its dual automorphism. Then, $\mathfrak{g}$ has a decomposition of $\sigma$

    $$
    \left\{
    \begin{aligned}
    & \mathfrak{g} = \mathfrak{k} \oplus \mathfrak{p} \\
    & \mathfrak{k} = \ker(\sigma - id) \\
    & \mathfrak{p} = \ker(\sigma + id)
    \end{aligned}
    \right.
    $$

    If $ad_p: \mathfrak{k} \rightarrow gl(\mathfrak{p}), ad: (X) \cdot Y = [X, Y], X \in K, Y \in P$ is a one-to-one correspondence, and $P$ has an $ad$, $K$ is a constant inner product $Q$, i.e., for any given $X \in K, Y, Z \in P$,

    $$
    Q([X, Y], Z) + Q(Y, [X, Z]) = 0
    $$

    is established, then $(\mathfrak{g}, \sigma, Q)$ is an orthogonal duality Lie algebra.
2.  Any orthogonal duality Lie algebra $(\mathfrak{g}, \sigma, Q)$ can be uniquely broken down into the following formula

    $$
    (\mathfrak{g}, \sigma, Q) = (\mathfrak{g}_0, \sigma_0, Q_0) \oplus (\mathfrak{g}_+, \sigma_+, Q_+) + (\mathfrak{g}_-, \sigma_-, Q_-)
    $$

    where $\mathfrak{g}_0 = \mathfrak{k}_0 \oplus \mathfrak{p}_0, \mathfrak{g}_+ = \mathfrak{k}_+ \oplus \mathfrak{p}_+, \mathfrak{g}_- = \mathfrak{k}_- \oplus \mathfrak{p}_-$,

    $$
    \sigma_0 = \sigma|_{\mathfrak{g}_0}, \sigma_+ = \sigma|_{\mathfrak{g}_+}, \sigma_- = \sigma|_{\mathfrak{g}_-}\ ,
    $$

    $$
    Q_0 = Q|_{\mathfrak{p}_0}, Q_+ = Q|_{\mathfrak{p}_+}, Q_- = Q|_{\mathfrak{p}_-}\ ,
    $$

    and $B|P_+, B|P_-$ represent positive and negative, respectively.

## **Hypothesis 1.3.** Consistency hypothesis of Lie group machine learning,

1.  Let $Q$ be the homomorphism of Lie group $G_1$ to Lie group $G_2$. Then, $Q^{-1}(I_2)$ is the closed normal subgroup of $G_1$. Let $\pi$ be the natural homomorphism of $G_1$ to $G_1$ $(Q^{-1}(I_2))$. Then, the homomorphism $\phi$ of $G_1/Q^{-1}(I_2)$ to Lie group $G_2$ makes $Q = \phi\pi$.
2.  Let $G$ be the $n$-dimensional connected exchange group (or complex Lie group). Then,

    $$
    G \cong R^k \otimes T^{n-k}
    $$

    where $T^{n-k} = \underline{R/Z \otimes R/Z \cdots \otimes R/Z}$ is the $n-k$-dimensional torus.

## **Definition 1.21.** If there is an $n^2$ polynomial set of $S$, the necessary and sufficient condition for $\mathfrak{g} = (g_{ij}) \in G$ is

$$
P(g) = P(g_{ij}) = 0\, (\forall p \in S)
$$

Then, the subgroup $G$ of the general linear group ($\mathrm{GL}\,(n, \mathbb{R})$, $\mathrm{GL}\,(n, \mathbb{C})$) is an algebraic group.
