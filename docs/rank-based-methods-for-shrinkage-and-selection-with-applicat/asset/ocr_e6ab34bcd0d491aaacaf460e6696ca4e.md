**SCAD** Although the LASSO method does both shrinkage and variable selection due to the nature of the L1-penalty by setting many coefficients identically to zero, it does not possess oracle properties, as discussed in Fan and Li (2001). To overcome the inefficiency of traditional variable selection procedures, Fan and Li (2001) proposed smoothly clipped absolute deviation (SCAD) to select variables and estimate the coefficients of variables automatically and simultaneously. The SCAD R-estimator is defined as

$$\hat{\boldsymbol{\beta}}_n^{\text{scadR}} = \underset{\boldsymbol{\beta}}{\operatorname{argmin}} \left\{ D(\boldsymbol{\beta}) + \lambda \sum_{j=1}^p p_{\alpha, \lambda}(\beta_j) \right\}.$$

Here \(p_{\alpha, \lambda}(\cdot)\) is the SCAD penalty. It is a symmetric and quadratic spline on \([0, \infty)\) with knots at \(\lambda\) and \(\alpha\lambda\), whose first order derivative is given by

\(p_{\alpha, \lambda}(\beta) = \begin{cases} \lambda |\beta|, & |\beta| \le \lambda \\ -(\beta^2 - 2\alpha\lambda |\beta| + \lambda^2) / [2(\alpha - 1)], & \lambda < |\beta| \le \alpha\lambda \\ (\alpha + 1)\lambda^2 / 2 & |\beta| > \alpha\lambda \end{cases}\)

Here \(\lambda > 0\) and \(\alpha > 2\) are the tuning parameters. For \(\alpha = \infty\), the expression in this equation is equivalent to the L1-penalty.

**MCP** Zhang (2010) introduced a new penalization method called minimax concave penalty (MCP) for variable selection. The MCP R-estimator is given by

$$\hat{\boldsymbol{\beta}}_n^{\text{mcpR}} = \underset{\boldsymbol{\beta}}{\operatorname{argmin}} \left\{ D(\boldsymbol{\beta}) + \sum_{j=1}^p \rho(|\beta_j|; \lambda) \right\},$$

where \(\rho(\cdot; \lambda)\) is the MCP penalty given by

\(\rho(t; \lambda) = \lambda \int_0^T (1 - \frac{x}{\gamma \lambda})_+ \, dx\)

and \(\gamma > 0\) and \(\lambda\) are regularization and penalty parameters, respectively.

**Enet** The elastic net (Enet) was proposed by Zou and Hastie (2005) to overcome the limitations of the LASSO and ridge methods. The Enet R-estimator is defined as