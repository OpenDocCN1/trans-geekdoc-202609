
$X$ denotes the number of times success was obtained, then it is best characterized by the binomial distribution with parameters $n = 200$ and $p = 0.1$. Formally:

$$X \sim \text{Binomial}(200, 0.1) . \tag{3.15}$$

The expectation of $X$ is given by:

$$E(X) = 200 \times 0.1 = 20, \tag{3.16}$$

and its respective variance is:

$$Var(X) = 200 \times 0.10(1 - 0.10) = 18.0 . \tag{3.17}$$

Here we propose two distinguished methods to answer the question.

Primarily, the straightforward solution is to employ the definition of the binomial distribution and substitute the value of $X$ in it. Namely:

$$\begin{aligned} P(X = 60; n = 200, p = 0.1) \\ &= \binom{200}{60} 0.1^{60} (1 - 0.1)^{200-60} \\ &\approx 2.7 \times 10^{-15} . \end{aligned} \tag{3.18}$$

This leads to an extremely high probability that the radiologist is mistaken.

The following approach is longer and more advanced, but grants the reader with insights and intuition regarding the results. To derive how wrong the radiologist is, we can employ an approximation by considering the standard normal distribution. In statistics, the **Z-score** allows us to understand how far from the mean is a data point in units of standard deviation, thus revealing how likely it is to occur (Fig. 3.17).

![](img/574135cb1d7125b50cf484d943cdd676_84_0.png)

![](img/574135cb1d7125b50cf484d943cdd676_85_0.png)

Therefore, the probability of correctly hitting 60 cells is:

$P(X\geq 60)=P(Z\geq \frac{60-20}{\sqrt{18.0}})=P(Z\geq 9.428)\approx 0.$ (3.20)

> Again, the outcome shows the likelihood that the radiologist was wrong approaches $1.$ Note: Why is the relation depicted in Fig. 3.17 deduces that $Z$ is a standard Gaussian? Under what terms is this conclusion valid? Why does eq. $(3.20)$ employ the cumulative distribution function and not the probability mass function?

## 3.3.2 Conditional Probability

### SOL-36 🏃 CH.SOL - 3.7.

1. For two events $A$ and $B$ with $P(B)>0$, the conditional probability of $A$ given that $B$ has occurred is defined as:

$P(A|B)=\frac{P(A \cap B)}{P(B)}.$ (3.21)

It is easy to note that if $P(B)=0$, this relation is not defined mathematically. In this case, $P(A|B)=P(A \cap B)=P(A).$

2. The annotated probabilities are displayed in Fig. 3.18:

![](img/574135cb1d7125b50cf484d943cdd676_85_1.png)

3. An example of a diagram depicting the intersected events $A$ and $B$ is displayed in Fig. 3.19:

![](img/574135cb1d7125b50cf484d943cdd676_86_0.png)

FIGURE 3.19: Venn diagram of the intersected events A and B in probability space $\mathcal{H}$

### SOL-37 CH.SOL- 3.8.

The Bayes formula reads:

$$P(A|B)=\frac{P(B|A)P(A)}{P(B|A)P(A)+P(B|A^c)P(A^c)},\tag{3.23}$$

where $P(A^{c})$ is the complementary probability of $P(A)$. The interpretation of the elements in Bayes formula is as follows:

$$\text{posterior probability}=\frac{\text{likelihood of the data} \times \text{prior probability}}{\text{normalization constant}}.\tag{3.24}$$

Note: What is the important role of the normalization constant? Analyze the cases where $P(B) \rightarrow 0$ and $P(B) \rightarrow 1$. The annotated probabilities are displayed in Fig. 3.20:

![](img/574135cb1d7125b50cf484d943cdd676_87_0.png)

$$P(A|B)=\frac{P(B|A)P(A)}{P(B|A)P(A)+P(B|A^{c})P(A^{c})}.\quad (3.25)$$

![](img/574135cb1d7125b50cf484d943cdd676_87_1.png)

### SOL-38 CH.SOL- 3.9.

Given $X$ as a discrete randomly distributed variable and given $\gamma$ as the parameter of interest, the likelihood and the log-likelihood of $X$ given $\gamma$ follow respectively:

$$\mathcal{L}_{\gamma}(X=x)=p(X=x|\gamma)\quad (3.26)$$

$$\ell_{\gamma}(X=x)=\ln\left(p(X=x|\gamma)\right)\quad (3.27)$$

The term likelihood can be intuitively understood from this definition; it deduces how likely it is to obtain a value $x$ when a prior information is given regarding its distribution, namely the parameter $\gamma$. For example, let us consider a biased coin toss with $p_{h}=\gamma$. Then:

