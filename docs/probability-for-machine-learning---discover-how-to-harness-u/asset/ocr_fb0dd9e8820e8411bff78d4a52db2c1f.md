The joint probability for events A and B is calculated as the probability of event A given event B multiplied by the probability of event B. This can be stated formally as follows:

$P(A \cap B) = P(A \text{ given } B) \times P(B)$
(4.10)

The calculation of the joint probability is sometimes called the fundamental rule of probability or the *product rule* of probability. Here, $P(A \text{ given } B)$ is the probability of event $A$ given that event $B$ has occurred, called the conditional probability, described below. The joint probability is symmetrical, meaning that $P(A \cap B)$ is the same as $P(B \cap A)$.

# 4.3.2 Marginal Probability

We may be interested in the probability of an event for one random variable, irrespective of the outcome of another random variable. For example, the probability of $X = A$ for all outcomes of $Y$. The probability of one event in the presence of all (or a subset of) outcomes of the other random variable is called the marginal probability or the marginal distribution. The marginal probability of one random variable in the presence of additional random variables is referred to as the marginal probability distribution.

It is called the marginal probability because if all outcomes and probabilities for the two variables were laid out together in a table ($X$ as columns, $Y$ as rows), then the marginal probability of one variable ($X$) would be the sum of probabilities for the other variable ($Y$ rows) on the margin of the table. There is no special notation for the marginal probability; it is just the sum or union over all the probabilities of all events for the second variable for a given fixed event for the first variable.

$P(X = A) = \sum_{y \in Y} P(X = A, Y = y)$
(4.11)

This is another important foundational rule in probability, referred to as the *sum rule*. The marginal probability is different from the conditional probability (described next) because it considers the union of all events for the second variable rather than the probability of a single event.

# 4.3.3 Conditional Probability

We may be interested in the probability of an event given the occurrence of another event. The probability of one event given the occurrence of another event is called the conditional probability. The conditional probability of one to one or more random variables is referred to as the conditional probability distribution. For example, the conditional probability of event $A$ given event $B$ is written formally as:

$P(A \text{ given } B)$
(4.12)

The *given* is denoted using the pipe ($|$) operator; for example:

$P(A \text{ given } B) = P(A|B)$
(4.13)