and $\hat{\boldsymbol{\beta}}_n^{\text{PTLiuR}}(d, \alpha)$ dominates $\hat{\boldsymbol{\beta}}_n^{\text{SSLiuR}}(d)$ when

$\Delta^2 > \Delta_2^2(\Delta^2, d, \alpha) = \frac{f_1(\Delta^2, d, \alpha)}{\text{Ch}_{\min}[(\mathbf{F}_d^\top \mathbf{F}_d \mathbf{C}^{-1}] \{Z(\alpha, \Delta^2) - (q - 2)Y(\Delta^2)\}},$

where $\text{Ch}_{\min}(\mathbf{A})$ and $\text{Ch}_{\max}(\mathbf{A})$ are the minimum and maximum characteristic roots of matrix $\mathbf{A}$.

Now, we consider the risk difference

$\text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{SSLiuR}}(d)) - \text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{PTLiuR}}(d))$

as a function of eigenvalues and define

$d_1(\Delta^2, \alpha) = \frac{f_2(\Delta^2, \alpha)}{g_1(\Delta^2, \alpha)},$

where

$$
\begin{aligned}
f_2(\Delta^2, \alpha) = & \max_i \left\{ \lambda_i \eta_i^{\star 2} \{ Z(\alpha, \Delta^2) - (q - 2)Y(\Delta^2) \} \right. \\
& \left. - \eta^2 q_{ii} \{ \mathcal{H}_{q+2}(\chi_{q,\alpha}^2; \Delta^2) - (q - 2)X(\Delta^2) \} \right. \\
& \left. + 2\theta_i \eta_i^{\star 2} \{ \mathcal{H}_{q+2}(\chi_{q,\alpha}^2; \Delta^2) - (q - 2)\mathbb{E}(\chi_{q+2}^{-2}(\Delta^2)) \} \right\}
\end{aligned}
$$

and

$$
\begin{aligned}
g_1(\Delta^2, \alpha) = & \min_i \left\{ \tau_y^2 q_{ii} \{ \mathcal{H}_{q+2}(\chi_{q,\alpha}^2; \Delta^2) - (q - 2)X(\Delta^2) \} \right. \\
& \left. - \eta_i^{\star 2} \{ Z(\alpha, \Delta^2) - (q - 2)Y(\Delta^2) \} \right. \\
& \left. + 2\theta_i \eta_i^{\star 2} \{ \mathcal{H}_{q+2}(\chi_{q,\alpha}^2; \Delta^2) - (q - 2)\mathbb{E}(\chi_{q+2}^{-2}(\Delta^2)) \} \right\}.
\end{aligned}
$$

Suppose that $d > 0$. Then, we have the following:

+   (1) If $g_1(\Delta^2, \alpha) > 0$ and $f_2(\Delta^2, \alpha) > 0$, it follows that for each positive $d$ with $d < d_1(\Delta^2, \alpha)$, $\hat{\boldsymbol{\beta}}_n^{\text{SSLiuR}}(d)$ has risk value less than that of $\hat{\boldsymbol{\beta}}_n^{\text{PTLiuR}}(d, \alpha)$.

+   (2) If $g_1(\Delta^2, \alpha) < 0$ and $f_2(\Delta^2, \alpha) < 0$, it follows that for each positive $d$ with $d > d_1(\Delta^2, \alpha)$, $\hat{\boldsymbol{\beta}}_n^{\text{SSLiuR}}(d)$ has risk value less than that of $\hat{\boldsymbol{\beta}}_n^{\text{PTLiuR}}(d, \alpha)$.