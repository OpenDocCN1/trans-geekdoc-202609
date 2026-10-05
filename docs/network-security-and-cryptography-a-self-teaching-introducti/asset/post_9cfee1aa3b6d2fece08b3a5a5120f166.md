
# MATHEMATICAL FOUNDATIONS FOR COMPUTER NETWORKS • 33

![](img/d3b56042c756fbcc011ff06f1b9f53f0_57_0.png)

FIGURE 2.1 Realizations of a random process.

Queueing is simply waiting in line, such as stopping at the toll booth, waiting in line for a bank cashier, stopping at a traffic light, waiting to buy stamps at the post office, and so on.

A queue consists of a line of customers or waiting to be served and a service center with one or more servers.

For example, there would be no need of queueing in a bank if there were an infinite number of people serving the customers. But that would be very expensive and impractical.

# 34 NETWORK SECURITY AND CRYPTOGRAPHY

Queuing theory is applied in several scientific disciplines such as computer systems, traffic management, operations, production, and manufacturing. It plays a significant role in modeling computer communication networks.

Reduced to its most basic form, a computer network consists of communication channels and processors (nodes). As message flow from node to node, queues begin to form at different nodes. For high traffic intensity the waiting or queuing time can be dominant, so that the performance of the network is dictated by the behavior of the queues at the nodes. Analytical derivation of the waiting time requires the knowledge of queuing theory.

This chapter provides a cursory review of the basic mathematical concepts needed throughout this book for computer networking and security. A reader already well-versed in these concepts may skip this chapter.

## 2.2 PROBABILITY FUNDAMENTALS

A fundamental concept in probability theory is the idea of an experiment. An experiment (or trial) is the performance of an operation that leads to results called *outcomes*. In other words, an outcome is a result of performing the experiment once. An *event* is one or more outcomes of an experiment. The relationship between outcomes and events is shown in the Venn diagram of Figure 2.2. Thus,

![](img/d3b56042c756fbcc011ff06f1b9f53f0_58_0.png)

FIGURE 2.2 Sample space (rectangle) illustrating the relationship between outcomes (dots) and events (circles).

# MATHEMATICAL FOUNDATIONS FOR COMPUTER NETWORKS • 35

An experiment consists of making a measurement or observation.
An outcome is a possible result of an experiment.
An event is a collection of outcomes.

An experiment is said to be random if its outcome cannot be predicted. Thus, a random experiment is one that can be repeated a number of times but yields unpredictable outcomes at each trial. Examples of random experiments are tossing a coin, observing the number of cars arriving at a toll booth, and keeping track of the number of telephone calls on your iPhone.

### 2.2.1 Simple Probability

We define the probability of an event. The probability of event A is the number of ways A can occur divided by the total number of possible outcomes. Suppose we perform $n$ trials of an experiment and observe that outcomes satisfying event A $n_A$ times. We define the probability $P(A)$ of event A occurring as

$$P(A) = \lim_{n\to\infty} \frac{n_A}{n}$$ (2.1)

This is known as the relative frequency of event A. Two key points should be noted from Equation (2.1). First, we note that the probability $P$ of an event is always a positive number and that

$$0 \le P \le 1$$ (2.2)

where $P = 0$ (0%) when an event is not possible (never occurs or is impossible) and $P = 1$ (100%) when the event is sure (always occurs or is certain). Second, observe that for the probability to have meaning, the trials of $n$ must be large.

For a finite number of outcomes of any sample space $S$ with events $A_1, A_2, \dots, A_f$ is always the total probability of all events equal to one, that is,

$$\sum_{i=1}^{f} P(A_i) = 1$$ (2.3)

Let $A$ and $B$ be two events. Then, the following are true.

# 36 • NETWORK SECURITY AND CRYPTOGRAPHY

- Intersection probability: $P(A \cap B)$ occurs when probability of both $A$ and $B$ occurs;
- Union probability: $P(A \cup B)$ occurs when probability of $A$ or $B$ occurs;
- Complement of probability: $P(\overline{A})$ occurs when probability of $A$ does not occur.

The events $A$ and $B$ are *mutually exclusive* if they are disjoint, that is, $A \cap B = \emptyset$, so

$$P(A \cap B) = 0$$ (2.4)

If $A$ and $B$ are *independent*, then the probability of event $A$ and $B$ occurring is equal to multiplying the probability of event $A$ with the probability of event $B$, that is

$$P(A \cap B) = P(A)P(B)$$ (2.5)

If $A$ and $B$ are *disjoint* or *mutually exclusive*, it follows that the two events cannot occur simultaneously or have outcomes in common, as shown in Figure 2.3. In this case, the probability that either event $A$ or $B$ occurs is equal to the sum of their probabilities, that is

