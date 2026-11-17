
## 7.8 Maximum-Likelihood Procedure for SMRQ

Since the SMRQ loss function is a smoother version of the check function, it is possible to use maximum-likelihood estimation (MLE), as described in Chapter 3. To derive the SMRQ loss using the maximum-likelihood procedure, we need a probability density function (PDF), \( f_X(x) \). Since we only have a loss function as a starting point, the reverse MLE rule can be used here (see Section 3.5). That is, we know that \( \rho(x) = -\log f_X(x) \). Then, it follows from the reverse MLE procedure that

\( f_X(x) = \frac{1}{\kappa} e^{-\rho_{SMRQ}(x;\tau)}, \tag{7.8.1} \)

where

\( \rho_{SMRQ}(x;\tau) = \frac{1}{3} \log \left( \cosh \left( \frac{3x}{2} \right) \right) + \left( \tau - \frac{1}{2} \right)x, \tag{7.8.2} \)

using \( a = 1.5 \) as in Eq. (7.5.7). Applying the procedure, the form of the PDF is given by

\( f_X(x) = \frac{e^{-(\tau - \frac{1}{2})x}}{\kappa \cosh(3x/2)^{\frac{1}{3}}}, \tag{7.8.3} \)

where the normalizing constant \(\kappa\) will vary as a function of the selected \(\tau\). For \(\tau = 0.5\), we obtain \(\kappa\) as follows

\(\kappa = \int_{-\infty}^{\infty} \frac{e^{-(\frac{1}{2}-\frac{1}{2})x}}{\cosh(3x/2)} = 4.857,\)

and for \(\tau = 0.25\), we find \(\kappa\) using

\(\kappa = \int_{-\infty}^{\infty} \frac{e^{-(\frac{1}{4}-\frac{1}{2})x}}{\cosh(3x/2)^{\frac{1}{3}}} = 6.546.\)

For \(\tau = 0.75\), we find \(\kappa\) using

\(\kappa = \int_{-\infty}^{\infty} \frac{e^{-(\frac{3}{4}-\frac{1}{2})x}}{\cosh(3x/2)^{\frac{1}{3}}} = 6.546.\)

![](img/f26d7f591c2a080d86425985301266a4_223_0.png)

![](img/f26d7f591c2a080d86425985301266a4_224_0.png)

Figure 7.14 PDFs of the quantile function for five different values of \(\tau\). The five plots are all combined in the bottom-right panel.

A graph of \(\kappa\) vs. \(\tau\) is provided in Figure 7.13 using a number of different values of \(\tau\). The distributions can now be plotted to reveal their characteristics.

Starting with Eq. (7.8.3) and the normalizing constants \(\kappa\) given in Figure 7.13, different values of \(\tau\) were selected and their associated distributions plotted in Figure 7.14. The cases shown are for \(\tau = 0, 0.25, 0.5, 0.75,\text{and } 1.0\). There is a one-to-one correspondence between Figures 7.14 and 7.5. The distributions for \(\tau = 0.25\) and \(\tau = 0.75\) are mirror images, as are distributions for \(\tau = 0.0\) and \(\tau = 1.0\). The only symmetric distribution is associated with \(\tau = 0.5\).

Since we now have the equations for the PDFs, we can find the expected values and variances. For example, setting \(\tau = 0.5\), we find that

\(\mathbb{E}[X] = 0\) (7.8.4)

and noting that \(\mathbb{E}[X^2] = 8.29\) via integration, we have

\(\text{Var}(X) = \mathbb{E}[X^2] - \mathbb{E}[X]^2 = 8.29 - 0^2 = 8.29\). (7.8.5)

However, for \(\tau = 0.75\), we obtain

\(\mathbb{E}[X] = -3.7\) (7.8.6)

and

\(\text{Var}(X) = \mathbb{E}[X^2] - \mathbb{E}[X]^2 = 34.4 - (-3.7)^2 = 20.7\). (7.8.7)

