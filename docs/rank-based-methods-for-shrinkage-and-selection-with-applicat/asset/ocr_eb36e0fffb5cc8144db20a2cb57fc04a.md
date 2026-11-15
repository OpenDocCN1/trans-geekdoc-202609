(2) For the definition of linear rank statistics, we consider the score generating function \(\varphi : (0, 1) \mapsto \mathbb{R}\) which is assumed to be non-constant, non-decreasing and square integrable on \((0, 1)\) so that

\(A_\varphi^2 = \int_0^1 \varphi^2(u) du - \left( \int_0^1 \varphi(u) du \right)^2 .\) (8.2.6)

The scores are defined in either of the following ways:

\(a_n(i) = \mathbb{E} \left[ \varphi(U_{i:n}) \right], \quad \text{or} \quad a_n(i) = \varphi \left( \frac{i}{n+1} \right), \quad i = 1, ..., n,\)

where \(U_{1:n} \le ... \le U_{n:n}\) are order statistics from a sample of size \(n\) from the uniform distribution \(\mathcal{U}(0, 1)\).

(3) Let us define

\(\mathbf{C}_n = \frac{1}{n} \sum_{i=1}^n \boldsymbol{x}_i \boldsymbol{x}_i^{\top},\) (8.2.7)

where \(\boldsymbol{x}_i\) is the \(i\)'th row of \(\boldsymbol{X}\). We assume that

(a) \(\lim_{n \to \infty} \mathbf{C}_n = \mathbf{C}\) and (b) \(\lim_{n \to \infty} \max_{1 \le i \le n} \boldsymbol{x}_i^{\top} \mathbf{C}_n^{-1} \boldsymbol{x}_i = 0\) (8.2.8)

where \(\mathbf{C}\) is a non-negative definite matrix.

(4)

\(\lim_{n \to \infty} \boldsymbol{F}_n(d) = \boldsymbol{F}_d, \quad \boldsymbol{F}_d = (\mathbf{C} + \boldsymbol{I}_p)^{-1}(\mathbf{C} + d\boldsymbol{I}_p),\)

where

\(\boldsymbol{F}_n(d) = (\mathbf{C}_n + \boldsymbol{I}_p)^{-1}(\mathbf{C}_n + d\boldsymbol{I}_p).\)

Then, we define the unrestricted Liu-type R-estimator (ULRE) as

\(\hat{\boldsymbol{\beta}}_n^{\text{ULiR}}(d) = \boldsymbol{F}_n(d) \hat{\boldsymbol{\beta}}_n^{\text{UR}}, \quad 0 < d < 1.\) (8.2.9)

# 8.3 Shrinkage Liu-type R-estimators

Suppose we are provided with the sub-space restriction, incorporated as the prior information, \(\boldsymbol{H}\boldsymbol{\beta} = \boldsymbol{h}\), where \(\boldsymbol{H}\) is a \(q \times p (q < p)\) matrix and \(\boldsymbol{h}\) is a \(q\)-vector of known constants. Under such prior information, we define the restricted Liu-type R-estimator (RLRE) as