
## Using Smooth Transition Regressions to Model Risk Regimes

- Nguyen, H., Dimovski, W. and Brooks, R. (2010). Underpricing, Risk Management, Hot Issue and Crowding Out Effects: Evidence from the Australian Resources Sector Initial Public Offerings. *Review of Pacific Basin Financial Markets and Policies* **13**, 333–361.
- Nystrup, P., Madsen, H. and Lindström, E. (2018). Dynamic Portfolio Optimization Across Hidden Market Regimes. *Quantitative Finance* **18**, 83–95.
- Ócal, N. and Osborn, D.R. (2000). Business Cycle Non-linearities in UK Consumption and Production. *Journal of Applied Econometrics* **15**, 27–43.
- Potter, S. (1999). Nonlinear Time Series Modelling: An Introduction. *Journal of Economic Surveys* **13**, 505–528.
- Ritter, J.R. and Welch, I. (2002). A Review of IPO Activity, Pricing, and Allocations. *Journal of Finance* **57**, 1795–1828.
- Saikkonen, P. and Luukkonen, R. (1988). Lagrange Multiplier Tests for Testing Non-linearities in Time Series Models. *Scandinavian Journal of Statistics* **15**, 55–68.
- Sarantis, N. (1999). Modeling Non-linearities in Real Effective Exchange Rates. *Journal of International Money and Finance* **18**, 27–45.
- Shadab, H.B. (2013). Hedge Fund Governance. *Stanford Journal of Business and Finance* **19**, 141.
- Skalin, O. and Teräsvirta, T. (1999). Another Look at Swedish Business Cycles, 1861–1988. *Journal of Applied Econometrics* **14**, 359–378.
- Teräsvirta, T. (1994). Specification, Estimation, and Evaluation of Smooth Transition Autoregressive Models. *Journal of the American Statistical Association* **89**, 208–218.
- Teräsvirta, T. and Anderson, H.M. (1992). Characterizing Nonlinearities in Business Cycles Using Smooth Transition Autoregressive Models. *Journal of Applied Econometrics* **7**, 119–136.
- Tong, H. and Lim, K.S. (1980). Threshold Autoregression, Limit Cycles and Cyclical Data. *Journal of the Royal Statistical Society. Series B (Methodological)* **42**, 245–292.
- Van Dijk, D. and Franses, P.H. (1999). Modeling Multiple Regimes in the Business Cycle. *Macroeconomic Dynamics* **3**, 311–340.
- Van Dijk, D., Teräsvirta, T. and Franses, P.H. (2002). Smooth Transition Autoregressive Models — a Survey of Recent Developments. *Econometric Reviews* **21**, 1–47.
- Welch, I. (1989). Seasoned Offerings, Imitation Costs, and the Underpricing of Initial Public Offerings. *Journal of Finance* **44**, 421–449.
- Zheng, S.X., Ogden, J.P. and Jen, F.C. (2005). Pursuing Value Through Liquidity in IPOs: Underpricing, Share Retention, Lockup, and Trading Volume Relationships. *Review of Quantitative Finance and Accounting* **25**, 293–312.

### Appendix 125A Smooth Transition Regression

This appendix provides a more general discussion of smooth transition regression than found in Section 125.2. In addition to a more detailed description of the methodology, the development of STR in the context of other state dependent methods and suggested extensions to STR are discussed. Smooth transition regression is a well-established methodology, a key advantage of adopting it for risk modeling, and consequently it is accessible in a number

To include an endogenous trigger for regime change we must move to threshold models introduced by Tong and Lim (1980). These models were introduced in the context of autoregressive series and consequently known as threshold autoregressive (TAR) models. The transition function is defined as

$$f(z_t)=\begin{cases}1, & z_t>c,\\0, & z_t<c,\end{cases}\qquad(125A.6)$$

where $z_t$ is the transition variable and $c$ is the critical (threshold) value of $z_t$ that defines the change of state. Using this, the model becomes:

$$y_t=\begin{cases}\beta'x_t+\varepsilon_t, & z_t>c,\\\varphi'x_t+\varepsilon_t, & z_t<c.\end{cases}\qquad(125A.7)$$

In the case of much of the work on this model, it was assumed that $z_t$ was a lagged value of $y_t$ but this is not a necessary part of the model. The key advance of TAR over Markov models is the specification of the transition variable that triggers the transition between states. It is worth noting that it is only necessary to specify the transition variable, the critical value can be derived from the data (Chan, 1993).

