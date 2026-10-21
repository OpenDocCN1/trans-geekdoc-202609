
supply and demand for capital assets. The hypothesis implied by the model is also presented in this section. Section 100.3 describes the two sets of data used in this paper. The empirical finding for the hypothesis and tests constructed in previous section are then presented. Our summary is presented in Section 100.4.

## 100.2 Development of Multiperiod Asset Pricing Model with Supply Effect

Based on framework of Black (1976), we derive a multiperiod equilibrium asset pricing model in this section. Black modifies the static wealth-based CAPM by explicitly allowing for the endogenous supply effect of risky securities. The demand for securities is based on well-known model of Tobin (1958) and Markowitz (1959). However, Black further assumes a quadratic cost function of changing short-term capital structure under long-run optimality condition. He also assumes that the demand for security may deviate from supply due to anticipated and unanticipated random shocks.

Lee and Gweon (1986) modify and extend Black’s framework to allow time varying dividends and then test the existence of supply effect. In Lee and Gweon’s model, two major differing assumptions from Black’s model are: (1) the model allows for time-varying dividends, unlike Black’s assumption constant dividends; and (2) there is only one random, unanticipated shock in the supply side instead of two shocks, anticipated and unanticipated shocks, as in Black’s model. We follow the Lee and Gweon set of assumptions. In this section, we develop a simultaneous equation asset pricing model. First, we derive the demand function for capital assets, then we derive the supply function of securities. Next, we derive the multiperiod equilibrium model. Thirdly, the simultaneous equation system is developed for testing the existence of supply effects. Finally, the hypothesis of testing supply effect is developed.

### 100.2.1 Demand function for capital assets

The demand equation for the assets is derived under the standard assumptions of the CAPM.³ An investor’s objective is to maximize their expected utility function. A negative exponential function for the investor’s utility of wealth is assumed:

³The basic assumptions are: (1) a single period moving horizon for all investors; (2) no transactions costs or taxes on individuals; (3) the existence of a risk-free asset with rate of return, *r*⁎; (4) evaluation of the uncertain returns from investments in term of expected

$$U = a - h \times e^{-bW_{t+1}}.$$ (100.1)

Here the terminal wealth $W_{t+1} = W_t(1 + R_t)$, where $W_t$ is initial wealth and $R_t$ is the rate of return on the portfolio. The parameter $a$, $b$ and $h$ are assumed to be constants.

The dollar returns on $N$ marketable risky securities can be represented by

$$X_{j,t+1} = P_{j,t+1} - P_{j,t} + D_{j,t+1}, \quad j = 1,\dots,N.$$ (100.2)

where $P_{j,t+1}$ is the (random) price of security $j$ at time $t+1$, $P_{j,t}$ the price of security $j$ at time $t$, and $D_{j,t+1}$ the (random) dividend or coupon on security at time $t+1$.

These three variables are assumed to be jointly normal distributed. After taking the expected value of equation (100.2) at time $t$, the expected returns for each security, $x_{j,t+1}$, can be rewritten as

$$x_{j,t+1} = E_t X_{j,t+1} = E_t P_{j,t+1} - P_{j,t} + E_t D_{j,t+1}, \quad j = 1,\dots,N.$$ (100.3)

where $E_t P_{j,t+1} = E(P_{j,t+1}|\Omega_t)$, $E_t D_{j,t+1} = E(D_{j,t+1}|\Omega_t)$, $E_t X_{j,t+1} = E(X_{j,t+1}|\Omega_t)$, and $\Omega_t$ is the given information available at time $t$. Then, a typical investor's expected value of end-of-period wealth is

