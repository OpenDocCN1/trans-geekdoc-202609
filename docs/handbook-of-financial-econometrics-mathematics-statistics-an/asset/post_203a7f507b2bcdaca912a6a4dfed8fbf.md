
It is worth noting that none of the structural covariance matrices mentioned above is directly linked to auxiliary information, such as explanatory variables, spatial information, and social network. To this end, Zou *et al.* (2017) proposed a novel covariance regression model to study the relationship between the covariance matrix of responses and their associated similarity matrices induced by auxiliary information. Their method can not only explain the structure of the covariance matrix via the auxiliary information, but also can allow us to estimate the covariance matrix consistently. Accordingly, we employ the covariance regression model to investigate the stock return comovement and herding effect of mutual funds.

Due to complications of theoretical derivations, Zou *et al.* (2017) imposed the normality assumption on the response variable for inference in the covariance regression model. To broaden the usefulness of the covariance regression model in finance and accounting, we relax the normality assumption. Then we apply Lee’s (2004) approach to obtain inferences for covariance regression parameters based on the five estimators proposed by Zou *et al.* (2017), which are the maximum likelihood, ordinary least squares, constrained ordinary least squares, feasible generalized least squares and constrained feasible generalized least squares estimators.

The remainder of this chapter is organized as follows. Section 113.2 introduces covariance regression models. Section 113.3 proposes the estimation and inference procedure, while Section 113.4 presents two real examples to illustrate the usefulness of the covariance regression model in analyzing stock return comovement and herding behavior of mutual funds. Section 113.5 concludes the article with discussions.

## 113.2 Covariance Regression Model

Let \(Y=(Y_1,\ldots,Y_p)^T\in\mathbb{R}^p\) be the response vector including \(p\) components. For each component \(j\), let \(X_j=(X_{j1},\ldots,X_{jm})^T\in\mathbb{R}^m\) be the associated \(m\)-dimensional auxiliary information vector. In finance and accounting, \(Y_j\) can be the \(j\)th firm’s stock return and \(X_j\) are its corresponding attributes, including the industry, location, market value, book-to-market ratio, cash flow, etc. In addition, we assume that \(Y\) follows a multivariate normal distribution with mean 0 and covariance matrix \(\Sigma=\operatorname{cov}(Y)\).

Adopting Zou *et al.*’s (2017) approach, we consider the covariance regression model given below,

\[
\Sigma=\Sigma(\beta)=\beta_0 I_p+\beta_1 W_1+\cdots+\beta_m W_m,\tag{113.1}
\]

**Step II.** To ensure the positive definiteness of \(\Sigma(\beta)\), we employ Zou *et al.*’s (2017) Algorithm 1 to obtain the constrained OLS (OLS+) estimator \(\hat{\beta}_{p,\mathrm{OLS+}} = \arg\min_{\beta\in\mathcal{B}} D_p(\beta)\). Note that one can use \(\hat{\beta}_{p,\mathrm{OLS}}\) as the initial value in this iterative algorithm.

**Step III.** Obtain the unconstrained FGLS estimator \(\hat{\beta}_{p,\mathrm{FGLS}}\) by minimizing

\[
\tilde{D}_p(\beta) := \operatorname{vec}^T(YY^T - \Sigma(\beta))(\hat{\Sigma}^{-1} \otimes \hat{\Sigma}^{-1})\operatorname{vec}(YY^T - \Sigma(\beta)), \tag{113.5}
\]

where \(\hat{\Sigma}^{-1} = \Sigma^{-1}(\hat{\beta}_{p,\mathrm{OLS+}})\) is a consistent estimator of \(\Sigma^{-1}\), \(\otimes\) represents the Kronecker product of two matrices, and \(\operatorname{vec}(G)\) denotes the vectorization for any generic matrix \(G\). After simple algebraic simplification, (113.5) can be re-expressed as

\[
\tilde{D}_p(\beta) := \|\hat{\Sigma}^{-1/2} YY^T \hat{\Sigma}^{-1/2} - \hat{\Sigma}^{-1/2} \Sigma(\beta) \hat{\Sigma}^{-1/2}\|_F^2. \tag{113.6}
\]

