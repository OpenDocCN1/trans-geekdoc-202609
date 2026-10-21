$$Z_i = d + X_i + v_i, \tag{37.35}$$

in which $Y_i$, $W_i$, and $Z_i$ are observable for $i = 1, \dots, n$, while $X_i$, $e_i$, and $v_i$ are unobservable. Equations (37.34) and (37.35) imply that

$$Y_i = \alpha + b'W_i + cZ_i + \varepsilon_i. \tag{37.36}$$

However, since both $Z_i$ and $\varepsilon_i$ depend on $v_i$, estimators of $b$ and $c$ from OLS regression is inconsistent. Lewbel (1997) shows that the consistent estimators can be obtained by using TSLS with instruments 1, $W_i$, and $q_i$, where $q_i$ is some vector of instruments that are correlated with $X_i$ but not correlated with $e_i$ and $v_i$. $q_i$ can be chosen as

+   - $q_{1i} = (G_i - \bar{G})$\n- $q_{2i} = (G_i - \bar{G})(Z_i - \bar{Z})$\n- $q_{3i} = (G_i - \bar{G})(Y_i - \bar{Y})$\n- $q_{4i} = (Y_i - \bar{Y})(Z_i - \bar{Z})$\n- $q_{5i} = (Z_i - \bar{Z})^2$\n- $q_{6i} = (Y_i - \bar{Y})^2$

where $G_i = G(W_i)$ for any given function $G$ and $\bar{S}$ denote the sample mean of variables $S_i$ ($S_i$ can be $Y_i$, $Z_i$, or $G_i$).

Lewbel (1997) further empirically applies the instrumental variable method to testing elasticity of patent applications with respect to research and development (R&D) expenditures. He finds, using the TSLS instrumental variable model, the estimated elasticity yields very close to one. Therefore, the TSLS instrumental variable model can mitigate the effects of measurement error and confirm the relationship between patent and R&D.

In addition, Erickson and Whited (2000, 2002) propose a two-step generalized method of moments (GMM) estimators that exploit over-identifying information contained in the high-order moments of residuals obtained from perfectly measured regressors. Basing GMM estimation on residual moments of more than second order requires that the GMM covariance matrix be explicitly adjusted to account for the fact that estimated residuals are used instead of true residuals defined by population regressions. Erickson and Whited (2000) show that estimators obtained by using moments up to seventh order perform well in Monte Carlo simulations.

Almeida et al. (2010) use Monte Carlo simulations and empirically test investment models to compare the performance of the instrumental variables