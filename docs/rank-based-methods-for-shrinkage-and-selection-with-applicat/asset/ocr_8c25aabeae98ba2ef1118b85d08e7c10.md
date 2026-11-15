Because \( n^{\frac{1}{2}} L_n(\boldsymbol{\beta}^*) = O_p(1) \) and \( n^{\frac{1}{2}} |\hat{\beta}_j^{\text{UR}}| = O_p(1) \) for \( j = p_0 + 1, ..., p \), we have

\( n^{-\frac{1}{2}} \frac{\partial Q_n(\boldsymbol{\beta})}{\partial \beta_j} \bigg|_{\boldsymbol{\beta}=\boldsymbol{\beta}^*} = O_p(1) + n \lambda_n \frac{\text{sgn}(\beta_j^*)}{O_p(1)}, \quad j = p_0 + 1, ..., p. \quad (6.6.22) \)

Further, \( n \lambda_n \to \infty \), the sign of \( \frac{\partial Q_n(\boldsymbol{\beta})}{\partial \beta_j} \bigg|_{\boldsymbol{\beta}=\boldsymbol{\beta}^*} \) is the same as that of \( \hat{\beta}_j^* \neq 0, \quad j = p_0 + 1, ..., p \) as \( n \) is large enough. This implies that \( P(\boldsymbol{\beta}_2 = \boldsymbol{0}) \to 1 \). Coupled with the definition \( \hat{\boldsymbol{\beta}}_n^* \), we can show that

\(\begin{aligned} \frac{\partial Q_n(\boldsymbol{\beta})}{\partial \beta_j} \bigg|_{\boldsymbol{\beta}=\boldsymbol{\beta}^*} &= n^{-\frac{1}{2}} \boldsymbol{L}_{n_1} \begin{pmatrix} \hat{\boldsymbol{\beta}}_{1n}^* \\ \boldsymbol{0} \end{pmatrix} + \sqrt{n} \lambda_n \begin{pmatrix} \frac{\text{sgn}(\hat{\boldsymbol{\beta}}_1^{\text{UR}})}{|\hat{\boldsymbol{\beta}}_1^{\text{UR}}|} & \dots & \frac{\text{sgn}(\hat{\boldsymbol{\beta}}_{p_0}^{\text{UR}})}{|\hat{\boldsymbol{\beta}}_{p_0}^{\text{UR}}|} \end{pmatrix} \\ &= n^{-\frac{1}{2}} \boldsymbol{L}_{n_1} (\hat{\boldsymbol{\beta}}_{1n}^*) + \gamma(\phi, f) \boldsymbol{C}_{11} (\hat{\boldsymbol{\beta}}_{1n}^* - \boldsymbol{\beta}_1) \\ &+ n^{\frac{1}{2}} \lambda_n \begin{pmatrix} \frac{\text{sgn}(\hat{\boldsymbol{\beta}}_1^{\text{UR}})}{|\hat{\boldsymbol{\beta}}_1^{\text{UR}}|} & \dots & \frac{\text{sgn}(\hat{\boldsymbol{\beta}}_{p_0}^{\text{UR}})}{|\hat{\boldsymbol{\beta}}_{p_0}^{\text{UR}}|} \end{pmatrix} . \end{aligned}\)

Now, \( \sqrt{n} \lambda_n \to \lambda_0 \) and \( \hat{\beta}_j^{\text{UR}} \xrightarrow{P} \beta_j^* \neq 0 \) for \( j = 1, ..., p_0 \) and

\( n^{\frac{1}{2}} \gamma(\phi, f) \boldsymbol{C}_{11} ((\hat{\boldsymbol{\beta}}_{1n}^* - \boldsymbol{\beta}^*) + n^{-\frac{1}{2}} \gamma^{-1}(\phi, f) \boldsymbol{C}_{11}^{-1} \lambda_0 \boldsymbol{b}_1 = n^{-\frac{1}{2}} \boldsymbol{L}_{n_1} (\boldsymbol{\beta}^*) + o_p(1) . \)

Given that we have \( n^{\frac{1}{2}} \boldsymbol{L}_{n_1} (\boldsymbol{\beta}^*) \xrightarrow{D} \mathcal{N}_{p_0} \left( \boldsymbol{0}, A_{\phi}^2 \boldsymbol{C}_{11} \right) \), this leads to the result that \( \sqrt{n} (\hat{\boldsymbol{\beta}}_{1n}^* - \boldsymbol{\beta}_1) \xrightarrow{D} \mathcal{N}_{p_0} \left( \boldsymbol{0}, \eta^2 \boldsymbol{C}_{11}^{-1} \right) . \)

# ## 6.7 Summary

In this chapter, we considered the non-orthogonal multiple regression model. We provided comparative performance characteristics of the primary penalty estimators, namely, ridge, LASSO, elastic net and aLASSO together with the unrestricted, restricted, preliminary test and Stein–Saleh type R-estimators. We used the marginal distribution theory and asymptotic distributional L2-risk function to evaluate the estimators. We also detailed the oracle properties of aLASSO.