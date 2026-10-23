
### E.7.5 p-values

When we reject $H_0$ we often say the result is **statistically significant** at level $\alpha$. However, the result may be statistically significant but not practically significant, depending on how far from the decision boundary the test statistic is.

Rather than arbitrarily declaring a result as significant or not, it is preferable to quote the **p-value**. This is defined as the probability, under the null hypothesis, of observing a test statistic that is as large or larger than that actually observed:

$$\operatorname{pval}(\tau(\mathcal{D})) \triangleq \Pr(\tau(\widetilde{\mathcal{D}}) \geq \tau(\mathcal{D})\mid \widetilde{\mathcal{D}}\sim H_0)$$  
(E.134)

In other words, $\operatorname{pval}(\tau_{\mathrm{obs}}) \triangleq \Pr(\tau_{\mathrm{null}} \geq \tau_{\mathrm{obs}})$, where $\tau_{\mathrm{obs}}=\tau(\mathcal{D})$ and $\tau_{\mathrm{null}}=\tau(\widetilde{\mathcal{D}})$, where $\widetilde{\mathcal{D}}\sim H_0$ is hypothetical future data. To see the connection with hypothesis testing, suppose we pick a decision threshold $t^*$ such that $\Pr(\tau(\widetilde{\mathcal{D}})\geq t^*\mid H_0)=\alpha$. If we set $t^*=\tau(\mathcal{D})$, then $\alpha=\operatorname{pval}(\tau(\mathcal{D}))$.

Thus if we only accept hypotheses where the p-value is less than $\alpha=0.05$, then 95% of the time we will correctly reject the null hypothesis. However, this does *not* mean that the alternative hypothesis $H_1$ is true with probability 0.95. Indeed, even most scientists misinterpret p-values.⁵ The quantity that most people want to compute is the Bayesian posterior $p(H_1\mid D)=0.95$. For more on this important distinction, see Sec. [E.8.2].

## E.8 Pathologies of frequentist statistics

Frequentist statistics exhibits various forms of unintuitive (arguably pathological) properties, which have been pointed out in multiple articles (see e.g., [Mat98; MS11; Kru13; Gel16; Hoe+14; Lyu+20; Cha+19b]). In this section, we summarize a few of them. For example, suppose the 95% confidence interval of some quantity $\theta$ estimated from data $D$ is, say, $I=[0.1,0.2]$, this does *not* mean that $p(\theta\in I\mid D)=0.95$, despite what most people think (see Sec. [E.8.1]). Similarly, if the p-value of the data given some model hypothesis $H$ is 0.05, this does not mean $p(H\mid D)=0.05$, despite what most people think (see Sec. [E.8.2]).

### E.8.1 Confidence intervals are not credible

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

If \( \theta = 39 \), we would expect the following outcomes each with probability 0.25:

\( (39,39), (39,40), (40,39), (40,40) \) (E.136)

Let \( m = \min(y_1, y_2) \) and define the following interval:

\( [\ell(\mathcal{D}), u(\mathcal{D})] = [m, m] \) (E.137)

For the above samples this yields

\( [39,39], \; [39,39], \; [39,39], \; [40,40] \) (E.138)

Hence Eq. (\textbf{E.137}) is clearly a 75\% CI, since 39 is contained in 3/4 of these intervals. However, if we observe \( \mathcal{D} = (39,40) \) then \( p(\theta = 39|\mathcal{D}) = 1.0 \), so we know that \( \theta \) must be 39, yet we only have 75\% “confidence” in this fact. We see that the CI will “cover” the true parameter 75\% of the time, if we compute multiple CIs from different randomly sampled datasets, but if we just have a single observed dataset, and hence a single CI, then the frequentist “coverage” probability can be very misleading.

Another, less contrived, example is as follows. Suppose we want to estimate the parameter \( \theta \) of a Bernoulli distribution. Let \( \bar{y} = \frac{1}{N} \sum_{n=1}^N y_n \) be the sample mean. The MLE is \( \hat{\theta} = \bar{y} \). An approximate 95\% confidence interval for a Bernoulli parameter is \( \bar{y} \pm 1.96 \sqrt{\bar{y}(1-\bar{y})/N} \) (this is called a **Wald interval** and is based on a Gaussian approximation to the Bernoulli distribution; compare to Eq. (7.23)). Now consider a single trial, where \( N = 1 \) and \( y_1 = 0 \). The MLE is 0, which overfits, as we saw in Sec. 4.4.1. But our 95\% confidence interval is also (0, 0), which seems even worse. It can be argued that the above flaw is because we approximated the true sampling distribution with a Gaussian, or because the sample size was too small, or the parameter “too extreme”. However, the Wald interval can behave badly even for large \( N \), and non-extreme parameters [BCD01]. By contrast, a Bayesian credible interval with a non-informative Jeffreys prior behaves in the way we would expect.

