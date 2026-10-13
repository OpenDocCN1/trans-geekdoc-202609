
### 5. Generate the observations

**x**[*n*] ∼ 𝒩(**AZ**, *σ*[*η*]²**I**), *n* = 1, 2, …, *N*.

The hidden/latent variables are:
(a) the stick breaking lengths, *β*[*k*];
(b) the elements of **Z**; and
(c) the elements of matrix **A**.

In practice, a truncated stick breaking process is considered, where we assume that *P*[*k*] = 0, *k* > *K*. Thus, the matrix of the hidden/latent variables is **W** = [**β**, **A**, **Z**]. Given the set of observations, 𝒳 = {**x**[1], …, **x**[*N*]}, the posterior to be maximized with respect to the unknown parameters, *α*, *σ*[*A*]² and *σ*[*η*]² is given by

*p*(**β**, **A**, **Z** | 𝒳; *α*, *σ*[*A*]², *σ*[*η*]²).

However, it turns out that this is not in a tractable form and the mean field approximation technique can be mobilized (e.g., [15]). In analogy to Eq. [(13.123)](#Chp013_635-716_B9780443292385000196.xhtml#deq186), the factorized family for the variational approximation of the posterior is given by

```
q(W) = ∏_{k=1}^{K} q_{γ_k}(β_k) ∏_{k=1}^{K} q_{Φ_k}(a_k) ∏_{n=1}^{N} q_{ν_{nk}}(z_{nk})
```
