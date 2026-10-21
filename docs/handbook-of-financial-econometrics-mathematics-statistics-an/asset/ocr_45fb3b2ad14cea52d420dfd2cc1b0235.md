consistent estimators. The first method is the two stage least square (2SLS) estimator, and the other is the maximum likelihood estimator (MLE).

One can reformulate the above model by considering periods of rising prices $\Delta P_t>0$ and periods of falling prices $\Delta P_t<0$. As a result, in the period with rising prices, the supply function (99.8) can be estimated using the observed quantity, $Q_t$, as the dependent variable since there will be excess demand and thus, $Q_t$ will be equal to $Q_{S,t}$. Thus, the disequilibrium system described as equations (99.7)–(99.10) can be reformulated and summarized as the following equations:

$$Q_t=\alpha_1P_t+\beta_1'X_{D,t}-\frac{1}{\gamma}\Delta P_t^+ +\mu_t, \tag{99.15a}$$

$$Q_t=\alpha_1P_t+\beta_2'X_{S,t}-\frac{1}{\gamma}\Delta P_t^- +\nu_t. \tag{99.15b}$$

$$\Delta P_t^+=\begin{cases}\Delta P_t & \text{if }\Delta P_t>0,\\0 & \text{otherwise,}\end{cases}$$

where

$$\Delta P_t^- =\begin{cases}-\Delta P_t & \text{if }\Delta P_t<0,\\0 & \text{otherwise}\end{cases}$$

Two alternative methods (two-stage least squares (2SLS), and MLE) for estimating the above disequilibrium model are also proposed in the following sections.

# 99.4.2  *Two-stage least squares (2SLS) estimator*

The equations system shown in (99.15) contains the jointly dependent variables $Q_t$, $P_t$, $\Delta P_t^+$, and $\Delta P_t^-$. The parameters in the modified model can be consistently estimated by conventional two-stage least squares (2SLS) method. This can be briefly described as the following two stages. In the first stage, regress $\Delta P_t^+$ and $\Delta P_t^-$ on all the exogenous variables, $X_{D,t}$ and $X_{S,t}$ to obtain the estimates of $\widehat{\Delta P_t^+}$ and $\widehat{\Delta P_t^-}$, in the second stage, regress $Q_t$ on $X_{1t}$ and $\widehat{\Delta P_t^+}$ in equation (99.15a), and regress $Q_t$ on $X_{2t}$ and $\widehat{\Delta P_t^-}$ in equation (99.15b). However, the estimators of $\hat{\alpha}_1$, $\hat{\alpha}_2$, $\hat{\beta}_1$ and $\hat{\beta}_2$ are not asymptotically efficient in this model, though could be consistent if the predictions of the endogenous variables are used for all observations.⁷

⁷ Amemiya shows that the Two-Stage Least Squares (2SLS) estimators proposed by Fair and Jaffee are not consistent since the expected value of error in first equation, $E\mu_t$ given $t$ belonging to period B is not zero, or, according to Quandt, the plim $X_a'\mu_a/T$ is not zero (see Amemiya, 1974; Quandt, 1988).