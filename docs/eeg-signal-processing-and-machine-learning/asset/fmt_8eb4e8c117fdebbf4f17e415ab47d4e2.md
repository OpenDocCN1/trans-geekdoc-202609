
### 方程 (3.45)

![equation](images/c3-disp-0047.png)

and `a[0] = 1`. On the basis of [(3.39)](#c03.xhtml#c3-disp-0041), `y(n)` is calculated as the weighted sum of its `p` past values. `y(n)` is then constructed and the parameters `f[k]` and `r[k]` are estimated. Hence, the damping factors are obtained as

### 方程 (3.46)

![equation](images/c3-disp-0048.png)

and the resonance frequencies as

### 方程 (3.47)

![equation](images/c3-disp-0049.png)

where `Re(.)` and `Im(.)` denote respectively the real and imaginary parts of a complex quantity. The `w[k]` parameters are calculated using the fact that

![images](images/c3-i0021.png)

or

### 方程 (3.48)

![equation](images/c3-disp-0050.png)

In vector form this can be illustrated as `Rw = y`, where

![images](images/c3-i0022.png)

`k = 0, 1, ⋯, p − 1`, `l = 1, ⋯, p` denoting the elements of the matrix in the above equation. Therefore, `w = R^(−1) y`, assuming `R` is a full‐rank matrix, i.e. there are no repeated poles. Often, this is simply carried out by implementing the Cholesky decomposition algorithm [[34]](#c03.xhtml#c3-bib-0034). Finally, using `w[k]`, the amplitude and initial phases of the exponential terms are calculated as follows:

### 方程 (3.49)

![equation](images/c3-disp-0051.png)

and
