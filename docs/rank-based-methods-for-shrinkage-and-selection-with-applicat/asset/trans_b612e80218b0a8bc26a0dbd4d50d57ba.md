

| \(\Delta^2\) | 0 | 0.05 | 0.1 | 0.5 | 1 | 2ln(2) | 2 | 5 | 10 |
|---|---|---|---|---|---|---|---|---|---|
| ADRE | 4.30 | 3.83 | 3.46 | 2.03 | 1.42 | 1.19 | 0.98 | 0.68 | 0.62 |

对比表3.3和表3.4可证实，正则Saleh型R估计量的风险小于Saleh型R估计量。因此，该估计量对Saleh型R估计量是一种改进。

### 3.6.4 \(\theta\)的弹性网型R估计量

If we combine the ridge and LASSO R-estimators, we obtain the elastic net-type R-estimator (EnetRE) of \(\theta\). This estimator is defined by

\(\hat{\theta}_n^{\text{EnetR}}(\lambda, \alpha) = \text{argmin}_{\theta \in \mathbb{R}} \left\{ \sum_{i=1}^n |y_i - \theta|a_n^+(R_n^+(\theta)) + \lambda \left[ \eta\alpha|\theta| + \frac{1-\alpha}{2}\theta^2 \right] \right\}.\)

Correspondingly, the naive Enet-type R-estimator (nEnetRE) is given by

\(\hat{\theta}_n^{\text{nEnetR}}(\lambda, \alpha) = \frac{\hat{\theta}_n^\text{UR}}{1 + \lambda(1 - \alpha)} \left( 1 - \frac{\lambda\alpha}{\sqrt{\mathcal{L}_n}} \right) I(\mathcal{L}_n > \lambda^2\alpha^2)\) (3.6.11)

or equivalently

\(\sqrt{n}\hat{\theta}_n^{\text{nEnetR}}(\lambda, \alpha) = \eta \frac{\text{sgn}(Z_n)}{1 + \lambda(1 - \alpha)} (|Z_n| - \lambda\alpha)^+, \quad Z_n = \frac{\sqrt{n}\hat{\theta}_n^\text{UR}}{\eta},\)

where \(0 < \alpha < 1\), and \(\lambda > 0\). If \(\alpha = 0\), then the nEnetRE becomes the ridge-type R-estimator, \((\eta Z_n)/(1 + \lambda)\). On the other hand, taking \(\alpha = 1\), it reduces to the positive-rule Saleh-type (i.e. LASSO-type) R-estimator, \(\eta\text{sgn}(Z_n)(|Z_n| - \lambda)^+\).

### Theorem 3.9 Under the local alternative hypothesis, \(K_{(n)}\), the ADB and ADL\(_2\)-risk of the naive elastic net-type R-estimator of \(\theta\) are

\(\text{ADB}(\hat{\theta}_n^{\text{nEnetR}}(\lambda, \alpha)) = -\eta \frac{1}{1 + \lambda(1 - \alpha)} \left\{ \Delta\mathcal{H}_3(\lambda^2\alpha^2, \Delta^2) \right.\)
\(\left. - \lambda\alpha \left( \Phi(\lambda\alpha - \Delta) - \Phi(\lambda\alpha + \Delta) \right) - \lambda(1 - \alpha)\Delta \right\}\)

and

\(\text{ADL}_2\text{-risk}(\hat{\theta}_n^{\text{nEnetR}}(\lambda, \alpha)) = \eta^2 \frac{1}{[1 + \lambda(1 - \alpha)]^2} \rho_\text{EN}(\lambda, \alpha, \Delta)\)

![](img/f3b106d7e76ae3afcec8895afa28732c_160_0.png)

### Figure 3.4 The ADRE of nEnet-type R-estimators.

where

\begin{align*}
\rho_{EN}(\lambda, \alpha, \Delta) &= \Bigg( 1 - \mathcal{H}_3(\lambda^2 \alpha^2, \Delta^2) + \Delta^2 \Big( 2 \mathcal{H}_3(\lambda^2 \alpha^2, \Delta^2) - \mathcal{H}_5(\lambda^2 \alpha^2, \Delta^2) \Big) \\
&+ \lambda^2 \alpha^2 \Big( 1 - \mathcal{H}_1(\lambda^2 \alpha^2, \Delta^2) \Big) - 2 \lambda \alpha \Big( \big[ \phi(\lambda \alpha + \Delta) + \phi(\lambda \alpha - \Delta) \big] \Big) \Bigg) \\
&+ 2 \lambda (1 - \alpha) \Delta \Big( \Delta \mathcal{H}_3(\lambda^2 \alpha^2, \Delta^2) - \lambda \alpha \big( \Phi(\lambda \alpha - \Delta) - \Phi(\lambda \alpha + \Delta) \big) \Big) \\
&+ \lambda^2 (1 - \alpha)^2 \Delta^2 \\
&= \rho_{ST}(\lambda \alpha, \Delta) + \lambda^2 (1 - \alpha)^2 \Delta^2 + 2 \lambda (1 - \alpha) \Delta \Bigg( \Delta \mathcal{H}_3(\lambda^2 \alpha^2, \Delta^2) \\
&- \lambda \alpha \big( \Phi(\lambda \alpha - \Delta) - \Phi(\lambda \alpha + \Delta) \big) \Bigg).
\end{align*}

