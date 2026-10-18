
Under the assumption that the sample size `n` is so large such that the random orthogonal matrix `H` is stabilized, we can then view `β = H ⟂ α` as essentially constant. Then the (remaining) variance of the residual term `ŷ − Σ(j=1 to K) αⱼ⁽ᴺ⁾ f̃ⱼ(x)` with `ŷ = Σ(j=1 to K) βⱼ Pⱼ(x)` by using only the truncated coefficients `αⱼ⁽ᴺ⁾`'s is:

```
Var(ŷ − Σ(j=1 to K) αⱼ⁽ᴺ⁾ f̃ⱼ(x)) = Var(ŷ − Σ(j=1 to N) βⱼ Pⱼ(x)) = Var(Σ(j=N+1 to K) βⱼ Pⱼ(x))
= Σ(j=N+1 to K) βⱼ² Var(Pⱼ(x)) ≤ ε² Σ(j=N+1 to K) Var(Pⱼ(x)) ≤ ε² δ Σ(j=1 to K) λⱼ.
```

Hence, as we expect `ε` to be not too large, one can just take `δ = 0.01` and we adjust the number `N` of PCs to be taken. Based on the discussion above, we can work backward, so the PCR can be carried out as follows:
