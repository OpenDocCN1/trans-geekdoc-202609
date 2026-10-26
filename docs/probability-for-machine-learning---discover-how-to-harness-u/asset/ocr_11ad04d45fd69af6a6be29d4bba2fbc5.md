# 17.2 Bayes Theorem of Modeling Hypotheses

Bayes Theorem is a useful tool in applied machine learning. It provides a way of thinking about the relationship between data and a model. A machine learning algorithm or model is a specific way of thinking about the structured relationships in the data. In this way, a model can be thought of as a hypothesis about the relationships in the data, such as the relationship between input (X) and output (y). The practice of applied machine learning is the testing and analysis of different hypotheses (models) on a given dataset. Bayes Theorem provides a probabilistic model to describe the proportional relationship between data (D) and a hypothesis (H); for example:

$$P(h|D) = \frac{P(D|h) \times P(h)}{P(D)}$$ (17.1)

Breaking this down, it says that the probability of a given hypothesis holding or being true given some observed data can be calculated as the probability of observing the data given the hypothesis multiplied by the probability of the hypothesis being true regardless of the data, divided by the probability of observing the data regardless of the hypothesis.

> Bayes theorem provides a way to calculate the probability of a hypothesis based on its prior probability, the probabilities of observing various data given the hypothesis, and the observed data itself.
> 
> — Page 156, Machine Learning, 1997.

Under this framework, each piece of the calculation has a specific name; for example:

+   - P(h|D): Posterior probability of the hypothesis (the thing we want to calculate).
+   - P(h): Prior probability of the hypothesis.

This gives a useful framework for thinking about and modeling a machine learning problem. If we have some prior domain knowledge about the hypothesis, this is captured in the prior probability. If we don’t, then all hypotheses may have the same prior probability. If the probability of observing the data P(D) increases, then the probability of the hypothesis holding given the data P(h|D) decreases. Conversely, if the probability of the hypothesis P(h) and the probability of observing the data given the hypothesis increases, the probability of the hypothesis holding given the data P(h|D) increases.

The notion of testing different models on a dataset in applied machine learning can be thought of as estimating the probability of each hypothesis (h1, h2, h3, … , ∈ H) being true given the observed data. Under this framework, the probability of the data (D) is constant as it is used in the assessment of each hypothesis. Therefore, it can be removed from the calculation to give the simplified unnormalized estimate as follows:

$$\max_{h \in H} P(h|D) = P(D|h) \times P(h)$$ (17.2)

If we do not have any prior information about the hypothesis being tested, they can be assigned a uniform probability, and this term too will be a constant and can be removed from the calculation to give the following:

$$\max_{h \in H} P(h|D) = P(D|h)$$ (17.3)