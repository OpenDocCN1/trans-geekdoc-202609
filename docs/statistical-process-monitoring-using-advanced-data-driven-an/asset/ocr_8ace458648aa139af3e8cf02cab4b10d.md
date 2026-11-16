```
\(\mathbf{u}_i = \begin{cases} \mathbf{0}, & \text{if } \mathbf{z}_i = \mathbf{0}, \\ F_{\chi_p^2}^{-1} \left( \frac{g_i}{1+n} \right) \frac{\mathbf{z}_i}{\|\mathbf{z}_i\|}, & \text{if } \mathbf{z}_i \neq \mathbf{0}, \end{cases}\)
```

where \(\|\mathbf{v}\| = \sqrt{\mathbf{v}'\mathbf{v}}\) is the Euclidean norm of \(\mathbf{v}\); \(g_i\) is the rank of \(\{\|\mathbf{z}_1\|, \dots, \|\mathbf{z}_n\|\}\); and \(F_{\chi_p^2}^{-1}(\cdot)\) is the quantile function of a \(\chi^2\) random variable with \(p\) degrees of freedom. A version for subgrouped data is given in [8,40].

+   2. Screening. Next, an initial screening process using forward selection identifies \(K\) locations where a fault is most likely to have occurred, where \(K\) is either selected by the user or is chosen to be the minimum of 50 and the integer closest to \(\sqrt{n}\). For the \(k\)th iteration, \(k=1, 2, \dots, K\), of the forward selection process, an additional shift at time step \(i=2, \dots, n-1\) is added to the model. This time step is chosen as that with the minimum residual sum of squares conditional on the previously identified \(k-1\) shifts, namely \(\sum_{i=1}^n ||\mathbf{u}_i - \hat{\mathbf{u}}_i^{(k)}||^2\), where \(\hat{\mathbf{u}}_i^{(k)}\) comes from a model fitted with a potentially different mean vector at each time point. Shifts within \(l_{\min}\) time steps of the \(k-1\) shifts already present are not considered. After each step, the explained variance is computed as

```
\(T_k = \sum_{i=1}^n ||\hat{\mathbf{u}}_i^{(k)}||^2 - n||\bar{\mathbf{u}}||^2,\)
```

where \(\bar{\mathbf{u}}\) is the overall mean of the signed ranks.

+   3. Testing. Then, \(T_k, k=1, \dots, K\), test statistics are aggregated to form a single test statistic as follows:

```
\(W_{\text{OBS}} = \max_{k=1, \dots, K} \frac{T_k - \text{E}_0(T_k)}{\sqrt{\text{Var}_0(T_k)}}.\)
```

The expected value and variance of \(T_k\) are estimated with the sample mean and variance of \(T_k\), respectively. A permutation-based \(p\)-value is computed by permuting the iid observations to test the null hypothesis that the process does not display any step or isolated shifts and is stable in its location.

+   4. Post-signal diagnostic. If the null hypothesis is rejected, fault isolation is performed via adaptive lasso to further prune the estimated coefficients from the forward selection screening process, which are used as initial estimates [35]. Adaptive lasso drives some of the small shifts to zero. The particular model fit is as follows: \(\mathbf{u}_i = \mathbf{S}_r^{-1/2}\delta_0 + \mathbf{S}_r^{-1/2}\delta_1\xi_i^{(1)} + \cdots + \mathbf{S}_r^{-1/2}\delta_K\xi_i^{(K)} + \epsilon_i\). Here, \(\delta_0\) is the intercept while \(\delta_1, \dots, \delta_K\) are the directions of the potential location shifts to be estimated, and \(\xi_i^{(k)} = I(i \ge \tau^{(k)}), k=1, \dots, K\), corresponds to a step shift at time \(\tau^{(k)}\). Then, the penalized objective function to minimize is

```
\(\sum_{i=1}^n ||\mathbf{u}_i - \mathbf{S}_r^{-1/2}\delta_0 - \sum_{k=1}^K \mathbf{S}_r^{-1/2}\delta_k \xi_i^{(k)}||^2 + \gamma \sum_{k=1}^K \sum_{h=1}^g \left| \frac{\delta_{k,h}}{\hat{c}_{k,h}^s} \right|, \quad (3.7)\)
```