Hence,

\(\text{ADRE}(\hat{\theta}_n^{\text{nEnetR}}(\lambda, \alpha) : \hat{\theta}_n^{\text{UR}}) = [1 + \lambda(1 - \alpha)]^2 \left( \rho_{EN}(\lambda, \alpha, \Delta) \right)^{-1}.\)

Figure 3.4 shows that the ADRE of nEnet-type R-estimators for different \(\alpha\) values.

![](img/f3b106d7e76ae3afcec8895afa28732c_161_0.png)

Figure 3.5 Figure of the ADRE of all R-estimators for different \(\Delta^2\).

## 3.7 位置参数R估计量的比较研究

This section provides a summary of the results obtained using all the R-estimators of the location model. Figure 3.5 and Table 3.5 provide the corresponding graphical and tabular data, respectively. Note that for PTE, we use \(\lambda = \lambda^* = \sqrt{2\ln(2)}\); for the Saleh-type and its positive-rule Saleh-type, we set \(\lambda = \lambda_{opt} = \sqrt{\frac{2}{\pi}}\); and, finally, for the nEnet R-estimator, we use \(\lambda = \sqrt{2\ln(2)}\) and \(\alpha = 0.5\).

| Δ² | RR | ridgeR | PTR/HTR | SR | SR+ | nEnetR |
|---|---|---|---|---|---|---|
| 0 | ∞ | ∞ | 1.411 | 2.752 | 4.303 | 3.869 |
| 0.01 | 100.000 | 101.000 | 1.399 | 2.705 | 4.199 | 3.842 |
| 0.02 | 50.000 | 51.000 | 1.387 | 2.659 | 4.101 | 3.816 |
| 0.03 | 33.333 | 34.333 | 1.375 | 2.615 | 4.007 | 3.791 |
| 0.04 | 25.000 | 26.000 | 1.364 | 2.573 | 3.918 | 3.766 |
| 0.05 | 20.000 | 21.000 | 1.353 | 2.533 | 3.833 | 3.743 |
| 0.1 | 10.000 | 11.000 | 1.301 | 2.350 | 3.463 | 3.636 |
| 0.2 | 5.000 | 6.000 | 1.213 | 2.064 | 2.916 | 3.471 |
| 0.3 | 3.333 | 4.333 | 1.141 | 1.849 | 2.532 | 3.355 |
| 0.4 | 2.500 | 3.500 | 1.082 | 1.683 | 2.248 | 3.277 |
| 0.5 | 2.000 | 3.000 | 1.031 | 1.550 | 2.029 | 3.224 |
| 1 | 1.000 | 2.000 | 0.869 | 1.157 | 1.417 | 3.084 |
| 2 ln(2) | 0.721 | 1.721 | 0.801 | 1.000 | 1.187 | 2.854 |
| 2 | 0.500 | 1.500 | 0.743 | 0.856 | 0.980 | 2.224 |
| 3 | 0.333 | 1.333 | 0.713 | 0.739 | 0.813 | 1.332 |
| 4 | 0.250 | 1.250 | 0.720 | 0.683 | 0.730 | 0.839 |
| 5 | 0.200 | 1.200 | 0.746 | 0.653 | 0.685 | 0.561 |
| 10 | 0.100 | 1.100 | 0.908 | 0.614 | 0.619 | 0.141 |
| 20 | 0.050 | 1.050 | 0.996 | 0.611 | 0.611 | 0.033 |
| 30 | 0.033 | 1.033 | 1.000 | 0.611 | 0.611 | 0.015 |
| 40 | 0.025 | 1.025 | 1.000 | 0.611 | 0.611 | 0.008 |
| 50 | 0.020 | 1.020 | 1.000 | 0.611 | 0.611 | 0.005 |

- (a) RRE vs. URE. We first consider the comparison of unrestricted and restricted R-estimators of \(\theta\) from Section 3.2.2. The \(ADL_2\)-risk difference of the two R-estimators is given by \(\eta^2(1 - \Delta^2)\). Thus, the restricted R-estimator, \(\hat{\theta}_n^{RR}\), outperforms the unrestricted R-estimator, \(\hat{\theta}_n^{UR}\), when \(0 \le \Delta^2 \le 1\) and \(\hat{\theta}_n^{UR}\) outperforms \(\hat{\theta}_n^{RR}\) whenever \(\Delta^2 > 1\), as seen in the 1st column of the table derived from

\(\text{ADRE}(\hat{\theta}_n^{RR} : \hat{\theta}_n^{UR}) = \Delta^{-2}\).

- (b) General shrinkage R-estimator vs. URE. A comparative study of the general shrinkage R-estimator of the location parameter, \(\hat{\theta}^{\text{ShrinkageR}}(c_{opt})\), and URE, \(\hat{\theta}_n^{UR}\), produces an ADL\(_2\)-risk difference given by

