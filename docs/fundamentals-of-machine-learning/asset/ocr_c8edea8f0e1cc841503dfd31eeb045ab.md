# 6.2 Moments: mean, variance, etc.

In the following, we only consider independent random values that are drawn from identical pdf, often labeled as iid (independent and identically distributed) data. That is, we do not consider cases with different probabilities when given a specific value of a random variable. We assume, mainly for simplicity, that static probability density function describes all we can know about the corresponding random variable.

Let us consider the arbitrary pdf, $p(x)$, with the following graph:

![](bbox=[0.368, 0.296, 0.609, 0.432])

Any curve like this is strictly positive and where the area under the curve is bounded to one (see Egn 6.3) is a possible probability density function. The specific curve can be characterized as multimodal because it has several peaks. It would be useful to have this function parameterized in an analytical format, and we will list some parameterized density function below. Since we don't know the probability density function of the quantities of interest in a machine learning, we will have to estimate pdfs. This approximation is the learning process in machine learning, and we will use outline specific methods to do this.

Communicating the form of a pdf is difficult, and traditionally it is common to describe random variables with a small set of numbers that are meant to capture some properties of variables density function. For example, we might ask what the most frequent value is when drawing many examples. This number is given by the largest value of the distribution.

$p^{max} = \argmax_x p(x).$

Even more common is to ask about the average value of the random sample when drawing examples. A common quantity is to think the expected arithmetic average of these numbers, which is called the mean, expected value, or expectation value of the distribution. This is defined as

$$\mu = \int_{-\infty}^{\infty} xp(x)dx.$

This formula formalizes the calculation of adding all the different numbers with their corresponding frequencies.

A careful reader might have noticed a little oddity in our discussion. On the one hand, we are saying that we want to characterize random variables through some simple measurements because we do not know the pdf, yet the last formula seems to assume that we know the pdf $p(x)$. To solve this apparent oddity, we need to be more careful