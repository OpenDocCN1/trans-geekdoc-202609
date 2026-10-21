$$R_{\text{weekly}}^2 = \frac{\beta_{\text{daily}}^2 (1\ 1\ 1\ 1\ 1)\,\text{Var}(\mathbf{X})\begin{pmatrix}1\\1\\1\\1\\1\end{pmatrix}}{\beta_{\text{daily}}^2 (1\ 1\ 1\ 1\ 1)\,\text{Var}(\mathbf{X})\begin{pmatrix}1\\1\\1\\1\\1\end{pmatrix}+5\sigma^2}.\tag{114.23}$$

Substituting (114.20) into (114.23) yields that

$$R_{\text{weekly}}^2 = \frac{1}{1 + \frac{5\sigma^2}{\text{Var}(X_t)\left(5+8\rho_X^1+6\rho_X^2+4\rho_X^3+2\rho_X^4\right)\beta_{\text{daily}}^2}}.\tag{114.24}$$

And note that from equation (114.22), we have that

$$\frac{\sigma^2}{\beta_{\text{daily}}^2\,\text{Var}(X_t)} = \frac{1 - R_{\text{daily}}^2}{R_{\text{daily}}^2}.\tag{114.25}$$

Finally, we substitute (114.25) into (114.24) and obtain that

$$R_{\text{weekly}}^2 = \frac{R_{\text{daily}}^2}{R_{\text{daily}}^2 + k_{d-w}\left(1 - R_{\text{daily}}^2\right)},\tag{114.26}$$

where $k_{d-w}$ is the daily-to-weekly multiplier for $R^2$'s estimated by using daily data and weekly data:

$$k_{d-w} = \frac{1}{1 + \frac{8}{5}\rho_X^1 + \frac{6}{5}\rho_X^2 + \frac{4}{5}\rho_X^3 + \frac{2}{5}\rho_X^4}.\tag{114.27}$$

Thus, if $k_{d-w} < 1$, then $R_{\text{weekly}}^2 > R_{\text{daily}}^2$, which implies that the estimated goodness of fitness grows as the time interval increase. On the other hand, if $k_{d-w} > 1$, then $R_{\text{weekly}}^2 < R_{\text{daily}}^2$. It means that the estimation of $R^2$ using weekly data would be smaller than that estimated by daily data. In Section 112.3, we will provide empirical results concerning the change in the estimations of $R^2$'s when the investment horizon increase.