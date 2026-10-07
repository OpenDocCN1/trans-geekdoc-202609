# Bayes theorem 2

Suppose X and Y are two events. Then, Bayes theorem states that:

```
$P(X|Y) = \frac{P(Y|X) \cdot P(X)}{P(Y)}$
```

We will focus on the aspect of the Bayes theorem that we need to work with the Naïve Bayes algorithm.

Notice that we have inverted the need to find in the Bayes theorem. To find $P(X|Y)$, we will determine $P(Y|X)$ along with $P(X)$ and $P(Y)$. This is useful in many circumstances. Let us understand through this example.

We consider the same example we used to understand the Total Probability theorem. So, we have 40% females in a class. The probability that a male student is 6' tall is 20%, and the likelihood that a female student is 6' tall is 1%. Now, suppose that we observed a 6' tall student. We want to determine the probability that this 6' tall student is a female.

We consider that Y is the event that the student is 6' tall. So, $P(6') = P(Y)$.

Also, consider that $X_i$ is the event that a student is a Male, that is, $P(Male) = P(X_i)$ and $X_j$ is the event that a student is a Female, that is, $P(Female) = P(X_j)$. We know that:

```
$P(Female) = P(X_j) = 40\%$ and $P(Male) = P(X_i) = 1 - P(Female) = 1 - P(X_j) = 60\%$
```

```
$P(6'|Male) = P(Y|X_i) = 20\%$ and $P(6'|Female) = P(Y|X_j) = 1\%$
```

We need to find the probability that a student is a female, given that the student is 6' tall. or we want to find $P(Female|6') = P(X_j|Y)$.

Using Bayes theorem, we know that:

```
$P(X_2|Y) = (P(Y|X_j) \cdot P(X_j)) / P(Y)$
```

From the Total probability theorem, we know that:

```
$P(Y) = P(Y|X_i) \cdot P(X_i) + P(Y|X_j) \cdot P(X_j)$
```

So, we get:

```
$P(X_2|Y) = \frac{P(Y|X_2) \cdot P(X_2)}{P(X_1) \cdot P(X_1) + P(Y|X_2) \cdot P(X_2)}$
```