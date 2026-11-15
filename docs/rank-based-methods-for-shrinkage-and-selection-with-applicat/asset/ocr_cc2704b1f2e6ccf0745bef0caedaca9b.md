+\lambda^2 \alpha \left( 1 - \mathcal{H}_1(\lambda^2 \alpha^2, \Delta_j^2) \right) + \lambda^2(1 - \alpha)^2
-2\lambda \alpha \left( \phi(\lambda \alpha - \Delta_j) + \phi(\lambda \alpha + \Delta_j) \right)
+2\lambda(1 - \alpha) \Delta_j \left( \Delta_j \mathcal{H}_3(\lambda \alpha, \Delta_j^2) \right)
-\lambda \alpha \left( \Phi(\lambda \alpha - \Delta_j) - \Phi(\lambda \alpha + \Delta_j) \right) \right\} \} \} \ge 1.

For \alpha = 0,

ADL_2\text{-risk}(\hat{\beta}_n^{nEnetR}(\lambda, 0)) = \eta^2 \left[ \sum_{j=1}^p \frac{1 + \lambda^2}{\kappa_j Q_j (1 + \lambda \kappa_j Q_j)^2} \right]

and for \alpha = 1,

ADL_2\text{-risk}(\hat{\beta}_n^{nEnetR}(\lambda, 1)) = \eta^2 \left[ \sum_{j=1}^p \frac{1}{\kappa_j Q_j} \left\{ \left( 1 - \mathcal{H}_3(\lambda^2, \Delta_j^2) \right) \right. \right.
\left. \left. + \Delta_j \left( 2 \mathcal{H}_3(\lambda, \Delta_j^2) - \mathcal{H}_5(\lambda, \Delta_j^2) \right) \right. \right.
\left. + \lambda^2 \left( 1 - \mathcal{H}_1(\lambda^2, \Delta_j^2) \right) \right. \right.
\left. - 2\lambda \left( \phi(\lambda - \Delta_j) + \phi(\lambda + \Delta_j) \right) \right\} \right].

Alternatively, we can use the lower bound of ADL_2-risk of \hat{\beta}_n^{nEnet}(\lambda, \alpha) given by

ADL_2^*\text{-risk}(\hat{\beta}_n^{nEnetR}(\lambda, \alpha)) = \eta^2 \left( \text{tr}(D_{22}^{[1]}) + \Delta^2 \text{Ch}_{\min}(D_{22}^{[2]}) \right). \quad (5.5.2)

Then,

ADRE(\hat{\beta}_n^{nEnetR}(\lambda, \alpha) : \hat{\beta}_n^{UR}) = \left( 1 + \frac{\text{tr}(D_{22}^{[2]})}{\text{tr}(D_{22}^{[1]})} \right) \left( 1 + \frac{\Delta^2 \text{Ch}_{\min}(D_{22}^{[2]})}{\text{tr}(D_{22}^{[1]})} \right)^{-1}.

# 5.6 R-estimator of Intercept When Slope Has Sparse Subset

From Section 5.2, we know that

\begin{pmatrix} \sqrt{n}(\hat{\theta}_n^{UR} - \theta) \\ \sqrt{n}(\hat{\beta}_n^{UR} - \beta) \end{pmatrix} \sim N_{2p} \left( \begin{pmatrix} 0 \\ 0 \end{pmatrix}, \eta^2 \begin{pmatrix} D_{11} & -T_0 D_{22} \\ -T_0' D_{22} & D_{22} \end{pmatrix} \right) \quad (5.6.1)