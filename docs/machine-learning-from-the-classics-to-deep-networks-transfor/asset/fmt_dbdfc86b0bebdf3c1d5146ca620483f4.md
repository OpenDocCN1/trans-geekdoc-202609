
## 4.6 MSE linear filtering: a frequency domain point of view

Let us now turn our attention to the more general case, and assume that our filter is of *infinite impulse response* (IIR). Then Eq. [(4.41)](#Chp004_119-175_B978044329238500010X.xhtml#deq63) becomes

```
d̂_n = ∑_{i=-∞}^{+∞} w_i u_{n-i}.
```

Moreover, we have allowed the filter to be *noncausal*.^([^(20)](#fn20))

The orthogonality condition generalizes to (involving an infinite number of terms):

```
∑_{i=-∞}^{+∞} w_i E[u_{n-i} u_{n-j}] = E[d_n u_{n-j}], j ∈ ℤ.
```

A rearrangement of the terms results in

```
∑_{i=-∞}^{+∞} w_i r(j - i) = r_{du}(j), j ∈ ℤ.
```

### Key Definitions

*   The output is given as `d̂[n] = w^H u[n]`.
*   `p = E[u[n] d[n]^*]`.
*   `Σ_u = E[u[n] u[n]^H]`.
*   `r(-k) = r^*(k)`.