$$P(A \cup B) = P(A) + P(B)$$ (2.6)

Sample space
![](img/d3b56042c756fbcc011ff06f1b9f53f0_60_0.png)
FIGURE 2.3 Mutually exclusive or disjoint events.

To prove this, suppose in an experiment with $n$ trials, event $A$ occurs $n_A$ times while event $B$ occurs $n_B$ times. Then event $A$ or $B$ occurs $n_A + n_B$ times, and

$$P(A \text{ or } B) = \frac{n_A + n_B}{n} = \frac{n_A}{n} + \frac{n_B}{n} = P(A) + P(B)$$ (2.7)

This result can be extended to the case when all events in an experiment are

$$n_A + n_B + \dots = n$$

Dividing by $n$ and assuming $n$ is large, we obtain

$$P(A) + P(B) + \dots = 1$$ (2.8)

which indicates that the probabilities of mutually exclusive events must add up to unity. A special case of this is when two events are complementary, that is, if event $A$ occurs $B$ must not occur, and vice versa. In this case,

$$P(A) + P(B) = 1$$ (2.9)

or

$$P(A) = 1 - P(B)$$ (2.10)

For example, in tossing a coin, the event of a head is complementary to that of a tail. Since the probability of either event is $1/2$, their probabilities add up to 1. The sum of the probability of any event A and its complement must be equal to 1, that is

$$P(A) + P(\overline{A}) = 1$$ (2.11)

Or

$$P(\text{not } A) = P(\overline{A}) = 1 - P(A)$$ (2.12)

## 2.2.2 Joint Probability

Next, we consider when events A and B are not mutually exclusive. Two events are non-mutually exclusive if they have one or more outcomes in common, as illustrated in Figure 2.4. The probability of the union event A or B (or $A \cup B$) is

$$P(A \cup B) = P(A) + P(B) - P(A \cap B)$$ (2.13)

Sample space
![](img/d3b56042c756fbcc011ff06f1b9f53f0_62_0.png)

where $P(A \cap B)$ is called the joint probability of events A and B, that is, the probability of the intersection of joint event $A \cap B$.

The probability of event A occurs, but not B; that is

$$P(A - B) = P(A) - P(A \cap B)$$ (2.14)

# **Example 2.1**

Consider two events A and B with $P(A) = 0.6, P(B) = 0.3$, and $P(A \cap B) = 0.1$.

Find: (a) the probability of A does not occur, (b) the probability of A or B occurs, and (c) the probability of A but not B occurs.

# **Solution**

- **A.** $P(\text{not } A) = P(\bar{A}) = 1-P(A) = 1-0.6 = 0.4$
- **B.** $P(A \text{ or } B \text{ occurs}) = P(A \cup B) = P(A) + P(B) - P(A \cap B) = 0.6 + 0.3 - 0.1 = 0.8$
- **C.** $P(A \text{ but not B}) = P(A - B) = P(A) - P(A \cap B) = 0.6 - 0.1 = 0.5$

# MATHEMATICAL FOUNDATIONS FOR COMPUTER NETWORKS • 39

## 2.2.3 Conditional Probability

Sometimes we are confronted with a situation in which the outcome of one event depends on another. The dependence of event B on event A is measured by the *conditional probability* $P(B|A)$ given by

$$P(B|A) = \frac{P(A \cap B)}{P(A)}$$

where $P(A \cap B)$ is the joint probability of events A and B. The notation $B|A$ stands for “B given A”. In case $A$ and $B$ are mutually exclusive, the joint probability $P(A \cap B) = 0$ so that the conditional probability $P(B|A) = 0$. Similarly, the conditional probability of A given B is

$$P(A|B) = \frac{P(A \cap B)}{P(B)}$$

From Equations (2.15) and (2.16), we obtain

$$P(A \cap B) = P(B|A)P(A) = P(A|B)P(B)$$

which is a form of *Bayes’ theorem*.

# ### Example 2.2

A box contains 10 balls of which 7 are yellow and 3 are orange. Three balls are drawn at random one after the other. Find the probability $P(E)$ that all three are yellow.

# ### Solution

The probability that the first ball is yellow is 7/10, since 7 of the 10 balls are yellow. So, if the first ball is yellow, then the probability that the second ball is yellow is 6/9, since only 6 of the remaining 9 balls are yellow. If the first two drawn balls are yellow, then the probability that the third ball is yellow is 5/8, since only 5 of the remaining balls are yellow. Therefore, using the multiplication theory of conditional probability,