All of the distributions encountered in this book thus far have a mean that is 0 but in quantile regression, the associated PDFs do not have a mean of 0 except for \(\tau = 0.5\). From the above, the mean of the distribution for \(\tau = 0.75\) is negative rather than 0 and for \(\tau = 0.25\) it would be positive rather than 0. This can be seen in Figure 7.14. Furthermore, the variance is not constant but increases as \(\tau\) approaches either 1 or 0.

The MLE can be derived for a given \(\tau\) using the following steps. First, the likelihood function is

\(\begin{aligned} L(\mathbf{x}_1, ..., \mathbf{x}_n | \tau) = \prod_{i=1}^n \left( \frac{e^{-(\tau - \frac{1}{2}) x_i}}{\kappa \cosh (3x_i / 2)^{\frac{1}{3}}} \right). \end{aligned}\)

Then, the negative log-likelihood is

\(\begin{aligned} -\ell(x_1, ..., x_n | \tau) = \sum_{i=1}^n \left[ \frac{1}{3} \log \left( \cosh \left( \frac{3x_i}{2} \right) \right) + \left( \tau - \frac{1}{2} \right) x_i \right] + n \log(\kappa). \end{aligned}\)

Therefore, after removing the constant term, we obtain the loss function as

\(\begin{aligned} J^{\text{SMRQ}}(\boldsymbol{\beta} | \tau) = \sum_{i=1}^n \left[ \frac{1}{3} \log \left( \cosh \left( \frac{3x_i}{2} \right) \right) + \left( \tau - \frac{1}{2} \right) x_i \right]. \end{aligned}\)

The estimates are obtained by selecting \(\tau\) and then carrying out the optimization as follows:

\(\begin{aligned} \hat{\boldsymbol{\beta}}^{\text{SMRQ}} = \text{argmin}_{\boldsymbol{\beta} \in \mathbb{R}^{d+1}} \sum_{i=1}^n \left[ \frac{1}{3} \log \left( \cosh \left( \frac{3r_i}{2} \right) \right) + \left( \tau - \frac{1}{2} \right) r_i \right]. \end{aligned}\)

In the above, the dummy variable \(x_i\) is replaced with residuals \(r_i = y_i - \mathbf{x}_i^\top \hat{\boldsymbol{\beta}}^{\text{SMRQ}}\) for \(i = 1, ..., n\).

## 7.9 Standard Error Computation

Standard errors (s.e.’s) represent the uncertainty around the estimates, as described in Chapter 3. It is essentially the computed value of the standard deviation for each estimate. In the case of quantile regression using log-cosh, the same general formulation of Chapter 3 can be used to obtain the standard errors. However, there will be a different set of s.e.’s for each \(\tau\) so they must be computed separately for each case. For large \(n\), we treat the estimates as normally distributed so that we can use

\(\text{Var}(\hat{\boldsymbol{\beta}}^{\text{SMRQ}}) = \nu^2 (\mathbf{X}^\top \mathbf{X})^{-1},\)

and then define the term \(\nu^2\) as follows:

