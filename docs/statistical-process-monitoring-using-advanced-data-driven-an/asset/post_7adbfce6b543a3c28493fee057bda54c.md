
Commonly chosen options for \( g_{\gamma_j}(\cdot) \) include

- \( L_0 \) penalty. The \( L_0 \) penalty is \( g_{\gamma_j}(\cdot) = \gamma \cdot I(|\beta_j| \neq 0) \), making the second term in Eq. (3.6) equal to \( \gamma \sum_{j=1}^p I(\beta_j \neq 0) \). This penalty constrains the number of predictors that can enter the model to be less than a prespecified number, denoted \( s \).

- \( L_1 \) penalty. The \( L_1 \) penalty is \( g_{\gamma_j}(\cdot) = \gamma \cdot |\beta_j| \), making the second term in Eq. (3.6) equal to \( \gamma \sum_{j=1}^p |\beta_j| \). This then corresponds to the least absolute shrinkage and selection operator (lasso) proposed by [34]. As \( \gamma \rightarrow 0 \), the estimator converges to the least squares estimator of \( \boldsymbol{\beta} \).

- Weighted \( L_1 \) penalty. This penalty weights the coefficients by an initial estimate of the coefficients, as follows:
  \( g_{\gamma_j}(\cdot) = \gamma \frac{|\tilde{\beta}_j|}{|\tilde{\beta}_j|^\alpha}, \)

where \( \tilde{\beta}_j \) is the initial estimate of \( \beta_j \), which can be the least squares estimate, and \( \alpha > 0 \) is a prespecified constant. It is often recommended to set \( \alpha = 1 \) [35, 36]. This weighted penalty corresponds to what is called *adaptive lasso*, and the weight allows for different shrinkage to be applied to different predictors, forcing those with already small coefficients to be driven to zero even faster. Adaptive lasso produces asymptotically unbiased coefficient estimates and has oracle properties, meaning it identifies the correct subset of variables and has an optimal estimation rate [35,37].

![](img/aa2f42c739937b682075082233e335bb_95_0.png)

**FIGURE 3.4** Values of the coefficients in a linear model as \( \gamma \) increases.

An excellent overview of lasso and its extensions is given in [38], and a coefficient path as \( \gamma \) changes is shown in Fig. 3.4 to illustrate the impact of \( \gamma \) on the coefficients. Choosing \( \gamma \) can be done through cross-validation. In Fig. 3.4, the dashed vertical line shows \( \gamma_{se} \), which is the largest value of \( \gamma \) such that the squared error is within one standard error of the minimum. At this point, three predictors remain in the model out of the initial 17 that were included in the fit.

To employ variable selection techniques for fault isolation, the multiple linear regression model is reframed so that the mean vector is being monitored and those variables whose mean is unchanged are filtered out. Several variations of the penalties presented here have also been employed, and a few specific methods will be presented in the following subsections.

### 3.2.3.1 Phase I variable selection

One of the primary goals of a Phase I analysis is to test whether a set of observations could reasonably be expected to come from an IC process. As such, data used in a Phase I analysis could be contaminated by multiple faults simultaneously. A secondary goal may be to retrospectively analyze a fault or multiple faults that occurred so that operators may begin to diagnose them. We present an example of each type of analysis in this section.

Example method 1, mphase1. Capizzi and Masarotto [8] developed a distribution-free retrospective change point detection method designed to test for multiple change-points over a given period of time, called mphase1. Their approach is designed to first test whether the period of time under consideration is IC; if not, then the shifted variables can be identified, along with their shift sizes and directions. Their method assumes that the observations are iid when the process is IC. It also allows for subgrouped data, in which multiple realizations of the process are present at a single time points. This allows the user to detect outlying observations at a single isolated time point in addition to detecting step shifts. For simplicity, we ignore the potential presence of subgrouped observations in our description of the method.

A user-friendly R package called dfphase1 contains code to implement mphase1 [8]. It is not assumed that data from an IC period exists. The following steps are performed:

- 1. Standardization. The data are standardized and transformed to the multivariate signed ranks using a robust estimate of the center and spread. For the location estimate, \( \ell \), the transformation–retransformation spatial median is applied to subgroup means [39]. For the spread, a robust scatter matrix, \( \mathbf{S}_r \), is constructed as

