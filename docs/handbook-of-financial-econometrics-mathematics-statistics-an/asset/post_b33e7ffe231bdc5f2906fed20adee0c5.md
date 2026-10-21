
we have

$a = 1 + \text{INT}\left[\frac{\ln(X/S_0) - \mu + \sigma\sqrt{T}\sqrt{\frac{\theta}{1-\theta}}}{\sigma/\sqrt{T\theta(1-\theta)}}\right]$

Then, equation (102.50) holds. Now

$Z_1 = \frac{a - T\varphi}{\sqrt{T\varphi(1-\varphi)}} = \frac{1 + \text{INT}\left[\frac{\ln(X/S_0) - \mu + \sigma\sqrt{T}\sqrt{\frac{\theta}{1-\theta}}}{\sigma/\sqrt{T\theta(1-\theta)}}\right] - T\varphi}{\sqrt{T\varphi(1-\varphi)}}. \quad (102.51)$

In the limit, the term $1 + \text{INT}[\cdot]$ will be simplified to $[\cdot]$. Therefore, $Z_1$ can be restated as

$Z_1 \sim \frac{\ln\left(\frac{X}{S_0}\right) - \mu}{\sigma\sqrt{\frac{\varphi(1-\varphi)}{\theta(1-\theta)}}} + \frac{\sqrt{T}(\theta - \varphi)}{\sqrt{\varphi(1-\varphi)}}. \quad (102.52)$

Substituting $H^+$ and $H^-$ in equations (102.46) and (102.47) and $1+R = e^{r/T}$ into equation (102.39), we have

$\varphi = \frac{(1+R-H^-)H^+}{(1+R)(H^+ - H^-)} = \frac{\left(e^{r/T} - e^{\mu/T - (\sigma/\sqrt{T})\sqrt{\theta/(1-\theta)}}\right) e^{\mu/T + (\sigma/\sqrt{T})\sqrt{(1-\theta)/\theta}}}{e^{r/T}\left(e^{\mu/T + (\sigma/\sqrt{T})\sqrt{(1-\theta)/\theta}} - e^{\mu/T - (\sigma/\sqrt{T})\sqrt{\theta/(1-\theta)}}\right)}$
$= \frac{e^{(\sigma/\sqrt{T})\sqrt{(1-\theta)/\theta}} - e^{\mu/T - r/T} + \left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}} - \sqrt{\frac{\theta}{1-\theta}}\right)}{e^{(\sigma/\sqrt{T})\sqrt{(1-\theta)/\theta}} - e^{-(\sigma/\sqrt{T})\sqrt{\theta/(1-\theta)}}}. \quad (102.53)$

Now, we expand Taylor's series$^{11}$ in $\frac{1}{\sqrt{T}}$, and obtain

$\varphi = \frac{\left(\frac{\sigma}{\sqrt{T}}\right)\sqrt{\frac{1-\theta}{\theta}} - (\mu - r)/T - \left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}} - \sqrt{\frac{\theta}{1-\theta}}\right) + O\left(\frac{1}{\sqrt{T}}\right)}{\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}} + \sqrt{\frac{\theta}{1-\theta}}\right) + O\left(\frac{1}{\sqrt{T}}\right)}$
$= \frac{\left(\frac{\sigma}{\sqrt{T}}\right)\sqrt{\frac{\theta}{1-\theta}} + O\left(\frac{1}{\sqrt{T}}\right)}{\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}} + \sqrt{\frac{\theta}{1-\theta}}\right) + O\left(\frac{1}{\sqrt{T}}\right)}, \quad (102.54)$

where $O\left(\frac{1}{\sqrt{T}}\right)$ denotes a function tending to zero more rapidly than $\frac{1}{\sqrt{T}}$.

It can be shown that

$$\lim_{T\to\infty}\varphi = \frac{\sqrt{\frac{\theta}{1-\theta}}}{\sqrt{\frac{1-\theta}{\theta}}+\sqrt{\frac{\theta}{1-\theta}}}= \frac{\sqrt{\frac{\theta}{1-\theta}}}{\sqrt{\frac{1-\theta+\theta}{\theta(1-\theta)}}}= \theta.$$ 
(102.55)

Similarly, we have

$$\sqrt{T}(\theta-\varphi)=\sqrt{T}\left(\theta-\frac{e^{(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{1-\theta}{\theta}}}-e^{\frac{\mu}{T}-\frac{r}{T}+(\frac{\sigma}{\sqrt{T}})\left(\sqrt{\frac{1-\theta}{\theta}}-\sqrt{\frac{\theta}{1-\theta}}\right)}}{e^{(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{1-\theta}{\theta}}}-e^{-(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{\theta}{1-\theta}}}}\right)$$ 

