(b) *Test of linearity.* The second step involves testing linearity against STR models using the linear model specified in equation (125.5) as the null. This test is based on the auxiliary regression:

$$u_t = \beta'_0 x_t + \beta'_1 x_t z_t + \beta'_2 x_t z_t^2 + \beta'_3 x_t z_t^3 + \varepsilon_t, \qquad (125.6)$$ 

where the values of $u_t$ are the residuals of the linear model specified in the first step and $z_t$ is the transition variable. The null hypothesis of linearity is

$$H_0 : \beta_1 = \beta_2 = \beta_3 = 0. \qquad (125.7)$$

This hypothesis test can also be used to select from among a number of candidates for the transition variable, $z_t$. The linear model (equation (125.5)) and the auxiliary regression (equation (125.6)) are run for each potential variable. The hypothesis test is then run for each of these and the variable producing the smallest (significant) $P$-value selected.

(c) *Selection of L-STR or E-STR.* The final step, assuming linearity has been rejected, is selection between L-STR and E-STR models. This is based on the results of the auxiliary regression (Equation (125.6)) and requires a series of nested $F$-tests.

$$H_3 : \beta_3 = 0, \qquad (125.8)$$ 

$$H_2 : \beta_2 = 0 | \beta_3 = 0, \qquad (125.9)$$ 

$$H_1 : \beta_1 = 0 | \beta_2 = \beta_3 = 0. \qquad (125.10)$$

Rejecting $H_3$ leads to an L-STR model. Accepting $H_3$ and rejecting $H_2$ indicates selecting an E-STR model. Accepting both $H_3$ and $H_2$ while rejecting $H_1$ leads to an L-STR model. Granger and Terasvirta (1993) argue that strict application of this sequence of tests may lead to incorrect conclusions, where $H_3$ is accepted and both $H_2$ and $H_1$ are rejected. They suggest estimating the $P$-values of the $F$-tests of $H_2$ and $H_1$ and selecting the STR model based on the lowest $P$-value for $H_2$ or $H_1$ to overcome this problem.

# 125.3 Applications of Smooth Transition Regression

# 125.3.1 *Convertible arbitrage*

We now analyse the performance of a hedge fund strategy, both to demonstrate the use of STR and to highlight potential insights to be gained from its application. A number of hedge fund strategies have been shown to be sensitive to changes in market state, including cross-sectional momentum