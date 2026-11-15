

and $\hat{\boldsymbol{\beta}}_n^{\text{PTLiuR}}(d, \alpha)$ dominates $\hat{\boldsymbol{\beta}}_n^{\text{SSLiuR}}(d)$ when

$$
\Delta^2 > \Delta_2^2(\Delta^2, d, \alpha) = \frac{f_1(\Delta^2, d, \alpha)}{\text{Ch}_{\min}[(\mathbf{F}_d^\top \mathbf{F}_d \mathbf{C}^{-1}] \{Z(\alpha, \Delta^2) - (q - 2)Y(\Delta^2)\}},
$$

where $\text{Ch}_{\min}(\mathbf{A})$ and $\text{Ch}_{\max}(\mathbf{A})$ are the minimum and maximum characteristic roots of matrix $\mathbf{A}$.

Now, we consider the risk difference

$$
\text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{SSLiuR}}(d)) - \text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{PTLiuR}}(d))
$$

as a function of eigenvalues and define

$$
d_1(\Delta^2, \alpha) = \frac{f_2(\Delta^2, \alpha)}{g_1(\Delta^2, \alpha)},
$$

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

- (1) If $g_1(\Delta^2, \alpha) > 0$ and $f_2(\Delta^2, \alpha) > 0$, it follows that for each positive $d$ with $d < d_1(\Delta^2, \alpha)$, $\hat{\boldsymbol{\beta}}_n^{\text{SSLiuR}}(d)$ has risk value less than that of $\hat{\boldsymbol{\beta}}_n^{\text{PTLiuR}}(d, \alpha)$.

- (2) If $g_1(\Delta^2, \alpha) < 0$ and $f_2(\Delta^2, \alpha) < 0$, it follows that for each positive $d$ with $d > d_1(\Delta^2, \alpha)$, $\hat{\boldsymbol{\beta}}_n^{\text{SSLiuR}}(d)$ has risk value less than that of $\hat{\boldsymbol{\beta}}_n^{\text{PTLiuR}}(d, \alpha)$.

Under \(\mathcal{H}_o : \mathbf{H}\boldsymbol{\beta} = \mathbf{h}\), the risk difference reduces to

$$
\eta^2 \sum_{i=1}^p \frac{q_{ii}(\lambda_i + d)^2}{(\lambda_i + 1)^2} \{ \mathcal{H}_{q+2}(\chi_{q,\alpha}^2; 0) - (q - 2)X(0) \},
$$

where

$$
\mathcal{H}_{q+2}(\chi_{q,\alpha}^2; 0) = \chi_{q+2}^2(\frac{q\chi_{q,\alpha}^2}{q+2}; 0) = 1 - \alpha.
$$

Thus, the risk of $\widehat{\boldsymbol{\beta}}_n^{\text{SSLiuR}}(d)$ is smaller than that of $\widehat{\boldsymbol{\beta}}_n^{\text{PTLiuR}}(d, \alpha)$ when the critical value $\chi_{q,\alpha}^2$ satisfies

$$
\chi_{q,\alpha}^2 \le \frac{q+2}{q} \chi_{q+2}^{-2}((q-2)X(0)).
$$

Otherwise, the risk of $\widehat{\boldsymbol{\beta}}_n^{\text{PTLiuR}}(d, \alpha)$ is smaller than the risk of $\widehat{\boldsymbol{\beta}}_n^{\text{SSLiuR}}(d)$.

### Remark 8.1
For $\alpha = 1$, we will have the comparison between SSlre and ULRE and, for $\alpha = 0$, we will have comparison between SSlre and RLRE.

## 8.5.2 Comparison of PRLSRE and PTLRE

### Case 1. Under the null hypothesis, \(\mathcal{H}_o : \mathbf{H}\boldsymbol{\beta} = \mathbf{h}\).

The risk difference is

$$
\text{ADL}_2\text{-risk}(\widehat{\boldsymbol{\beta}}_n^{\text{SSLiuR+}}(d)) - \text{ADL}_2\text{-risk}(\widehat{\boldsymbol{\beta}}_n^{\text{PTLiuR}}(d)) = \sum_{i=1}^p \frac{q_{ii}(\lambda_i + d)^2 \eta^2}{(\lambda_i + 1)^2} \times \{ \mathcal{H}_{q+2}(\chi_{q,\alpha}^2; 0) - (q - 2)X(0) - \mathbb{E}\left[ (1 - (q - 2)\chi_{q+2}^{-2}(0))^2 I(\chi_{q,\alpha}^2 \le q - 2) \right] \} \ge 0
$$

