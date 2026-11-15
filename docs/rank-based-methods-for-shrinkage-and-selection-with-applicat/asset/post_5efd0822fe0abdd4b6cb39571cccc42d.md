
= \hat{\boldsymbol{\beta}}_{\widehat{s}_1}^{\text{ridgeR}}(y_n) + \boldsymbol{C}_{n11}^{-1} \boldsymbol{C}_{n12} \hat{\boldsymbol{\beta}}_{\widehat{s}_2}^{\text{ridgeR}}(y_n) I(\mathcal{L}_n \le \lambda^2) ,

where the last equality follows from Eq. (10.4.22).

- (b) Stein–Saleh-type R-estimator

Now, the continuous version of the $\hat{\boldsymbol{\beta}}_{\widehat{s}_1}^{\text{PTR}}(y_n)$ estimator is given by

$$
\hat{\boldsymbol{\beta}}_{\widehat{s}_1}^{\text{SSR}}(y_n) = \hat{\boldsymbol{\beta}}_{1n}^{\text{RR}} + \left(\hat{\boldsymbol{\beta}}_{\widehat{s}_1}^{\text{ridgeR}}(y_n) - \hat{\boldsymbol{\beta}}_{1n}^{\text{RR}}\right)(1 - d\mathcal{L}_n^{-1})
= \hat{\boldsymbol{\beta}}_{\widehat{s}_1}^{\text{ridgeR}}(y_n) - \left(\hat{\boldsymbol{\beta}}_{\widehat{s}_1}^{\text{ridgeR}}(y_n) - \hat{\boldsymbol{\beta}}_{1n}^{\text{RR}}\right)d\mathcal{L}_n^{-1}
= \hat{\boldsymbol{\beta}}_{\widehat{s}_1}^{\text{ridgeR}}(y_n) + \boldsymbol{C}_{n11}^{-1} \boldsymbol{C}_{n12} \hat{\boldsymbol{\beta}}_{\widehat{s}_2}^{\text{ridgeR}}(y_n) d\mathcal{L}_n^{-1} ,
$$

where \(d = s_2 - 2\), \(s_2 = |\mathcal{S}_2| + o_p(1)\) and \(s_2 \ge 3\).

Note that $\hat{\boldsymbol{\beta}}_{\widehat{s}_1}^{\text{SSR}}(y_n)$ may change the sign of the estimators. We correct this by defining the positive-rule shrinkage estimator.

- (c) Positive-rule Stein–Saleh-type R-estimator

$$
\hat{\boldsymbol{\beta}}_{\widehat{s}_1}^{\text{SSR}+}(y_n) = \hat{\boldsymbol{\beta}}_{\widehat{s}_1}^{\text{ridgeR}}(y_n) - \left(\hat{\boldsymbol{\beta}}_{\widehat{s}_1}^{\text{ridgeR}}(y_n) - \hat{\boldsymbol{\beta}}_{1n}^{\text{RR}}\right)d\mathcal{L}_n^{-1}I(\mathcal{L}_n > d)
= \hat{\boldsymbol{\beta}}_{\widehat{s}_1}^{\text{ridgeR}}(y_n) + \boldsymbol{C}_{n11}^{-1} \boldsymbol{C}_{n12} \hat{\boldsymbol{\beta}}_{\widehat{s}_2}^{\text{ridgeR}}(y_n) d\mathcal{L}_n^{-1}I(\mathcal{L}_n > d) .
$$

These estimators depend on the tuning parameters and \(\gamma_n\).

## 10.6 Asymptotic Properties of the Ridge R-estimators

For the asymptotic properties of the above estimators, and \(\hat{\boldsymbol{\beta}}_n^{\text{ridgeR}}(y_n)\) in particular, we make the following assumptions:

- B(i) The random \(\varepsilon_i \sim F(x)\) with p.d.f. \(f(x)\) has a finite Fisher information \(I(f) < \infty\).

- B(ii) \(\mathfrak{g}_{1n}^{-1} = O(n^{-\eta})\) where \(\tau < \eta \le 1\) for \(\tau\) in A(ii).

- B(iii) \(\log(p_n) = O(n^\gamma)\) for \(0 < \gamma < 1\).

- B(iv) There exists a positive definite matrix \(\mathbf{C}\) such that \(\lim_{n\to\infty} \mathbf{C}_n = \mathbf{C}\) where the eigenvalues satisfy \(0 < \xi_1 < \xi_\Xi < \xi_2 < \infty\).

Condition B(ii) guarantees the positive eigenvalues of \(\mathbf{U}^\top \mathbf{M}_{\mathcal{S}_1} \mathbf{U}\) cannot be too small with a rate associated with the weak signal strengths in \(\mathcal{S}_2\). Condition B(iii) permits the ultra-high dimensional case such that the number of variables can grow with the sample size at almost an exponential rate. Condition B(iv) is the regularity condition of \(\mathbf{X}_{\mathcal{S}_1^c} = (\mathbf{z}_1, \dots, \mathbf{z}_n)^\top\) to have asymptotic normality.

