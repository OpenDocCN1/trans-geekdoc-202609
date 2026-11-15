

使用 \( Z_n = \sqrt{n}\hat{\theta}_n^{UR}/\eta \)，硬阈值 R-估计量 \( \theta \) 的定义可以改写为

\[ \sqrt{n}\hat{\theta}_n^{HTR}(\lambda) = \eta Z_n I(|Z_n| > \lambda). \]

### 定理 3.6
在局部备择假设下，\( K_{(n)} \)，\( \theta \) 的硬阈值 R-估计量（即 \( \hat{\theta}_n^{HTR}(\lambda) \)）的 ADB、ADV 和 ADL\(_2\)-风险为

\(\text{ADB}(\hat{\theta}_n^{HTR}(\lambda)) = -\eta\Delta\mathcal{H}_3(\lambda^2, \Delta^2),\)

\(\text{ADV}(\hat{\theta}_n^{HTR}(\lambda)) = \eta^2[1 - \mathcal{H}_3(\lambda^2, \Delta^2) - \Delta^2\mathcal{H}_3^2(\lambda^2, \Delta^2) + \Delta^2(2\mathcal{H}_3(\lambda^2, \Delta^2) - \mathcal{H}_5(\lambda^2, \Delta^2)) ],\)

\(\text{ADL}_2\text{-risk}(\hat{\theta}_n^{HTR}(\lambda)) = \eta^2\rho_{PT}(\lambda, \Delta^2),\)

respectively, where

\(\rho_{PT}(\lambda, \Delta^2) = 1 - \mathcal{H}_3(\lambda^2, \Delta^2) + \Delta^2(2\mathcal{H}_3(\lambda^2, \Delta^2) - \mathcal{H}_5(\lambda^2, \Delta^2))\)

and \( \mathcal{H}_\nu(\lambda^2, \Delta^2) \) is the c.d.f. of a \( \chi^2 \)-distribution with \( \nu \) d.f.

如果在初步检验 R-估计量中将 \( \chi^2_1(\alpha) \) 替换为 \( \lambda^2 \)，则将得到硬阈值 R-估计量。由于 \( \hat{\theta}_n^{HTR}(\lambda) \) 实际上与 \( \hat{\theta}_n^{PTR}(\alpha) \) 相同，我们跳过证明。

One may use \( \lambda^* = \sqrt{2 \ln(2)} \) which is the minimax value of \( \lambda \) to compute the ADRE of \( \hat{\theta}_n^{HTR}(\lambda^*) \) w.r.t. \( \hat{\theta}_n^{UR} \), i.e.

\(\text{ADRE}\left( \hat{\theta}_n^{HTR}(\lambda^*) : \hat{\theta}_n^{UR} \right) = \rho_{PT}^{-1}(\lambda^*, \Delta).\)

See Saleh et al. (2019) for details of the choice \( \lambda^* \). Figure 3.3 shows the ADRE function of the HT (or PT) R-estimator for different \( \Delta^2 \) values. From this figure, it is obvious that the PTRE has a better performance than the unrestricted R-estimation in the case of \( \Delta^2 \le 0.6 \) and vice versa when \( \Delta^2 > 0.6 \). Also, as \( \Delta^2 \) goes to \( \infty \), the estimator behaves like the unrestricted case.

## 3.6.2 Saleh-type R-estimator of \( \theta \)

Again, following the spirit of Sections 3.3 and 3.5, we define a continuous version of PTRE, namely the Saleh-type R-estimator (SRE), denoted by \( \hat{\theta}_n^{SR}(\lambda) \), and given by

![](img/f3b106d7e76ae3afcec8895afa28732c_156_0.png)

**Figure 3.3** The ADRE of the preliminary test (or hard threshold) R-estimator for different \(\Delta^2\) based on \(\lambda^* = \sqrt{2\ln(2)}\).

\(\hat{\theta}_n^{\text{SR}}(\lambda) = \hat{\theta}_n^{\text{UR}}(1 - \frac{\lambda}{\sqrt{\mathcal{L}_n}}) = \hat{\theta}_n^{\text{UR}} - \lambda\eta \frac{\hat{\theta}_n^{\text{UR}}}{|\sqrt{n}\hat{\theta}_n^{\text{UR}}|}.\) (3.6.2)

This can be rewritten as

