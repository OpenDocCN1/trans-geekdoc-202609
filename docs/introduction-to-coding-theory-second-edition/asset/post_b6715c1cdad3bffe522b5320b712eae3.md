
nondegenerate quadratic form represents each field element precisely once, we obtain $p_m(c) = q^{2m}$ for all $c$ in characteristic 2. In particular, we conclude that the formulas for the number of points on our quadrics are the same as in odd characteristic.

- 1. Let $q = 2^f$ and $V = V(k, q)$.
- 2. In characteristic 2 quadratic forms (described by homogeneous quadratic polynomials) and symmetric bilinear forms are not equivalent. The quadratic form carries more information.
- 3. The bilinear form underlying the quadratic form $Q$ is $(x, y) = Q(x + y) + Q(x) + Q(y)$. It is symplectic (and symmetric).
- 4. If $Q(x_1, \dots, x_n) = \sum_{1 \le i \le j \le n} q_{ij} x_i x_j$, then each $q_{ij}$ for $i < j$ contributes $a_{ij} = a_{ji} = q_{ij}$ in the Gram matrix of $(\, ,\,)$. Terms $q_{ii}$ do not contribute to $A$. If $A$ is given, then the coefficients $q_{ij}, i < j$ of the quadratic form are determined. The diagonal terms $q_{ii}$ are arbitrary.
- 5. A vector $x$ is **singular** if $Q(x) = 0$, a subspace is **totally singular** if all its vectors are singular. A space is **asingular** if $Q(x) \neq 0$ for all $x \neq 0$.
- 6. $Q$ is **nondegenerate** if it is asingular on the radical of $(\, ,\,)$.
- 7. A two-dimensional nondegenerate space $V$ is either a **quadratic hyperbolic plane** (two singular points) or it is asingular (no singular point).
- 8. Let $tr : \mathbb{F}_q \to \mathbb{F}_2$ be the trace. In the analysis the distinction between elements of trace 0 and of trace 1 replaces the distinction between squares and nonsquares in odd characteristic.
- 9. The results are as in odd characteristic, the words singular, asingular replacing isotropic, anisotropic.
- 10. The formulas for the number of singular points are the same as in odd characteristic.

## Quadrics in PG(2,q) and in PG(3,q)

Let us go back to the quadratic form Q(x) = x1 x3 − x2^2 defining the normal rational curve in PG(2,q). In odd characteristic the corresponding symmetric bilinear form is

$(x,y) = \frac{1}{2} x_1 y_3 + \frac{1}{2} x_3 y_1 - x_2 y_2.$

Its Gram matrix is $A = \begin{pmatrix} 0 & 0 & 1/2 \\ 0 & -1 & 0 \\ 1/2 & 0 & 0 \end{pmatrix}$. We saw this example in the opening stages of the present section. As $det(A)=1/4$, we have that $Q$ is nondegenerate. Its isotropic points form $Q(2,q)$, a set of $q+1$ points (this is the case $m=1$ of Theorem 17.43). As $Q$ has Witt index 1, there is no totally isotropic line. It follows that no more than two points of $Q(2,q)$ are collinear. Lines $l$ containing just one point $P$ of $Q(2,q)$ (tangents) correspond to degenerate two-dimensional spaces. As $P$ is in the radical of $l$, we must have $l = P^{\perp}$. This shows that every point of $Q(2,q)$ is on precisely one tangent. All this confirms results obtained earlier by calculations with coordinates and by combinatorial counting.

This example also illustrates the bijection between symmetric bilinear forms and quadratic forms in odd characteristic. Terms $c_{ii} X_i^2$ lead to entry $a_{ii}=c_{ii}$ in the Gram matrix, whereas each mixed term $c_{ij} X_i X_j$ yields entries $a_{ij}=a_{ji}=c_{ij}/2$ in the Gram matrix.

Now let $q$ be a power of 2. The Gram matrix is $A = \begin{pmatrix} 0 & 0 & 1 \\ 0 & 0 & 0 \\ 1 & 0 & 0 \end{pmatrix}$. Recall that $A$ describes the underlying symplectic bilinear form, not the quadratic form. We have $det(A)=0$, so $( , )$ is degenerate. Recall that this is always so in odd dimension. Nondegenerate symplectic forms exist only in even dimension. The radical of $( , )$ is $V_0 = \langle e_2 \rangle$. We have that $Q$ is nondegenerate as $Q(e_2)=Q(0,1,0)=1$. As $(e_1,e_3)=1$ and $Q(e_1)=Q(e_3)=0$, the space $H_1 = \langle v_1, v_3 \rangle$ is a quadratic hyperbolic plane.

Recall that each oval in $PG(2,q)$ is embedded in a uniquely determined hyperoval when $q$ is a power of 2. The tangents of the oval meet in a unique point, the nucleus $N$, which complements the oval to a hyperoval. Can we confirm that from our quadratic point of view? Well, the nucleus corresponds to the radical of the underlying symplectic form. This radical is one-dimensional, so we talk about a point in $PG(2,q)$, and $Q$ is nondegenerate on it, so $N \notin Q(2,q)$. More importantly, all tangent lines meet in $N$, as the tangent lines are the duals of the points of the quadric, and vectors from $N$ are orthogonal to everything.

We have recovered all the information that we gathered earlier concerning $Q(2,q)$. Let us go one dimension higher.

Consider $Q(x_1,x_2,x_3,x_4)=x_1^2+x_2^2+x_3^2+x_4^2$. In characteristic 2 we have $Q(x)=(\sum_i x_i)^2$. As $Q$ vanishes on a three-dimensional subspace, it clearly is degenerate. Let $q$ be odd.

