# Table 102.2: Comparison between Rendleman and Bartter's and Cox et al.'s approaches.

| Model | Rendleman and Bartter (1979) | Cox et al. (1979) |
|---|---|---|
| Mathematical and Probability Theory Knowledge | Basic Algebra
Taylor Expansion
Binomial Theorem
Central Limit Theorem
Properties of Binomial Distribution | Basic Algebra
Taylor Expansion
Binomial Theorem
Central Limit Theorem
Properties of Binomial Distribution
Lyapunov's Condition |
| Assumption | The mean and variance of logarithmic returns of the stock are held constant over the life of the option | The stock follows a binomial process from one period to the next. It can only go up by a factor of u with probability p or go down by a factor of d with probability 1 − p
In order to apply the Central Limit Theorem, u, d, and p are needed to be chosen |
| Advantage and Disadvantage | 1. Readers who have undergraduate level training in mathematics and probability theory can follow this approach
2. The approach is intuitive, but the derivation is more complicated and tedious | 1. Readers who have advanced level knowledge in probability theory can follow this approach; but for those who do not, it may be difficult to follow
2. The assumption on the parameters u, d, and p makes this approach more restricted |

(Lee et al., 2013b). Denote the current stock price by $S$ and the stock price at the end of $t$th period by $S_t$. Then $\frac{S_t}{S_{t-1}} = \exp(K_t)$ is a random variable with a lognormal distribution, where $K_t$ is the rate of return in $t$th period and is assumed as a random variable with normal distribution. Assume $K_t$ has the same expected value $\mu_k$ and variance $\sigma_k^2$ for each. Then $K_1 + K_2 + \cdots + K_T$ is a normal random variable with expected value $T\mu_k$ and variance $T\sigma_k^2$.

# Property of lognormal distribution.

*If a continuous random variable y is normally distributed, then the continuous variable x defined in equation (102.61) is lognormally distributed:*

$x = e^{y}.$
(102.62)