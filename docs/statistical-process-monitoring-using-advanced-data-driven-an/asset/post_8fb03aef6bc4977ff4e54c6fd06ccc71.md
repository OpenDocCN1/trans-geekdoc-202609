
the control chart signals a shift when

$Q_f = \max_{k=1,\dots,q} \frac{W_{j,k} - \text{E}(W_{j,y})}{\sqrt{\text{Var}(W_{j,y})}} > L,$

where \( L \) is a control limit chosen to give a particular IC ARL. This \( L \) can be determined through simulation and must be determined by a one-time computation prior to performing Phase II monitoring. In practice, the \(\frac{2-\lambda}{\lambda[1-(1-\lambda)^{2j}]}\) factor in \( W_{j,y} \) can be replaced with the asymptotic form \((2-\lambda)/\lambda\). LEWMA is evaluated through simulation, particularly with respect to its ARL in OC settings, for \( p=5 \) and \( p=15 \). It is compared to two other EWMA charting statistics across multiple shift sizes in varying numbers of variables. The results show that LEWMA provides well-rounded protection against a variety of shifts in terms of ARL. Furthermore, the authors assess the ability of the method to correctly identify all shifted variables in a set of 15 variables. For a single shifted variable out of the 15, LEWMA correctly identifies the shifted variable in approximately 55 to 60% of simulations; however, as the number of shifted variables increases from 1 to 2 to 3, the highest proportion of simulations in which the correct shifted variables are identified drops from 60% to 37%, to 24%. Conversely, the proportion of simulations in which an error is made in identifying shifted variables (either a shifted variable is not identified or an un-shifted variable is selected) increase as the number of shifted variables in the simulation increase from 6% for 1 shifted variable to 22% for 2 shifted variables, to 34% for three shifted variables. Nevertheless, LEWMA still performs better than its competitors. This study is one of the first to assess the performance of fault isolation in addition to fault detection, and similarly to [25], the results indicate that fault isolation is a very challenging problem, and methods have room for improvement.

### Example method 3. APC-PCSR.

Adaptive PC and PC-based Signal Recovery (APC-PCSR) adaptively chooses principal components (PCs), allowing them to vary over time, and then incorporates a diagnostic approach that exploits adaptive lasso [55]. This method tends to work better in high-dimensional settings than [2,6,16,17], which are computationally burdensome as the dimension grows. It can be used when variables are dependent, and knowledge of the fault direction, size, and/or number of affected variables are not needed.

To reduce the dimension of the data, PCA is performed. Here, \(\mathbf{A}\) is the \( p \times p \) matrix of eigenvectors of \(\mathbf{\Sigma}\), and \(\mathbf{y}_i = \mathbf{A}\mathbf{x}_i\) denotes the PC scores. The eigenvectors in \(\mathbf{A}\) are ordered such that the corresponding eigenvalues are in decreasing order with \(\lambda_1 \ge \lambda_2 \ge \cdots \ge \lambda_p\). Monitoring just the top \( l \) PCs (usually those with the largest eigenvalues) can sometimes miss the fault because the variance of the top PCs is larger, so the bottom PCs can be more sensitive to the fault. To account for this, the standardized PC scores are computed as

\(\tilde{y}_{i,j} = \frac{y_{i,j}}{\sqrt{\lambda_j}}, \quad j=1,\dots,p.\)

