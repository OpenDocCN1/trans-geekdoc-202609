The resulting MR factors *v* are shown in Figure 7.20. The in-sample $R_2$ is around 30%. This is the combined signal available using only the *marginal* correlations (i.e., univariate correlations) between each NIR measurement and the octane.

![](bbox=[0.22, 0.19, 0.83, 0.39])

FIGURE 7.20: Fitted MR factors *v* (i.e., the first PLS direction) versus octane *y*.

PARTIAL LEAST SQUARES IS AN EXTENSION OF MARGINAL REGRESSION. Instead of stopping after running the single MR, you iterate: take the *residuals* from the first MR and repeat a second MR to predict these residuals. You can then take the residuals from the second MR and repeat, continuing until you reach the minimum of *p* and *n*.

# **ALGORITHM 21** Partial Least Squares (PLS)

Begin by running MR from Algorithm 20 for *y* on *x*. Store the MR factor as $v_1$, the 1st PLS direction, and PLS(1) forward regression fitted values as $\hat{y}_1 = \alpha + \beta_1 \cdot v_1$. Then, for $k = 2 \ldots K$, calculate the following:

+   * Residuals $\hat{v}_i^{k-1} = y_i - \hat{y}_i^{k-1}$
* Loadings
$\boldsymbol{\varphi}_k$ via $\varphi_{kj} = \text{cor}(x_j, \hat{y}_i^{k-1})/\text{sd}(x_j)$ and factors $v_i^k = x_i'\boldsymbol{\varphi}_k$
* Fitted values $\hat{y}_i^k = \hat{y}_i^{k-1} + \beta_k \, v_i^k$ where $\beta_k = \text{cor } (v_i^k, \hat{y}^{k-1})/\text{sd } (v_i^k)$

This yields PLS rotations $\Phi = [\varphi_1 \ldots \varphi_K]$ and factors $V = [v_1 \ldots v_K]$.