\(\begin{aligned} \sqrt{n}\hat{\theta}_n^{\text{SR}}(\lambda) &= \sqrt{n}\hat{\theta}_n^{\text{UR}} - \lambda\eta \frac{\sqrt{n}\hat{\theta}_n^{\text{UR}}}{|\sqrt{n}\hat{\theta}_n^{\text{UR}}|} \\ &= \eta \left(1 - \frac{\lambda}{|Z_n|}\right) Z_n = \eta(Z_n - \lambda \text{sgn}(Z_n)) \end{aligned}\) (3.6.3)

with \(Z_n = \sqrt{n}\hat{\theta}_n^{\text{UR}}/\eta \sim \mathcal{N}(\Delta, 1)\).

### Theorem 3.7
Under the local alternative, \(K_{(n)}\), the ADB and \(\text{ADL}_2\text{-risk}\) of the Saleh-type R-estimator of \(\theta\) are

\(\text{ADB}(\hat{\theta}_n^{\text{SR}}(\lambda)) = -\eta\lambda [2\Phi(\Delta) - 1],\)

and

\(\text{ADL}_2\text{-risk}(\hat{\theta}_n^{\text{SR}}(\lambda)) = \eta^2 \left[ 1 + \lambda^2 - 2\lambda \sqrt{\frac{2}{\pi}} \exp \left\{ -\frac{\Delta^2}{2} \right\} \right].\)

Table 3.3 The ADRE values of the Saleh-type R-estimator for \(\lambda^*_{\max} = \sqrt{\frac{2}{\pi}}\) and different \(\Delta^2\).

| \(\Delta^2\) | 0 | 0.05 | 0.1 | 0.5 | 1 | 2ln(2) | 2 | 5 | 10 |
|---|---|---|---|---|---|---|---|---|---|
| ADRE | 2.75 | 2.53 | 2.35 | 1.55 | 1.16 | 1.00 | 0.86 | 0.65 | 0.61 |

### Corollary 3.2
The optimum value of \(\lambda\) is

\(\lambda^* = \sqrt{\frac{2}{\pi}} \exp \left\{ -\frac{\Delta^2}{2} \right\},\)

with a maximum \(\lambda^*_{\max} = \sqrt{\frac{2}{\pi}}\) at \(\Delta^2 = 0\).

Thus, the optimum value is

\(\text{ADL}_2\text{-risk}(\hat{\vartheta}^{\text{SR}}_n(\lambda^*_{\max})) = \eta^2 \left[ 1 - \frac{2}{\pi} \left( 2 \exp \left\{ -\frac{\Delta^2}{2} \right\} - 1 \right) \right].\)

The ADRE of \(\hat{\vartheta}^{\text{SR}}_n(\lambda^*_{\max})\) is then given by

\(\text{ADRE}(\hat{\vartheta}^{\text{SR}}_n(\lambda^*_{\max}) : \hat{\vartheta}^{\text{UR}}_n) = \left[ 1 - \frac{2}{\pi} \left( 2 \exp \left\{ -\frac{\Delta^2}{2} \right\} - 1 \right) \right]^{-1}. \) (3.6.4)

Table 3.3 shows the ADRE values of Eq. (3.6.4) for some selected values of \(\Delta^2\). It is easy to see from Table 3.3 that \(\hat{\vartheta}^{\text{SR}}_n(\lambda^*_{\max})\) performs better than \(\hat{\vartheta}^{\text{UR}}_n\) whenever \(0 < \Delta^2 \le 2 \ln(2)\) and \(\hat{\vartheta}^{\text{UR}}_n\) performs better than \(\hat{\vartheta}^{\text{SR}}_n(\lambda^*_{\max})\) for \(\Delta^2 > 2 \ln(2)\).

## 3.6.3 Positive-rule Saleh-type (LASSO-type) R-estimator of \(\vartheta\)

From Section 3.6.2, consider the Saleh-type R-estimator of \(\vartheta\) which was defined as

\(\hat{\vartheta}^{\text{SR}}_n(\lambda) = \hat{\vartheta}^{\text{UR}}_n (1 - \frac{\lambda}{\sqrt{\mathcal{L}_n}}).\)

Notice that as \(|\hat{\vartheta}^{\text{UR}}_n| \to \infty\), \(\hat{\vartheta}^{\text{SR}}_n(\lambda)\) retains its sign. However, if \(|\hat{\vartheta}^{\text{UR}}_n| \to 0\), then the sign of \(\hat{\vartheta}^{\text{SR}}_n(\lambda)\) changes. To correct this anomaly, we define the positive-rule Saleh-type R-estimator as