The TAR model is still limited to instantaneous changes of state. In order to allow a gradual move between states $f(z_t)$ must change continuously as $z_t$ changes. There are a number of definitions of $f(z_t)$ that meet the definition of smooth transition, two are particularly useful and well understood, the logistic and exponential transition functions. These transition functions generate logistic (L-STR) and exponential (E-STR) smooth transition regression models, respectively. The logistic transition function is defined as

$$f(z_t)=\left[1+\exp\left(-\gamma(z_t-c)\right)\right]^{-1},\quad \gamma>0,\qquad(125A.8)$$

where $\gamma$ is the smoothness parameter (i.e., the slope of the transition function) and $c$ is the threshold. Choosing this transition function yields the L-STR model. In the limit, as $\gamma\to0$ or $\gamma\to\infty$, the L-STR model becomes linear as the value of $f(z_t)$ is constant. For intermediate values of $\gamma$, the degree of decay depends upon the value of $z_t$. As $z_t\to-\infty$, $f(z_t)\to0$ and the behavior of $y_t$ is given by $y_t=\beta'x_t+\varepsilon_t$. As $z_t\to+\infty$, $f(z_t)\to1$ and the behavior of $y_t$ is given by $y_t=(\beta'+\varphi')x_t+\varepsilon_t$.

The alternative exponential transition function is

$$f(z_t)=1-\exp\left(-\gamma(z_t-c)^2\right),\quad \gamma>0.\qquad(125A.9)$$

Again $\gamma$ is the smoothness parameter while the function is symmetric around $z_t=c$. This function produces the E-STR model. Like before as $\gamma\to0$ or $\gamma\to\infty$, the E-STR model becomes linear as $f(z_t)$ becomes constant. Otherwise, the model displays nonlinear behavior. Unlike the L-STR model, E-STR is symmetric, as $(z_t-c)\to\pm\infty$, $f(z_t)\to1$ and the behavior of $y_t$ is given by $y_t=(\beta'+\varphi')x_t+\varepsilon_t$. As $z_t\to c$, $f(z_t)\to0$ and the behavior of $y_t$ is given by $y_t=\beta'x_t+\varepsilon_t$. Both the logistic and exponential transition functions are bounded by 0 and 1.

Before moving on it is useful to note that the specification for the STR model in equation (125A.2) can be rewritten as

$$y_t = \beta'_1 x_t + (\beta'_2 - \beta'_1) x_t f(z_t) + \varepsilon_t. \tag{125A.10}$$

Setting $\beta = \beta_1$ and $\varphi = \beta_2 - \beta_1$ generates the form used in the analysis in the main text.

$$y_t = \beta'_1 x_t + \varphi' x_t f(z_t) + \varepsilon_t. \tag{125A.11}$$

While this discussion has focused on two state STR models, the method can easily be extended to combine multiple regimes (Van Dijk et al., 2002). In discussing multiple states, it is convenient to define the transition function as dependent on the transition variable, smoothness factor and critical value. It is denoted as $f(z_i,\gamma_j,c_k)$, where the subscripts $i$, $j$ and $k$ denote multiple transition variables, smoothness factors and critical values, respectively. It is possible to categorize the extended models into two groups. In the first case, the transition functions are functions of the same transition variable, with different smoothness factors and threshold values. In the case of a three state model (two critical values) this becomes

$$y_t = \beta' x_t + \varphi'_1 x_t f(z_t, \gamma_1, c_1) + \varphi'_2 x_t f(z_t, \gamma_2, c_2) + \varepsilon_t. \tag{125A.12}$$

The alternative is multiple transition variables. Van Dijk and Franses (1999) develop multiple regime STR (MRSTR) model for this case. Their model generates $2^m$ regimes, for $m$ transition variables. In the case of two transition variables the model can be simplified to:

$$y_t = \beta' x_t + \varphi'_1 x_t f(z_{1,t}, \gamma_1, c_1) + \varphi'_2 x_t f(z_{2,t}, \gamma_2, c_2) + \varphi'_1 x_t f(z_{1,t}, \gamma_1, c_1) f(z_{2,t}, \gamma_2, c_2). \tag{125A.13}$$

#### 125A.2 Specification

Tests for the E-STR and L-STR were presented in Saikkonen and Luukkonen (1988) and Luukkonen et al. (1988), respectively. Tests of linearity are based on Lagrange Multiplier (LM) tests, first proposed to test econometric models by Breusch and Pagan (1980). The LM tests are useful as they require only estimation of the null (linear) model. Both methods rely on a two-step