$$w_{t+1} = E_t W_{t+1} = W_t + r^*(W_t - q'_{t+1}P_t) + q'_{t+1}x_{t+1},$$ (100.4)

where $P_t = (P_{1,t}, P_{2,t}, P_{3,t},\dots,P_{N,t})'$, $x_{t+1} = (x_{1,t+1},x_{2,t+1},x_{3,t+1},\dots,x_{N,t+1})' = E_t P_{t+1} - P_t + E_t D_{t+1}$, $q_{t+1} = (q_{1,t+1},q_{2,t+1},q_{3,t+1},\dots,q_{N,t+1})'$, $q_{j,t+1}$ is the number of units of security $j$ after reconstruction of his portfolio, and $r^*$ is the risk-free rate. In equation (100.4), the first term on the right-hand side is the initial wealth, the second term is the return on the risk-free investment, and the last term is the return on the portfolio of risky securities. The variance of $W_{t+1}$ can be written as

$$V(W_{t+1}) = E(W_{t+1} - w_{t+1})(W_{t+1} - w_{t+1})' = q'_{t+1} S_{q,t+1},$$ (100.5)

where $S = E(X_{t+1} - x_{t+1}) (X_{t+1} - x_{t+1})'$ is the covariance matrix of returns of risky securities.

Maximization of the expected utility of $W_{t+1}$ is equivalent to:

$$\text{Max}\, w_{t+1} - \frac{b}{2}V(W_{t+1}). \tag{100.6}$$

By substituting equations (100.4) and (100.5) into equation (100.6), equation (100.6) can be rewritten as

$$\text{Max}(1 + r^*)W_t + q_{t+1}'(x_{t+1} - r^* P_t) - \left(\frac{b}{2}\right) q_{t+1}' S q_{t+1}. \tag{100.7}$$

Differentiating equation (100.7), one can solve the optimal portfolio as

$$q_{t+1} = b^{-1} S^{-1}(x_{t+1} - r^* P_t). \tag{100.8}$$

Under the assumption of homogeneous expectation, or by assuming that all the investors have the same probability belief about future return, the aggregate demand for risky securities can be summed as

$$Q_{t+1} = \sum_{k=1}^{m} q_{t+1}^k = c S^{-1}[E_t P_{t+1} - (1 + r^*)P_t + E_t D_{t+1}]. \tag{100.9}$$

where $c = \sum (b^k)^{-1}$.

In the standard CAPM, the supply of securities is fixed, denoted as $Q^*$. Then, equation (100.9) can be rearranged as $P_t = (1/r^*)(x_{t+1} - c^{-1} S Q^*)$, where $c^{-1}$ is the market price of risk. In fact, this equation is similar to the Lintner's (1965) well-known equation in capital asset pricing.

### 100.2.2 Supply function of securities

An endogenous supply side to the model is derived in this section, and we present our resulting hypothesis, mainly regarding market imperfections. For example, the existence of taxes causes firms to borrow more since the interest expense is tax-deductible. The penalties for changing contractual payment (i.e., direct and indirect bankruptcy costs) are material in magnitude, so the value of the firm would be reduced if firms increase borrowing. Another imperfection is the prohibition of short sales of some securities.⁴ The costs generated by market imperfections reduce the value of a firm, and thus, a firm has incentives to minimize these costs.

⁴Theories as to why taxes and penalties affect capital structure are first proposed by Modigliani and Miller (1958), and then Miller (1977). Another market imperfection, prohibition on short sales of securities, can generate “shadow risk premiums,” and thus, provide further incentives for firms to reduce the cost of capital by diversifying their securities.

Three more related assumptions are made here. First, a firm cannot issue a risk-free security; second, these adjustment costs of capital structure are quadratic; and third, the firm is not seeking to raise new funds from the market.

It is assumed that there exists a solution to the optimal capital structure and that the firm has to determine the optimal level of additional investment. The one-period objective of the firm is to achieve the minimum cost of capital vector with adjustment costs involved in changing the quantity vector, $Q_{i,t+1}$:

Min    $E_t D_{i,t+1} Q_{i,t+1} + \left(\frac{1}{2}\right) (\Delta Q'_{i,t+1} A_i \Delta Q_{i,t+1})$, 
subject to    $P_{i,t} \Delta Q_{i,t+1} = 0,$
(100.10)

where $A_i$ is an $n_i \times n_i$ positive definite matrix of coefficients measuring the assumed quadratic costs of adjustment. If the costs are high enough, firms tend to stop seeking to raise new funds or retire old securities. The solution to equation (100.10) is

$\Delta Q_{i,t+1} = A_i^{-1} (\lambda_i P_{i,t} - E_t D_{i,t+1}),$ 
(100.11)

where $\lambda_i$ is the scalar Lagrangian multiplier.

Aggregating equation (100.11) over $N$ firms, the supply function is given by

$\Delta Q_{t+1} = A^{-1} (B P_t - E_t D_{t+1}),$ 
(100.12)

where
$A^{-1} = \begin{bmatrix} A_1^{-1} & & \\ & A_2^{-1} & \\ & & \ddots & \\ & & & A_N^{-1} \end{bmatrix}, \quad B = \begin{bmatrix} \lambda_1 I & & \\ & \lambda_2 I & \\ & & \ddots & \\ & & & \lambda_N I \end{bmatrix}, \quad \text{and} \quad Q = \begin{bmatrix} Q_1 \\ Q_2 \\ \vdots \\ Q_N \end{bmatrix}.$

Equation (100.12) implies that a lower price for a security will increase the amount retired of that security. In other words, the amount of each security newly issued is positively related to its own price and is negatively related to its required return and the prices of other securities.

### 100.2.3 Multiperiod equilibrium model

The aggregate demand for risky securities presented by equation (100.9) can be seen as a difference equation. The prices of risky securities are determined
