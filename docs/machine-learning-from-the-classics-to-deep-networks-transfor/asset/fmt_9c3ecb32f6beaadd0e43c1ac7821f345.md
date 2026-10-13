
Looking at Eqs. [(4.23)](#Chp004_119-175_B978044329238500010X.xhtml#deq32) and [(4.24)](#Chp004_119-175_B978044329238500010X.xhtml#deq33), we observe that starting from the direct generalization of the linear estimation task for real-valued signals, which led to the adoption of `ŷ = θ^(H)x`, resulted in a matrix, `Θ`, of a *very special structure*.

### 4.4.1 Widely linear complex-valued estimation

Let us define the linear two-channel estimation task starting from the definition of a linear operation in vector spaces. The task is to generate a vector output, `ŷ = [ŷ_r, ŷ_i]^T ∈ ℝ^2`, from the input vector variables, `x = [x_r^T, x_i^T]^T ∈ ℝ^(2l)`, via the linear operation

```
ŷ = [ŷ_r; ŷ_i] = Θ[x_r; x_i],
```
(4.25)

where

```
Θ := [θ_11^T  θ_12^T; θ_21^T  θ_22^T],
```
(4.26)

and compute the matrix `Θ` so as to minimize the total error variance
