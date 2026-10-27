
portfolio performance instead of \(R^2\) are quite limited, at least in this specific setting. But they also illustrate once more that \(R^2\) measures can be quite misleading as indicators of portfolio performance.

The bottom line conclusion from this section is that the effects of regularization on \(R^2\) and portfolio performance in validation data are sensitive to the scaling of covariates. For regularization to be effective, we need to bring in some prior knowledge about the likely relative importance of different covariates in the prediction task. This raises the question of how we might come up with prior beliefs that can help us scale covariates appropriately to make regularization effective. As the next section shows, financial economics suggests links between covariances and expected returns, and these links can help us pin down how we should regularize.

### 3.4 Links between Expected Returns and Covariances

The Bayesian regression framework we discussed in Section 2.4 allows us to tackle the question of covariate scaling by showing how economic links between expected returns and covariances relate to regularization. Recall that for a cross-sectional regression model \(\bar{r}=Xg+\bar{e}\) with a prior \(g \sim N(0, \Sigma_g)\), where \(\bar{r}\) and \(\bar{e}\) are averages of \(r_t\) and \(e_t\) from a sample of size \(\tau\), and \(\Sigma = \operatorname{var}(e_t)\), we get the posterior mean

\[
\hat{g}=\left( X'\Sigma^{-1}X + \frac{1}{\tau}\Sigma_g^{-1} \right)^{-1} X'\Sigma^{-1}\bar{r}. \tag{3.21}
\]

Within this framework, we now look for a specification of \(X\) and prior beliefs about \(g\) that are economically sensible. For this purpose, we also need a more realistic specification of the covariance matrix. The assumption that \(\Sigma = I_N \sigma^2\) that we worked with above is sometimes useful for illustration, but not a realistic property of asset returns. Here we let \(\Sigma\) have a general form. As before, we still assume that \(\Sigma\) is known and does not need to be estimated.

Economic reasoning suggests that covariates that predict returns should be related to stock return covariances. Specifically, the link to the covariance matrix should be such that if a long-short portfolio formed based on the values of a covariate produces a substantial mean return, it should also have substantial return volatility. For example, if small firm size predicts high returns, then a portfolio that takes a long position in small stocks and a short position in large stocks should have substantial volatility. This requires covariance risk exposure in the sense that small stocks co-move with each other more than with large stocks and large stocks co-move with each other more than with small stocks. This within-group comovement prevents risk from diversifying away with the consequence that a long-short portfolio then has relatively high return variance. As Kozak, Nagel, and Santosh (2018) discuss, such links between mean returns and covariances are predicted by a wide range of asset pricing models, including ones with rational investors and ones that include investors whose asset demand is driven by sentiment or behavioral biases. If such links between expected returns and covariances were absent, economically implausible near-arbitrage opportunities would exist.

To arrive at a particularly transparent result, we specify this link between return-predicting covariates and covariances through the somewhat stark assumption that the \(K\) vectors of covariates used to predict returns are equal to \(K\) eigenvectors of \(\Sigma\). Let \(\Sigma = Q\Lambda Q'\) be the eigendecomposition of \(\Sigma\) and let \(Q_K\) be a selection of \(K\) columns of the orthogonal matrix \(Q\). We then assume that \(X = Q_K\), which implies \(X'X = I_K\). The assumption that covariates are exactly equal to the eigenvectors is, of course, a strong assumption, but it will give us a particularly clear result.

Since the portfolio weights are based on eigenvectors, or principal components, of the return covariance matrix, we label them principal component (PC) portfolios. The PC portfolios have expected returns and variance

\[
\mathbb{E}[Q_K'r_t] = g, \qquad \operatorname{var}(Q_K'r_t) = \Lambda_K, \tag{3.22}
\]

where \(\Lambda_K\) is a diagonal matrix with the \(K\) eigenvalues corresponding to the \(K\) eigenvectors in \(Q_K\) on its diagonal.

We are now in a position to specify economically motivated prior beliefs about \(g\). For this purpose, it is useful to note that the Sharpe ratios associated with each of these \(K\) PC portfolio returns, \(r_p = Q_K'r_t\), are \(\Lambda_K^{-1/2}g\). An assumption about these Sharpe ratios that has some economic plausibility—more on this in the next chapter—is that high Sharpe ratios are concentrated among PC portfolios that have relatively high variance. Here this would mean that the Sharpe ratio vector \(\Lambda_K^{-1/2}g\) is likely to take on greater magnitudes for those elements \(j\) associated with high \(\lambda_j\). Prior beliefs

\[
g \sim N(0, \gamma^{-1}\Lambda_K^2), \qquad 0 < \gamma < 1, \tag{3.23}
\]

would be consistent with this reasoning because they imply prior beliefs about the Sharpe ratio vector \(\Lambda_K^{-1/2}g \sim N(0, \gamma^{-1}\Lambda_K)\). This prior distribution for the Sharpe ratio vector allows for greater magnitude (positive or negative) of Sharpe ratios for those portfolio returns in \(r_p = Q_K'r_t\) that are based on columns of \(Q_K\) (or \(X\)) associated with high \(\lambda_j\).

Proceeding with this assumption, the hyperparameter \(\gamma\) now has an economic interpretation as controlling the expected squared Sharpe ratio under prior beliefs. To see this, note that the maximum squared Sharpe

have to change the prior about \(g\) accordingly. For example, if we divide covariate \(j\) by a constant \(c\), we have to multiply the corresponding coefficient \(g_j\) in our prior by \(c\), which means multiplying its variance in the prior distribution by \(c^2\). As a consequence, the posterior mean of \(\mu\) would remain invariant to such rescaling. We revisit these questions again in the next chapter within a more general framework. This framework will allow us to specify prior beliefs in an empirically plausible way.

### 3.5 Return Covariances and Portfolio Aggregation

Covariances of prediction errors play a much bigger role in asset pricing than in typical ML applications. If our aim is to use a return prediction model to form a portfolio with high return relative to the level of risk, the covariance matrix of the unpredictable component of returns plays an important role.

While we have assumed so far that the covariance matrix is known, in practice it must be estimated. This introduces an additional layer of estimation errors that can lead to substantial problems in portfolio construction. In the extreme case, if one wanted to work with thousands of individual stocks, finding the mean–variance efficient combination of these stocks would require an estimate of a huge covariance matrix with millions of elements. Estimating this covariance matrix would be difficult without imposing substantial constraints on its functional form or some form of shrinkage estimation applied to the covariance matrix. Moreover, typical individual stock return data sets are unbalanced panels that may be difficult to work with for the purpose of covariance matrix estimation. Finally, in data sets spanning many years or decades, an individual stock’s covariance properties are likely to change over time as the firm’s characteristics change.

For this reason, it can make sense to first aggregate stocks into portfolios based on the covariates of the return prediction model. If the characteristics that we use to form portfolios are related to stocks’ covariance exposures, the covariances of portfolios could be much more stable than covariances of individual stocks. And portfolio aggregation should help with covariance matrix estimation, at least as long as the number of covariates is smaller than the number of assets, i.e., \(K < N\).

What would be ideal conditions under which we can aggregate into these portfolios, and hence get these benefits, without negatively affecting the investment opportunities in terms of the maximum squared Sharpe ratio? To make this more concrete, assume again, as earlier in (3.4), that returns are generated as \(r = Xg + \varepsilon\), with a predictable component \(\mu = Xg\). Consider covariate-weighted portfolios with realized return \(r_p = X' r\),