The IC observations are assumed to be distributed as \(\mathbf{x}_i \sim N(\mathbf{0}, \mathbf{\Sigma})\), but under OC conditions, the distribution becomes \(\mathbf{x}_i \sim N(\mu, \Sigma)\). Thus, the OC process’ PC scores will have distribution \(\mathbf{y}_i \sim N(\mathbf{\Lambda}'\mu, \mathbf{\Lambda})\), where \(\mathbf{\Lambda} = \text{diag}(\lambda_1, \lambda_2, \dots, \lambda_p)\). Then, monitoring is conducted using an EWMA statistic, similar to the one presented in Eq. (3.14) but modified to apply to the standardized PC scores as follows:

\(u_{i,j} = \lambda \tilde{y}_{i,j} + (1 - \lambda)u_{i-1}, \quad i = 1, 2, \dots, \quad j = 1, 2, \dots, p,\)

with \(u_0 = 0\), and \(\lambda \in (0, 1]\), as before. Note, a \(\lambda\) with no subscript denotes the weight in the EWMA statistic, but with a subscript, it denotes an eigenvalue. Then, an IC process will have \(u_{i,j} \sim N(0, \sigma^2 = \frac{\lambda}{1-\lambda})\), and its squared standardized value is

\(d_{i,j} = \left( \frac{u_{i,j}}{\sqrt{\frac{\lambda}{1-\lambda}}} \right)^2 \sim \chi^2_{(1)}.\)

In an OC process with a mean shift, some of the \(d_{i,j}\) will become large, but Ebrahimi et al. [55] recommend filtering out some of the PCs. They simply threshold the \(d_{i,j}\) using the \(\alpha\) upper-tail quantile from the \(\chi^2_{(1)}\) distribution and monitor the new statistic,

\(R_i = \sum_{j=1}^p \left( d_{i,j} - \chi^2_{(1), \alpha} \right)_+, \quad\)

where \((\cdot)_+ = \max(0, \cdot)\). When \(R_i\) exceeds some threshold, then an alarm is issued, and this threshold is obtained through simulation under IC conditions to achieve a prespecified ARL.

Once a fault is detected, the second step is to integrate the PCs into the fault isolation. Assuming that each observation is measured with noise, the OC state can be represented as \(\mathbf{x}_i = \mu + \epsilon_i\) with \(\epsilon \sim (\mathbf{0}, \mathbf{\Sigma})\). Then, the OC PC scores are \(\mathbf{y}_i = \mathbf{A}\mathbf{x}_i = \mathbf{A}\mu + \tilde{\epsilon}\), with \(\tilde{\epsilon} = \mathbf{A}\epsilon\). The goal is to estimate a sparse \(\mu\), so this is done with adaptive lasso

\(\mu^* = \text{argmin}_{\mu} \left( (\mathbf{y}_i - \mathbf{A}\mu)'(\mathbf{y}_i - \mathbf{A}\mu) + \gamma \sum_{j=1}^p \frac{1}{\tilde{x}_j} |\mu_j| \right), \quad\)

where \(\tilde{x}_j\) is the least squares mean of the \(j\)th variable. However, the covariance of each variable in \(\mathbf{y}_i\) varies, so the standardized PC scores and PCs are used, written in matrix form, as follows:

\(\tilde{\mathbf{y}}_i = \mathbf{\Lambda}^{-1/2}\mathbf{y}_i, \quad \text{and} \quad \tilde{\mathbf{A}} = \mathbf{\Lambda}^{-1/2}\mathbf{A}.\)

Incorporating these into the adaptive lasso estimation yields the following objective function:

\(\mu^* = \text{argmin}_\mu \left( (\tilde{\mathbf{y}}_i - \tilde{\mathbf{A}}\mu)'(\tilde{\mathbf{y}}_i - \tilde{\mathbf{A}}\mu) + \gamma \sum_{j=1}^p \frac{1}{\tilde{x}_j} |\mu_j| \right) .\)

Ebrahimi et al. [55] test their method in simulation with values of \(p\) ranging from 100 to 10,000, so they are able to test very high-dimensional settings. In IC settings, the percentage of false detections is reported, and this reaches the nominal setting of \(\alpha = 0.05\) when \(p \ge 5000\). The ARL is computed for OC settings for varying shift magnitudes, and the APC-PCSR approach outperforms the benchmark comparison methods. The ability of the PCSR method to isolate shifted variables is also evaluated via several metrics, including

- false negative percentage (FN%)—the percentage of shifted variables not detected out of the total number of shifted variables;
- false positive percentage (FP%)—the percentage of the nonshifted variables identified out of the total number of nonshifted variables; and
- parameter selection score (PSS)—total number of variables incorrectly classified (either as shifted or nonshifted).

While the FN% is relatively low across multiple shift sizes and simulation settings, the FP% and PSS can be large for small shifts, but both decline rapidly as the shift size increases. PCSR performs similarly to [3], another lasso-based fault isolation method, for processes with nonsparse covariance matrices. However, PCSR is better if the process has a sparse covariance matrix, and the authors of [55] argue that such settings are common in practice since variables are usually only correlated with a small subset of the total monitored variables. Thus, APC-PCSR is a promising method to apply in high-dimensional settings, and its use is illustrated in a case study in Sect. 3.5.2. Jiang et al. [56] also reduce variables for use in PCA-based monitoring but with an optimization algorithm.

## Additional Phase II Fault Isolation Methods.

Many methods for Phase II fault isolation have been proposed for specific purposes. Jiang et al. [6] propose a variable selection multivariate EWMA (VS-MEWMA) chart that continues to use the \(L_0\) penalty of the VS-MSPC chart of [2]. Yan et al. [57] propose a VS-based control chart for high-dimensional Gaussian mixture models. Kuang et al. [58] incorporate VS into discriminant analysis for multivariate fault isolation. Various types of Kalman filters are used in [59] and [60] to detect and isolate sensor faults.

The Phase II VS-based control charts described herein assume that the mean and covariance matrix are known, so Li et al. [61] introduce a robust self-starting approach that reduces the number of IC observations needed to initiate the VS-MEWMA chart. Liang et al. [62] propose a version of the LEWMA [16] that can be applied to any continuous process generated within the family of elliptical distributions, performing better for heavy-tailed and skewed multivariate