for all $\alpha$ satisfying the condition

$$
\left\{ \alpha : \chi_{q,\alpha}^2 \ge \mathcal{H}_{q+2}\left( (q - 2)X(0) + \mathbb{E}\left[ (1 - (q - 2)\chi_{q+2}^{-2}(0))^2 I(\chi_{q+2}^2(0) \le q - 2) \right] ; 0 \right) \right\}. \quad (8.5.2)
$$

Thus, the risk of PTLRE is smaller than that of PRLRE when the critical value $\chi_{q,\alpha}^2$ satisfies the relation in Eq. (8.5.2). However, the risk of PRLRE is smaller than that of PTLRE when the critical value $\chi_{q,\alpha}^2$ satisfies the opposite relation to Eq. (8.5.2).

### Case 2. When the null hypothesis does not hold.

The risk difference \(\text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{SSLiuR+}}(d)) - \text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{PTLiuR}}(d))\) will be non-positive when

$$
\eta^T F_d^T F_d \eta \ge \frac{f_3(\Delta^2, d, \alpha)}{g_2(\Delta^2, \alpha)} \tag{8.5.3}
$$

where

$$
f_3(\Delta^2, d, \alpha) = \eta^2 \text{tr}(F_d A F_d^T) \{ \mathcal{H}_{q+2}(\chi_{q,\alpha}^2; \Delta^2) - (q-2)X(\Delta^2) + a_1 \} -2(1-d)\eta^T F_d^T (C + I_p)^{-1} \beta \{ (q-2) E(\chi_{q+2}^{-2}(\Delta^2)) - \mathcal{H}_{q+2}(\chi_{q,\alpha}^2; \Delta^2) - a_3 \}
$$

and

$$
g_2(\Delta^2, \alpha) = Z(\alpha, \Delta^2) - (q-2)Y(\Delta^2) + a_2 + 2a_3.
$$

Also,

$$
\begin{aligned}
a_1 &= \mathbb{E} \left[ \left( 1 - (q-2)\chi_{q+2}^{-2}(\Delta^2) \right)^2 I \left( \chi_{q+2}^2(\Delta^2) \le q-2 \right) \right] \\
a_2 &= \mathbb{E} \left[ \left( 1 - (q-4)\chi_{q+4}^{-2}(\Delta^2) \right)^2 I \left( \chi_{q+4}^2(\Delta^2) \le q-4 \right) \right] \\
a_3 &= \mathbb{E} \left[ \left( (q-2)\chi_{q+2}^{-2}(\Delta^2) - 1 \right) I \left( \chi_{q+2}^2(\Delta^2) \le q-2 \right) \right].
\end{aligned}
$$

Since \(\Delta^2 > 0\), assume that both the numerator and the denominator of Eq. (8.5.3) are positive or negative, respectively. Then \(\hat{\boldsymbol{\beta}}_n^{\text{SSLiuR+}}(d)\) dominates \(\hat{\boldsymbol{\beta}}_n^{\text{PTLiuR}}(d, \alpha)\) when

$$
\Delta^2 \le \Delta_3^2(\Delta^2, d, \alpha) = \frac{f_3(\Delta^2, d, \alpha)}{\text{Ch}_{\max}[(F_d^T F_d) C^{-1}] \times g_2(\Delta^2, \alpha)},
$$

and \(\hat{\boldsymbol{\beta}}_n^{\text{PTLiuR}}(d, \alpha)\) dominates \(\hat{\boldsymbol{\beta}}_n^{\text{SSLiuR+}}(d)\) when

$$
\Delta^2 > \Delta_4^2(\Delta^2, d, \alpha) = \frac{f_3(\Delta^2, d, \alpha)}{\text{Ch}_{\min}[(F_d^T F_d) C^{-1}] \times g_2(\Delta^2, \alpha)}.
$$

Now, we consider the risk difference of PRLRE and PTLRE as a function of the eigenvalues and define

$$
d_2(\Delta^2, \alpha) = \frac{f_4(\Delta^2, \alpha)}{g_3(\Delta^2, \alpha)},
$$

