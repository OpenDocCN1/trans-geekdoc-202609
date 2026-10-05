# Big data recommender systems, volume 1

from the current state to another state (or remain in the same state) according to a probability distribution.

Here we have included the interval when each symptom reflects the visualisation of the condition. The set of Markov state equations describes the probabilistic transition from the initial states to the final states. The transition visualisation probabilities obeying the following rules:

+   1. Transitive aspect: Transitive aspect defines how a symptom passes from one condition to another condition. We will provide a mathematical simulation including conditional graph where the others describe the matrix passes. The probabilities of more than one transition in time are infinitesimals of higher order and can be neglected.

+   2. Temporary aspect: Temporary aspect is defined as the interval needed to the requirements on one to the others. In another word, the probability of transition in time $\Delta t$ from one condition to another is given by gain into $\Delta t$.

The interval is estimated by the point of views condition and refers to transformation probabilities or simply perceived the probabilities. The transformation probability is represented by itself the average interval passes, from the condition of end diagnosing/monitoring of the condition and, before reception, by them next probability condition during the same interval. The Markov model can be illustrated by means of a state transition diagram, which shows all the states and transition probabilities.

The chain describe as follows: We have a set of states, $\mathcal{S} = \{S_0, S_1, S_2, \dots, S_n\}$. The process starts in one of these states and moves successively from one state to another. Each move is called a step. If the chain is currently in $S_i$, it moves to $S_j$ at the next step with a probability denoted by $S_{ij}$, and this probability does not depend upon the state in which the chain was before the current state. The probabilities $S_{ij}$ are called transition probabilities. The process can remain with an initial probability distribution, defined on $\mathcal{S}$, specifies the starting state. This is usually done by specifying a particular state as the starting state. Using the transition matrix $S$, the hypertension probability could be represented as $S_{00}, \dots, S_{06}$.

Figure 5.7 shows the Markov chain with respect to the different hypertension probabilities. The other events also have probabilities that can be written as products of entries of $S$. In general, if a Markov chain has $r$ states, then

```
$S_{06}^{(2)} = \sum_{\mu} S_{0\mu} S_{\mu6}$ (5.11)
```

The following general theorem is easy to be proved by using the above observation and induction. There is an initial probability distribution to the set of states. We can define a Markov model as follows:

```
$S_0(k+1) = 0 + 0 + 0 + 0 + 0 + 0 + 0$ (5.12)
```