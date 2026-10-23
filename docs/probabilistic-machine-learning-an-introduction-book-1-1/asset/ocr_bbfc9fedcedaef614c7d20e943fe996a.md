# 11.6.2.3 Posterior

With this prior and likelihood, one can show (see Sec. 7.2.4.4) that the posterior has the following form:

$p(\mathbf{w}, \sigma^2 | \mathcal{D}) = \text{NIG}(\mathbf{w}, \sigma^2 | \hat{\mathbf{w}}, \hat{\mathbf{\Sigma}}, \hat{a}, \hat{b})$ (11.137)
$\hat{\mathbf{w}} = \hat{\mathbf{\Sigma}} (\tilde{\mathbf{\Sigma}}^{-1} \tilde{\mathbf{w}} + \mathbf{X}^\top \mathbf{y})$ (11.138)
$\hat{\mathbf{\Sigma}} = (\tilde{\mathbf{\Sigma}}^{-1} + \mathbf{X}^\top \mathbf{X})^{-1}$ (11.139)
$\hat{a} = \tilde{a} + N/2$ (11.140)
$\hat{b} = \tilde{b} + \frac{1}{2} \left( \tilde{\mathbf{w}}^\top \tilde{\mathbf{\Sigma}}^{-1} \tilde{\mathbf{w}} + \mathbf{y}^\top \mathbf{y} - \hat{\mathbf{w}}^\top \hat{\mathbf{\Sigma}}^{-1} \hat{\mathbf{w}} \right)$ (11.141)

The expressions for $\tilde{\mathbf{w}}$ and $\hat{\mathbf{\Sigma}}$ are similar to the case where $\sigma^2$ is known. The expression for $\hat{a}$ is also intuitive, since it just updates the counts. The expression for $\hat{b}$ can be interpreted as follows: it is the prior sum of squares, $\tilde{b}$, plus the empirical sum of squares, $\mathbf{y}^\top \mathbf{y}$, plus a term due to the error in the prior on $\mathbf{w}$. (If we set $\mathbf{X}=1$ and $\mathbf{w}=\mu$, we recover the results in Sec. 7.2.3.3 for inferring $p(\mu, \sigma^2 | \mathcal{D})$.)

The posterior marginals are as follows. For the variance, we have

$p(\sigma^2 | \mathcal{D}) = \int p(\mathbf{w} | \sigma^2, \mathcal{D}) p(\sigma^2 | \mathcal{D}) d\mathbf{w} = \text{IG}(\sigma^2 | \hat{a}, \hat{b})$ (11.142)

For the regression weights, it can be shown that

$p(\mathbf{w} | \mathcal{D}) = \int p(\mathbf{w} | \sigma^2, \mathcal{D}) p(\sigma^2 | \mathcal{D}) d\sigma^2 = \mathcal{T}\left(\mathbf{w} | \hat{\mathbf{w}}, \frac{\hat{b}}{\hat{a}} \hat{\mathbf{\Sigma}}, 2\hat{a}\right)$ (11.143)

We give a worked example of using these equations in Sec. 11.6.3.2.

# 11.6.2.4 Posterior predictive distribution

In machine learning we usually care more about uncertainty (and accuracy) of our predictions, not our parameter estimates. Fortunately, one can derive the posterior predictive distribution in closed form. In particular, one can show that, given $N'$ new test inputs $\tilde{\mathbf{X}}$, we have

$p(\tilde{\mathbf{y}} | \tilde{\mathbf{X}}, \mathcal{D}) = \iint p(\tilde{\mathbf{y}} | \tilde{\mathbf{X}}, \mathbf{w}, \sigma^2) p(\mathbf{w}, \sigma^2 | \mathcal{D}) d\mathbf{w} d\sigma^2$ (11.144)
$= \iint \mathcal{N}(\tilde{\mathbf{y}} | \tilde{\mathbf{X}} \mathbf{w}, \sigma^2 \mathbf{I}_{N'}) \text{NIG}(\mathbf{w}, \sigma^2 | \hat{\mathbf{w}}, \hat{\mathbf{\Sigma}}, \hat{a}, \hat{b}) d\mathbf{w} d\sigma^2$ (11.145)
$= \mathcal{T}\left(\tilde{\mathbf{y}} | \tilde{\mathbf{X}} \hat{\mathbf{w}}, \frac{\hat{b}}{\hat{a}} (\mathbf{I}_{N'} + \tilde{\mathbf{X}} \hat{\mathbf{\Sigma}} \tilde{\mathbf{X}}^\top), 2\hat{a}\right)$ (11.146)

The posterior predictive mean is equivalent to “normal” linear regression, but where we plug in $\hat{\mathbf{w}} = \mathbb{E}[\mathbf{w} | \mathcal{D}]$ instead of the MLE. The posterior predictive variance has two components: $\hat{b}/\hat{a} \mathbf{I}_{N'}$ due to the measurement noise, and $\hat{b}/\hat{a} \tilde{\mathbf{X}} \hat{\mathbf{\Sigma}} \tilde{\mathbf{X}}^\top$ due to the uncertainty in $\mathbf{w}$. This latter term varies depending on how close the test inputs are to the training data. The results are similar to using a Gaussian prior (with fixed $\sigma^2$), illustrated in Fig. 11.19(b), except the predictive distribution is even wider, since we are taking into account uncertainty about $\sigma^2$.