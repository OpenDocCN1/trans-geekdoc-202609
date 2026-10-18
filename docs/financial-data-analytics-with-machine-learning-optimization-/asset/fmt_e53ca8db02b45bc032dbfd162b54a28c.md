
where `y(n) := Σ(i=1 to n) a_i^2` and `x(k, n) := Σ(i=1 to n-k) a_i a_(i+k)`. First we evaluate the moments of `y(n)`:

```
E(y(n)) = E(Σ(i=1 to n) a_i^2) = Σ(i=1 to n) E(a_i^2) = nσ²,
```

and observe that, for `i > j`, the tower property leads to `E(a_i² a_j²) = E(E(a_i² | F_j) a_j²) = E(a_i²) E(a_j²)`. Hence, we have
