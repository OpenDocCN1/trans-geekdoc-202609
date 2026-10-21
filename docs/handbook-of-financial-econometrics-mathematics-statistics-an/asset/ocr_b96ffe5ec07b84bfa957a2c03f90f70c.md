general write-down function. Under this general setting, we propose an integral equation approach for the bond prices. As an application of this approach, we study the analytic properties of the bond prices. Also we derive an infinite series expression for the bond prices.

**Keywords**
Jump diffusion • Default barrier • Write-down function • Bond price • Credit spread.

# 110.1 Introduction

We want to price bonds issued by a firm. Assume that the firm issues a zero coupon bond with one dollar face value which matures at time $T$. First we consider the basic extension of the Merton model due to Black and Cox (1976). The idea is to capture the possibility that defaults may occur at any time before maturity for this zero coupon bond. Black and Cox considered an asset value process which, under the risk neutral measure, follows the dynamic:

$dV_t = (r - a)V_t dt + \sigma V_t dW_t.$

Here $a$ is the payout rate of the firm and $r > 0$ is the risk free interest rate. Moreover, they defined the default boundary as

$K_t = K_0 e^{\kappa t}, \quad 0 \le t \le T, \qquad (110.1)$

where $\kappa \in R$. (Longstaff and Schwartz (1995) adopted the constant boundary, that is, $\kappa = 0$.) More precisely, the default time is defined by

$\tau(T) \triangleq \inf\{0 \le t \le T; V_t \le K_t\}, \qquad (110.2)$

with the usual convention that $\inf\{\emptyset\} = +\infty$. Then, in the Black–Cox model, the payoff at maturity is $B(V_t,T) = \min(V_t,1)$, if there is no default up to time $T$. If boundary is hit before or at the maturity of the bond, bond holders will take over the firm and receive the remaining value of the firm at the default time: $B(V_{\tau(T)},\tau(T)) = K_{\tau(T)}$. To get the price of the bond payout at maturity if there is no default, we use results on pricing of barrier options. To get the price of the bond payout on the default barrier, one can use the density of the hitting time of Brownian motion and the joint density of Brownian motion and its maximum process. (For details, see Lando (2004)).

To take into account such empirical phenomenon as asymmetric leptokurtic features of the distributions of assets’ returns and reproduce the volatility smile, throughout this paper, we assume that, under the