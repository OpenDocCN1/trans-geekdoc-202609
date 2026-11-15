
We note that ADL$_2$-risk of $\hat{\theta}_n^{SR+}(\lambda)$ is better than the Saleh-type R-estimator, $\hat{\theta}_n^{SR}(\lambda)$, uniformly in $\Delta^2 \in \mathbb{R}^+$, as seen in the fourth and fifth columns of the table. It may be noted that $\hat{\theta}_n^{SR+}(\lambda)$ is also better than $\hat{\theta}_n^{UR}$ for $0 < \Delta^2 < 2 \ln(2)$; otherwise, $\hat{\theta}_n^{UR}$ is better than $\hat{\theta}_n^{SR+}(\lambda)$. See column 5 of the table.

- (g) nEnet-type vs. positive-rule Saleh-type R-estimators. Consider ADL$_2$-risk difference of $\hat{\theta}_n^{ENetRE}(\lambda, \alpha)$ and $\hat{\theta}_n^{SR+}(\lambda)$ given by

$$
\eta^2 \left( \rho_{ST}(\lambda \alpha, \Delta) - \frac{1}{[1 + \lambda(1 - \alpha)]^2} \left[ \rho_{ST}(\lambda \alpha, \Delta) + \lambda^2(1 - \alpha)^2 \Delta^2 + 2\lambda(1 - \alpha)\Delta \{ \Delta \mathcal{H}_3(\lambda \alpha, \Delta^2) - \lambda \alpha (\Phi(\lambda \alpha - \Delta) - \Phi(\lambda \alpha + \Delta)) \} \right] \right) = \eta^2 \rho_{ST}(\lambda \alpha, \Delta) \left[ 1 - \frac{1}{[1 + \lambda(1 - \alpha)]^2} \right] - \frac{1}{[1 + \lambda(1 - \alpha)]^2} \left[ \lambda^2(1 - \alpha)^2 \Delta^2 + 2\lambda(1 - \alpha)\Delta \{ \Delta \mathcal{H}_3(\lambda \alpha, \Delta) - \lambda \alpha (\Phi(\lambda \alpha - \Delta) - \Phi(\lambda \alpha + \Delta)) \} \right].
$$

This expression may be “positive”, “negative” or zero. Thus, neither the positive-rule Saleh nor nEnetRE dominates the other uniformly in $\Delta^2$ and, likewise, neither ridge nor nEnetRE dominates the other. This is shown in columns 2, 5 and 6. These results are expected since nEnetRE is a combination of the two R-estimators.

## 3.8 Simple Linear Model

In this section, we consider the simple linear model,

$$
y_i = \theta + \beta x_i + \varepsilon_i, \ i = 1, ..., n \tag{3.8.1}
$$

where $\varepsilon_1, ..., \varepsilon_n$ are i.i.d. random variables with symmetric c.d.f. $F(\cdot)$ and a p.d.f. $f(\cdot)$ having a finite Fisher information, $I(f) < \infty$. Let $Q_n = \sum_{i=1}^n (x_i - \bar{x}_n)^2$. We may rewrite (3.8.1) as

$$
y_i = \theta^* + \beta^* Q_n^{-\frac{1}{2}}(x_i - \bar{x}_n) + \varepsilon_i, \ i = 1, ..., n \tag{3.8.2}
$$

where $\theta^* = \theta + \beta \bar{x}_n$ and $\beta^* = Q_n^{\frac{1}{2}} \beta$. Clearly,

$$
Q_n^{-\frac{1}{2}} \sum_{i=1}^n (x_i - \bar{x}_n) = 0 \quad \text{and} \quad Q_n^{-1} \sum_{i=1}^n (x_i - \bar{x}_n)^2 = 1.
$$

Let $c_i = Q_n^{-\frac{1}{2}}(x_i - \bar{x}_n), \ i = 1, ..., n$. Also, suppose $R_n^+(\theta^*, \beta^*)$ is the rank of $|y_i - \theta^* - \beta^* c_i|$ among $|y_1 - \theta^* - \beta^* c_1|, ..., |y_n - \theta^* - \beta^* c_n|$. Then, we may write the rank dispersion function as

$$
D_n(\theta, \beta) = \sum_{i=1}^n |y_i - \theta - \beta c_i| a_i^+(R_n^+(\theta, \beta))
$$