We now present some linearity results as \(n \to \infty\) from Puri and Sen (1985).

- (a) $$n^{-\frac{1}{2}} \left\| \boldsymbol{L}_{n(2)}\left(\hat{\boldsymbol{\beta}}_{1n}^{\text{RR}}, \mathbf{0}\right)-\boldsymbol{L}_{n(2)}\left(\hat{\boldsymbol{\beta}}_{s_1}^*, \mathbf{0}\right)+\gamma(\phi, f) \boldsymbol{C}_{n 21}\left(\hat{\boldsymbol{\beta}}_{1n}^{\text{RR}}-\hat{\boldsymbol{\beta}}_{s_1}^*\right)\right\| \stackrel{P}{\longrightarrow} 0.$$

- (b) $$n^{-\frac{1}{2}} \left\| \boldsymbol{L}_{n(2)}\left(\hat{\boldsymbol{\beta}}_{1n}^{\text{RR}}, \mathbf{0}\right)-\boldsymbol{L}_{n(2)}\left(\hat{\boldsymbol{\beta}}_{s_1}^*, \mathbf{0}\right)+\gamma(\phi, f) \boldsymbol{C}_{n 11}\left(\hat{\boldsymbol{\beta}}_{1n}^{\text{RR}}-\hat{\boldsymbol{\beta}}_{s_1}^*\right)\right\| \stackrel{P}{\longrightarrow} 0.$$

- (c) $$n^{-\frac{1}{2}} \left\| \boldsymbol{L}_{n(2)}\left(\hat{\boldsymbol{\beta}}_{1n}^{\text{RR}}, \mathbf{0}\right)-\left\{\boldsymbol{L}_{n(2)}\left(\hat{\boldsymbol{\beta}}_{s_1}^*, \mathbf{0}\right)-\boldsymbol{C}_{n 21} \boldsymbol{C}_{n 11}^{-1} \boldsymbol{L}_{n(1)}\left(\hat{\boldsymbol{\beta}}_{s_1}^*, \mathbf{0}\right)\right\}\right\| \stackrel{P}{\longrightarrow} 0.$$

Then, under \(\mathcal{H}_0 : \boldsymbol{\beta}_{s_2}^* = \mathbf{0}, \left(\boldsymbol{L}_{n(1)}(\mathbf{0}, \mathbf{0})^{\top}, \boldsymbol{L}_{n(2)}(\mathbf{0}, \mathbf{0})^{\top}\right)^{\top}\) has the same joint distribution as \(\left(\boldsymbol{L}_{n(1)}(\mathbf{0}, \mathbf{0})^{\top}, \boldsymbol{L}_{n(2)}(\mathbf{0}, \mathbf{0})^{\top}\right)^{\top}\) under \(\mathcal{H}^* : \hat{\boldsymbol{\beta}}_{s_1}^* = \mathbf{0}\) and \(\hat{\boldsymbol{\beta}}_{s_2}^* = \mathbf{0}\). Hence,

$$n^{-\frac{1}{2}}\left(\boldsymbol{L}_{n(1)}(\mathbf{0}, \mathbf{0})^{\top}, \boldsymbol{L}_{n(2)}(\mathbf{0}, \mathbf{0})^{\top}\right)^{\top} \stackrel{\mathcal{D}}{\longrightarrow} \mathcal{N}_{p_{1n}+p_{2n}}\left(0, \eta^2 \boldsymbol{C}\right).$$

Thus, using Eqs. (10.6.2) and (10.6.3), we can conclude that

$$n^{-\frac{1}{2}} \boldsymbol{L}_{n(2)}\left(\hat{\boldsymbol{\beta}}_{1n}^{\text{RR}}, \mathbf{0}\right) \stackrel{\mathcal{D}}{\longrightarrow} \mathcal{N}_{p_{2n}}\left(0, \eta^2 \boldsymbol{C}_{22 \cdot 1}\right).$$

Under the set of local alternatives \(\boldsymbol{\beta}_{s_2}^* = n^{-\frac{1}{2}} \delta \boldsymbol{s}_2\) and the contiguity results, one can show that \(n^{-\frac{1}{2}}\left(\boldsymbol{L}_{n(1)}(\hat{\boldsymbol{\beta}}_{s_1}^*, \mathbf{0})^{\top}, \boldsymbol{L}_{n(2)}(\hat{\boldsymbol{\beta}}_{s_1}^*, \mathbf{0})^{\top}\right)^{\top}\) has the same joint normal distribution as that of \(n^{-\frac{1}{2}}\left(\boldsymbol{L}_{n(1)}(\mathbf{0}, \mathbf{0})^{\top}, \boldsymbol{L}_{n(2)}(\mathbf{0}, \mathbf{0})^{\top}\right)^{\top}\) under \(\hat{\boldsymbol{\beta}}_{s_1}^* = \mathbf{0}\) and \(\hat{\boldsymbol{\beta}}_{s_2}^* = n^{-1/2} \delta \boldsymbol{s}_2\) with mean vector and covariance matrix, respectively, given by

