
- The distribution of sum of squares of $n$ normal random variables: $\sum_i^n Z_i^2 \sim \chi_n^2$

The sum of two $\chi^2$ RV with $p$ and $q$ df is a $\chi^2$ RV with $p + q$ df. This is useful when summing/subtracting sum of squares.

The $\chi^2$-distribution is used to model errors measured as sum of squares or the distribution of the sample variance.

The F-distribution, $F_{n,p}$, with $n$ and $p$ degrees of freedom is the ratio of two independent $\chi^2$ variables. Let $X \sim \chi_n^2$ and $Y \sim \chi_p^2$ then:

$$F_{n,p} = \frac{X/n}{Y/p}$$

The F-distribution plays a central role in hypothesis testing answering the question: Are two variances equal? Is the ratio of two errors significantly large?

```
import numpy as np
from scipy.stats import f
import matplotlib.pyplot as plt
%matplotlib inline
fvalues = np.linspace(1, 5, 100)
# pdf(x, df1, df2): Probability density function at x of F.
plt.plot(fvalues, f.pdf(fvalues, 1, 30), 'b-', label="F(1, 30)")
plt.plot(fvalues, f.pdf(fvalues, 5, 30), 'r-', label="F(5, 30)")
plt.legend()
# cdf(x, df1, df2): Cumulative distribution function of F.
# ie.
proba_at_f_inf_3 = f.cdf(3, 1, 30) # P(F(1,30) < 3)
# ppf(q, df1, df2): Percent point function (inverse of cdf) at q of F.
f_at_proba_inf_95 = f.ppf(.95, 1, 30) # q such P(F(1,30) < .95)
assert f.cdf(f_at_proba_inf_95, 1, 30) == .95
# sf(x, df1, df2): Survival function (1 - cdf) at x of F.
proba_at_f_sup_3 = f.sf(3, 1, 30) # P(F(1,30) > 3)
assert proba_at_f_inf_3 + proba_at_f_sup_3 == 1
# p-value: P(F(1, 30)) < 0.05
low_proba_fvalues = fvalues[fvalues > f_at_proba_inf_95]
plt.fill_between(low_proba_fvalues, 0, f.pdf(low_proba_fvalues, 1, 30),
alpha=.8, label="P < 0.05")
plt.show()
```

![](img/c2ad4b400bf63af9804b2d44510f76a6_82_0.png)

### 7.2.4 The Student's t-distribution

Let $M \sim \mathcal{N}(0,1)$ and $V \sim \chi_n^2$. The t-distribution, $T_n$, with $n$ degrees of freedom is the ratio:

$$T_n = \frac{M}{\sqrt{V/n}}$$

The distribution of the difference between an estimated parameter and its true (or assumed) value divided by the standard deviation of the estimated parameter (standard error) follows a t-distribution. Is this parameter different from a given value?

## 7.3 Hypothesis Testing

- Test a proportion: Biased coin? 200 heads have been found over 300 flips, is the coin biased?
- Test the association between two variables.
  - Example height and sex: In a sample of 25 individuals (15 females, 10 males), is female height different from male height?
  - Example age and arterial hypertension: In a sample of 25 individuals, is age highly correlated with arterial hypertension?

1. Model the data
2. Fit: estimate the model parameters (frequency, mean, correlation, regression coefficient)
3. Compute a test statistic from the model parameters.
4. Formulate the null hypothesis: What would be the (distribution of the) test statistic if the observations are the result of pure chance.
5. Compute the probability (p-value) to obtain a larger value for the test statistic by chance (under the null hypothesis).

### 7.3.1 Flip coin: Simplified example

Biased coin? 2 heads have been found over 3 flips, is the coin biased?

1. Model the data: number of heads follows a Binomial distribution.
2. Compute model parameters: N=3, P = the frequency of number of heads over the number of flips: 2/3.
3. Compute a test statistic, same as frequency.
4. Under the null hypothesis the distribution of the number of heads is:

| 1 | 2 | 3 | count #heads |
|---|---|---|---------------|
|   |   |   | 0 |
| H |   |   | 1 |
|   | H |   | 1 |
|   |   | H | 1 |
| H | H |   | 2 |
| H |   | H | 2 |
|   | H | H | 2 |
| H | H | H | 3 |

8 possible configurations, probabilities of different values for x are: x measures the number of successes.

- P(x = 0) = 1/8
- P(x = 1) = 3/8
- P(x = 2) = 3/8
- P(x = 3) = 1/8

```
plt.bar([0, 1, 2, 3], [1/8, 3/8, 3/8, 1/8], width=0.9)
_ = plt.xticks([0, 1, 2, 3], [0, 1, 2, 3])
plt.xlabel("Distribution of the number of heads over 3 flips under the null hypothesis")
```

```
Text(0.5, 0, 'Distribution of the number of heads over 3 flips under the null hypothesis')
```

![](img/c2ad4b400bf63af9804b2d44510f76a6_84_0.png)

Distribution of the number of heads over 3 flips under the null hypothesis

