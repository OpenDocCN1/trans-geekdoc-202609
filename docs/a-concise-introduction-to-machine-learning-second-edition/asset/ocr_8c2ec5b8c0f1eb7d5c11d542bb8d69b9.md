# 12 ■ A Concise Introduction to Machine Learning

![](bbox=[0.283, 0.173, 0.722, 0.417])

Figure 2.2: The normal probability density function for various values of $\mu$ and $\sigma$.

too small for interpretation. This is also known as *overfitting*, where the model does not generalize to unseen data. For example, assume that we discretized the ages so finely that in each age group there is only one woman, or possibly we can then make no prediction at all for a new participant of the study, if that age group is empty, or we will make the prediction according to the mortality of that woman in that age group, which could be completely wrong.

Discretization is one way of dealing with probabilities of a continuous-valued variable $x$. Another way is the *probability density function (pdf)* $f(x)$ over $x$ which describes the distribution. Formally, it is defined by $f(x)\Delta x$ being the probability of a sample falling inside the interval $(x, x+\Delta x)$ as the interval size $\Delta x$ approaches zero. The probability density function is always nonnegative. It can be viewed as taking discretization to the limit. There is a valid probability for $x$ falling into an interval $(a, b)$ and it is given by

> $p(x \in (a, b)) = \int_{a}^{b} f(x)dx$$

If $a = -\infty$ and $b = \infty$, that we integrate over all possible values of $x$, the probability is one.

As continuous variables can be discretized, discrete variables can be viewed as continuous. In this case, $f(x)$ is called the *probability mass function (pmf)*, because the probabilities for each discrete possible value of $x$, are concentrated as point masses at these values. For all other values of $x$ the probability is zero.