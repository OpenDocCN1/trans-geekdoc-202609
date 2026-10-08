+   * P (B| AI). In other words, 80% of the time, it rains as predicted by the weerman.

+   * P (B| AII). This means that 20% of the time, it doesn't rain as predicted by the weerman.

This formula will ensure that you compute the naïve Bayes probability:

```
P(AI | B) = P(AI)P(B | AI) / (P(AI)P(B | AI) + P(AII)P(B | AII))
```

```
P(AI | B) = (0.0164 * 0.8) / (0.0164 * 0.8 + 0.9834 * 0.2)
```

```
P(AI | B) = 0.065
```

Therefore, the preceding computation says that although the weerman forecasted rain, there is only a 6.5% probability that it will rain with respect to Bayes theorem.

The naïve Bayes is heavily applied in e-mail filtering. It requires the instance of every word in an e-mail and calculates the likelihood of whether the e-mail is spam or not. The naïve Bayes model learns from the previous data of eemails and marks emails as spam, which is important in coming to the conclusion on whether an e-mail is a spam or not.

# The K-means Clustering

The k-means clustering is a technique of unsupervised learning that is important in segregating data of n observations into k buckets of the same observations.

![](bbox=[0.119, 0.584, 0.503, 0.789])

This clustering algorithm called so because it operates by computing the mean of the feature, which represents the dependent variables you cluster things like customer classification on an average transaction amount and the average number of products purchased in a quarter of a year. The average