5. Compute the probability (p-value) to observe a value larger than or equal to 2 under the null hypothesis. This probability is the p-value:

$$P(x \geq 2|H_0) = P(x = 2) + P(x = 3) = 3/8 + 1/8 = 4/8 = 1/2$$

### 7.3.2 Flip coin: Real Example

Biased coin? 60 heads have been found over 100 flips, is the coin biased?

1. Model the data: number of heads follows a Binomial distribution.
2. Compute model parameters: N=100, P=60/100.
3. Compute a test statistic, same as frequency.
4. Compute a test statistic: 60/100.
5. Under the null hypothesis the distribution of the number of heads (k) follows the **binomial distribution** of parameters N=100, **P=0.5**:

$$\Pr(X = k|H_0) = \Pr(X = k|n = 100, p = 0.5) = \binom{100}{k} 0.5^k (1 - 0.5)^{100-k}.$$

$$\Pr(X = k \geq 60|H_0) = \sum_{k=60}^{100} \binom{100}{k} 0.5^k (1 - 0.5)^{100-k} = 1 - \sum_{k=0}^{60} \binom{100}{k} 0.5^k (1 - 0.5)^{100-k}, \text{ the cumulative distribution function.}$$

### Use tabulated binomial distribution

```
import scipy.stats
import matplotlib.pyplot as plt

#tobs = 2.39687663116 # assume the t-value
success = np.linspace(30, 70, 41)
plt.plot(success, scipy.stats.binom.pmf(success, 100, 0.5), 'b-', label="Binomial(100, 0.5)")
upper_success_tvalues = success[success > 60]
plt.fill_between(upper_success_tvalues, 0, scipy.stats.binom.pmf(upper_success_tvalues, 100, 0.5), alpha=.8, label="p-value")
_ = plt.legend()

pval = 1 - scipy.stats.binom.cdf(60, 100, 0.5)
print(pval)
```

```
0.01760010010885238
```

![](img/c2ad4b400bf63af9804b2d44510f76a6_85_0.png)

### Random sampling of the Binomial distribution under the null hypothesis

```
success_h0 = scipy.stats.binom.rvs(100, 0.5, size=10000, random_state=4)

#success_h0 = np.array([] for i in range(5000)])
import seaborn as sns
_ = sns.distplot(success_h0, hist=False)

pval_rnd = np.sum(success_h0 >= 60) / (len(success_h0) + 1)
print("P-value using monte-carlo sampling of the Binomial distribution under H0=", pval_rnd)
```

```
P-value using monte-carlo sampling of the Binomial distribution under H0= 0.025897410258974102
```

### Example

Given the following samples, we will test whether its true mean is 1.75.

Warning, when computing the std or the variance, set ddof=1. The default value, ddof=0, leads to the biased estimator of the variance.

```
import numpy as np

x = [ 1.83,  1.83,  1.73,  1.82,  1.83,  1.73,  1.99,  1.85,  1.68,  1.87]

xbar = np.mean(x)  # sample mean
mu0 = 1.75  # hypothesized value
s = np.std(x, ddof=1)  # sample standard deviation
n = len(x)  # sample size

tobs = (xbar - mu0) / (s / np.sqrt(n))
print(tobs)
```

```
2.3968766311585883
```

The $p$-value is the probability to observe a value $t$ more extreme than the observed one $t_{obs}$ under the null hypothesis $H_0$: $P(t > t_{obs}|H_0)$

```
import scipy.stats as stats
import matplotlib.pyplot as plt

#tobs = 2.39687663116  # assume the t-value
tvalues = np.linspace(-10, 10, 100)
plt.plot(tvalues, stats.t.pdf(tvalues, n-1), 'b-', label='T(n-1)')
upper_tval_tvalues = tvalues[tvalues > tobs]
plt.fill_between(upper_tval_tvalues, 0, stats.t.pdf(upper_tval_tvalues, n-1), alpha=.8, label='p-value')
_ = plt.legend()
```

![](img/c2ad4b400bf63af9804b2d44510f76a6_87_0.png)

## 7.4 Testing pairwise associations

Univariate statistical analysis: explore association between pairs of variables.

- In statistics, a categorical variable or factor is a variable that can take on one of a limited, and usually fixed, number of possible values, thus assigning each individual to a particular group or "category". The levels are the possible values of the variable. Number of levels = 2: binomial; Number of levels > 2: multinomial. There is no intrinsic ordering to the categories. For example, gender is a categorical variable having two categories (male and female) and there is no intrinsic ordering to the categories. For example, Sex (Female, Male), Hair color (blonde, brown, etc.).
- An ordinal variable is a categorical variable with a clear ordering of the levels. For example: drinks per day (none, small, medium and high).
- A continuous or quantitative variable x ∈ ℝ is one that can take any value in a range of possible values, possibly infinite. E.g.: salary, experience in years, weight.

What statistical test should I use?
See: http://www.ats.ucla.edu/stat/mult_pkg/whatstat/

![](img/c2ad4b400bf63af9804b2d44510f76a6_88_0.png)

> Fig. 7.1: Statistical tests
