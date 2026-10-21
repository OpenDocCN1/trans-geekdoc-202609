natural logarithm. The logarithm of the likelihood function then is

$$L(l)=\sum_{i\in S_1}\log P(X_i,\beta)+\sum_{i\in S_2}\log\left(1-P(X_i,\beta)\right), \tag{126A.2}$$

where $S_1$ is the set of bankrupt firms; and $S_2$ is the set of non-bankrupt firms.

The maximum likelihood estimators for $\beta_s$ can be obtained by solving $\max_{\beta} L(l)$.

In logistic model, the probability of company $i$ going bankrupt given independent variables $X_i$ is defined as

$$P(X_i,\beta)=\frac{1}{1+\exp(-\beta'X_i)}. \tag{126A.3}$$

The two implications here are (1) $P(\cdot)$ is increasing in $\beta'X_i$ and (2) $\beta'X_i$ is equal to $\log\left[\frac{P}{(1-P)}\right]$.

We then classify bankrupt firms and non-bankrupt firms by setting a “cut-off” probability attempting to minimize Type I and Type II errors.

In probit models, the probability of company $i$ going bankrupt given independent variables $X_i$ is defined as

$$P(X_i,\beta)=\int_{-\infty}^{\beta'X_i}\frac{1}{\sqrt{2\pi}}e^{-z^2/2}\,dz, \tag{126A.4}$$

the cumulative standard normal distribution function.

Maximum likelihood estimators from probit model can obtained similarly as in the logistic models. Although probit models and logistic models are similar, logistic models are preferred to probit models due to the nonlinear estimation in probit models (Gloubos and Grammatikos, 1998).

Moreover, the MIDAS Logit model generalizes the simple Logit model and provides better prediction accuracy. The MIDAS Logit Regression introduces mixed-data sampling (MIDAS) aggregation to construct financial predictors in logistic regression. MIDAS regression is a rather new topic in statistics software where data with different frequencies are employed. In other words, a regression includes variables with combined frequencies, quarterly and annually. It is a rule of thumb that in the traditional methods, the estimation of dependent and independent variables should use the same frequency, and no combinations of higher or lower frequency are allowed. This rule becomes even more restrictive when panel data is used (to achieve strongly balanced panels).

The MIDAS Logit method allows for relaxing the limitation of conventional annual aggregation where an assumed equal weight of four quarters