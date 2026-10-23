# ### E.7.5  p-values

When we reject $H_0$ we often say the result is **statistically significant** at level $\alpha$. However, the result may be statistically significant but not practically significant, depending on how far from the decision boundary the test statistic is.

Rather than arbitrarily declaring a result as significant or not, it is preferable to quote the **p-value**. This is defined as the probability, under the null hypothesis, of observing a test statistic that is as large or larger than that actually observed:

$$\operatorname{pval}(\tau(\mathcal{D})) \triangleq \Pr(\tau(\widetilde{\mathcal{D}}) \geq \tau(\mathcal{D})\mid \widetilde{\mathcal{D}}\sim H_0)$$  
(E.134)

In other words, $\operatorname{pval}(\tau_{\mathrm{obs}}) \triangleq \Pr(\tau_{\mathrm{null}} \geq \tau_{\mathrm{obs}})$, where $\tau_{\mathrm{obs}}=\tau(\mathcal{D})$ and $\tau_{\mathrm{null}}=\tau(\widetilde{\mathcal{D}})$, where $\widetilde{\mathcal{D}}\sim H_0$ is hypothetical future data. To see the connection with hypothesis testing, suppose we pick a decision threshold $t^*$ such that $\Pr(\tau(\widetilde{\mathcal{D}})\geq t^*\mid H_0)=\alpha$. If we set $t^*=\tau(\mathcal{D})$, then $\alpha=\operatorname{pval}(\tau(\mathcal{D}))$.

Thus if we only accept hypotheses where the p-value is less than $\alpha=0.05$, then 95% of the time we will correctly reject the null hypothesis. However, this does *not* mean that the alternative hypothesis $H_1$ is true with probability 0.95. Indeed, even most scientists misinterpret p-values.⁵ The quantity that most people want to compute is the Bayesian posterior $p(H_1\mid D)=0.95$. For more on this important distinction, see Sec. [E.8.2].

# ## E.8  Pathologies of frequentist statistics

Frequentist statistics exhibits various forms of unintuitive (arguably pathological) properties, which have been pointed out in multiple articles (see e.g., [Mat98; MS11; Kru13; Gel16; Hoe+14; Lyu+20; Cha+19b]). In this section, we summarize a few of them. For example, suppose the 95% confidence interval of some quantity $\theta$ estimated from data $D$ is, say, $I=[0.1,0.2]$, this does *not* mean that $p(\theta\in I\mid D)=0.95$, despite what most people think (see Sec. [E.8.1]). Similarly, if the p-value of the data given some model hypothesis $H$ is 0.05, this does not mean $p(H\mid D)=0.05$, despite what most people think (see Sec. [E.8.2]).

# ### E.8.1  Confidence intervals are not credible

A 95% frequentist confidence interval for a parameter $\theta$ is defined as any interval $I(\widetilde{D})$ such that $\Pr(\theta\in I(\widetilde{D})\mid \widetilde{D}\sim\theta)=0.95$, as we explain in Sec. [E.3.4]. This does *not* mean that the parameter is 95% likely to live inside this interval given the observed data. That quantity—which is usually what we want to compute—is instead given by the Bayesian credible interval $p(\theta\in I\mid D)$, as we explain in Sec. [7.1.2.2]. These concepts are quite different: In the frequentist approach, $\theta$ is treated as an unknown fixed constant, and the data is treated as random. In the Bayesian approach, we treat the data as fixed (since it is known) and the parameter as random (since it is unknown).

This counter-intuitive definition of confidence intervals can lead to bizarre results. Consider the following example from [Ber85, p11]. Suppose we draw two integers $\mathcal{D}=(y_1,y_2)$ from

$$p(y\mid\theta)=
\begin{cases}
0.5 & \text{if } y=\theta\\
0.5 & \text{if } y=\theta+1\\
0 & \text{otherwise}
\end{cases}$$  
(E.135)

5. See e.g., https://fivethirtyeight.com/features/not-even-scientists-can-easily-explain-p-values/.