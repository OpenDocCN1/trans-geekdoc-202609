
The joint probability for events A and B is calculated as the probability of event A given event B multiplied by the probability of event B. This can be stated formally as follows:

$P(A \cap B) = P(A \text{ given } B) \times P(B)$
(4.10)

The calculation of the joint probability is sometimes called the fundamental rule of probability or the *product rule* of probability. Here, $P(A \text{ given } B)$ is the probability of event $A$ given that event $B$ has occurred, called the conditional probability, described below. The joint probability is symmetrical, meaning that $P(A \cap B)$ is the same as $P(B \cap A)$.

### 4.3.2 Marginal Probability

We may be interested in the probability of an event for one random variable, irrespective of the outcome of another random variable. For example, the probability of $X = A$ for all outcomes of $Y$. The probability of one event in the presence of all (or a subset of) outcomes of the other random variable is called the marginal probability or the marginal distribution. The marginal probability of one random variable in the presence of additional random variables is referred to as the marginal probability distribution.

It is called the marginal probability because if all outcomes and probabilities for the two variables were laid out together in a table ($X$ as columns, $Y$ as rows), then the marginal probability of one variable ($X$) would be the sum of probabilities for the other variable ($Y$ rows) on the margin of the table. There is no special notation for the marginal probability; it is just the sum or union over all the probabilities of all events for the second variable for a given fixed event for the first variable.

$P(X = A) = \sum_{y \in Y} P(X = A, Y = y)$
(4.11)

This is another important foundational rule in probability, referred to as the *sum rule*. The marginal probability is different from the conditional probability (described next) because it considers the union of all events for the second variable rather than the probability of a single event.

### 4.3.3 Conditional Probability

We may be interested in the probability of an event given the occurrence of another event. The probability of one event given the occurrence of another event is called the conditional probability. The conditional probability of one to one or more random variables is referred to as the conditional probability distribution. For example, the conditional probability of event $A$ given event $B$ is written formally as:

$P(A \text{ given } B)$
(4.12)

The *given* is denoted using the pipe ($|$) operator; for example:

$P(A \text{ given } B) = P(A|B)$
(4.13)

The conditional probability for events A given event B is calculated as follows:

$$P(A|B) = \frac{P(A \cap B)}{P(B)}\tag{4.14}$$

This calculation assumes that the probability of event B is not zero, e.g. is not impossible. The notion of event A given event B does not mean that event B has occurred (e.g. is certain); instead, it is the probability of event A occurring after or in the presence of event B for a given trial.

## 4.4 Probability for Independence and Exclusivity

When considering multiple random variables, it is possible that they do not interact. We may know or assume that two variables are not dependent upon each other instead are independent. Alternately, the variables may interact but their events may not occur simultaneously, referred to as exclusivity. We will take a closer look at the probability of multiple random variables under these circumstances in this section.

### 4.4.1 Independence

If one variable is not dependent on a second variable, this is called independence or statistical independence. This has an impact on calculating the probabilities of the two variables. For example, we may be interested in the joint probability of independent events A and B, which is the same as the probability of A and the probability of B. Probabilities are combined using multiplication, therefore the joint probability of independent events is calculated as the probability of event A multiplied by the probability of event B. This can be stated formally as follows:

Joint Probability : $P(A \cap B) = P(A) \times P(B)$\tag{4.15}

As we might intuit, the marginal probability for an event for an independent random variable is simply the probability of the event. It is the idea of probability of a single random variable that are familiar with:

Marginal Probability : $P(A)$\tag{4.16}

We refer to the marginal probability of an independent probability as simply the probability. Similarly, the conditional probability of A given B when the variables are independent is simply the probability of A as the probability of B has no effect. For example:

Conditional Probability : $P(A|B) = P(A)$\tag{4.17}

We may be familiar with the notion of statistical independence from sampling. This assumes that one sample is unaffected by prior samples and does not affect future samples. Many machine learning algorithms assume that samples from a domain are independent to each other and come from the same probability distribution, referred to as independent and identically distributed, or i.i.d. for short.

### 4.4.2 Exclusivity

If the occurrence of one event excludes the occurrence of other events, then the events are said to be mutually exclusive. The probability of the events are said to be disjoint, meaning that they cannot interact, are strictly independent. If the probability of event *A* is mutually exclusive with event *B*, then the joint probability of event *A* and event *B* is zero.

$P(A \cap B) = 0.0$ (4.18)

Instead, the probability of an outcome can be described as event *A* or event *B*, stated formally as follows:

$P(A \text{ or } B) = P(A) + P(B)$ (4.19)

The *or* is also called a union and is denoted as a capital *U* letter (∪); for example:

$P(A \text{ or } B) = P(A \cup B)$ (4.20)

If the events are not mutually exclusive, we may be interested in the outcome of either event. The probability of non-mutually exclusive events is calculated as the probability of event *A* and the probability of event *B* minus the probability of both events occurring simultaneously. This can be stated formally as follows:

$P(A \cup B) = P(A) + P(B) - P(A \cap B)$ (4.21)

## 4.5 Further Reading

This section provides more resources on the topic if you are looking to go deeper.

### 4.5.1 Books

- *Probability: For the Enthusiastic Beginner*, 2016. https://amzn.to/2jULJsu
- *Pattern Recognition and Machine Learning*, 2006. https://amzn.to/2JwHE7I
- *Machine Learning: A Probabilistic Perspective*, 2012. https://amzn.to/2xKSTCP

### 4.5.2 Articles

- Probability, Wikipedia. https://en.wikipedia.org/wiki/Probability
- Notation in probability and statistics, Wikipedia. https://en.wikipedia.org/wiki/Notation_in_probability_and_statistics
- Independence (probability theory), Wikipedia. https://en.wikipedia.org/wiki/Independence_(probability_theory)
- Independent and identically distributed random variables, Wikipedia. https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables
- Mutual exclusivity, Wikipedia. https://en.wikipedia.org/wiki/Mutual_exclusivity
- Marginal distribution, Wikipedia. https://en.wikipedia.org/wiki/Marginal_distribution
- Joint probability distribution, Wikipedia. https://en.wikipedia.org/wiki/Joint_probability_distribution
- Conditional probability, Wikipedia. https://en.wikipedia.org/wiki/Conditional_probability

## 4.6 Summary

In this tutorial, you discovered a gentle introduction to joint, marginal, and conditional probability for multiple random variables. Specifically, you learned:

- Joint probability is the probability of two or more events occurring simultaneously.
- Marginal probability is the probability of an event irrespective of the outcome of other variables.
- Conditional probability is the probability of one event occurring in the presence of one or more other events.

### 4.6.1 Next

In the next tutorial, you will discover how to develop an intuition for the different types of probability with worked examples.
