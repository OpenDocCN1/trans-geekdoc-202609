# Algorithm 46.3: (Search Procedure for the Optimal Rate of Return)

This algorithm is analogous to Algorithm 46.2 with φ replaced by ρ.

# 46.7 Computational Examples

This section contains sample optimization problems and their solutions. Throughout this section, the parameters λ, μ, ν and ω, η, γ, α, β, ℓ will be given as exogenous data, and the decision variables will be S, G, and H. Since there are a large number of combinations of exogenous parameters and optimization problems, we will only treat a subset of interest.

# 46.7.1 Equilibrium pmf of the cash conversion process

Recall that a unique equilibrium pmf exists for the Markovian model of the cash conversion process {(I(t), C(t), R(t)) : t ≥ 0}; cf. Corollary 46.1 and Lemma 46.1. In this subsection, we compute and exhibit the aforementioned joint pmf and its marginal pmfs, using Algorithm 46.1 (except for the case S = A, where an analytical solution is available by Theorem 46.1), for various representative parameter settings.

To this end, nine representative cash conversion models were selected, in which the inventory base stock level was fixed at S = 30, and the available funds maximum was fixed at A = 50. The values of the rate parameters of these models are displayed in Table 46.1, arranged in a 3×3 matrix with elements of the form (λ, μ, ν) preceded by a model number, where the arrival rate was fixed at the baseline value λ = 1, while the value of μ was fixed across each row, and the value of ν was fixed across each column. The values of μ and ν were chosen to represent “low”, “medium” and “high” values relative to λ, keeping in mind that the actual transition rates from the receivables pool to the funds pool and from the funds pool to the inventory are jν and L_{n,k}μ, respectively.

Table 46.1: 3×3 matrix of rate parameters (λ, μ, ν).

|  |  |  |
|---|---|---|
| (1) (1, 1/45, 1/40) | (2) (1, 1/45, 1/20) | (3) (1, 1/45, 1/10) |
| (4) (1, 1/15, 1/40) | (5) (1, 1/15, 1/20) | (6) (1, 1/15, 1/10) |
| (7) (1, 1/5, 1/40) | (8) (1, 1/5, 1/20) | (9) (1, 1/5, 1/10) |