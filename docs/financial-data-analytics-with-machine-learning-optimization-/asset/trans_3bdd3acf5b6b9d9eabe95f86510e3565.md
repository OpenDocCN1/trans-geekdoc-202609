

### 3. 相关性

The correlation of `y_u ~ Ber(p_u)` and `y_v ~ Ber(p_v)` is:

(4.24)
```
ρ_ij := Corr(y_u, y_v) = Cov(y_u, y_v) / sqrt(Var(y_u) * Var(y_v)) =
{ 1, if u = v
  -sqrt(p_u * p_v / ((1 - p_u) * (1 - p_v))), if u ≠ v }
```

在讨论卡方拟合优度检验之前，我们首先介绍一个重要的矩阵逆公式：

**[Proposition 4.1](#c04.xhtml#R_c04-fea-0018) *(Sherman–Morrison formula* [\[18](#c04.xhtml#c04-bib-0018), [41\]](#c04.xhtml#c04-bib-0041)*)***

Suppose that `A` is an `n × n` invertible square matrix, and `u, v` are `n`-dimensional vectors. The inverse `(A + u v^T)^(-1)` exists if and only if `1 + v^T A^(-1) u ≠ 0`, and it is given by:

(4.25)
```
(A + u v^T)^(-1) = A^(-1) - (A^(-1) u v^T A^(-1)) / (1 + v^T A^(-1) u)
```

