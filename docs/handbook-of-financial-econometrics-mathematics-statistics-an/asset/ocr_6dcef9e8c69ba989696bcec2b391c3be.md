yields for individual firms given the very small number of actively traded corporate bonds.

# 50.3.2.5  *Problems of the GMM method*

GMM has the advantage that it requires specification only of certain moment conditions rather than the full density. Nonetheless, it is also a drawback of GMM that it often does not make efficient use of all the information in the sample. Moreover, neither the traditional econometric method nor economic theory necessarily identifies a unique set of moment conditions. The GMM estimates are often sensitive to the choice of moment conditions (see Hamilton, 1994; and the references therein).

# 50.3.2.6  *Problems of the MLE method*

Bruche (2005) points out two related drawbacks of the MLE approach: (1) Only the price of equity is used in model estimation, while other information like bond prices, credit and equity derivatives, and accounting information are not utilized; (2) Given that the asset prices, including equity prices, are influenced by market microstructure or agency problems, it is not sensible to make the assumption of zero (observed) equity pricing error.<sup>10</sup>

# 50.3.3  *Monte Carlo experiment*

We follow Duan *et al.* (2004) and set the following parameter values to perform the simulation experiment: interest rate $r = 0.05$, asset drift $\mu_V = 0.1$, asset volatility $\sigma_V = 0.3$, initial firm value $V_0 = 1.0$, face value of debt $F = 1.0$, and option maturity $T = 2$. The sampling period is set to be 252 days a year, and maturity is set to be $(2 - i\delta)$ years for the $i$th data point of the simulated time series. Finally, we change the value of the default barrier in order to examine its effect on parameter estimation.

Our results in Table 50.3 are based on 1,000 simulated samples following the procedure by Duan *et al.* (2004) to mimic the daily sample of observed

<sup>10</sup>Bruche (2005) proposes a simulated maximum likelihood procedure, which allows one to use data on any of the firm’s traded claims, including equity, bonds, CDS as well as balance sheet information to improve the efficiency of the estimation. This approach explores the possibility of considering the noise of security prices, and, therefore, it can avoid the bias that may be incurred by the zero equity pricing error assumption of the MLE approach. In addition, the estimation is related to the problem of recovering the value of the latent or unobserved asset value from the observed variables; it is one of calculating posterior densities, or filtering.