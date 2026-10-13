
## Remarks 13.5

1. This is achieved by moment matching, and the new `q^(i+1)` is defined so that the expectations of the respective sufficient statistics are matched to those of `(1/Z_k) * f_k(θ) * q_/k^(i)(θ)`, and this operation is assumed to be computationally tractable.

2. **Step 5:** Compute `f̂_k^(i+1)` such that

```
f̂_k^(i+1)(θ) := K * q^(i+1)(θ) / q_/k^(i)(θ)
```
(13.107)

3. where the proportionality constant is computed so that

```
∫ f̂_k^(i+1)(θ) * q_/k^(i)(θ) dθ = ∫ f_k(θ) * q_/k^(i)(θ) dθ
```
(13.108)

4. which results in `K = Z_k`.

The procedure is then applied for the estimation of `f̂_k+1^(i+1)`. For convergence, more than one passes have to be performed. The evidence can be approximated as

```
p(X) ≈ ∫ ∏_j f̂_j(θ) dθ
```
(13.109)

A detailed application of the algorithm in the context of a simple-to-follow example is given in [49].