In dimension $k=4$ and odd characteristic, the hyperbolic quadric has discriminant 1, and the elliptic quadric has discriminant $-1$. This means that the determinant of the Gram matrix is a square in the hyperbolic case, a non-square in the elliptic case. The Gram matrix of our form is the unit matrix. It follows that the quadric is hyperbolic. We know $|Q(3,q)|=(q+1)^2$. It is not all that easy to confirm this by concrete calculations with coordinates.

Let us use the standard form corresponding to a decomposition in hyperbolic planes, in odd characteristic. The Gram matrix is $A=\begin{pmatrix}0&1&0&0\\1&0&0&0\\0&0&0&1\\0&0&1&0\end{pmatrix}$.

The quadratic form is $Q(x)=2x_1x_2+2x_3x_4$. We can use just as well $Q(x)=x_1x_2+x_3x_4$. There should be $(q+1)^2$ isotropic points.

There are $4q$ points such that $x_1x_2=x_3x_4=0$. All remaining points must have all coordinates $\neq0$. We can choose $x_1=1$. For arbitrary nonzero values of $x_2,x_3$, we can find precisely one value of $x_4$ such that $x_4x_3=x_2$. This gives us $(q-1)^2$ points all of whose coordinates are $\neq0$. We count $|Q^+(3,q)|=(q-1)^2+4q=(q+1)^2$, as predicted.

An elliptic four-dimensional quadratic form in odd characteristic is described by the Gram matrix $A=\begin{pmatrix}0&1&0&0\\1&0&0&0\\0&0&1&0\\0&0&0&-\nu\end{pmatrix}$. The quadratic form is $Q(x)=2x_1x_2+x_3^2-\nu x_4^2$. We expect $q^2+1$ isotropic points. This is in fact easy to count directly. Assume at first $x_3=x_4=0$. As either $x_1=0$ or $x_2=0$, this gives us the two points $\langle e_1\rangle,\langle e_2\rangle$. Now let $(x_3,x_4)\neq(0,0)$. Then $x_3^2-\nu x_4^2\neq0$. We can choose $x_1=1$ and obtain a unique solution $x_2$. This gives us $q^2-1$ points. We have confirmed that $|Q^-(3,q)|=q^2+1$.

As the Witt index is 1, there are no totally isotropic lines. It follows that each line intersects $Q^-(3,q)$ in at most two points. In other words, the elliptic quadric in $PG(3,q)$ is a cap.

Consider planes and how they intersect the elliptic quadric. Let $P\in Q^-(3,q)$ and $E=P^\perp$. Then $E$ intersects $Q^-(3,q)$ only in $P$. We see that each point $P\in Q^-(3,q)$ is contained in precisely one such tangent plane. If $E$ is not one of the $q^2+1$ tangent planes, then the restriction of the quadratic form to $E$ is nondegenerate. It follows that $|E\cap Q^-(3,q)|=q+1$ in this case, and the $q+1$ points of intersection form an oval. Observe that all this is true in any characteristic.

### **17.52 Proposition.** *The elliptic quadric $Q^-(3,q)\subset PG(3,q)$ is a cap. Each point $P\in Q^-(3,q)$ is on precisely one plane $P^\perp$ meeting $Q^-(3,q)$ only in $P$.*

*Any plane which is not one of the q² + 1 tangent planes meets Q⁻(3,q) in q + 1 points, which form an oval.*

Now consider the hyperbolic quadric in PG(3,q). As the Witt index is 2, totally singular lines exist. Let us count them.

Fix P ∈ Q⁺(3,q). Then P^⊥ is the orthogonal sum of P and a hyperbolic plane. It follows that P is on precisely two totally singular lines (in odd characteristic we can speak equivalently of isotropy instead of singularity). By double counting we see that the total number of totally singular lines is 2(q+1)²/(q+1)=2(q+1).

Can we determine the structure of this family of 2(q+1) lines? Fix one such line l, let P₁,…,P_{q+1} be the points of l and g_i, i=1,…,q+1 the second totally singular line through P_i (aside from l). Assume lines g_i, g_j intersect in a point R. Then the plane E through the points P_i,P_j,R contains the lines l,g_i,g_j. It is clear that E must be totally singular, which is impossible, as the Witt index is 2. We conclude that the lines g_i are mutually disjoint (one says, skew). It follows that the lines g_i,i=1,2,…,q+1 partition the points of Q⁺(3,q). Starting from one of the g_i, we see that l also is part of such a parallel class.

### **17.53 Proposition.** *Let Q⁺(3,q) ⊂ PG(3,q) be the hyperbolic quadric. There are 2(q+1) totally singular lines. These come in two parallel classes of q+1 each. Each parallel class partitions the points of the quadric, whereas two lines from different parallel classes intersect in a point.*

## Exercises 17.2

**17.2.1.** Let (,) be the bilinear form with A = $\begin{pmatrix}1 & 0 & 2 \\ \mu & 1 & 0 \\ \lambda & 0 & 1\end{pmatrix}$ as the Gram matrix in odd characteristic. For which λ, μ is it degenerate?

**17.2.2.** Let Q(x₁,x₂,x₃)=x₁²−x₃²+2x₁x₃+3x₂x₃ over 𝔽_p, p≠2. Determine the corresponding bilinear form. In which characteristic is this nondegenerate?

**17.2.3.** Consider the preceding example in characteristic 5. Find a standard basis.

**17.2.4.** Let (,) be the bilinear form with A = $\begin{pmatrix}0 & 1 & 1 & 1 \\ 1 & 0 & 1 & 1 \\ 1 & 1 & 0 & a \\ 1 & 1 & a & 1\end{pmatrix}$ as the Gram matrix, in odd characteristic. When is it degenerate?
