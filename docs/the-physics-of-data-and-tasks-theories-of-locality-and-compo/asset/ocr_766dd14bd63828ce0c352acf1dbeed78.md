# 2.4 ASYMPOTIC LEARNING CURVES FOR RIDGLESS REGRESSION

# 2.4 ASYMPOTIC LEARNING CURVES FOR RIDGLESS REGRESSION

In follows, we explicitly focus on translationally-invariant kernels $c(x_i)=c(x_i-x_j)$ and assume a uniform data distribution $p(d^s)$ over a d-dimensional torus. This assumption ensures that lower-dimensional marginals are uniformly distributed over smaller-dimensional tori. Under these conditions, Mercer's decomposition can be conveniently represented in Fourier space waves [Sso1], where the eigenfunctions $\phi_k^{(s)}(x)=e^{ik^	op x}$ and the eigenvalues coincide with the Fourier transform of $c$. Thus, all the conditions for lemmas 2.3.3 and 2.3.4 are satisfied. Moreover, for kernels characterized by size $s$ or $t$ and smoothness exponent $\alpha$, their eigenvalues decay with a power $-(s+\alpha_s)$ or $-(t+\alpha_t)$ of the wave modulus $k=\sqrt{k^	op k}$ [Wid6].

In this setting, we present our central result:

**Theorem 2.4.1.** Let $K_t$ be a d-dimensional convolutional kernel with a translationally-invariant t-dimensional constituent and leading nonanalyticicity at the origin controlled by the exponent $\alpha_t > 0$. Let $K_s$ be a d-dimensional convolutional or local student with a translationally-invariant s-dimensional constituent, and with a nonanalyticicity at the origin controlled by the exponent $\alpha_s > 0$. If all the t-dimensional patches of the teacher are contained in at least one of the s-dimensional patches of the student, and data are uniformly distributed on a d-dimensional torus, the following asymptotic equivalence holds in the limit $P 	o \infty$

> $E(P) \sim P^{-eta}, \quad \beta = \alpha_s/s.$

Combining Theorem 2.4.1 with Equation 28, and under the additional assumption that $\alpha_t \le 2(\alpha_s+s)$, we derive the following prediction for the asymptotic of the learning curve:

> $E(P) \sim P^{-eta}, \quad \beta = \alpha_s/s.$

Importantly, $eta$ does not depend on the input dimension $d$, we conclude that the cost of dimensionality becomes when a convolutional target is learned with a convolutional or local kernel. In fact, Equation 42 indicates that there is no asymptotic advantage in using a convolutional rather than local student when learning a convolutional task, supporting the notion that the primary factor underlying the empirical success of convolutional architectures is their locality rather than weight sharing. Empirical evidence validating these predictions is presented in Section 2.5.

2 This condition is satisfied when $s \ge t$ in the fully overlapping-patches case, while requires that $s$ is an integer multiple of $t$ in the nonoverlapping-patches case.