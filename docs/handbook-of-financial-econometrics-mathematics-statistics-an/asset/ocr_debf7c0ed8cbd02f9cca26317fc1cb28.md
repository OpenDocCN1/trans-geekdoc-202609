and Litterman (1992), He and Litterman (1999), Satchell and Scowcroft (2000) and Allaj (2013). In this paper, $\tau$ is set as 0.025 (Idzorek, 2004).

The BL model inversely employs assets market weight to obtain the implied market equilibrium return

$$\pi = \lambda \Sigma \omega^{M},$$  
(14.2.c)

where $\lambda$ is a constant denoting the risk aversion coefficient, $\Sigma$ is an $m \times m$ covariance matrix of the assets, and the market weight $\omega^{M} = (\omega^{M}_1, \ldots, \omega^{M}_m)'$ in a portfolio is a $m \times 1$ vector calculated by the following equation

$$\omega_i^{M} = \frac{P_iQ_i}{\sum_{i=1}^{m} P_iQ_i},$$  
(14.2.d)

for $i = 1, \ldots, m$. Here, $P_i$ is the market price of the ith asset and $Q_i$ is the outstanding shares of the ith asset.

To construct the views for investors’ expected returns, the BL model considers that the expectation of the views are related to the parameter $\mu$. Thus, the uncertainty with the views, $v$, is a random vector that follows:

$$v\mid\mu \sim N(P\mu,\Omega),$$  
(14.2.e)

where $P$ is a $K \times m$ matrix to represent $K$ views, and the covariance matrix $\Omega$ quantifies investors’ confidence level toward their views. For mathematical simplicity, it is assumed that

$$\Omega = \tau P\Sigma P',$$  
(14.2.f)

where the constant $\tau$ characterizes the uncertainty about the confidence of the views. We remark that there is no rule to set up the value of $\tau$. For example, Almadi et al. (2014) set $\tau$ to be unity and Michaud et al. (2013) set $\tau$ to be $1/T$ where $T$ is the number of return observations. In this paper, we set $\tau = 0.025$ to indicate a relatively high level about the confidence toward investors’ views (Idzorek, 2004).

Given the expected returns $\mu$ and investors’ views $v$, Bayes’ formula yields the following critical formulas for the return,

$$r\mid v,\,\Omega \sim N(\mu_{BL},\Sigma_{BL}),$$  
(14.2.g)

where

$$\mu_{BL} = \pi + \tau\Sigma P'\left(\tau P\Sigma P' + \Omega\right)^{-1}(v - P\pi),$$  
(14.2.h)

$$\Sigma_{BL} = (1+\tau)\Sigma - \tau^2\Sigma P'\left(\tau P\Sigma P' + \Omega\right)^{-1}P\Sigma.$$  
(14.2.i)