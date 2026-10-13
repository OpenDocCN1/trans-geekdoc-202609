
Σ[x] = 𝔼 [x x^(T)].

![Equation](images/B978044329238500010X/si14.png)

Thus, the weights/parameters of the optimal linear estimator are obtained via a linear system of equations, provided that the covariance matrix is *positive definite* and hence it can be inverted (Appendix A). Moreover, in this case, the solution is *unique*. On the contrary, if Σ[x] is singular and hence cannot be inverted, there are infinitely many solutions (Problem [4.1](#Chp004_119-175_B978044329238500010X.xhtml#o0010)).

### 4.2.1 The cost function surface

Elaborating on the cost function J(θ), as defined in Eq. [(4.2)](#Chp004_119-175_B978044329238500010X.xhtml#deq3), we get

J(θ) = σ[y]² − 2θ^(T)p + θ^(T)Σ[x]θ.

![Equation](images/B978044329238500010X/si16.png)(4.7)

Adding and subtracting the term θ[*]^(T)Σ[x]θ[*] and taking into account the definition of θ[*] from Eq. [(4.5)](#Chp004_119-175_B978044329238500010X.xhtml#deq7), it is readily seen that

![Equation](images/B978044329238500010X/fx002.jpg)(4.8)

where

J(θ[*]) = σ[y]² − p^(T)Σ[x]^(−1)p = σ[y]² − θ[*]^(T)Σ[x]θ[*] = σ[y]² − p^(T)θ[*].

![Equation](images/B978044329238500010X/si19.png)(4.9)

is the minimum achieved at the optimal solution. From Eqs. [(4.8)](#Chp004_119-175_B978044329238500010X.xhtml#deq11) and [(4.9)](#Chp004_119-175_B978044329238500010X.xhtml#deq12), the following remarks can be made.

**Remarks 4.1**
