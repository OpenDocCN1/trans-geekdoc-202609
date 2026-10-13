
### 3. Even if points (1) and (2) above are fulfilled, uniqueness is still not guaranteed

In fact, not every low-rank matrix is liable to exact completion, regardless of the number and the positions of the observed entries. Let us demonstrate this via an example. Let one of the singular vectors be sparse. Assume, without loss of generality, that the third left singular vector, `u[3]`, is sparse with sparsity level `k = 1` and also that its nonzero component is the first one, that is, `u[31] ≠ 0`. The rest of `u[i]` and all `v[i]` are assumed to be dense.

Let us return to SVD for a while in Eq. [(20.119)](#Chp020_1103-1179_B9780443292385000263.xhtml#deq181). Observe that the matrix `M` is written as the sum of `r` `l[1] × l[2]` matrices `σ[i] u[i] v[i]^(T)`, `i = 1, …, r`. Thus, in this specific case where `u[3]` is `k = 1`-sparse, the matrix `σ[3] u[3] v[3]^(T)` has zeros everywhere except for its first row. In other words, the information that `σ[3] u[3] v[3]^(T)` brings to the formation of `M` is concentrated in its first row only. This argument can also be viewed from another perspective; the entries of `M` obtained from any row except the first one do not provide any useful information with respect to the values of the free parameters `σ[3]`, `u[3]`, `v[3]`. As a result, in this case, unless one incorporates extra information about the sparse nature of the singular vector, the entries from the first row that are missed are not recoverable, because the number of parameters concerning this row is larger than the number of the available data.

Intuitively, when a matrix has dense singular vectors it is better rendered for exact completion, as each one among the observed entries carries information associated with all the `d[M]` parameters that fully describe it. To this end, a number of conditions which evaluate the suitability of the singular vectors have been established. The simplest one is the following [33]:

```
\| \mathbf{u}_{i} \|_{\infty} \leq \sqrt{\frac{\mu_{B}}{l}},\quad\| \mathbf{v}_{i} \|_{\infty} \leq \sqrt{\frac{\mu_{B}}{l}},\ i = 1,\ldots,r,
```
(20.121)
