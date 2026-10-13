
where `η` denotes the set of the involved noise variables. Note that such a model covers the case of our familiar regression task, where the unknown parameters `θ` are considered random, which is in line with the Bayesian philosophy, as discussed in Chapter [3](#Chp003_65-117_B9780443292385000093.xhtml). Once more, we assume zero mean vectors; otherwise, the respective mean values are subtracted. The dimensions of `y` (`η`) and `θ` may not necessarily be the same; to be in line with the notation used in Chapter [3](#Chp003_65-117_B9780443292385000093.xhtml), let `y`, `η` ∈ ℝ^N and `θ` ∈ ℝ^l. Hence, `X` is an `N` × `l` matrix. Note that the matrix `X` is considered to be deterministic and not random.

Assume the covariance matrices of our zero mean variables,

```
Σ[θ] = 𝔼[θθ^T],  Σ[η] = 𝔼[ηη^T],
```

are known. The goal is to compute a matrix `H` of dimension `l` × `N` so that the linear estimator

```
θ̂ = Hy
```
(4.83)

minimizes the MSE cost

```
J(H) := 𝔼[(θ - θ̂)^T(θ - θ̂)] = Σ_{i=1}^l 𝔼[(θ_i - θ̂_i)^2].
```
(4.84)

Note that this is a *multichannel* estimation task and it is equivalent to solving `l` optimization tasks, one for each component, `θ[i]`, of `θ`. Defining the error vector as

```
ε := θ - θ̂,
```

the cost function is equal to the trace of the corresponding *error covariance matrix*, so that

```
J(H) := trace {𝔼[εε^T]}.
```

Focusing on the *i*th component in Eq. [(4.83)](#Chp004_119-175_B978044329238500010X.xhtml#deq148), we write
