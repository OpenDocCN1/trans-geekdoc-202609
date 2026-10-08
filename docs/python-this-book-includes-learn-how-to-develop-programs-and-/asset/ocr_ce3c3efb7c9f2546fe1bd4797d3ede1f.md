Below is a graph representing the Bernoulli distribution:

![](bbox=[0.142, 0.126, 0.597, 0.396])

A perfect example of the Bernoulli distribution is voting in an election.
The Bernoulli distribution can be produced using the bernoulli.rvs () function of the SciPy package. This generates a Bernoulli distribution using a probability of scipy.0.7.

```
>>> from scipy import stats
>>> stats.bernoulli.rvs(0.7, size=100)
array([1, 1, 1, 1, 1, 0, 0, 1, 1, 0, 1, 1, 0, 0, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 0, 0, 1, 1, 0, 0, 0, 0, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 0, 1])
```

If the above output represents the number of votes for a candidate by people, then the candidate has 70% of the votes.

# The A-Z Score

In simple terms, this is a score that describes the value of distribution in standard deviation with respect to the average. Consider the following formula that computes the z-score: