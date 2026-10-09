*X uniform (0, γ) random variable and fires with a probability of γ. The uniform distribution is, of course, a very simple case:*

$$ f(x; a, b) = \frac{1}{b-a} \quad \text{for} \quad a \leq x \leq b \tag{3.77} $$

*Therefore:*

$$ f(x|\gamma) = \begin{cases} 0 & \text{if } \gamma < x \text{ or } x < 0 \\ 1/\gamma & \text{if } 0 \leq x \leq \theta \end{cases} \tag{3.78} $$

# **SOL-64 ▸ CH.SOL- 3.35.**

*The provided distribution is from the exponential family. Therefore, a single neuron becomes inactive with a probability of:*

$$ p = P(X < 20) = \int_{0}^{20} e^{-x} \, dx = 1 - e^{-20}. \tag{3.79} $$

*The OnOffLayer is off only if at least 150 out of 200 neurons are off. Therefore, this may be represented as a Binomial distribution and the probability for the layer to be off is:*

$$ \binom{200}{150} p^{2}(1-p) + \binom{200}{200} p^{200} = 200p^{2}(1-p) + p^{200}. \tag{3.80} $$

*Hence, the probability of the layer being active for at least 20 seconds is 1 minus this value:*

$$ [1 - (200p^{2}(1-p) + p^{200})]. \tag{3.81} $$

# **SOL-65 ▸ CH.SOL- 3.36.**

*The observed data, e.g the dropped neurons are distributed according to:*

$$ (x_1, \dots, x_n)|\theta \stackrel{iid}{\sim} \mathrm{Bern}(\theta) \tag{3.82} $$