\(\hat{\vartheta}^{\text{SR}+}_n(\lambda) = \hat{\vartheta}^{\text{UR}}_n (1 - \frac{\lambda}{\sqrt{\mathcal{L}_n}})^+ = \left( \hat{\vartheta}^{\text{UR}}_n - \frac{\lambda \eta}{\sqrt{n}} \text{sgn}(\hat{\vartheta}^{\text{UR}}_n(\lambda)) \right) I(\mathcal{L}_n > \lambda^2). \) (3.6.5)

A LASSO-type R-estimator, based on the derivation given earlier is:

\(\hat{\theta}_n^{\text{LassoR}}(\lambda) = \text{sgn}(\hat{\theta}_n^{\text{UR}}) \left( |\hat{\theta}_n^{\text{UR}}| - \lambda \frac{\eta}{\sqrt{n}} \right)^+.\)

Since \(\mathcal{L}_n = n(\hat{\theta}_n^{\text{UR}})^2/\eta^2\), we find that it can be rewritten as

\(\hat{\theta}_n^{\text{LassoR}}(\lambda) = \text{sgn}(\hat{\theta}_n^{\text{UR}}) \left( |\hat{\theta}_n^{\text{UR}}| - \lambda \frac{|\hat{\theta}_n^{\text{UR}}|}{\sqrt{\mathcal{L}_n}} \right)^+.\)

This is the same as (3.6.5), and was shown to be a linearized version of true LASSO R-estimator. Hence, this is referred to as a LASSO-type R-estimator of \(\theta\). Since it is different from the actual LASSO R-estimator, we refer to it as a positive-rule Saleh-type R-estimator. Considering \(Z_n = \sqrt{n}\hat{\theta}_n^{\text{UR}}/\eta\), the positive-rule Saleh-type R-estimator of \(\theta\) can be written as

\(\sqrt{n} \hat{\theta}_n^{\hat{\text{SR}}^+}(\lambda) = \eta Z_n \left( 1 - \frac{\lambda}{|Z_n|} \right)^+ = \eta Z_n \left( 1 - \frac{\lambda}{|Z_n|} \right) I(|Z_n| > \lambda)\)
\(= \eta \text{sgn}(Z_n) (|Z_n| - \lambda)^+ = \eta(Z_n - \lambda \text{sgn}(Z_n))I(|Z_n| > \lambda). (3.6.6)\)

### Theorem 3.8
Under the local alternative hypothesis, \(K_{(n)}\), the ADB and \(\text{ADL}_2\text{-risk}\) of \(\hat{\theta}_n^{\hat{\text{SR}}^+}(\lambda)\) are given by

\(\text{ADB}(\hat{\theta}_n^{\hat{\text{SR}}^+}(\lambda)) = -\eta \left\{ \Delta \mathcal{H}_3(\lambda^2, \Delta^2) - \lambda(\Phi(\lambda - \Delta) - \Phi(\lambda + \Delta)) \right\}, (3.6.7)\)

and

\(\text{ADL}_2\text{-risk}(\hat{\theta}_n^{\hat{\text{SR}}^+}(\lambda)) = \eta^2 \rho_{\text{ST}}(\lambda, \Delta), (3.6.8)\)

where

\(\rho_{\text{ST}}(\lambda, \Delta) = 1 - \mathcal{H}_3(\lambda^2, \Delta^2) + \Delta^2(2\mathcal{H}_3(\lambda^2, \Delta^2) - \mathcal{H}_5(\lambda^2, \Delta^2)) + \lambda^2(1 - \mathcal{H}_1(\lambda^2, \Delta^2)) - 2\lambda(\phi(\lambda - \Delta) + \phi(\lambda + \Delta)) = \rho_{\text{PT}}(\lambda, \Delta) + \lambda^2(1 - \mathcal{H}_1(\lambda^2, \Delta^2)) - 2\lambda (\phi(\lambda - \Delta) + \phi(\lambda + \Delta)). (3.6.9)\)

Hence,

\(\text{ADRE}(\hat{\theta}_n^{\hat{\text{SR}}^+}(\lambda) : \hat{\theta}_n^{\text{UR}}) = \rho_{\text{ST}}^{-1}(\lambda, \Delta). (3.6.10)\)

Table 3.4 shows the ADRE values of Eq. (3.6.10) for a range of \(\Delta^2\).

Further, it may be seen that \(\text{ADL}_2\text{-risk}(\hat{\theta}_n^{\hat{\text{SR}}^+}(\lambda_{\text{max}}^*)) \le \text{ADL}_2\text{-risk}(\hat{\theta}_n^{\text{UR}}(\lambda_{\text{max}}^*))\) uniformly in \(\Delta^2 \in \mathbb{R}^+\). See Tables 3.3 and 3.4.

