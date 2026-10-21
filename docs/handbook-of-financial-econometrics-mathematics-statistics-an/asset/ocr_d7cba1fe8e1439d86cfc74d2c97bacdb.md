vector. Then Y is said to have skew-normal distribution if its probability density function is given as follows:

$f_Y(y) = 2\phi_k(y,\Omega_Y)\Phi(\alpha^t y)$

where $\alpha$ is a $k$-dimensional column vector, $\phi_k(y,\Omega_Y)$ is the probability density function of a $k$-dimensional standard normal random variable with zero mean and correlation matrix $\Omega_Y$ and $\Phi(\alpha^t y)$ is the probability distribution function of a 1D standard normal random variable evaluated at $\alpha^t y$.

# 11.3.1.3 ARCH and GARCH Methods

Ever since the development of ARCH and GARCH models, the OLS method of estimating the hedge ratio has been generalized to take into account the heteroscedastic nature of the error term in equation (11.20). In this case, rather than using the unconditional sample variance and covariance, the conditional variance and covariance from the GARCH model are used in the estimation of the hedge ratio. As mentioned above, such a technique allows an update of the hedge ratio over the hedging period.

Consider the following bivariate GARCH model (see Cecchetti et al., 1988; Baillie and Myers, 1991):

$\begin{bmatrix} \Delta S_t \\ \Delta F_t \end{bmatrix} = \begin{bmatrix} \mu_1 \\ \mu_2 \end{bmatrix} + \begin{bmatrix} e_{1t} \\ e_{2t} \end{bmatrix} \iff \Delta Y_t = \mu + e_t,$

$e_t|\Omega_{t-1} \sim N(0, H_t), \quad H_t = \begin{bmatrix} H_{11,t} & H_{12,t} \\ H_{12,t} & H_{22,t} \end{bmatrix},$ 

$\operatorname{vec}(H_t) = C + A \operatorname{vec}(e_{t-1} e'_{t-1}) + B \operatorname{vec}(H_{t-1}). \quad (11.22)$

The conditional MV hedge ratio at time $t$ is given by $h_{t-1} = H_{12,t}/H_{22,t}$. This model allows the hedge ratio to change over time, resulting in a series of hedge ratios instead of a single hedge ratio for the entire hedging horizon. Equation (11.22) represents a GARCH model. This GARCH model will reduce to ARCH if $B$ equal to zero.

SAS Applications: Based upon monthly S&P 500 index and its futures as presented in Appendix 11C, we use ARCH and GARCH method in term of equation (11.22) to estimated hedge ratio in this section.

```
proc autoreg data = sp500monthly;
model C_spot = C_future/nlag=2 garch=(q=1,p=1) maxit=50;
ods output ParameterEstimates=estimate_autoreg;
run;
```