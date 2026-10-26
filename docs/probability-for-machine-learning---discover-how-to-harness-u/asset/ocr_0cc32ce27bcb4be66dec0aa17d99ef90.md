Listing 9.4: Example of calculating the values that define the middle of the distribution.

Running the example gives the exact outcomes that define the middle 95% of expected outcomes that are very close to our standard-deviation-based heuristics of 40 and 60.

```
Middle 95% between 40.2 and 59.8
```

Listing 9.5: Example output from calculating the values that define the middle of the distribution.

An important related distribution is the Log-Normal probability distribution.

# 9.4 Exponential Distribution

The exponential distribution is a continuous probability distribution where a few outcomes are the most likely with a rapid decrease in probability to all other outcomes. It is the continuous random variable equivalent to the geometric probability distribution for discrete random variables. Some examples of domains that have exponential distribution events include:

+   - The time between clicks on a Geiger counter.
+   - The time until the failure of a part.
+   - The time until the default of a loan.

The distribution can be defined using one parameter:

+   - **Scale** (Beta or β): The mean and standard deviation of the distribution.

Sometimes the distribution is defined more formally with a parameter lambda or rate. The beta parameter is defined as the reciprocal of the lambda parameter (β = 1/λ)

+   - **Rate** (lambda or λ) = Rate of change in the distribution.

We can define a distribution with a mean of 50 and sample random numbers from this distribution. We can achieve this using the exponential() NumPy function. The example below samples and prints 10 numbers from this distribution.

```
```python
# sample an exponential distribution
from numpy.random import exponential
# define the distribution
beta = 50
n = 10
# generate the sample
sample = exponential(beta, n)
print(sample)
```
```

Listing 9.6: Example of sampling from an exponential distribution.

Running the example prints 10 numbers randomly sampled from the defined distribution.