![](img/aa2f42c739937b682075082233e335bb_96_0.png)

Then, they use \( \ell \) and \( \mathbf{S}_r \) to standardize the data, \( \mathbf{z}_i = \mathbf{S}_r^{-1/2} (\mathbf{x}_i - \ell) \), and compute the multivariate signed ranks \( \mathbf{u}_i \) as follows:

\(\mathbf{u}_i = \begin{cases} \mathbf{0}, & \text{if } \mathbf{z}_i = \mathbf{0}, \\ F_{\chi_p^2}^{-1} \left( \frac{g_i}{1+n} \right) \frac{\mathbf{z}_i}{\|\mathbf{z}_i\|}, & \text{if } \mathbf{z}_i \neq \mathbf{0}, \end{cases}\)

where \( \|\mathbf{v}\| = \sqrt{\mathbf{v}'\mathbf{v}} \) is the Euclidean norm of \( \mathbf{v} \); \( g_i \) is the rank of \( \{\|\mathbf{z}_1\|, \dots, \|\mathbf{z}_n\|\} \); and \( F_{\chi_p^2}^{-1}(\cdot) \) is the quantile function of a \( \chi^2 \) random variable with \( p \) degrees of freedom. A version for subgrouped data is given in [8,40].

- 2. Screening. Next, an initial screening process using forward selection identifies \( K \) locations where a fault is most likely to have occurred, where \( K \) is either selected by the user or is chosen to be the minimum of 50 and the integer closest to \( \sqrt{n} \). For the \( k \)th iteration, \( k=1, 2, \dots, K \), of the forward selection process, an additional shift at time step \( i=2, \dots, n-1 \) is added to the model. This time step is chosen as that with the minimum residual sum of squares conditional on the previously identified \( k-1 \) shifts, namely \( \sum_{i=1}^n ||\mathbf{u}_i - \hat{\mathbf{u}}_i^{(k)}||^2 \), where \( \hat{\mathbf{u}}_i^{(k)} \) comes from a model fitted with a potentially different mean vector at each time point. Shifts within \( l_{\min} \) time steps of the \( k-1 \) shifts already present are not considered. After each step, the explained variance is computed as

\(T_k = \sum_{i=1}^n ||\hat{\mathbf{u}}_i^{(k)}||^2 - n||\bar{\mathbf{u}}||^2,\)

where \( \bar{\mathbf{u}} \) is the overall mean of the signed ranks.

- 3. Testing. Then, \( T_k, k=1, \dots, K \), test statistics are aggregated to form a single test statistic as follows:

\(W_{\text{OBS}} = \max_{k=1, \dots, K} \frac{T_k - \text{E}_0(T_k)}{\sqrt{\text{Var}_0(T_k)}}.\)

The expected value and variance of \( T_k \) are estimated with the sample mean and variance of \( T_k \), respectively. A permutation-based \( p \)-value is computed by permuting the iid observations to test the null hypothesis that the process does not display any step or isolated shifts and is stable in its location.

- 4. Post-signal diagnostic. If the null hypothesis is rejected, fault isolation is performed via adaptive lasso to further prune the estimated coefficients from the forward selection screening process, which are used as initial estimates [35]. Adaptive lasso drives some of the small shifts to zero. The particular model fit is as follows: \( \mathbf{u}_i = \mathbf{S}_r^{-1/2}\delta_0 + \mathbf{S}_r^{-1/2}\delta_1\xi_i^{(1)} + \cdots + \mathbf{S}_r^{-1/2}\delta_K\xi_i^{(K)} + \epsilon_i \). Here, \( \delta_0 \) is the intercept while \( \delta_1, \dots, \delta_K \) are the directions of the potential location shifts to be estimated, and \( \xi_i^{(k)} = I(i \ge \tau^{(k)}), k=1, \dots, K \), corresponds to a step shift at time \( \tau^{(k)} \). Then, the penalized objective function to minimize is

\(\sum_{i=1}^n ||\mathbf{u}_i - \mathbf{S}_r^{-1/2}\delta_0 - \sum_{k=1}^K \mathbf{S}_r^{-1/2}\delta_k \xi_i^{(k)}||^2 + \gamma \sum_{k=1}^K \sum_{h=1}^g \left| \frac{\delta_{k,h}}{\hat{c}_{k,h}^s} \right|, \quad (3.7)\)