$$\mathcal{L}_{\gamma}(X="H")=p(X="H"|\gamma)=\gamma.\quad (3.28)$$

$$\ell_{\gamma}(X="H")=\ln\left(p(X="H"|\gamma)\right)=\ln\left(\gamma\right).\quad (3.29)$$

Note: The likelihood function may also follow continuous distributions such as the normal distribution. In the latter, it is recommended and often obligatory to employ the log-likelihood. Why? We encourage the reader to modify the above to the continuous case of normal distribution and derive the answer.

### SOL-39 CH.SOL- 3.10.

The continuous prior distribution, $f(\Gamma=\gamma)$ represents what is known about the probability of the value $\gamma$ before the experiment has commenced. It is termed as being subjective, and therefore may vary considerably between researchers. By proceeding with the previous example, $f(\Gamma=0.8)$ holds the probability of randomly flipping a coin that yields “heads” with chance of 80% of times.

### SOL-40 ✏ CH.SOL- 3.11.

The essence of Bayesian analysis is to draw inference of unknown quantities or quantiles from the posterior distribution $p(\Gamma = \gamma | X = x)$, which is traditionally derived from prior beliefs and data information. Bayesian statistical conclusions about chances to obtain the parameter $\Gamma = \gamma$ or unobserved values of random variable $X = x$, are made in terms of probability statements. These probability statements are conditional on the observed values of X, which is denoted as $p(\Gamma = \gamma | X = x)$, called posterior distributions of parameter $\gamma$. Bayesian analysis is a practical method for making inferences from data and prior beliefs using probability models for quantities we observe and for quantities which we wish to learn. Bayes rule provides a relationship of this form:

$$\text{posterior} \propto p(\mathbf{x}|\gamma) p(\gamma) \propto \text{data given prior} \times \text{chance of prior} . (3.30)$$

### SOL-41 ✏ CH.SOL- 3.12.

The posterior density summarizes what is known about the parameter of interest $\gamma$ after the data is **observed**. In Bayesian statistics, the posterior density $p(\Gamma = \gamma | X = x)$ becomes the **prior** for this next experiment. This is part of the well-known Bayesian updating mechanism wherein we update our knowledge to reflect the actual distribution of data that we observed. To summarize, from the perspective of Bayes Theorem, we update the **prior distribution** to a **posterior distribution** after seeing the data.

### SOL-42 ✏ CH.SOL- 3.13.

Two events A and B are statistically independent if (and only if):

$P(A \cap B) = P(A) P(B)$. (3.31)

> *Note: Use conditional probability and rationalize this outcome. How does this property become extremely useful in practical researches that consider likelihood of normally distributed features?*

## 3.3.3 Bayes Rule

### SOL-43 🖇 CH.SOL- 3.14.

*Let $\gamma$ stand for the number of half-integer spin states, and given the prior knowledge that both states are equally probable:*

$$P(\gamma=2|\gamma \geq 1)$$

$$= \frac{P(\gamma=2, \gamma \geq 1)}{P(\gamma \geq 1)} (3.33)$$

$$= \frac{P(\gamma=2)}{1-P(\gamma=0)} = \frac{1/4}{1-1/4} = \frac{1}{3} (3.34)$$

*Note: Under what statistical property do the above relations hold?*

### SOL-44 🖇 CH.SOL- 3.15.

*Let event $A$ indicate present hereditary-disease and let event $B$ to hold a positive test result. The calculated probabilities are presented in Table 3.1. We were asked to find the probability of a test indicating that hereditary-disease is present, namely $P(B)$. According to the law of total probability:*

$P(B)=P(B|A)*P(A)+P(B|\overline{A})*P(\overline{A})$ (3.35)

$=[0.95*0.01]+[0.05*0.99]=0.059$

*Note: In terms of performance evaluation, $P(B|A)$ is often referred to as the probability of detection and $P(B|\overline{A})$ is considered the probability of false alarm. Notice that these measures do not, neither logically nor mathematically, combine to probability of $1$.*

| PROBABILITY | EXPLANATION |
|---|---|
| P(A)=0.01 | The probability of hereditary-disease. |
| P($\overline{A}$)=1-0.01=0.99 | The probability of no hereditary-disease. |
| P($\overline{B}|\overline{A}$)=0.95 | The probability that the test will yield a negative result [$\overline{B}$] if hereditary-disease is NOT present [$\overline{A}$]. |
| P(B|\overline{A})=0.05 | The probability that the test will yield a positive result [B] if hereditary-disease is NOT present. |
