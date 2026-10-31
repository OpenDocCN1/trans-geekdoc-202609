# 21.5 The Riemann-Hurwitz formula

The general strategy in deriving a formula that relates the genus of $F$ and of its finite extension $F'$ is to start from a canonical divisor for $F$ (of degree $2g_F-2$) and embed it in the divisor group of $F'$ such that a canonical divisor of $F'$ (of degree $2g_{F'}-2$) results. One important instrument in the construction is the trace $tr : F' \longrightarrow F$. The trace is a nonzero $F$ linear mapping if and only if the extension $F' \mid F$ is separable. It is therefore assumed that $F' \mid F$ is separable. The trace defines a nondegenerate symmetric bilinear form, the trace form $\langle x, y\rangle$ by $\langle x, y\rangle = tr(xy)$. Here $F'$ is seen as a vector space over $F$, but in the definition of the trace form multiplication in $F$ is used. Recall that bilinear forms were introduced in Section 16.2. Whenever a basis $\{z_1,\dots,z_n\}$ of $F' \mid F$ is given, there is also the dual basis $\{z^*_1,\dots,z^*_n\}$ defined by $tr(z_i z^*_j)=\delta_{ij}$. This is used to prove the following (Corollary 3.3.5 of [198]):

# 21.18 Theorem.

*Let $F' \mid F$ be a finite separable extension of the function field $F \mid K$ and $P$ a place of $F$. Then the integral closure $\mathcal{O}'_P$ in $F'$ is the intersection*

$\mathcal{O}'_P = \cap_{P' \mid P} \mathcal{O}_{P'}$.

*There exists a basis $\{u_1, u_2, \dots, u_n\}$ of $F' \mid F$ (an integral basis) such that*

$\mathcal{O}'_P = \sum_{i=1}^n \mathcal{O}_P u_i$.

Moreover, each basis of $F' \mid P$ is an integral basis for almost all places $P$. There is an obvious way to embed the divisor group of $F$ into the divisor group of $F'$ :

# 21.19 Definition.

*Let $P$ be a place of $F$. The conorm of $P$ is*

$Con(P) = \sum_{P' \mid P} e(P' \mid P) P'$.

*This mapping is extended by linearity to a mapping $Con$ from divisors of $F$ to divisors of $F'$.*

# 21.20 Theorem.

One justification for this definition is that $con$ maps principal divisors to principal divisors. Also, it is transitive in towers: $Con_{F'' \mid F}(A) = Con_{F'' \mid F'}(Con_{F' \mid F}(A))$. The degrees are easily controlled (Corollary 3.1.14 of [198]):

$deg(Con_{F' \mid F}(A)) = \frac{[F' : F]}{[K' : K]} deg(A)$.