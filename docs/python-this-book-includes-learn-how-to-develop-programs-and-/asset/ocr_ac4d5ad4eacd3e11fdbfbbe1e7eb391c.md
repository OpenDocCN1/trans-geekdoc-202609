Let's discuss these probabilities with the help of Bayes' rule:

```
$P(positive|review) = \frac{P(review|positive) * P(positive)}{P(review)}$$\nP(negative|review) = \frac{P(review|negative) * P(negative)}{P(review)}$
```

As you compare these two equations to finalize the prediction, you can ignore the denominator, which is a simple scaling factor.
The LHS (left-hand side) of the preceding equation is known as the posterior probability.
Let's consider the numerator of the RHS (right-hand side)

```
$P(review|positive) * P(positive)$
```

P (positive) refers to the probability of a positive class. It's the belief the positive class label distribution depending on the training set.
You will approximate it from the training test set. It's computed as follows:

```
$P(positive) = \frac{No\ of\ reviews\ with\ positive\ class\ label}{Total\ reviews\ in\ the\ corpus}$
```

P(review|positive) is the probability. It addresses the question: what is the odd of getting the review, provided that the class is positive. Again, you will estimate it from the training set.
Before we explore the probability equation further, let's introduce the feature of independence assumption. The algorithm is prefixed as naïve because of this assumption. Contrary to this, you assume that the words occur in a document independent of each other. You will apply this assumption to compute the likelihood.
A look at the list of words. Let's apply some mathematical notation:

```
$review = \{word_1, word_2, ..., word_n\}$
```

With the independence assumption, you can conclude that the probability of each of these words taking place in a review is the product of all