$$\gamma(\phi, f)\left(\begin{array}{c} \boldsymbol{C}_{11} \delta \boldsymbol{s}_2^* \\ \boldsymbol{C}_{22} \delta \boldsymbol{s}_2^* \end{array}\right), \text{ and } \eta^2 \boldsymbol{C}.$$

Therefore,

$$\gamma^{-1}(\phi, f) n^{-\frac{1}{2}} \boldsymbol{L}_{n(2)}(\hat{\boldsymbol{\beta}}_{1n}^{\text{RR}}, \mathbf{0}) = \gamma^{-1}(\phi, f) n^{-\frac{1}{2}} \left[ \boldsymbol{L}_{n(2)}\left(\hat{\boldsymbol{\beta}}_{s_1}^*, \mathbf{0}\right) - \boldsymbol{C}_{n 21} \boldsymbol{C}_{n 11}^{-1} \boldsymbol{L}_{n(1)}\left(\hat{\boldsymbol{\beta}}_{s_1}^*, \mathbf{0}\right) \right]
\xrightarrow{\mathcal{D}} \mathcal{N}_{p_{2n}}(\mathbf{C}_{22\cdot1}\boldsymbol{\delta}^*_{\mathcal{S}_1}, \eta^2\mathbf{C}_{22\cdot1}). \quad (10.6.7)$$

We can now state the following theorem.

### Theorem 10.1

Suppose the sparse model of Eq. (10.1.1) satisfies the signal strength assumptions A(i)–A(iii) and model assumptions B(i)–B(iii). If we choose

\(\gamma_n = c_1^{-2}c_2 n^{2\alpha} (\log(\log(n)))^3 \log(n \vee p_n)\)

for some \(c_2 > 0\) with \(\alpha < (\eta - \gamma - \tau)/3\), then \(\hat{\delta}_2\) defined by Eq. (10.4.8) satisfies

\(P(\hat{S}_2 = S_2 | \hat{S}_1 = S_1) \ge 1 - (n \vee p_n)^{-t} \quad \text{for some } t > 0\)

where \(0 < \gamma \le \frac{1}{2}, \tau, \eta\) defined in A(ii), B(ii) and B(iii), respectively.

### Proof

The proof is due to Shao and Deng (2012) and Gao et al. (2017). Assume \(n\) is sufficiently large such that \(\log(\log(n)) > 0\). Let \(\gamma_n = c_2 a_n^{-2}(\log(\log n))^3 \log(n \vee p_n)\), where \(a_n = c_1 n^{-\alpha}, 0 < \alpha \le 1/2\), for some \(c_1 > 0\). Then, for \(u_n = 1 + \log(\log(n))\), we have

\(\frac{|\text{ADB}(\hat{\beta}^{\text{ridgeR}}_{jn}(\gamma_n))|}{a_n \log(\log(n))} \le \frac{\gamma_n n^{\tau-\eta}}{a_n \log(\log(n))} \le \frac{c_2(\log(\log(n)))^4}{a_n^3 n^{\eta-\tau-\gamma}} \le \frac{c_2(\log(\log(n)))^4}{c_1^3 n^{\eta-\tau-\gamma-3\alpha}} \to 0 \quad \text{if } \alpha < \frac{1}{3}(\eta - \gamma - \tau).\)

From the normal distribution of the rank estimators, we have

\(\text{Cov}(\sqrt{n}\hat{\delta}^{\text{ridgeR}}_{\mathcal{S}_1^c}(\gamma_n)) \le \eta^2 k_n^{-1} \mathbf{I}_{q_n}.\)

Thus,

\(\forall j \notin \mathcal{S}_1, \quad \text{Var}(\sqrt{n}\hat{\beta}^{\text{RR}}_{jn}(\gamma_n)) = O(\gamma_n^{-1}).\)

Further, note that

\(\sqrt{\gamma_n} a_n (\log(\log(n))) = O(\log(\log(n))) \to \infty.\)

We then find that

\(\frac{a_n \log(\log(n))}{\sqrt{\text{Var}(\hat{\beta}^{\text{ridgeR}}_j(\gamma_n))}} \ge a_n (\log(\log(n)))\sqrt{\gamma_n} \to \infty\)
