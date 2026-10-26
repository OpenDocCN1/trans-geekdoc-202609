
## 外空条约

本条约缔约国，

鉴于1963年12月13日联合国大会通过的题为“各国探测及使用外太空工作之法律宣言”的第1962(XVIII)号决议，

鉴于上述决议吁请在探测及使用外太空前，应顾及法律后果，并促进国际合作，

深信人类探测及使用外太空所获之发展，关系全体人类之共同利益，

鉴于1967年1月27日签订之条约，确认探测及使用外太空应为所有国家之利益而进行，而不论其经济或科学发展程度如何，

切愿促进探测及使用外太空（包括月球与其他天体）之和平用途，并防止外太空军事化，

同意下列条款：

第一条
探测及使用外太空，包括月球与其他天体，应为所有国家之利益而进行，不论其经济或科学发展程度如何，并应为全体人类之福利。

第二条
外太空，包括月球与其他天体，不得由国家以主张主权之方式占有或使用。

第三条
本条约缔约国进行探测及使用外太空，应遵守国际法，包括联合国宪章。

- Pareto distribution.

Some examples of domains with well-known continuous probability distributions include:

- The probabilities of the heights of humans form a Normal distribution.
- The probabilities of movies being a hit form a Power-law distribution.
- The probabilities of income levels form a Pareto distribution.

We will take a closer look at continuous probability distributions in Chapter 9.

## 7.6 Further Reading

This section provides more resources on the topic if you are looking to go deeper.

### 7.6.1 Books

- *Probability Theory: The Logic of Science*, 2003.
  https://amzn.to/21nW2pp
- *Introduction to Probability*, 2nd edition, 2019.
  https://amzn.to/2xPvobK
- *Probability: For the Enthusiastic Beginner*, 2016.
  https://amzn.to/2jULJsu

### 7.6.2 Articles

- Random variable, Wikipedia.
  https://en.wikipedia.org/wiki/Random_variable
- Moment (mathematics), Wikipedia.
  https://en.wikipedia.org/wiki/Moment_(mathematics)
- Probability distribution, Wikipedia.
  https://en.wikipedia.org/wiki/Probability_distribution
- List of probability distributions, Wikipedia.
  https://en.wikipedia.org/wiki/List_of_probability_distributions

## 7.7 Summary

In this tutorial, you discovered a gentle introduction to probability distributions. Specifically, you learned:

- Random variables in probability have a defined domain and can be continuous or discrete.

## 8.3 Bernoulli Distribution

The Bernoulli distribution is a discrete probability distribution that covers a case where an event will have a binary outcome as either a 0 or 1.

$$x \in \{0,1\}$$

A *Bernoulli trial* is an experiment or case where the outcome follows a Bernoulli distribution. The distribution and the trial are named after the Swiss mathematician Jacob Bernoulli. Some common examples of Bernoulli trials include:

- The single flip of a coin that may have a heads (0) or a tails (1) outcome.
- A single birth of either a boy (0) or a girl (1).

A common example of a Bernoulli trial in machine learning might be a binary classification of a single example as the first class (0) or the second class (1). The distribution can be summarized by a single variable $p$ that defines the probability of an outcome 1. Given this parameter, the probability for each event can be calculated as follows:

$$P(x = 1) = p$$
$$P(x = 0) = 1 - p$$

In the case of flipping a fair coin, the value of $p$ would be 0.5, giving a 50% probability of each outcome.

## 8.4 Binomial Distribution

The repetition of multiple independent Bernoulli trials is called a Bernoulli process. The outcomes of a Bernoulli process will follow a Binomial distribution. As such, the Bernoulli distribution would be a Binomial distribution with a single trial. Some common examples of Bernoulli processes include:

- A sequence of independent coin flips.
- A sequence of independent births.

The performance of a machine learning algorithm on a binary classification problem can be analyzed as a Bernoulli process, where the prediction by the model on an example from a test set is a Bernoulli trial (correct or incorrect). The Binomial distribution summarizes the number of successes in a given number of Bernoulli trials $k$, with a given probability of success for each trial $p$. We can demonstrate this with a Bernoulli process where the probability of success is 30% or $P(x = 1) = 0.3$ and the total number of trials is 100 ($k = 100$).