where

$$
f_4(\Delta^2, \alpha) = \max_i \{ \lambda_i q_{ii} P_1 + \lambda_i \eta_i^{*2} P_2 + \theta_i \eta_i^{*} P_3 \}
$$

and

$$
g_3(\Delta^2, \alpha) = \min_i \left\{ 2 + \theta_i \lambda_i \eta_i^\star P_3 - \lambda_i q_{ii} P_1 - \lambda_i \eta_i^{\star 2} P_2 \right\}.
$$

Also,

$$
\begin{aligned}
P_1 &= \mathcal{H}_{q+2}(\chi_{q,\alpha}^2 ; \Delta^2) - (q-2)X(\Delta^2) + a_1, \\
P_2 &= (q-2)Y(\Delta^2) - a_2 - 2a_3 - Z(\alpha, \Delta^2), \\
P_3 &= (q-2)\mathbb{E}\left[ \chi_{q+2}^{-2}(\Delta^2) \right] - a_3 - \mathcal{H}_{q+2}(\chi_{q,\alpha}^2 ; \Delta^2) - (q-2)X(\Delta^2).
\end{aligned}
$$

Suppose that \( d > 0 \). Then, we have the following statements.

- (1) If \( g_3(\Delta^2, \alpha) > 0 \) and \( f_4(\Delta^2, \alpha) > 0 \), it follows that for each positive \( d \) with \( d > d_2(\Delta^2, \alpha) \), \( \hat{\boldsymbol{\beta}}_n^{\text{SSLiuR+}}(d) \) has risk value less than that of \( \hat{\boldsymbol{\beta}}_n^{\text{PTLiuR}}(d, \alpha) \).

- (2) If \( g_3(\Delta^2, \alpha) < 0 \) and \( f_4(\Delta^2, \alpha) < 0 \), it follows that for each positive \( d \) with \( d < d_2(\Delta^2, \alpha) \), \( \hat{\boldsymbol{\beta}}_n^{\text{SSLiuR+}}(d) \) has risk value less than that of \( \hat{\boldsymbol{\beta}}_n^{\text{PTLiuR}}(d, \alpha) \).

### Remark 8.2
For \( \alpha = 0 \), we obtain the superiority condition of \( \hat{\boldsymbol{\beta}}_n^{\text{SSLiuR+}}(d) \) over \( \hat{\boldsymbol{\beta}}_n^{\text{RLiuR}}(d) \) and, for \( \alpha = 1 \), we obtain the superiority condition of \( \hat{\boldsymbol{\beta}}_n^{\text{SSLiuR+}}(d) \) over \( \hat{\boldsymbol{\beta}}_n^{\text{ULiuR}}(d) \).

## 8.5.3 Comparison of PRLRE and SSLRE

In this case, we have

$$
\begin{aligned}
\text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{SSLiuR+}}(d)) - \text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{SSLiuR}}(d)) = {} & \\
& -\eta^2 \left\{ \text{tr}(\mathbf{F}_d^\top \mathbf{A} \mathbf{F}_d) \mathbb{E} \left[ \left( 1 - (q-2) \chi_{q+2}^{-2}(\Delta^2) \right)^2 I(\chi_{q+2}^2(\Delta^2) \le q-2) \right] \right. \\
& \left. + \eta^2 (\eta^\top \mathbf{F}_d^\top \mathbf{F}_d \eta) \mathbb{E} \left[ \left( 1 - (q-2) \chi_{q+4}^{-2}(\Delta^2) \right)^2 I(\chi_{q+4}^2(\Delta^2) \le q-2) \right] \right\} \\
& - 2 (\eta^\top \mathbf{F}_d^\top \mathbf{F}_d \eta) \mathbb{E} \left[ \left( (q-2) \chi_{q+2}^{-2}(\Delta^2) - 1 \right) I(\chi_{q+2}^2(\Delta^2) \le q-2) \right] \\
& - 2(1-d) \eta^\top \mathbf{F}_d^\top (\mathbf{C} + \mathbf{I}_p)^{-1} \beta \\
& \times \mathbb{E} \left[ \left( (q-2) \chi_{q+2}^{-2}(\Delta^2) - 1 \right) I(\chi_{q+2}^2(\Delta^2) \le q-2) \right].
\end{aligned} \tag{8.5.4}

