# 20.37 Definition. The divisor (ω) of the Weil differential ω is the uniquely determined largest divisor A such that ω sends A_F(A) to 0.

It follows directly from the definition that, for x ∈ F, we have (xω) = (x)+(ω). Because of Proposition 20.36, it follows that the divisors of nonzero Weil differentials form a uniquely determined equivalence class of divisors:

# 20.38 Definition. The canonical divisors are the equivalence class of divisors of nonzero Weil differentials.

The space Ω_F(A) consists of those differentials ω satisfying A ≤ (ω). In the case A = 0, this leads to the g-dimensional space Ω_F(0). This is another characterization of the genus g, as the dimension of the space of holomorphic differentials.

The standard form of the Riemann-Roch theorem is obtained by the formal observation that, for a canonical divisor W, the spaces Ω_F(A) and L(W − A) have the same dimension (which is i(A)). This is a duality theorem. An isomorphism simply sends x ∈ L(W − A) to xω where of course ω is chosen such that (ω) = W. This follows directly from the definitions. Here is the central theorem:

# 20.39 Theorem (Riemann-Roch theorem). Let W be a canonical divisor. Then for every divisor A, we have

dim(A) = deg(A) + 1 − g + dim(W − A).

Some consequences are immediate: the special case A = 0 shows 1 = dim(0) = 0 + 1 − g + dim(W). Consequently, dim(W) = g. This is not really new. In fact we just saw the duality theorem which implies that W and Ω_F(0) have the same dimension. Use Riemann-Roch again, this time applying it to W. This shows deg(W) = 2g − 2. It is easy to see that the canonical divisor class is characterized by these properties:

# 20.40 Proposition. A divisor W is canonical if and only if it has deg(W) = 2g − 2, dim(W) = g.

Another important application of the Riemann-Roch theorem and its proof is the following strengthening of Theorem 20.15, Theorem 1.6.5 of [198]:

# 20.41 Theorem (strong approximation theorem). Let S be a proper set of places (so there must be at least one place outside S) and P1,..., Pr ∈ S. Let x1,..., xr ∈ F and integers n1,..., nr be given. Then there exists an element x ∈ F satisfying the following:

+   - v_{P_i}(x − x_i) = n_i, i = 1,2,..., n.
+   - v_P(x) ≥ 0 for all remaining P ∈ S.