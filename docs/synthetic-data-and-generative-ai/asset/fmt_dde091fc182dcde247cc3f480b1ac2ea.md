
## 7.2 Synthetic Data Generation and Correlation Structure

Rather than testing the methodology on a few real-life data sets, I tested it on a large number of very different synthetic data sets, each with its unique correlation structure. These data sets are generated via simulations, as follows. First, generate `m` column vectors `Z[1]`, …, `Z[m]`, with `Z[i]` consisting of `n` deviates `Z_ij` (1 ≤ `i` ≤ `m`, 1 ≤ `j` ≤ `n`). One of the simplest distributions to sample from is the generalized logistic. See examples in Chapter [16](#Chp016_293-327_B9780443218576000205.xhtml), to simulate cluster processes. In this case I used

$$
Z_{ij} = - \log\frac{U_{ij}^{\gamma}}{1 - U_{ij}^{\gamma}},
$$

where `γ` > 0 is a parameter, and `U_ij`'s are independently and identically distributed uniform deviates on [0, 1]. Then, I generated `m` column vectors `X[1]`, …, `X[m]` as random linear combinations of the `Z[i]`'s:

$$
X_{i} = \sum\limits_{j = 1}^{m} w_{ij} Z_{i}, \quad i = 1,\ldots,m.
$$ (7.3)

The `m` × `m` matrix `W` = (`w_ij`) is called the weight matrix. Here again, the `w_ij`'s are deviates from the same family of generalized logistic distributions. Finally, the simulated response is

$$
Y = \sum\limits_{i = 1}^{m} \alpha_{i} X_{i} + \tau \epsilon, \quad i = 1,\ldots,m,
$$

where `ε` (a column vector with `n` independent entries) is an artificially generated white noise, and `τ` ≥ 0 controls the amount of noise. The `α_i`'s can be prespecified or randomly generated. In any case, the exact, prespecified set of regression coefficients is the column vector `α` = (`α_1`, …, `α_m`)^(`T`). The estimated coefficients, at the `k`th iteration of the fixed point algorithm, using formula [(7.2)](#Chp007_113-129_B9780443218576000114.xhtml#deq3), comprise the column vector `β_k` = (`β_k1`, …, `β_km`)^(`T`). Thus in this setting, we are able to measure how close the estimate `β_k` is to the exact value `α`. In real-life applications, the exact value is never known. If it was, there would be no need to perform statistical inference.

### 7.2.1 Correlation structure

Let `Ω_X` (respectively `Ω_Z`) be the `m` × `m` covariance matrix [[Wiki](https://en.wikipedia.org/wiki/Covariance_matrix)] attached to `X[1]`, …, `X[m]` (respectively to `Z[1]`, …, `Z[m]`). Likewise, define the correlation matrices as `R_X`, `R_Z`, with

$$
R_X = [D(\Omega_X)]^{-1/2} \Omega_X [D(\Omega_X)]^{-1/2} \quad \text{and} \quad R_Z = [D(\Omega_Z)]^{-1/2} \Omega_Z [D(\Omega_Z)]^{-1/2}.
$$

Here `D(A)` is the matrix consisting of the diagonal elements of the matrix `A`. We have

$$
\Omega_X = W \Omega_Z W^T = (W \Omega_X^{1/2})(W \Omega_X^{1/2})^T, \quad \text{thus } W = \Omega_X^{1/2} \Omega_Z^{-1/2}.
$$

These formulas allow you to easily compute `R_X` based on the weight matrix `W` and `Ω_W`. Though more difficult, it is possible to solve the inverse problem: prespecify the correlation structure `R_X` of the data set, and then find `W` that yields the desired, target `R_X`. This is best accomplished using an iterative algorithm similar to the fixed point discussed in Section [7.1](#Chp007_113-129_B9780443218576000114.xhtml#s0010), using the above formulas.

The formulas to solve the inverse problem involve the square root of positive semidefinite matrices [[Wiki](https://en.wikipedia.org/wiki/Square_root_of_a_matrix)]. The solution is not unique. See how it is done, in Chapter [3](#Chp003_49-60_B9780443218576000072.xhtml) entitled “Gentle Introduction to Linear Algebra”. Without loss of generality, a simplification consists of simulating standardized `Z[1]`, …, `Z[m]` (from a distribution with zero mean and unit variance) so that `R_Z` = `Ω_Z` is the identity matrix. If, in addition, the observed `X[1]`, …, `X[m]` are also standardized, then `R_X` = `Ω_X`, and thus, `W` = `R_X^{1/2}`. Multiple square roots exist, in the same way that 2 and −2 are two “square roots” of 4.

### 7.2.2 Standardized regression

Under stable conditions, the predicted values for `Y` are very close to those obtained via standard statistical regression, even though the estimated regression coefficients may be quite different. The accompanying spreadsheet and computations are now stable. However, in previous tests, with a different damping schedule (the matrix `Λ`), sometimes the `β_k` diverged as `k` → ∞. Yet after normalizing `β_k`, the instability was essentially removed and, again, the predicted `Y` was sound. I provide here the normalizing formula, to guarantee that the standard deviation of the response `Y`, denoted as `σ_Y`, is identical to that measured on the predicted `Y`. The new `β_k`, denoted as `β_k^*`, is computed as follows:

$$
\beta_{k}^{*} = \frac{\sigma_{Y}}{\sqrt{\beta_{k}^{T} \Omega_{X} \beta_{k}}} \cdot \Omega_{W} \beta_{k}.
$$

This may be useful if you modify `Λ` when doing some research, as a technique to stabilize the predictions. I also included the computation of `β_k^*` in the spreadsheet. However, it is best to avoid standardizing the regression coefficients when the algorithm is numerically stable. It results in more realistic variance in the predicted values as the uncorrected regression acts as a smoother, but it also comes with a price – a larger mean squared error.

To the contrary, shifting the predicted values so that their mean matches that of the observed values on the training set, is always useful. It is included in my computations (and in the spreadsheet) as a final, postprocessing step. It does not impact the R-squared. Also, it allows you to ignore the intercept parameter in the regression model. Indeed, this is an easy workaround to using an actual intercept parameter.

### 7.2.3 Initial conditions