$$=\frac{\theta\sqrt{T}\left(e^{(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{1-\theta}{\theta}}}-e^{-(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{\theta}{1-\theta}}}\right)-\sqrt{T}\left(e^{(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{1-\theta}{\theta}}}-e^{\frac{\mu}{T}-\frac{r}{T}+(\frac{\sigma}{\sqrt{T}})\left(\sqrt{\frac{1-\theta}{\theta}}-\sqrt{\frac{\theta}{1-\theta}}\right)}\right)}{e^{(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{1-\theta}{\theta}}}-e^{-(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{\theta}{1-\theta}}}}\.$$
(102.56)

We also expand Taylor's series in $\frac{1}{\sqrt{T}}$, and we can obtain

$$\sqrt{T}(\theta-\varphi)=\frac{\theta\sqrt{T}\left[\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}}+\sqrt{\frac{\theta}{1-\theta}}\right)+\frac12\left(\frac{\sigma}{\sqrt{T}}\right)^2\left(\frac{1-\theta}{\theta}-\frac{\theta}{1-\theta}\right)+O\left(\frac1T\right)\right]}{\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}}+\sqrt{\frac{\theta}{1-\theta}}\right)+O\left(\frac1{\sqrt{T}}\right)}-\frac{\sqrt{T}\left[\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}}\right)+\frac12\left(\frac{\sigma}{\sqrt{T}}\right)^2\left(\frac{1-\theta}{\theta}\right)-\left(\frac{\mu-r}{T}+\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}}-\sqrt{\frac{\theta}{1-\theta}}\right)\right]}{\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}}+\sqrt{\frac{\theta}{1-\theta}}\right)+O\left(\frac1{\sqrt{T}}\right)}+\frac{\frac12\left(\frac{\sigma}{\sqrt{T}}\right)^2\left(\sqrt{\frac{1-\theta}{\theta}}-\sqrt{\frac{\theta}{1-\theta}}\right)^2+O\left(\frac1T\right)}{\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}}+\sqrt{\frac{\theta}{1-\theta}}\right)+O\left(\frac1{\sqrt{T}}\right)}$$ 

$$=\frac{\frac12\theta\frac{\sigma^2}{\sqrt{T}}\left(\frac{1-\theta}{\theta}-\frac{\theta}{1-\theta}\right)+\frac{\mu-r}{\sqrt{T}}+\frac12\frac{\sigma^2}{\sqrt{T}}\left(\frac{\theta}{1-\theta}-2\right)+O\left(\frac1{\sqrt{T}}\right)}{\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}}+\sqrt{\frac{\theta}{1-\theta}}\right)+O\left(\frac1{\sqrt{T}}\right)}.$$
(102.57)

## Table 102.2: Comparison between Rendleman and Bartter's and Cox et al.'s approaches.

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

## Property of lognormal distribution.

*If a continuous random variable y is normally distributed, then the continuous variable x defined in equation (102.61) is lognormally distributed:*

$x = e^{y}.$
(102.62)

If the variable y has mean μ and variance σ², then the mean μ_x and variance σ_x² of variable x is defined as follows, respectively:

μ_x = e^{μ+1/2 σ²}. (102.63) σ_x² = e^{2μ+σ²}(e^{σ²} - 1). (102.64)

Following the property, we then can define the expected value of S_T / S = exp(K₁ + K₂ + ⋯ + K_T) as

E(S_T / S) = exp(T μ_k + T σ_k² / 2). (102.65)

Under the assumption of a risk-neutral investor, the expected return E(S_T / S) is assumed to be e^{rT} (where r is the riskless rate of interest). In other words, the following equality holds:

μ_k = r - σ_k² / 2. (102.66)

The call option price C can be determined by discounting the expected value of the terminal option price by the risk-free rate:

C = e^{-rT} E[Max(S_T - X, 0)]. (102.67)

Note that in equation (102.66): Max(S_T - X, 0) = { S_T - X for S_T > X, 0 otherwise, } where T is the time of expiration and X is the exercise price.

Let x = S_T / S be a lognormal distribution. Then we have C = e^{-rT} E[Max(S_T - X)] = e^{-rT} ∫_{X/S}^{∞} S [x - X/S] g(x) dx = e^{-rT} S ∫_{X/S}^{∞} x g(x) dx - e^{-rT} S X/S ∫_{X/S}^{∞} g(x) dx, (102.68) where g(x) is the probability density function x = S_T / S.

Here, we will use properties of normal distribution, lognormal distribution, and their mutual relations to derive the Black–Scholes model. We