which is convex, continuous and piece-wise linear in \((\theta, \beta)\). Thus, we define the R-estimator of \((\theta^*, \beta^*)^\top$ as

$$
(\hat{\theta}_n^{*\text{UR}}, \hat{\beta}_n^{*\text{UR}})^\top = \underset{(\theta, \beta)^\top \in \mathbb{R}^2}{\text{argmin}} \{D_n(\theta, \beta)\}.
$$

It is easy to verify that at the point of continuity of \(D_n(\theta, \beta)\), we have

$$
\frac{\partial D_n(\theta, \beta)}{\partial \theta} = - \sum_{i=1}^n \text{sgn}(y_i - \theta - \beta c_i) a_i^+(R_n^+(\theta, \beta)) = -n^{-\frac{1}{2}} T_n(\theta, \beta)
$$

and

$$
\frac{\partial D_n(\theta, \beta)}{\partial \beta} = - \sum_{i=1}^n c_i \text{sgn}(y_i - \theta - \beta c_i) a_i^+(R_n^+(\theta, \beta)) = -n^{-\frac{1}{2}} L_n(\theta, \beta).
$$

This result provides the motivation and justification for incorporation of weighted signed-rank statistics for simultaneous R-estimation of \((\theta^*, \beta^*)$ or \((\theta, \beta)$ based on (3.8.1) or (3.8.2), respectively. Further, using the asymptotic linearity results, we obtain that for any (fixed) \((\theta, \beta)^\top \in \mathbb{R}^2$, as \(n \to \infty\),

$$
|T_n(n^{-\frac{1}{2}}\omega_1, \omega_2) - T_n(0, 0) + \omega_1 \gamma(\phi, f)| \xrightarrow{P} 0, \quad (3.8.3)
$$

and

$$
|L_n(\omega_1, n^{-\frac{1}{2}}\omega_2) - L_n(0, 0) + \omega_2 \gamma(\phi, f)| \xrightarrow{P} 0. \quad (3.8.4)
$$

Hence,

$$
D_n(n^{-\frac{1}{2}}\omega_1, n^{-\frac{1}{2}}\omega_2) - D_n(0, 0) + \omega_1 T_n(0, 0) + \omega_2 L_n(0, 0) + \frac{\gamma(\phi, f)}{2}(\omega_1^2 + \omega_2^2) \xrightarrow{P} 0. \quad (3.8.5)
$$

The above mentioned convexity of \(D_n(\theta, \beta)$, and point-wise stochastic convergence in (3.8.5), is uniform in \((\theta, \beta), \theta^2 + \beta^2 < k^2$ with same uniform convergence as for (3.8.3) and (3.8.4). Following the proof of Theorem 5.5.2 of Jurečková and Sen (1996), we conclude as \(n \to \infty\),

$$
\left\| \begin{pmatrix} \sqrt{n}(\hat{\theta}_n^{*\text{UR}} - \theta^*) \\ (\hat{\beta}_n^{*\text{UR}} - \beta^*) \end{pmatrix} - \underset{(\theta, \beta) \in \mathbb{R}^2}{\text{argmin}} \left\{ \frac{\gamma(\phi, f)}{2} (\omega_1^2 + \omega_2^2) - \omega_1 T_n(0, 0) - \omega_2 L_n(0, 0) \right\} \right\| \xrightarrow{P} 0.
$$

Therefore,

$$
\begin{pmatrix} \sqrt{n}(\hat{\theta}_n^{\text{UR}}-\theta^*) \\ (\hat{\beta}_n^{\text{UR}}-\beta^*) \end{pmatrix}-\gamma^{-1}(\phi, f) \begin{pmatrix} T_n(0, 0) \\ L_n(0, 0) \end{pmatrix} \rightarrow^P 0. \quad (3.8.6)
$$

Because of the transformation scale-equivariance properties of the R-estimator, we have from (3.8.6),

$$
\begin{pmatrix} \sqrt{n}(\hat{\theta}_n^{\text{UR}}-\theta) \\ Q_n^{\frac{1}{2}}(\hat{\beta}_n^{\text{UR}}-\beta) \end{pmatrix}-\gamma^{-1}(\phi, f) \begin{pmatrix} 1 & -\sqrt{n}\bar{x}_n/Q_n^{\frac{1}{2}} \\ 0 & 1 \end{pmatrix} \begin{pmatrix} T_n(0, 0) \\ L_n(0, 0) \end{pmatrix} \rightarrow^P 0
$$

where \((\hat{\theta}_n^{\text{UR}}, \hat{\beta}_n^{\text{UR}})^\top$ refers to the R-estimator of \((\theta, \beta)^\top$ using \(D_n(\theta, \beta)\). Hence,

$$
\begin{pmatrix} \sqrt{n}(\hat{\theta}_n^{\text{UR}}-\theta) \\ \sqrt{n}(\hat{\beta}_n^{\text{UR}}-\beta) \end{pmatrix} \rightarrow^\mathcal{D} \mathcal{N}_2 \left( \begin{pmatrix} 0 \\ 0 \end{pmatrix}, \eta^2 \begin{pmatrix} 1+\frac{\bar{x}^2}{Q} & -\frac{\bar{x}}{Q} \\ -\frac{\bar{x}}{Q} & \frac{1}{Q} \end{pmatrix} \right) \text{ as } n \rightarrow \infty ,
$$

where \(Q = \lim_{n \rightarrow \infty} n^{-1} Q_n$ .

### 3.8.1 Restricted R-estimator of Slope

Clearly, if \(\beta\) is suspected to be 0, the restricted R-estimator (RRE) of \(\beta\), denoted by \(\hat{\beta}_n^{\text{RR}}\), is

$$
\hat{\beta}_n^{\text{RR}}=0 .
$$

To overcome the difficulty of identical asymptotic distributions of different large-sample estimators under fixed alternatives, \(\mathcal{H}_A : \beta \neq 0\), we consider the local alternatives

$$
K_{(n)} : \beta_{(n)}=\frac{1}{\sqrt{n}}\delta, \quad (3.8.7)
$$

where \(\delta\) is a fixed number.

### Theorem 3.10 Under the local alternatives, \(K_{(n)}\), the asymptotic distributional bias, and ADL$_2$-risk of the restricted R-estimator, \(\hat{\beta}_n^{\text{RR}}\), are respectively given by

$$
\text{ADB}(\hat{\beta}_n^{\text{RR}})=-\delta,
$$

$$
\text{ADL}_2\text{-risk}(\hat{\beta}_n^{\text{RR}})=\eta^2\Delta^2,\ \ \ \ \ \Delta^2=\frac{Q\delta^2}{\eta^2}.
$$

In what follows, we define the shrinkage and penalty estimators for the slope parameter in the simple linear model (3.8.1).

### 3.8.2 Shrinkage R-estimator of Slope

Consider the shrinkage R-estimator of the slope given by

$$
\hat{\beta}_n^{\text{ShrinkageR}}(c) = c\hat{\beta}_n^{\text{UR}}, \quad 0 \le c \le 1. \tag{3.8.8}
$$

### Theorem 3.11 Under the local alternative hypothesis, \(K_{(n)} : \beta = n^{-\frac{1}{2}}\delta\), the ADB and ADL$_2$-risk of \(\hat{\beta}_n^{\text{ShrinkageR}}(c)\) are given by

$$
\text{ADB}(\hat{\beta}_n^{\text{ShrinkageR}}(c)) = -(1-c)\delta = -\frac{\eta}{\sqrt{Q}}(1-c)\Delta,
$$

$$
\text{ADL}_2\text{-risk}(\hat{\beta}_n^{\text{ShrinkageR}}(c)) = \frac{\eta^2}{Q}[c^2 + (1-c)^2\Delta^2], \quad \Delta^2 = \frac{Q\delta^2}{\eta^2}. \tag{3.8.9}
$$

### Corollary 3.3 The optimum value of c of the shrinkage R-estimator of \(\beta\) is given by

$$
c_{\text{opt}} = \frac{\Delta^2}{1 + \Delta^2}.
$$

### Proof: Minimizing (3.8.9) w.r.t. c, one finds

$$
\frac{\partial\text{ADL}_2\text{-risk}(\hat{\beta}_n^{\text{ShrinkageR}}(c))}{\partial c} = \frac{\eta^2}{Q} [2c - 2(1-c)\Delta^2] = 0
$$

which leads to \(\Delta^2/(1 + \Delta^2)\) as the optimum value.

Using this optimum value in (3.8.9) yields

$$
\text{ADL}_2\text{-risk}(\hat{\beta}_n^{\text{ShrinkageR}}(c_{\text{opt}})) = \eta^2 \frac{\Delta^2}{1 + \Delta^2}.
$$

Hence,

$$
\text{ADRE}(\hat{\beta}_n^{\text{ShrinkageR}}(c_{\text{opt}}) : \hat{\beta}_n^{\text{UR}}) = 1 + \frac{1}{\Delta^2}.
$$

### 3.8.3 Ridge-type R-estimation of Slope

Now, consider (3.8.8) with \(c = 1/(1 + \lambda), \lambda > 0\). Then, the ridge-type R-estimator of \(\beta\) is given by

$$
\hat{\beta}_n^{\text{ridgeR}}(\lambda) = \frac{1}{1 + \lambda} \hat{\beta}_n^{\text{UR}}.
$$

### Theorem 3.12 Under the local alternative hypothesis, \(K_{(n)}\), the ADB and ADL$_2$-risk of the ridge-type R-estimator of \(\beta\), i.e. \(\hat{\beta}_n^{\text{ridgeR}}(\lambda)\), are