We can simulate the Bernoulli process with randomly generated cases and count the number of successes over the given number of trials. This can be achieved via the `binomial()` NumPy function. This function takes the total number of trials and probability of success as arguments and returns the number of successful outcomes across the trials for one simulation.

```
# example of simulating a binomial process and counting success
from numpy.random import binomial
# define the parameters of the distribution
p = 0.3
k = 100
# run a single simulation
success = binomial(k, p)
print('Total Success: %d' % success)
```

Listing 8.1: Example of simulating a binomial process.

We would expect that 30 cases out of 100 would be successful given the chosen parameters (k × p or 100 × 0.3). A different random sequence of 100 trials will result each time the code is run, so your specific results will differ. Try running the example a few times. In this case, we can see that we get slightly less than the expected 30 successful trials.

```
Total Successes: 28
```

Listing 8.2: Example output from simulating a binomial process.

We can calculate the moments of this distribution, specifically the expected value or mean and the variance using the binom.stats() SciPy function.

```
# calculate moments of a binomial distribution
from scipy.stats import binom
# define the parameters of the distribution
p = 0.3
k = 100
# calculate moments
mean, var, _, _ = binom.stats(k, p, moments='mvsk')
print('Mean=%.3f, Variance=%.3f' % (mean, var))
```

Listing 8.3: Example of calculating the moments of a binomial distribution.

Running the example reports the expected value of the distribution, which is 30, as we would expect, as well as the variance of 21, which if we calculate the square root, gives us the standard deviation of about 4.5.

```
Mean=30.000, Variance=21.000
```

Listing 8.4: Example output from calculating the moments of a binomial distribution.

We can use the probability mass function to calculate the likelihood of different numbers of successful outcomes for a sequence of trials, such as 10, 20, 30, to 100. We would expect 30 successful outcomes to have the highest probability.

```
# example of using the pmf for the binomial distribution
from scipy.stats import binom
# define the parameters of the distribution
p = 0.3
k = 100
# define the distribution
dist = binom(k, p)
# calculate the probability of n successes
for n in range(10, 110, 10):
    print('P of %d success: %.3f%%' % (n, dist.pmf(n)*100))
```

Listing 8.5: Example of calculating probabilities for values from the binomial mass function.

Running the example defines the binomial distribution and calculates the probability for each number of successful outcomes in [10, 100] in groups of 10. The probabilities are multiplied by 100 to give percentages, and we can see that 30 successful outcomes has the highest probability at about 8.6%.

```
P of 10 success: 0.000%
P of 20 success: 0.758%
P of 30 success: 8.678%
P of 40 success: 0.849%
P of 50 success: 0.001%
P of 60 success: 0.000%
P of 70 success: 0.000%
P of 80 success: 0.000%
P of 90 success: 0.000%
P of 100 success: 0.000%
```

Listing 8.6: Example output from calculating probabilities for values from the binomial mass function.

Given the probability of success is 30% for one trial, we would expect that a probability of 50 or fewer successes out of 100 trials to be close to 100%. We can calculate this with the cumulative distribution function, demonstrated below.

```
# example of using the cdf for the binomial distribution
from scipy.stats import binom
# define the parameters of the distribution
p = 0.3
k = 100
# define the distribution
dist = binom(k, p)
# calculate the probability of <=n successes
for n in range(10, 110, 10):
    print('P of %d success: %.3f%%' % (n, dist.cdf(n)*100))
```

Listing 8.7: Example of calculating probabilities for values from the binomial cumulative function.

Running the example prints each number of successes in [10, 100] in groups of 10 and the probability of achieving that many success or less over 100 trials. As expected, after 50 successes or less covers 99.999% of the successes expected to happen in this distribution.

```
P of 10 success: 0.000%
P of 20 success: 1.646%
P of 30 success: 54.912%
P of 40 success: 98.750%
P of 50 success: 99.999%
P of 60 success: 100.000%
P of 70 success: 100.000%
P of 80 success: 100.000%
P of 90 success: 100.000%
P of 100 success: 100.000%
```

Listing 8.8: Example output from calculating probabilities for values from the binomial cumulative function.