\(\nu^2 = s^2 \frac{\text{E}[\psi_{\text{SMRQ}}(z)^2]}{\text{E}[\psi'_{\text{SMRQ}}(z)]^2},\)

where \(z = (r - \mu) / s\), which has an unbiased estimate that can be obtained by replacing expectations with averages (as described in Chapter 3):

\(\hat{\nu}^2 = s^2 \frac{ \frac{1}{n} \sum \psi_{\text{SMRQ}}(r_i / \hat{s})^2 }{ [\frac{1}{n} \sum \psi'_{\text{SMRQ}}(r_i / \hat{s})]^2 } \frac{n}{n - d - 1}.\)

In the above, we assume \(\tau = 0.5\) with

\(\psi_{\text{SMRQ}}(r_i / \hat{s}) = \frac{1}{2} \tanh \left( \frac{3r_i}{2\hat{s}} \right) + \left( \tau - \frac{1}{2} \right),\)

and

\(\psi'_{\text{SMRQ}}(r_i / \hat{s}) = \frac{3}{4} \text{sech}^2 \left( \frac{3r_i}{2\hat{s}} \right),\)

Table 7.3 Swiss Fertility estimates and standard errors for RQ and SMRQ quantile regression with $\tau = 0.5$.

| Feature | $\hat{\beta}^{RQ}$ | s.e.$(\hat{\beta}^{RQ})$ | $\hat{\beta}^{SMRQ}$ | s.e.$(\hat{\beta}^{SMRQ})$ |
|---|---|---|---|---|
| (Intercept) | 63.49 | 15.60 | 62.14 | 10.41 |
| Agriculture | −0.20 | 0.10 | −0.20 | 0.07 |
| Examination | −0.46 | 0.37 | −0.27 | 0.25 |
| Education | −0.79 | 0.27 | −0.88 | 0.18 |
| Catholic | 0.10 | 0.05 | 0.10 | 0.03 |
| Infant mortality | 1.46 | 0.56 | 1.42 | 0.37 |

where the residuals are given by \(r_i = y_i - \mathbf{x}_i^\top \hat{\boldsymbol{\beta}}^{\text{SMRQ}}\), \(i = 1, \dots, n\). And finally, for the needed \(\hat{s}\) and \(\hat{s}^2\) terms, we first obtain a robust estimate of \(s\) as follows (see Eq. (1.4.6)):

\(\hat{s} = \text{MADN}(\mathbf{r}),\) (7.9.6)

and then square it. The s.e.’s are computed as the square root of the diagonal elements of the covariance matrix, \(\nu^2(\mathbf{X}^\top \mathbf{X})^{-1}\).

The estimates and s.e. values for RQ and SMRQ are provided in Table 7.3 using the Swiss Fertility dataset. In this case, the quantile of interest is \(\tau = 0.5\). The table indicates that, while the estimates are similar, the standard errors are slightly larger in RQ as compared to SMRQ.

In order to compare both methods over a range of quantiles, a table is not sufficient. Since this dataset has $d = 5$ explanatory variables, it is appropriate to show the aggregate s.e.’s for each \(\tau\) based on the \(L_2\)-norm. The following formula is used:

\(\|\text{s.e.}\|_2 = \sqrt{\text{s.e.}_1^2 + \cdots + \text{s.e.}_d^2}.\) (7.9.7)

**Exercise:** Compute the \(L_2\)-norm of the s.e.’s of the explanatory variables for the Swiss Fertility dataset with \(\tau = 0.5\) using Table 7.3.

**Ans.:** For RQ, \(\|\text{s.e.}\|_2 = \sqrt{0.10^2 + 0.37^2 + 0.27^2 + 0.05^2 + 0.56^2} = 0.732\).

For SMRQ, \(\|\text{s.e.}\|_2 = \sqrt{0.07^2 + 0.25^2 + 0.18^2 + 0.03^2 + 0.37^2} = 0.487\). \(\square\)

Figure 7.15 illustrates the relationship between s.e.’s and the quantile parameter \(\tau\) for the Swiss Fertility dataset. The \(L_2\)-norm of the standard errors for SMRQ and RQ is plotted in Figure 7.15. In the case of SMRQ in the top panel, several graphs are shown for different values of the robustness coefficient, \(a\). Each one has a different error trajectory as \(\tau\) moves from 0 to 1. The graph associated with \(a = 1.5\) provides a relatively low standard error for all values of \(\tau\). This is yet another reason why \(a = 1.5\) is a suitable value for SMRQ. The other graphs begin to stray from their mid-range values as \(\tau\) approaches either 0 or 1, especially for those with a low value of \(a\).

In the lower panel, the standard error graphs for RQ and SMRQ (\(a = 1.5\)) are compared. The graph for RQ indicates a higher overall standard error and it is not a smooth function of \(\tau\) due to the numerous