Then consider the following transformations \(\tilde{Y} = \hat{\Sigma}^{-1/2} Y\), \(\tilde{W}_k = \hat{\Sigma}^{-1/2} W_k \hat{\Sigma}^{-1/2}\), and \(\tilde{\Sigma}(\beta) = \sum_{k=0}^m \beta_k \tilde{W}_k\). It can be demonstrated that the unconstrained FGLS estimator \(\hat{\beta}_{p,\mathrm{FGLS}}\), obtained from the objective function (113.5) via \(\{Y, \Sigma(\beta)\}\), is the same as the unconstrained OLS estimator, \(\hat{\beta}_{p,\mathrm{OLS}}\), obtained from the objective function (113.3) via the transformed \(\{\tilde{Y}, \tilde{\Sigma}(\beta)\}\).

**Step IV.** To ensure the positive definiteness, the resulting constrained FGLS (FGLS+) estimator, \(\hat{\beta}_{p,\mathrm{FGLS+}} = \arg\min_{\beta\in\mathcal{B}} \tilde{D}_p(\beta)\) obtained from the objective function (113.5) via \(\{Y, \Sigma(\beta)\}\), is the same as the constrained OLS estimator, \(\hat{\beta}_{p,\mathrm{OLS+}}\), obtained from the objective function (113.3) via the transformed \(\{\tilde{Y}, \tilde{\Sigma}(\beta)\}\). Note that one can use \(\hat{\beta}_{p,\mathrm{FGLS}}\) as the initial value in the iterative algorithm. Instead of the constrained FGLS estimator, Zou *et al.* (2017) proposed the maximum likelihood estimation (MLE) approach. Specifically, under the assumption that \(Y\) follows a multivariate normal distribution with mean 0 and covariance \(\Sigma(\beta) = \operatorname{cov}(Y)\), the maximum likelihood estimator \(\hat{\beta}_{p,\mathrm{MLE}}\) can be obtained by maximizing the following log-likelihood function,

\[
\ell_p(\beta) = -\frac{p}{2} \log(2\pi) - \frac{1}{2} \sum_{j=1}^p \log \lambda_j(\Sigma(\beta)) - \frac{1}{2} Y^T \Sigma^{-1}(\beta) Y, \tag{113.7}
\]

where \(\lambda_j(\Sigma(\beta))\) are the \(j\)th largest eigenvalues of \(\Sigma(\beta)\) for \(j = 1, \ldots, p\). Although the MLE is asymptotically efficient under the normality assumption, it becomes computationally infeasible when \(p\) gets large. This is mainly due to computational burden of \(O(p^4)\) pointed out by Zou *et al.* (2017). It is worth noting that the OLS method alleviates the computational complexity, but the estimators \(\hat{\beta}_{p,\mathrm{OLS}}\) and \(\hat{\beta}_{p,\mathrm{OLS+}}\) are not efficient. Accordingly, Zou *et al.* (2017) proposed the constrained FGLS estimator mentioned above, which not only mitigates the computational complexity, but also achieves the same estimation efficiency as that of MLE. This is exactly the reason why they recommended the constrained FGLS estimator instead of MLE in real practice.

### 113.3.2 Inference for non-normal response

One limitation of Zou *et al.* (2017) is that the inferences of the aforementioned five estimators are relying on the normality assumption of responses. However, in the areas of finance and accounting, one may have heavy-tailed data, which are not necessarily normally distributed. This motivates us to extend the application of the covariance regression model by relaxing this assumption. To this end, we employ Lee’s (2004) approach to obtain the inference for all five estimators when the response is not necessarily normally distributed. Note that the unconstrained/constrained OLS and FGLS estimators are still applicable since they do not rely on the normality assumption. Moreover, maximizing the log-likelihood function (113.7) evaluated under the normal assumption can still lead to a consistent estimator even if the responses are not truly normally distributed. Lee (2004) called this method quasi-maximum likelihood estimation (QMLE), and we rename the resulting estimator by \(\hat{\beta}_{p,\mathrm{QMLE}}\). Applying similar techniques to those used in Zou *et al.* (2017) and Lee (2004), we obtain the asymptotic distributions of the unconstrained/constrained OLS and FGLS estimators and QMLE, for the non-normal responses.

