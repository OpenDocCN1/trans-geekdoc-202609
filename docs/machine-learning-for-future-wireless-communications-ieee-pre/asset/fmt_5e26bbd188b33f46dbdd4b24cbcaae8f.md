
In this section, the computational complexity of the polynomial canceler and the NN canceler is examined. The polynomial canceler operates on complex numbers, while the NN canceler operates on real numbers. Thus, in order to perform a fair comparison, the number of real additions and real multiplications that are required to perform the computations of each method are counted. Let `a`, `b` ∈ `C` and let `a_R` = ℜ{`a`} and `a_I` = ℑ{`a`} for simplicity. Then, complex addition can be written as:

(18.26)
```
a + b = (a_R + b_R) + j (a_I + b_I)
```

and complex multiplication can be written as:

(18.27)
```
a b = (a_R + j a_I)(b_R + j b_I)
```
(18.28)
```
= (a_R b_R - a_I b_I) + j ((a_R + a_I)(b_R + b_I) - a_R b_R - a_I b_I)
```

Thus, one complex addition is equivalent to two real additions, while one complex multiplication is equivalent to three real multiplications and five real additions.

### 18.2.4.1 Linear Cancellation
The evaluation of the linear cancellation expression in Eq. (`18.18`) requires `L` complex multiplications and `L - 1` complex additions. Equivalently, it requires `N_{MUL,linear} = 3 L` real multiplications and `N_{MUL,linear} = 7 L - 2` real additions.

### 18.2.4.2 Polynomial Nonlinear Cancellation
The total number of complex-valued parameters `ζ_{p,q}[l]` in Eq. (`18.14`) can be calculated as Korpi et al. (`2017`):

(18.29)
```
N_{poly} = L/4 (P + 1)(P + 3)
```
