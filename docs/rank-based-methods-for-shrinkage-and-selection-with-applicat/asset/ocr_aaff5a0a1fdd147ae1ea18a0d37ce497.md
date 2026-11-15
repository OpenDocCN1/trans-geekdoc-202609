ADB\(\left(\hat{\beta}_n^{\text{ridgeR}}(\lambda)\right) = -\frac{\lambda \delta}{1+\lambda} = -\frac{\eta}{\sqrt{Q}}\frac{\lambda}{1+\lambda}\Delta\)

ADL\(_2\)\-risk\(\left(\hat{\beta}_n^{\text{ridgeR}}(\lambda)\right) = \frac{\eta^2}{\sqrt{Q}}\frac{1+\lambda^2\Delta^2}{(1+\lambda)^2}.\)

The optimum value of \(\lambda\) is \(\lambda_{opt} = \Delta^{-2}\). Hence,

ADL\(_2\)\-risk\((\hat{\beta}_n^{\text{ridgeR}}(\Delta^{-2})) = \frac{\eta^2}{Q}\frac{\Delta^2}{1+\Delta^2}.\)

Therefore,

ADRE\((\hat{\beta}_n^{\text{ridgeR}}(\Delta^{-2}) : \hat{\beta}_n^{\text{UR}}) = 1 + \frac{1}{\Delta^2}.\)

# 3.8.4 Hard-Threshold R-estimator of Slope

Using Section 3.6.1, we define the hard threshold R-estimator (HTRE) of the slope as follows,

\(\hat{\beta}_n^{\text{HTR}}(\lambda) = \hat{\beta}_n^{\text{UR}} I(|\hat{\beta}_n^{\text{UR}}| > \frac{\lambda}{\sqrt{n}}\frac{\eta}{\sqrt{Q_n}}). \quad (3.8.10)\)

Thus,

\(\sqrt{n}\hat{\beta}_n^{\text{HTR}}(\lambda) = \sqrt{n}\hat{\beta}_n^{\text{UR}} I(|\sqrt{n}\hat{\beta}_n^{\text{UR}}| > \frac{\lambda \eta}{\sqrt{Q_n}})\)
\(= \frac{\eta}{\sqrt{Q_n}} Z_n I(|Z_n| > \lambda).\)

**Theorem 3.13** Under the local alternative hypothesis, \(K_{(n)}\), the ADB and ADL\(_2\)-risk of the hard threshold R-estimator of \(\beta\) are

ADB\((\hat{\beta}_n^{\text{HTR}}(\lambda)) = -\frac{\eta}{\sqrt{Q}}\Delta \mathcal{H}_3(\lambda^2, \Delta^2)\)

ADL\(_2\)\-risk\((\hat{\beta}_n^{\text{HTR}}(\lambda)) = \frac{\eta^2}{Q} \rho_{\text{PT}}(\lambda, \Delta^2),\)

respectively, where

\(\rho_{\text{PT}}(\lambda, \Delta^2) = 1 - \mathcal{H}_3(\lambda^2, \Delta^2) + \Delta^2 \left( 2\mathcal{H}_3(\lambda^2, \Delta^2) - \mathcal{H}_5(\lambda^2, \Delta^2) \right)\)

and \(\mathcal{H}_\nu(\lambda^2, \Delta^2)\) is the c.d.f. of a \(\chi^2\)-distribution with \(\nu\) d.f.