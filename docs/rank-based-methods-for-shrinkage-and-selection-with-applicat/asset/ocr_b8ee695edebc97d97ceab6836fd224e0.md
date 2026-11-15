\(\boldsymbol{L}_{n(2)}(\boldsymbol{\beta}_1, \boldsymbol{\beta}_2) = (\boldsymbol{L}_{n_{p+1}}(\boldsymbol{\beta}_1, \boldsymbol{\beta}_2), \dots, \boldsymbol{L}_{n_p}(\boldsymbol{\beta}_1, \boldsymbol{\beta}_2))^{\top}.\)

Let

\(\dot{\boldsymbol{L}}_{n(2)}(\hat{\boldsymbol{\beta}}_{1n}^{\text{UR}}, \mathbf{0}) = (\dot{\boldsymbol{L}}_{n_{p+1}}(\hat{\boldsymbol{\beta}}_{1n}^{\text{UR}}, \mathbf{0}), \dots, \dot{\boldsymbol{L}}_{n_p}(\hat{\boldsymbol{\beta}}_{1n}^{\text{UR}}, \mathbf{0}))^{\top}.\) (6.4.6)

Then, we propose the following test statistic

\(\mathcal{L}_n = A_n^{-2} \dot{\boldsymbol{L}}_{n(2)}^{\top}(\hat{\boldsymbol{\beta}}_{1n}^{\text{UR}}, \mathbf{0}) \boldsymbol{C}_{22 \cdot 1}^{-1} \dot{\boldsymbol{L}}_{n(2)}(\hat{\boldsymbol{\beta}}_{1n}^{\text{UR}}, \mathbf{0}),\) (6.4.7)

where

\(A_n^2 = \frac{1}{n-1} \sum_{i=1}^n (a_n(i) - \bar{a}_n)^2, \quad \bar{a}_n = \frac{1}{n} \sum_{i=1}^n a_n(i).\)

Note that \(\mathcal{L}_n\) may be approximated as

\(\mathcal{L}_n \overset{\mathcal{D}}{=} \frac{\gamma^2(\boldsymbol{\phi}, f)}{A_{\phi}^2} \eta \hat{\boldsymbol{\beta}}_{1n}^{\text{UR}\top} \boldsymbol{C}_{22 \cdot 1} \hat{\boldsymbol{\beta}}_{1n}^{\text{UR}} + o_p(1)\)

Under the assumed regularity conditions of Eq. (6.2.6) as \(n \to \infty\), \(\mathcal{L}_n\) follows the \(\chi^2\) distribution with \(p_2\) d.f. under \(\mathcal{H}_0\).

We will find that

\(\text{ADB}(\hat{\boldsymbol{\beta}}_n^{\text{PTR}}(\lambda)) = \begin{pmatrix} \mathbf{0}_{p_1} \\ -\delta_2 \mathcal{H}_{p_2+2}(\lambda^2, \Delta^2) \end{pmatrix}\) (6.4.8)

and

\(\text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{PTR}}(\lambda)) = \eta^2 \left( \text{tr}(\boldsymbol{C}_{11 \cdot 2}^{-1}) + \text{tr}(\boldsymbol{C}_{22 \cdot 1}^{-1}) \left( 1 - \mathcal{H}_{p_2+2}(\lambda^2, \Delta^2) \right) + \eta^{-2} \delta_2^\top \delta_2 Z(\lambda, \Delta) \right)\) (6.4.9)

where

\(Z(\lambda, \Delta) = 2 \mathcal{H}_{p_2+2}(\lambda^2, \Delta^2) - \mathcal{H}_{p_2+4}(\lambda^2, \Delta^2).\) (6.4.10)

Hence, the lower bound is given by

\(\text{ADL}_2^*\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{PTR}}(\lambda)) = \eta^2 \left( \text{tr}(\boldsymbol{C}_{11 \cdot 2}^{-1}) + \text{tr}(\boldsymbol{C}_{22 \cdot 1}^{-1}) (1 - \mathcal{H}_{p_2+2}(\lambda^2, \Delta^2)) + \Delta^2 \text{Ch}_{\min}(\boldsymbol{C}_{22 \cdot 1}^{-1}) Z(\lambda, \Delta) \right)\)