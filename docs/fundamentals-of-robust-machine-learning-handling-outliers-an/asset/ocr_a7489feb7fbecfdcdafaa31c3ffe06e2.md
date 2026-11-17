We can now reformulate the quantile regression problem using this new loss term. It involves minimizing a new convex loss function which is the conditional quantile function for each \(\tau\). By replacing the dummy variable x with \(r_i\), we obtain

```
J(\boldsymbol{\beta}|\tau) = \sum_{i=1}^n \rho(r_i; \tau).
```

This loss function has a unique solution and can be optimized using gradient descent. Unfortunately, the new formulation may still exhibit the crossing problem if the degree of smoothness is not sufficient to eliminate it. We need a more general form of this loss function involving the robustness coefficient \(a\) and then we have to carefully select the value of \(a\) (rather than the 10 used above) to make the function smooth enough to avoid the crossing problem while delivering the required model accuracy.

The general M-estimator based on log-cosh for quantile regression is given by:

```
\hat{\boldsymbol{\beta}}^{\text{SMQR}} = \underset{\beta}{\text{argmin}} J^{\text{SMQR}}(\boldsymbol{\beta}|\tau),
```

where

```
J^{\text{SMQR}}(\boldsymbol{\beta}|\tau) = \sum_{i=1}^n \rho_{\text{SMQR}}(r_i; \tau),
```

and the loss term is

```
\rho_{\text{SMQR}}(r_i; \tau, a) = \frac{1}{2a} \log(\cosh(ar_i)) + \left(\tau - \frac{1}{2}\right) r_i,
```

where \(r_i = y_i - \boldsymbol{x}_i^T \boldsymbol{\beta}^{\text{SMQR}}\) and \(a\) is the robustness coefficient which controls the desired level of curvature of the function (i.e. the smoothness at the kink). This formulation is referred to as the “smooth regression quantiles” (SMRQ). We will use SMRQ to refer to this loss function whereas quantile regression using Eq. (7.4.1) will be referred to simply as “regression quantiles” (RQ). Both of these methods will be compared qualitatively and quantitatively in the sections to follow.

The value of \(a\) requires some discussion. For \(a=10\) used above, there is still a sharp corner in the loss term. The value needs to be reduced further within the range of \(0.5 < a < 10\) for optimal performance. We recommend the use of \(a = 1.5\) for reasons to be elaborated in Section 7.6.2. The resulting loss term is

```
\rho_{\text{SMQR}}(r_i; \tau) = \frac{1}{3} \log \left( \cosh \left( \frac{3}{2} r_i \right) \right) + \left( \tau - \frac{1}{2} \right) r_i.
```

This loss term is plotted as a function of \(r_i\) for different values of \(\tau\) in Figure 7.5. At the top, we note that the two cases for \(\tau=0.0\) and \(\tau=1.0\) are mirror images of one another. The same holds true for the middle pair of cases with \(\tau=0.25\) and \(\tau=0.75\). The case for \(\tau=0.5\) is the only symmetric case. The bottom right panel includes all five cases plotted together. Note that the kinks in the standard check function have all been smoothed out. This will eventually lead to quantile estimates that no longer exhibit the crossing problem. The reasons have to do with the strictly convex property of the SMRQ loss function (in contrast to RQ), which produces unique solutions for each \(\tau\), and the smoothness of the log-cosh check function, which leads to monotonic quantiles.