Several more interesting examples, along with Python code, can be found at [Van14]. See also [Hoc+14; Mor+16; Lyu+20; Cha+19b], who show that many people, including professional statisticians, misunderstand and misuse frequentist confidence intervals in practice, whereas Bayesian credible intervals do not suffer from these problems.

### E.8.2 p-values confuse deduction with induction

A p-value is often interpreted as the likelihood of the data under the null hypothesis, so small values are interpreted to mean that \( H_0 \) is unlikely, and therefore that \( H_1 \) is likely. The reasoning is roughly as follows:

If \( H_0 \) is true, then this test statistic would probably not occur. This statistic did occur. Therefore \( H_0 \) is probably false.

However, this is invalid reasoning. To see why, consider the following example (from [Coh94]):

If a person is an American, then he is probably not a member of Congress. This person is a member of Congress. Therefore he is probably not an American.

This is obviously fallacious reasoning. By contrast, the following logical argument is valid reasoning:

|  | Ineffective | Effective | Total |
|---|---|---|---|
| "Not significant" | 171 | 4 | 175 |
| "Significant" | 9 | 16 | 25 |
| Total | 180 | 20 | 200 |

Table E.3: *Some statistics of a hypothetical clinical trial. Source:* [SAM04, p74].

If a person is a Martian, then he is not a member of Congress. This person is a member of Congress. Therefore he is not a Martian.

The difference between these two cases is that the Martian example is using **deduction**, that is, reasoning forward from logical definitions to their consequences. More precisely, this example uses a rule from logic called **modus tollens**, in which we start out with a definition of the form $P \Rightarrow Q$; when we observe $\neg Q$, we can conclude $\neg P$. By contrast, the American example concerns **induction**, that is, reasoning backwards from observed evidence to probable (but not necessarily true) causes using statistical regularities, not logical definitions.

To perform induction, we need to use probabilistic inference (as explained in detail in [Jay03]). In particular, to compute the probability of the null hypothesis, we should use Bayes rule, as follows:

```
$p(H_{0}|\mathcal{D}) = \frac{p(\mathcal{D}|H_{0})p(H_{0})}{p(\mathcal{D}|H_{0})p(H_{0}) + p(\mathcal{D}|H_{1})p(H_{1})}$ (E.139)
```

If the prior is uniform, so $p(H_{0}) = p(H_{1}) = 0.5$, this can be rewritten in terms of the **likelihood ratio** $LR = p(\mathcal{D}|H_{0})/p(\mathcal{D}|H_{1})$ as follows:

```
$p(H_{0}|\mathcal{D}) = \frac{LR}{LR+1}$ (E.140)
```

In the American Congress example, $\mathcal{D}$ is the observation that the person is a member of Congress. The null hypothesis $H_{0}$ is that the person is American, and the alternative hypothesis $H_{1}$ is that the person is not American. We assume that $p(\mathcal{D}|H_{0})$ is low, since most Americans are not members of Congress. However, $p(\mathcal{D}|H_{1})$ is also low — in fact, in this example, it is 0, since only Americans can be members of Congress. Hence $LR = \infty$, so $p(H_{0}|\mathcal{D}) = 1.0$, as intuition suggests. Note, however, that **NHST** ignores $p(\mathcal{D}|H_{1})$ as well as the prior $p(H_{0})$, so it gives the wrong results — not just in this problem, but in many problems. Indeed, Selke, Bayarri, and Berger [SB01] show that even if the p-value is as low as 0.05, the posterior probability of $H_{0}$ can be as high as 30% or more.

### E.8.3 p-values overstate evidence against the null hypothesis

In general there can be huge differences between p-values and $p(H_{0}|\mathcal{D})$. In particular, Selke, Bayarri, and Berger [SB01] show that even if the p-value is as low as 0.05, the posterior probability of $H_{0}$ can be as high as 30% or more, even with a uniform prior.

Consider this concrete example from [SAM04, p74]. Suppose 200 clinical trials are carried out for some drug. Suppose we perform a statistical test of whether the drug has a significant effect or not. The test has a type I error rate of $\alpha = 0.05$ and a type II error rate of $\beta = 0.2$. The resulting data is shown in Table E.3.
