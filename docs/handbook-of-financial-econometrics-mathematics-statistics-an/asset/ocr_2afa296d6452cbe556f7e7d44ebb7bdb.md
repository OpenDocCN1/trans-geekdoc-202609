where

$S' = \left[\frac{2r e^{r\tau(2-\beta)}}{\delta^2(2-\beta)(e^{r\tau(2-\beta)} -1)}\right] S^{2-\beta},$ $K' = \left[\frac{2r}{\delta^2(2-\beta)(e^{r\tau(2-\beta)} -1)}\right] K^{2-\beta},$ $g(x|m)=\frac{e^{-x}x^{m-1}}{\Gamma(m)}$

is the gamma density function

$G(x|m)=\int_{x}^{\infty} g(y|m)dy,$

where $C$ is the call price; $S$, the stock price; $\tau$, the time to maturity; $r$, the risk-free rate of interest; $K$, the strike price; and $\beta$ and $\delta$, the parameters of the formula.

# 51.2.1.2 Previous empirical studies

MacBeth and Merville (1980) were the first to empirically test the CEV option model. They tested the CEV model against the Black–Scholes (BS) model using daily closing prices of call options on six companies’ stock from December 31, 1975 to December 31, 1976. Their estimation procedure is as follows:

From (51.1),

$\frac{(dS - \mu S dt)^2}{S^{\beta} dt} \equiv u_t \propto \chi^2(1), \qquad (51.5)$

where the constant or proportionality is $1/\delta^2$.

Following (51.5), for some interval of time $dt$,

$\ln[(dS - \mu S dt)^2] - \ln dt = 2 \ln \delta + \beta \ln S + \ln[\chi^2(1)]. \qquad (51.6)$

They first estimate $\mu$ from the sample of daily returns. Point estimates of the elasticity parameter $\beta$ can then be obtained using a linear regression since the Chi-square random variables are uncorrelated through time. Note that they only choose the integer value of $\beta$ and fix it the same for all options written on the same stock. The way they choose the integer value is that starting with their point estimate of $\beta$, they use a numerical routine to calculate an implied value of $\delta$ for each observed option price until they have approximately the same of value of $\delta$ for each option price. This is done on four arbitrarily selected days during a year. Finally, $\delta$ is deduced from