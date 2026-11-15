$$D_n(\theta) = \sum_{i=1}^n |y_i - \theta| \alpha_n^+(R_n^+(\theta)).$$

It may be noted that \(D_n(\theta)\) is a convex, continuous, and piece-wise linear function of \(\theta\). Hence, we define the unrestricted R-estimator (URE), denoted by \(\hat{\theta}_n^{UR}\), as

$$\hat{\theta}_n^{UR} = \underset{\theta \in \mathbb{R}}{\text{argmin}}\{D_n(\theta)\}.$$

Clearly,

$$\frac{\partial D_n(\theta)}{\partial \theta} = - \sum_{i=1}^n \text{sgn}(y_i - \theta) \alpha_n^+(R_n^+(\theta)) = -\sqrt{n}T_n(\theta),$$

where

$$T_n(\theta) = \frac{1}{\sqrt{n}} \sum_{i=1}^n \text{sgn}(y_i - \theta) \alpha_n^+(R_n^+(\theta)). \quad (3.2.2)$$

Hence, the minimum of \(D_n(\theta)\) occurs when \(T_n(\theta) = 0\) which we can now use to define the unrestricted R-estimation of \(\theta\) as

$$\hat{\theta}_n^{UR} = \frac{1}{2}(\hat{\theta}_n^{(U)} + \hat{\theta}_n^{(L)}),$$

where \(\hat{\theta}_n^{(U)} = \sup\{\theta : T_n(\theta) > 0\}\) and \(\hat{\theta}_n^{(L)} = \inf\{\theta : T_n(\theta) < 0\}\).

In fact, we can obtain an explicit expression for \(\hat{\theta}_n^{UR}\) by solving the equation

$$\hat{\theta}_n^{UR} = \underset{\theta \in \mathbb{R}}{\text{argmin}} \left\{ \sum_{i=1}^n |y_i - \theta| R_n^+(\theta) \right\},$$

based on Wilcoxon signed-rank statistics to obtain

$$\hat{\theta}_n^{UR} = \text{median}_{1 \le i \le j \le n} \left\{ \frac{y_i + y_j}{2} \right\}.$$

For the R-test of \(\mathcal{H}_o : \theta = 0\) vs. \(\mathcal{H}_A : \theta \neq 0\), the test-statistic is given by

$$T_n(0) = \frac{1}{\sqrt{n}} \sum_{i=1}^n \text{sgn}(y_i) \alpha_n^+(R_n^+(0)).$$

It may be shown easily that as \(n \to \infty\),

$$T_n(0) \xrightarrow{D} \mathcal{N}(0, A_\phi^2), \quad (3.2.3)$$

where \(A_\phi^2\) is given by (3.2.1).