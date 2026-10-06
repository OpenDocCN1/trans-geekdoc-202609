# CHAPTER 2. PREDICTING BEHAVIOR WITH CLASSIFICATION MODELS 62

section we learned decision trees are built recursively. Trees are built by first selecting a feature to be at the root, then the root is split into subnodes and on. How those subnodes are chosen depends on their parent node. With Naive Bayes, features don't need information about other features, thus the parameters for each feature can be learned in parallel.

To demonstrate how Naive Bayes works I will use the SMARTPHONE ACTIVITIES dataset as in the previous section. For any given query instance, the aim is to predict your most likely class based on the accelerometer features. For a new query instance, we want to estimate its class based on the features we have observed. Let's say we want to know what is the probability that the query instance belongs to the class ‘Walking’. This can be formulated as follows:

$P(C = Walking|f_1, \dots, f_n).

This reads the conditional probability that the class is ‘Walking’ given the observed evidence. For each instance, the evidence that we can observe are its features $f_1, \dots, f_n$. In this dataset, each instance has 39 features. If we want to estimate what is the most likely class all we need to do is compute the conditional probability for each class and return the highest one:

```
$y = \argmax_{k\in\1,\dots,K\}} P(C_k|f_1, \dots, f_n) \quad (2.10)$
```

where $K$ is the total number of possible classes. The arg notation means: Evaluate the right hand expression for every class $k$ and return the $k$ that resulted with the maximum probability. If instead of arg max we use max (without the arg) that would mean to return the actual maximum probability instead of the class $k$.

Now let's see how we can compute $P(C_k|f_1, \dots, f_n)$. To compute a conditional probability we can use Bayes’ rule:

```
$P(H|E) = \frac{P(H)P(E|H)}{P(E)} \quad (2.11)$
```

Let’s dissect that formula:

+   1. $P(H|E)$ is called the posterior and it is the probability of the hypothesis $H$ given the observed evidence $E$. In our example, the hypothesis can be that $C = Walking$ and the evidence consists of the measured features. This is the probability that ultimately we want to estimate for each class and pick the class with the highest probability.