In the application of large deviation bounds, we are mostly interested in the case that deviation $\epsilon$ is close to zero. As shown in Example 2.6, the optimal $\lambda$ we shall choose is $\lambda = O(\epsilon) \approx 0$. It is thus natural to consider the Taylor expansion of the logarithmic moment generating function around $\lambda = 0$. Proposition 2.8 implies that the leading terms of the Taylor expansion are

$$\Lambda_X(\lambda) = \lambda\mu + \frac{\lambda^2}{2}\operatorname{Var}[X] + o(\lambda^2),$$

where $\mu = \mathbb{E}[X]$. The first two terms match that of the normal random variable in Example 2.6. When $\epsilon > 0$ is small, to obtain the rate function

$$I_X(\mu + \epsilon) = \sup_{\lambda>0} \left[ \lambda(\mu + \epsilon) - \lambda\mu - \frac{\lambda^2}{2}\operatorname{Var}[X] - o(\lambda^2) \right],$$

we should set the optimal $\lambda$ approximately as $\lambda \approx \epsilon/\operatorname{Var}[X]$, and the corresponding rate function becomes

$$I_X(\mu + \epsilon) \approx \frac{\epsilon^2}{2\operatorname{Var}[X]} + o(\epsilon^2).$$

For specific forms of logarithmic moment generation functions, one may obtain more precise bounds of the rate function. In particular, the following general estimate is useful in many applications. This estimate is what we will use throughout the chapter.

# **Lemma 2.9**  *Consider a random variable $X$ so that $\mathbb{E}[X] = \mu$. Assume that there exists $\alpha > 0$ and $\beta \ge 0$ such that for $\lambda \in [0,\beta^{-1})$,*

$$\Lambda_X(\lambda) \le \lambda\mu + \frac{\alpha\lambda^2}{2(1-\beta\lambda)}, \tag{2.9}$$

*then for $\epsilon > 0$,*

$$-I_X(\mu + \epsilon) \le -\frac{\epsilon^2}{2(\alpha + \beta\epsilon)},$$ $$-I_X\left(\mu + \epsilon + \frac{\beta\epsilon^2}{2\alpha}\right) \le -\frac{\epsilon^2}{2\alpha}.$$

*Proof*  Note that $$-I_X(\mu + \epsilon) \le \inf_{\lambda>0} \left[ -\lambda(\mu + \epsilon) + \lambda\mu + \frac{\alpha\lambda^2}{2(1-\beta\lambda)} \right].$$ We can take $\lambda$ at $\bar\lambda = \epsilon/(\alpha + \beta\epsilon)$. This implies that $\alpha\bar\lambda/(1-\beta\bar\lambda) = \epsilon$. Therefore $$-I_X(\mu + \epsilon) \le -\bar\lambda\epsilon + \frac{\alpha\bar\lambda^2}{2(1-\beta\bar\lambda)} = -\frac{\bar\lambda\epsilon}{2} = -\frac{\epsilon^2}{2(\alpha + \beta\epsilon)}.$$ Moreover, with the same choice of $\bar\lambda$, we have $$-I_X\left(\mu + \epsilon + \frac{\beta}{2\alpha}\epsilon^2\right) \le -\bar\lambda\epsilon\left(1 + \frac{\beta}{2\alpha}\epsilon\right) + \frac{\alpha\bar\lambda^2}{2(1-\beta\bar\lambda)} = -\frac{\epsilon^2}{2\alpha}.$$