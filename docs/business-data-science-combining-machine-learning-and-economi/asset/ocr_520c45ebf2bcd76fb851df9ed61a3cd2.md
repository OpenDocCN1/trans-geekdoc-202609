Making life even simpler, consider the usual linear treatment model where *gp* = \u03b7p and Equation 5.23 becomes

$$\boldsymbol{\gamma}\boldsymbol{p}+\boldsymbol{e} \quad \text{(5.27)}$$

Combining this with Equation 5.25 yields the key equation for 2SLS:

$$\mathbb{E}[y|\boldsymbol{z}]=\boldsymbol{\gamma}\mathbb{E}[\boldsymbol{p}|\boldsymbol{z}] \quad \text{(5.28)}$$

Thus, you can estimate \u03b3 with a two-step algorithm (and any covariates \u2009*x* are just added to the conditioning set).

# **ALGORITHM 13  Two-Stage Least Squares (2SLS)**

+   \u2022  Fit the first-stage expectation \u2009$\u2009\mathbb{E}[\boldsymbol{p}~|~x_{i},\boldsymbol{z}]=\boldsymbol{\alpha}_{\boldsymbol{p}}+\boldsymbol{z}_{i}\boldsymbol{\tau}+\boldsymbol{x}_{i}^{\prime}\boldsymbol{\beta}_{\boldsymbol{p}}$\u2009 using OLS for \u2009* p* on \u2009*x* and \u2009* z*.

For each observed (*p*\u2009i, *x*\u2009i, *z*\u2009i, *y*\u2009i) tuple, this provides the *predicted* policy \u2009$\u2009\hat{\boldsymbol{p}}_{i}=\hat{\boldsymbol{\alpha}}_{\boldsymbol{p}}+\boldsymbol{z}_{i}\hat{\boldsymbol{\tau}}+\boldsymbol{x}_{i}^{\prime}\hat{\boldsymbol{\beta}}_{\boldsymbol{p}}$.

+   \u2022  Run a second-stage regression for your response onto the predicted policy and the covariates, using OLS to estimate:

$$\mathbb{E}[y|\hat{\boldsymbol{p}}_{i},\boldsymbol{x}_{i}]=\boldsymbol{\alpha}_{y}+\hat{\boldsymbol{p}}_{i}^{\prime}\boldsymbol{\gamma}+\boldsymbol{x}_{i}^{\prime}\boldsymbol{\beta}_{y} \quad \text{(5.29)}$$

You can then interpret the resulting \u2009*$\u2009\hat{\gamma}$* estimate as the *causal* effect of \u2009* p* on \u2009* y*.

In our earlier simulated pricing example, this algorithm proceeds in two simple steps. Recall that the observed prices were set as the sum of demand shocks and an independent random error: \u2009`p_observed = e + z`. Treating the \u2009* z* term as an observable instrument, we can run 2SLS: