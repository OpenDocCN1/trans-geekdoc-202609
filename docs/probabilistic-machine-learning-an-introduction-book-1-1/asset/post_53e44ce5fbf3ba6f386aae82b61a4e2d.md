
Then we have

$$\mathbb{V}[X] = \mathbb{E}[X^2] - (\mathbb{E}[X])^2 = \mathbb{E}[s_{X|Y}|Y] - (\mathbb{E}[\mu_{X|Y}|Y])^2 \tag{D.38}$$ $$= \mathbb{E}[\sigma_{X|Y}^2|Y] + \mathbb{E}[\mu_{X|Y}^2|Y] - (\mathbb{E}[\mu_{X|Y}|Y])^2 \tag{D.39}$$ $$= E_Y[\mathbb{V}[X|Y]] + \mathbb{V}_Y[\mu_{X|Y}] \tag{D.40}$$

To get some intuition for these formulas, consider a mixture of $K$ univariate Gaussians. Let $Y$ be the hidden indicator variable that specifies which mixture component we are using, and let $X = \sum_{y=1}^K \pi_y \mathcal{N}(X|\mu_y, \sigma_y)$. In Fig. D.4, we have $\pi_1 = \pi_2 = 0.5$, $\mu_1 = 0$, $\mu_2 = 2$, $\sigma_1 = \sigma_2 = 0.5$. Thus

$$\mathbb{E}[\mathbb{V}[X|Y]] = \pi_1\sigma_1 + \pi_2\sigma_2 = 0.5 \tag{D.41}$$ $$\mathbb{V}[\mathbb{E}[X|Y]] = \pi_1(\mu_1 - \bar{\mu})^2 + \pi_2(\mu_2 - \bar{\mu})^2 = 0.5(0 - 1)^2 + 0.5(2 - 1)^2 = 0.5 + 0.5 = 1 \tag{D.42}$$

So we get the intuitive result that the variance of $Y$ is dominated by which centroid it is drawn from (i.e., difference in the means), rather than the local variance around each centroid.

## D.4.2 Covariance

The covariance between two rv's $X$ and $Y$ measures the degree to which $X$ and $Y$ are (linearly) related. Covariance is defined as

$$\mathrm{Cov}[X,Y] \triangleq \mathbb{E}[(X - \mathbb{E}[X])(Y - \mathbb{E}[Y])] = \mathbb{E}[XY] - \mathbb{E}[X]\mathbb{E}[Y] \tag{D.43}$$

If $\mathbf{x}$ is a $D$-dimensional random vector, its covariance matrix is defined to be the following symmetric, positive semi definite matrix:

$$\mathrm{Cov}[\mathbf{x}] \triangleq \mathbb{E}[(\mathbf{x} - \mathbb{E}[\mathbf{x}])(\mathbf{x} - \mathbb{E}[\mathbf{x}])^\top] \triangleq \mathbf{\Sigma} \tag{D.44}$$ $$= \begin{pmatrix} \mathbb{V}[X_1] & \mathrm{Cov}[X_1,X_2] & \cdots & \mathrm{Cov}[X_1,X_D] \\ \mathrm{Cov}[X_2,X_1] & \mathbb{V}[X_2] & \cdots & \mathrm{Cov}[X_2,X_D] \\ \vdots & \vdots & \ddots & \vdots \\ \mathrm{Cov}[X_D,X_1] & \mathrm{Cov}[X_D,X_2] & \cdots & \mathbb{V}[X_D] \end{pmatrix} \tag{D.45}$$

from which we get the important result

$$\mathbb{E}[\mathbf{x}\mathbf{x}^\top] = \mathbf{\Sigma} + \boldsymbol{\mu}\boldsymbol{\mu}^\top \tag{D.46}$$

Another useful result is that the covariance of a linear transformation is given by

$$\mathrm{Cov}[\mathbf{A}\mathbf{x} + \mathbf{b}] = \mathbf{A}\mathrm{Cov}[\mathbf{x}]\mathbf{A}^\top \tag{D.47}$$

as shown in Exercise D.7.

The cross-covariance between two random vectors is defined as

$$\mathrm{Cov}[\mathbf{x},\mathbf{y}] = \mathbb{E}[(\mathbf{x} - \mathbb{E}[\mathbf{x}])(\mathbf{y} - \mathbb{E}[\mathbf{y}])^\top] \tag{D.48}$$

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_844_0.png)

## D.4.3 Correlation

Covariances can be between negative and positive infinity. Sometimes it is more convenient to work with a normalized measure, with a finite lower and upper bound. The (Pearson) **correlation coefficient** between $X$ and $Y$ is defined as

corr $[X, Y] \triangleq \frac{\operatorname{Cov}\left[X, Y\right]}{\sqrt{\mathbb{V}\left[X\right]} \sqrt{\mathbb{V}\left[Y\right]}}$  
(D.49)

One can show (Exercise **D.5**) that $-1 \leq$ corr $[X, Y] \leq 1$. One can also show that corr $[X, Y] = 1$ if and only if $Y = aX + b$ for some parameters $a$ and $b$, i.e., if there is a *linear* relationship between $X$ and $Y$ (see Exercise **D.6**). Intuitively one might expect the correlation coefficient to be related to the slope of the regression line, i.e., the coefficient $a$ in the expression $Y = aX + b$. However, as we show in Eq. (11.27), the regression coefficient is in fact given by $a = \operatorname{Cov}\left[X, Y\right] / \mathbb{V}\left[X\right]$. A better way to think of the correlation coefficient is as a degree of linearity. See [correlation_2d_interactive_plot.py](correlation_2d_interactive_plot.py) for a demo to illustrate this idea.

In the case of a vector $\mathbf{x}$ of related random variables, and the **correlation matrix** is given by

corr($\mathbf{x}$) $=\left(\begin{array}{ccc}1 & \frac{\mathbb{E}\left[(X_1-\mu_1)(X_2-\mu_2)\right]}{\sigma_1 \sigma_2} & \ldots & \frac{\mathbb{E}\left[(X_1-\mu_1)(X_D-\mu_D)\right]}{\sigma_1 \sigma_D} \\ \frac{\mathbb{E}\left[(X_2-\mu_2)(X_1-\mu_1)\right]}{\sigma_2 \sigma_1} & 1 & \ldots & \frac{\mathbb{E}\left[(X_2-\mu_2)(X_D-\mu_D)\right]}{\sigma_2 \sigma_D} \\ \vdots & \vdots & \ddots & \vdots \\ \frac{\mathbb{E}\left[(X_D-\mu_D)(X_1-\mu_1)\right]}{\sigma_D \sigma_1} & \frac{\mathbb{E}\left[(X_D-\mu_D)(X_2-\mu_2)\right]}{\sigma_D \sigma_2} & \ldots & 1\end{array}\right)$  
(D.50)

This can be written more compactly as

corr($\mathbf{x}$) $=(\operatorname{diag}(\mathbf{K}_{xx}))^{-\frac{1}{2}} \mathbf{K}_{xx}(\operatorname{diag}(\mathbf{K}_{xx}))^{-\frac{1}{2}}$  
(D.51)

where $\mathbf{K}_{xx}$ is the **auto-covariance matrix**

$\mathbf{K}_{xx} = \boldsymbol{\Sigma} \triangleq \mathbb{E}\left[(\mathbf{x} - \mathbb{E}[\mathbf{x}])(\mathbf{x} - \mathbb{E}[\mathbf{x}])^\top\right] = \mathbf{R}_{\mathbf{x}\mathbf{x}} - \boldsymbol{\mu}\boldsymbol{\mu}^\top$  
(D.52)

and $\mathbf{R}_{xx} = \mathbb{E}[\mathbf{x}\mathbf{x}^\top]$ is the autocorrelation matrix.

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_845_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_845_1.png)

Figure D.6: Examples of spurious correlation between causally unrelated time series. (a) Consumption of ice cream (red) and US murder rate (black) over time. From https://bit.ly/2zfbvuf. Used with kind permission of Karen Cyphers. (b) Divorce rate in Maine strongly correlates with per-capita US consumption of margarine (black). From http://www.tylervigen.com/spurious-correlations. Used with kind permission of Tyler Vigen.

## D.4.4 Uncorrelated does not imply independent

If X and Y are independent, meaning p(X,Y) = p(X)p(Y), then Cov[X,Y] = 0, and hence corr[X,Y] = 0. So independent implies uncorrelated. However, the converse is not true: uncorrelated does not imply independent. For example, let X ~ U(-1,1) and Y = X^2. Clearly Y is dependent on X (in fact, Y is uniquely determined by X), yet one can show (Exercise D.4) that corr[X,Y] = 0. Some striking examples of this fact are shown in Fig. D.5. This shows several data sets where there is clear dependence between X and Y, and yet the correlation coefficient is 0. A more general measure of dependence between random variables is mutual information, discussed in Sec. 6.3. This is zero only if the variables truly are independent.

## D.4.5 Correlation does not imply causation

It is well known that “correlation does not imply causation”. For example, consider Fig. D.6a. In red, we plot x_{1:T}, where x_t is the amount of ice cream sold in month t. In black, we plot y_{1:T}, where y_t is the murder rate in month t. (Quantities have been rescaled to make the plots overlap.) We see a strong correlation between these signals. Indeed, it is sometimes claimed that “eating ice cream causes murder” [Pet13]. Of course, this is just a spurious correlation, due to a hidden common cause, namely the weather. Hot weather increases ice cream sales, for obvious reasons. Hot weather also increases violent crime; the reason for this is hotly (ahem) debated; some claim it is due to an increase in anger [And01], but other claim it is merely due to more people being outside [Ash18], where most murders occur.

Another example is shown in Fig. D.6b. This time we plot the divorce rate in Maine (red) and margarine consumption (black). It is less obvious why these should be correlated. Indeed, this is very likely to not be a robust result; for example, if we looked over a longer period of time, we may find that these signals are uncorrelated.

Another famous example concerns the positive correlation between birth rates and the presence of storks (a kind of bird). This has given rise to the urban legend that storks deliver babies [Mat00].

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_846_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_846_1.png)

Figure D.7: Illustration of Simpson's paradox. (a) Overall, y decreases with x. (b) Within each group, y increases with x. From https://en.wikipedia.org/wiki/Simpson's_paradox. Used with kind permission of Wikipedia author Pace svwiki

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_846_2.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_846_3.png)

Figure D.8: Illustration of Simpson's paradox using covid19 data. (a) Case fatality rates (CFRs) in Italy and China by age group, and in aggregated form (“Total”, last pair of bars), up to the time of reporting (see legend). (b) Proportion of all confirmed cases included in (a) within each age group by country. From Figure 1 of [KGS20]. Used with kind permission of Julius von Kügelgen.

Of course, the true reason for the correlation is more likely due to hidden factors, such as increased living standards and hence more food. Many more amusing examples of such spurious correlations can be found in [Vig15].

These examples serve as a “warning sign”, that we should not treat the ability for x to predict y as an indicator that x causes y.

## D.4.6 Simpsons’ paradox

Simpson’s paradox says that a statistical trend or relationship that appears in several different groups of data can disappear or reverse sign when these groups are combined. This results in counterintuitive behavior if we misinterpret claims of statistical dependence in a causal way.

A visualization of the paradox is given in Fig. D.7. Overall, we see that y decreases with x, but within each subpopulation, y increases with x.
