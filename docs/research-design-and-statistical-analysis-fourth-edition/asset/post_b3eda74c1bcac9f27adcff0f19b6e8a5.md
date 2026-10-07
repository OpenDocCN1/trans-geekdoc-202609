
![](img/53d3130502f4ff3b15cbe3697d6e8c5a_105_0.png)

Figure 4.4 Binomial distributions for Y for $\pi=.25$ and $\pi = .35$ with $n=20$, and the areas under each distribution where $Y \ge 9$.

## Table 4.3 Steps in Computing the Power of a Test

- 1. Determine the theoretical sampling distribution of $Y$ assuming $H_0$ to be true.
- 2. Determine the rejection region.
- 3. Assume that the null hypothesis is incorrect and some specific alternative hypothesis, $H_A$ is correct.
- 4. Compute the probability of a result in the rejection region using the sampling distribution specified by the alternative hypothesis. The resulting value is the conditional probability of observing an outcome in the rejection region given that $H_A$ is true. This is the *power* of the test.

These calculations mean that a test of $H_0; \pi=.25$ has .238 probability of yielding a significant result if $\pi$ is actually .35. The experimental data will lead to an erroneous conclusion with probability $\beta=1-.238$, or $.762$. As anticipated, our experiment does not have a very good chance of discriminating $H_0$ from the assumed true state of the world, $H_{\Lambda}$.

## Research Design and Statistical Analysis

Power is one of the most difficult concepts to grasp – probably because so many things must be kept in mind. We need to consider two sampling distributions (those specified by $H_0$ and $H_A$), as well as the information provided by $H_1$ and $\alpha$. To find the rejection region for the test, we start with the sampling distribution that $H_0$ is true. We then need it to tell us how the rejection region is, and we need $H_A$ to tell us which tail to consider, or both tails must be evaluated. Power is the proportion of the $H_A$ distribution that falls in the rejection region.

### 4.5.3 Factors Affecting Power

We have seen that many factors are relevant to the calculation of our power experiment: the sampling distributions specified by $H_0$ and $H_A$ as well as the directionality of the alternative hypothesis specified by $H_1$. Some of those factors are affected by other experimental details. For example, the sampling distributions of $H_0$ and $H_A$ are affected by the sample size, $n$. As we see in Figure 4.2, as the sample size increases, the observed sample proportion, $Y$, is closer to the true value, $\pi$, and extreme proportions are less likely. Less likely the sampling distributions $H_0$ and $H_A$ overlap by a smaller amount, $\alpha$-level, and directionality of $H_1$ influence power.

Let's consider the hypothesis that $\pi = .5$. With a sample size of 15, we can use the methods of Section 4.5.2 to calculate the power of our study. We need to define the rejection region for a particular alpha-level, say $\alpha = .06$. Using Table 4.1, $P(Y \leq 4 | n=15, \pi=.5) = .0000 + .0025 + .0032 + .0417$, so we reject the null hypothesis when $Y \geq 4$. Next, we need a specific alternative hypothesis, $H_1: \pi = .25$. Then, we calculate $P(Y \leq 4 | n=15, \pi=.25)$, the part of the sampling distribution of $H_A$ that falls in the rejection region. Using Table 4.1, we calculate $P(Y \leq 4 | n=15, \pi=.25) = .0134 + .0668 + .2252 = .6865$, which is the power for this set of assumptions. We can plot that on a graph with possible values of $H_A$ on the x-axis and power on the y-axis. In the panel of Figure 4.5, that point $(.25, .6865)$ is marked with a dark dot. If we do the same calculations for other possible alternative hypotheses, assuming $H_A: \pi = .05$ or .10 or .85, for example, we will find the power for such cases. In fact, calculated values, as well as others, shown as the solid curve in the panel of Figure 4.5; this is a *power curve*. This power curve shows that power is higher when our $H_A$ is further from $H_0$ in the direction of $H_1$ (i.e., small values of $\pi$) and it drops to 0 for possible effect sizes, or assumptions about $H_A$ that are in the opposite direction from $H$, (i.e., large values of $\pi$).

The other curves in the panel of Figure 4.5 show the power of a one-tailed test under different sample size and alpha-level. These power functions have been plotted for four different cases: (1) $n=20, \alpha=.02$; (2) $n=20, \alpha=.06$; (3) $n=15, \alpha=.20$. The lower panel of Figure 4.5 shows curves for the same sets of assumptions about sample size and alpha-level, this assuming a two-tailed test. To generate the curves for two-tailed test.

![](img/53d3130502f4ff3b15cbe3697d6e8c5a_105_0.png)

## Developing the Fundamentals of Hypothesis Testing

Figure 4.4 Binomial distributions for Y for $\pi=.25$ and $\pi = .35$ with $n=20$, and the areas under each distribution where $Y \ge 9$.

**Figure 4.5 Power functions**

- 1. Power increases as $\alpha$ increases.
- 2. Power is affected by whether the test is one-tailed.
- 3. Power increases as the distance between $H_0$ and $H_A$ increases (the effect size of $H_A$).
- 4. Power increases as $n$ increases. This follows from the fact that as $n$ increases, $it$ is more likely that $Y/n$ is close to the true value $\pi$.

### 4.5.4 The Importance of A Priori Power Calculations

Power is important for researchers to understand and calculate *a priori* (in advance of collecting data). This allows an informed choice among possible statistical tests and various experimental designs. Also being equal, the design and the test that can afford the greatest power for a particular sample size. Additionally, a researcher who calculates *a priori* power can assess the consequence of potential violations of the assumptions of the test. Finally, and most importantly, the relationships between power, effect size, and sample size can be used to decide how much data should be collected. For example, suppose we want power of $.80$ to reject $H_0$ with a one-tailed test if $\pi$ is at $.6$. We can define power functions for various values of $n$ like those depicted in Figure 4.5. The n we want for our study is that one rises to a power in which (the y-axis value) is at .80 when the alternative hypothesis value ($\pi$) is .6.

The last point provides further comment. If we collect enough data, we are likely to obtain statistically significant results. Whether these results will be of practical importance or theoretical significance is another matter. Therefore, it makes sense before we collect data to ask the following: What is the smallest effect size that would be of interest and what power we want to do (i.e., find significance for) such an effect? The answer to these two questions will be major factors in determining the sample size for our research. Sometimes the required $n$ will be practically large and we will face the challenge of redesigning the research so that a smaller sample will achieve the desired power against the specific alternative hypothesis we had in mind.
