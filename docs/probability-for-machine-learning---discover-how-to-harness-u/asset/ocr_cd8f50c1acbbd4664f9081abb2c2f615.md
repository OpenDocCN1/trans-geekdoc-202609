Entropy can be calculated for a random variable $X$ with $K$ discrete states as follows:

$$H(X) = -\sum_{i=1}^{K} p(k_i) \times \log(p(k_i)) \tag{21.4}$$

That is the negative of the sum of the probability of each event multiplied by the log of the probability of each event. Like information, the $log()$ function uses base-2 and the units are bits. The natural logarithm can be used instead and the units will be nats. The lowest entropy is calculated for a random variable that has a single event with a probability of 1.0, a certainty. The largest entropy for a random variable will be if all events are equally likely. We can consider a roll of a fair die and calculate the entropy for the variable. Each outcome has the same probability of $\frac{1}{6}$, therefore it is a uniform probability distribution. We therefore would expect the average information to be the same information for a single event calculated in the previous section.

```
```python
# calculate the entropy for a dice roll
from math import log2
# the number of events
n = 6
# probability of one event
p = 1.0/n
# calculate entropy
entropy = -sum([p * log2(p) for _ in range(n)])
# print the result
print('entropy: %.3f bits' % entropy)
```
```

Listing 21.7: Example calculating the entropy of rolling a dice.

Running the example calculates the entropy as more than 2.5 bits, which is the same as the information for a single outcome. This makes sense, as the average information is the same as the lower bound on information as all outcomes are equally likely.

```
```text
entropy: 2.585 bits
```
```

Listing 21.8: Example output from calculating the entropy of rolling a dice.

If we know the probability for each event, we can use the `entropy()` SciPy function to calculate the entropy directly. For example:

```
```python
# calculate the entropy for a dice roll
from scipy.stats import entropy
# discrete probabilities
p = [1/6, 1/6, 1/6, 1/6, 1/6, 1/6]
# calculate entropy
e = entropy(p, base=2)
# print the result
print('entropy: %.3f bits' % e)
```
```

Listing 21.9: Example calculating the entropy of rolling a dice with SciPy.

Running the example reports the same result that we calculated manually.

```
```text
entropy: 2.585 bits
```
```

Listing 21.10: Example output from calculating the entropy of rolling a dice with SciPy.