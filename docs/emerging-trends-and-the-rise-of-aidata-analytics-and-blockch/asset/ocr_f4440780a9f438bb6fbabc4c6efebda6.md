# The asymmetric form of the DCC model is

```
$$Q_t = (1 - \vartheta - \rho)\overline{Q} + \vartheta u_{t-1}u'_{t-1} + \rho Q_{t-1} + \gamma\overline{N} + \gamma n_{t-1}n'_{t-1}$$
$$
\overline{N} = T^{-1} \sum_{t=1}^T n_t n'_t, \quad n_t = I[u_t < 0] \circ u_t, \quad \vartheta + \rho + \alpha \gamma < 1 \quad (4)$$

```

\(\alpha\) is the maximum eigenvalue of \([\overline{Q}^{-1/2}N\overline{Q}^{-1/2}]\), \(I\) is \(k \times 1\) indicator function. If \(u_t < 0\) is true, then \(I\) equals one; otherwise, it will be zero. “\(\circ\)” is pointwise operations notation. The impact of previous innovations and previous time-varying conditional correlations on the current dynamic conditional correlations are measured by \(\vartheta\) and \(\rho\) (Katzke, 2013; Qian and Diaz, 2017).

The maximum likelihood (Nelson et al., 2010) approach is commonly used to route estimate parameters in multivariate GARCH models. The conditional likelihood function is indicated as follows for sample observation of \(x = (x_1, \dots, x_n)\):

```
$$l(\tau) = \prod_{t=1}^n |H_t|^{-1/2} p_\epsilon \left( H_t^{-1/2} x_t \right) = \prod_{t=1}^n \left[ \prod_{i=1}^k h_{n,t,i}^{-1/2} \right] |R_t|^{-1/2} p_\epsilon \left( (D_t R_t D_t)^{-1/2} y_t \right)$$
$$
p(\epsilon_t) = \frac{\Gamma((v+k)/2)}{\Gamma(v/2)[\pi(v-2)]^{k/2}} \left[ 1 + \frac{\epsilon'_t \epsilon_t}{v-2} \right]^{-(v+k)/2} \quad (5)$$

```

\(p_\epsilon\) is the joint density function for \(\epsilon\), either the standardized multivariate normal distribution or multivariate Student-t distribution. It depends on the one best fitted for error distribution. The multivariate Student-t distribution is used for financial asset returns (Fioruci et al., 2014). \(\tau\) is the set of all model parameters to be estimated. \(\Gamma(.)\) is gamma function and \(\epsilon_t\) is multivariate Student-t distribution, which has an additional degree of freedom \(v\), and it is assumed to be larger than two because in this case \(H_t\) is always interpreted as a conditional covariance matrix (Fioruci et al., 2014).

In total, four criteria, such as AIC [5], BIC [6], DIC [7] and wDIC [8], were utilized to compare different estimated Bayesian DCC-MGARCH models. Models that have smaller values of EAIC, DIC and EBIC are suggested. The models were fitted with three shock distributions: mvn [9], mvt [10] and mvGED [11].

It is also assumed that the distributions of error terms have a skewed distribution. In this respect, we must use asymmetric densities instead of symmetric density to improve financial modeling (Bauwens and Laurent, 2005). Therefore, error terms follow a skew-mvt or a skew-mvGED. For instance, the skew-mvt can address the excess kurtosis and skewness in cryptocurrencies and the return of stock indices of blockchain-based technology companies. We are going to use the following density functions of multivariate skew distributions that are proposed by Bauwens and Laurent (2005):

```
$$s(y|\gamma) = 2^k \left( \prod_{i=1}^k \frac{\gamma_i}{1 + \gamma_i^2} \right) f(y^*), \quad i = 1 \dots k \quad (6)$$

```

\(f(.)\) is symmetric multivariate density. If \(y_i\) is larger than or equal to zero, then \(y^* = y_i/\gamma_i\), otherwise \(y^* = y_i\gamma_i\). The parameters \(\gamma_i\) control the degree of skewness. If \(\gamma_i\) is greater than one, then there is a right skewness, and the value smaller than one shows a left skewness. The last step in specifying the model is to specify prior distributions of all parameters in the model (Bauwens and Laurent, 2005). Bayesian estimation is used to determine the prior distributions for all the model parameters (for more detailed information on the