\(\eta^2 \left[ 1 - \frac{\Delta^2}{1 + \Delta^2} \right] = \frac{\eta^2}{1 + \Delta^2}.\)

Hence,

\(\text{ADRE}(\hat{\theta}^{\text{ShrinkageR}}(c_{\text{opt}}) : \hat{\theta}_n^{UR}) = 1 + \frac{1}{\Delta^2}.\)

The general shrinkage R-estimator of \(\theta\) outperforms \(\hat{\theta}_n^{UR}\) uniformly.

- (c) Ridge-type R-estimator vs. URE. Here, the ADL\(_2\)-risk difference of \(\hat{\theta}_n^{\text{ridgeR}}(\lambda_{\text{opt}})\) and \(\hat{\theta}_n^{UR}\) is again \(\frac{\eta^2}{1+\Delta^2}\). Therefore,

ADRE(\hat{\theta}_n^{\text{ridgeR}}(\lambda_{\text{opt}}) : \hat{\theta}_n^{\text{UR}}) = 1 + \frac{1}{\Delta^2}.

Hence, ridge-type R-estimator outperforms URE uniformly, as seen in the second column of the table.

- (d) HTRE (or PTR) vs. URE. In this case, the ADL\(_2\)-risk difference of \(\hat{\theta}_n^{\text{HTR}}(\lambda)\) (i.e. \(\hat{\theta}_n^{\text{PTR}}(\lambda)\) ) and \(\hat{\theta}_n^{\text{UR}}\) is given by

\(\mathcal{H}_3(\lambda^2, \Delta^2) - \Delta^2 \left( 2\mathcal{H}_3(\lambda^2, \Delta^2) - \mathcal{H}_5(\lambda^2, \Delta^2) \right).\)

The difference is non-negative whenever

\(0 \le \Delta^2 \le \frac{\mathcal{H}_3(\lambda^2, \Delta^2)}{2\mathcal{H}_3(\lambda^2, \Delta^2) - \mathcal{H}_5(\lambda^2, \Delta^2)}.\)

Therefore, \(\hat{\theta}_n^{\text{HTR}}(\lambda)\) outperforms \(\hat{\theta}_n^{\text{UR}}\), otherwise, \(\hat{\theta}_n^{\text{UR}}\) outperforms \(\hat{\theta}_n^{\text{HTR}}(\lambda)\) for \(\Delta^2\) in the complementary interval, as in the third column of the table. Finally,

\(\text{ADRE}(\hat{\theta}_n^{\text{HTR}}(\lambda) : \hat{\theta}_n^{\text{UR}}) = \left[ 1 - \mathcal{H}_3(\lambda^2, \Delta^2) + \Delta^2 \left( 2\mathcal{H}_3(\lambda^2, \Delta^2) - \mathcal{H}_5(\lambda^2, \Delta^2) \right) \right]^{-1}.\)

- (e) Saleh-type R-estimator vs. URE. The ADL\(_2\)-risk difference is

\(\frac{2}{\pi} \left[ 2 \exp \left\{ -\frac{\Delta^2}{2} \right\} - 1 \right].\)

Then for \(0 \le \Delta^2 \le 2 \ln 2\), the Saleh-type R-estimator is better than URE; otherwise, \(\hat{\theta}^{UR}(\lambda)\) is better. This is due to the fact that

\(\text{ADRE}(\hat{\theta}^{SR}(\lambda) : \hat{\theta}_n^{\text{UR}}) = \left[ \frac{\pi + 2}{\pi} - \frac{4}{\pi} \exp \left\{ -\frac{\Delta^2}{2} \right\} \right]^{-1}.\)

- (f) Positive-rule Saleh-type vs. Saleh-type R-estimators. The ADL\(_2\)-risk of \(\hat{\theta}_n^{SR+}\) is given by

ADL\(_2\)-risk(\(\hat{\theta}_n^{SR+}\)) = \(\eta^2\Big[(1 - \mathcal{H}_3(\lambda^2, \Delta^2)) + \Delta^2 \left( 2\mathcal{H}_3(\lambda^2, \Delta^2) - \mathcal{H}_5(\lambda^2, \Delta^2) \right) \big. \left. +\lambda^2 \left( 1 - \mathcal{H}_3(\lambda^2, \Delta^2) \right) - 2\lambda \left( \phi(\lambda + \Delta) + \phi(\lambda - \Delta) \right) \Big].\)

If \(\Delta^2 = 0\), then ADL\(_2\)-risk of \(\hat{\theta}_n^{SR+}(\lambda)\) is

\(\eta^2 \left[ (1 - \mathcal{H}_3(\lambda^2, 0)) + \lambda^2 \left( 1 - \mathcal{H}_1(\lambda^2, 0) \right) - 4\lambda \phi(\lambda) \right].\)

On the other hand,

ADL\(_2\)-risk(\(\hat{\theta}_n^{SR+}(\lambda)\)) \(\le \eta^2 \left[ (1 + \lambda^2) \right].\)

