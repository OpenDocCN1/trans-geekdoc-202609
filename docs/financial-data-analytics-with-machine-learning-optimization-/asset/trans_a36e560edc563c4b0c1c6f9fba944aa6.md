

[(6.5)](#c06.xhtml#R_c06-disp-0007)

```math
Q(θ|θ^(t)) - R(θ|θ^(t)) = Σ(i=1 to n) ∫supp(z) f(z|y_i; θ^(t)) (ln f(y_i, z; θ) - ln f(z|y_i; θ)) dz
                      = Σ(i=1 to n) ∫supp(z) f(z|y_i; θ^(t)) ln f(y_i, z; θ) dz
                      = Σ(i=1 to n) (ln f(y_i; θ) · 1) = ln L(θ; y_1, ..., y_n).
```

分别将 `θ = θ^(t)` 和 `θ = θ^(t+1)` 代入 ([6.5](#c06.xhtml#c06-disp-0007))，然后考虑它们的差，我们得到

