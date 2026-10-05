MATHEMATICAL FOUNDATIONS FOR COMPUTER NETWORKS • 39

# ## 2.2.3 Conditional Probability

Sometimes we are confronted with a situation in which the outcome of one event depends on another event. The dependence of event B on event A is measured by the *conditional probability* $P(B|A)$ given by

```
$P(B|A) = \frac{P(A \cap B)}{P(A)}$
```

where $P(A \cap B)$ is the joint probability of events A and $B$. The notation $B|A$ stands for “B given A.\ In case events $A$ and $B$ are mutually exclusive, the joint probability $P(A \cap B) = 0$ so that the conditional probability $P(B|A) = 0$. Similarly, the conditional probability of A given B is

```
$P(A|B) = \frac{P(A \cap B)}{P(B)}$
```

From Equations (2.15) and (2.16), we obtain

```
$P(A \cap B) = P(B|A)P(A) = P(A|B)P(B)$
```

Eliminating $P(AB)$ gives

```
$P(B|A) = \frac{P(A|B)P(B)}{P(A)}$
```

which is a form of *Bayes’ theorem*.

# ### Example 2.2

A box contains 10 balls of which 7 are yellow and 3 are orange. Three balls are drawn at random one after the other. Find the probability $P(E)$ that all three are yellow.

# ### Solution

The probability that the first ball is yellow is 7/10, since 7 of the 10 balls are yellow. So, if the first ball is yellow, then the probability that the second ball is yellow is 6/9, since only 6 of the remaining 9 balls are yellow. If the first two drawn balls are yellow, then the probability that the third ball is yellow is 5/8, since only 5 of the remaining balls are yellow. Therefore, using the multiplication theory of conditional probability,