
where the second last line follows due to the fact that the first integral in the bracket becomes 0 by the symmetric property of `K(·)`, while the second term can be rewritten as `∫_R K((y - y_i)/h_n) d((y - y_i)/h_n)`, which equals `y_i` by the very definition of the kernel function `K(·)`. Hence, we can obtain an estimate for `m(x)` as follows: for a fixed `x_0 ∈ R`,

```
m̂(x_0) = [∫_R y f̂(x_0, y) dy] / f̂(x_0)
        = [(1/(n h_n)) Σ_{i=1}^n K((x_0 - x_i)/h_n) y_i] / [(1/(n h_n)) Σ_{i=1}^n K((x_0 - x_i)/h_n)]
        = [Σ_{i=1}^n K((x_0 - x_i)/h_n) y_i] / [Σ_{i=1}^n K((x_0 - x_i)/h_n)]
```

which is precisely the Nadaraya–Watson estimate ([14.11](#c14.xhtml#c14-disp-0035)).

Meanwhile, recall the case for a general value of order `k`, `m(x)` is approximated by a `k`‐th order polynomial in `x - x_0` for a fixed `x_0 ∈ R`, and the resulting estimator is called the *local polynomial kernel regression estimator*; see [\[9\]](#c14.xhtml#c14-bib-0009) for a detailed discussion. Indeed, for a general value of `k`, the corresponding minimization problem takes the following form: for a pre‐specified `x_0 ∈ R`,