Assume that, for \(d = -1, 0, 1\),

\[
\frac{1}{p}\left(\operatorname{tr}(\Sigma^{d}W_{k1}\Sigma^{d}W_{k2})\right)_{(m+1)\times(m+1)} \to Q_{d}\in\mathbb{R}^{(m+1)\times(m+1)} \quad\text{and}\tag{113.8}
\]

\[
\frac{1}{p}\left(\operatorname{tr}\left\{\left(\Sigma^{d/2}W_{k1}\Sigma^{d/2}\right)\circ\left(\Sigma^{d/2}W_{k2}\Sigma^{d/2}\right)\right\}\right)_{(m+1)\times(m+1)} \to P_{d}\in\mathbb{R}^{(m+1)\times(m+1)},\tag{113.9}
\]

where \(\circ\) represents the Hadamard product of two matrices, and \(Q_d\) are \((m+1)\times(m+1)\) positive definite matrices for \(d=-1,0,1\). In addition, let \(Z = \Sigma^{-1/2}Y = (Z_j)_{p\times1} \in \mathbb{R}^p\) and define the fourth-order moment \(\mu^{(4)} = E(Z_j^4)\) for \(j = 1, \ldots, p\). Then, under some mild conditions, one can prove that the unconstrained/constrained OLS estimator is asymptotically normal with mean 0 and covariance \(2p^{-1}Q_0^{-1}Q_1Q_0^{-1} + p^{-1}(\mu^{(4)}-3)Q_0^{-1}P_1Q_0^{-1}\) as \(p \to \infty\). In addition, the unconstrained/constrained FGLS estimator is asymptotically normal with mean 0 and covariance matrix \(2p^{-1}Q_{-1}^{-1} + p^{-1}(\mu^{(4)}-3)Q_{-1}^{-1}P_{-1}Q_{-1}^{-1}\) as \(p \to \infty\). Moreover, the QMLE \(\hat{\beta}_{p,\mathrm{QMLE}}\) is asymptotically normal with mean 0 and covariance matrix \(2p^{-1}Q_{-1}^{-1} + p^{-1}(\mu^{(4)}-3)Q_{-1}^{-1}P_{-1}Q_{-1}^{-1}\) as \(p \to \infty\). Consequently, the constrained FGLS estimator and the QMLE still have the same asymptotic efficiency for non-normal response. But it has been pointed out at the end of Section 113.3.1 that the constrained FGLS estimator is computationally more feasible. Hence, we recommend using the constrained FGLS estimator in real practice.

To make inferences about the above five covariance regression parameter estimators, one needs to estimate their corresponding asymptotic covariance matrices. To this end, we propose to estimate them via (113.8) and (113.9) evaluated at \(\hat{\Sigma} = \Sigma(\hat{\beta})\), where \(\hat{\beta}\) can be one of the above five parameter estimators. In addition, \(\mu^{(4)}\) can be estimated by its empirical fourth-order moment of the vector \(\hat{Z} = \hat{\Sigma}^{-1/2}Y\). Accordingly, one can test the significance of regression parameters and assess the effect of the covariates on the covariance structure.

## 113.4 Real Data Analysis

In this section, we present two empirical examples to illustrate the usefulness of the covariance regression model via the US and Chinese stock markets, respectively. Example I employs the covariance regression model to study stock return comovement in the US stock market, while Example II investigates the herding behavior of mutual funds in the Chinese stock market. In both studies, we apply the constrained FGLS approach, recommended by Zou *et al.* (2017), to estimate the covariance regression model and obtain their associated standard errors without assuming the normality of responses.

### 113.4.1 Example I: Stock return comovement

Finding highly associated stocks whose returns move together is not only essential for studying asset pricing theory and asset allocation strategies (see, e.g., Green and Hwang, 2009), but also for implementing a pairs trading strategy (see, e.g., Gatev *et al.* 2006). “Moving together” refers to the similar response of these stock returns to market-wide information such as in the capital asset pricing model (CAPM) of Sharpe (1964) and Fama–French
