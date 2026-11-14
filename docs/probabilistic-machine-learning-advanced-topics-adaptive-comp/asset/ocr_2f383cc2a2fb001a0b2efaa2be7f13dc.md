# Theorem 7. Under the Austen sensitivity model, Equation (36.105), the outcome influence is

$$R^2_{Y,\text{par}}(\alpha, \delta) = \delta^2 \sum_{a=0}^1 \frac{\mathbb{E}[\psi_1(g(X)^a(1-g(X))^{1-a}(1/\alpha - 1) + 1[A=a])]}{\mathbb{E}[(Y-Q(A,X))^2]},$$

where \(\psi_1\) is the trigamma function.

See Veitch and Zaveri [VZ20] for the proof.

By design, \(\alpha\) — the strength of confounding influence on on treatment assignment — is already on a fixed, unitless scale. However, because the measure is tied to the model it may be difficult to interpret, and it is not obvious how to compute reference confounding strength values from the observed data. The next result clarifies these issues.

# Theorem 8. Under the Austen sensitivity model, Equation (36.105),

$$
\alpha = 1 - \frac{\mathbb{E}[\tilde{g}(X,U)(1 - \tilde{g}(X,U))]}{\mathbb{E}[g(X)(1 - g(X))]}.
$$

See Veitch and Zaveri [VZ20] for the proof. That is, the sensitivity parameter \(\alpha\) is measures how much more extreme the propensity scores become when we condition on \(U\). That is, \(\alpha\) is a measure of the extra predictive power \(U\) adds for \(A\), above and beyond the predictive power in \(X\). It may also be insightful to notice that

$$
\alpha = R^2_{A,\text{par}} = 1 - \frac{\mathbb{E}[(A - \tilde{g}(X,U))^2]}{\mathbb{E}[(A - g(X))^2]}.
$$ (36.106)

That is, \(\alpha\) is just the (non-parametric) partial coefficient of determination of \(U\) on \(A\)—the same measure used for the outcome influence. (To see this, just expand the expectations conditional on \(A=1\) and \(A=0\)).

**Estimating bias** In combination, Theorems 6 and 7 yield an expression for the bias in terms of \(\alpha\) and \(R^2_{Y,\text{par}}\). In practice, we can estimate the bias induced by confounding by fitting models for \(\hat{Q}\) and \(\hat{g}\) and replacing the expectations by means over the data.

# 36.7.2.1 Calibration using observed data

The analyst must make judgments about the influence a hypothetical unobserved confounder might have on treatment assignment and outcome. To calibrate such judgments, we’d like to have a reference point for how much the observed covariates influence the treatment assignment and outcome. In the sensitivity model, the degree of influence is measured by partial \(R_Y^2\) and \(\alpha\). We want to measure the degree of influence of an observed covariate \(Z\) given the other observed covariates \(X \\backslash Z\).

For the outcome, this can be measured as:

$$
R^2_{Y \cdot Z|T, X \\backslash Z} \triangleq 1 - \frac{\mathbb{E}(Y - Q(A, X))^2}{\mathbb{E}(Y - \mathbb{E}[Y|A, X \\backslash Z])^2}.
$$