# 548

# MACHINE LEARNING

We provide intuitive grounds for readers to develop their algorithms which could be built upon the presented principles.

First, let us define the three-armed bandit as a collection of three uniform distributions $P_1, P_2, P_3$, each given by $P_i \sim U[0, max_i]$. The set of three parameters – the upper bounds – defines the bandit and the mean of the bandit’s arms. Without loss of generality, let us further consider $maxP_1 < maxP_2 < maxP_3$. The multi-armed bandit with uniform distribution is implemented as:

```
.quantQ.m.MAB:[choice;mSpec]
// mabSpec -- vector of maxBoundK
// choice -- choice to be drawn
// first?f"$mSpec[choice];
```

The MAB has two arguments: the first is the bandit chosen, and the second is the selection of the bandit itself through mabSpec. The three-armed bandit is then defined by setting the mabSpec input variable to a three-dimensional array. The function returns a random draw for a given choice of the bandit’s arm:

```
.quantQ.mcts.MAB[(1.0;2.0;3.0)]
```

1.178257

Let us run a numerical experiment: we each arm 100 times and return the average outcome for every arm:

[avg .quantQ.mcts.MAB[(1.0;2.0;3.0)] each 100ux each til 3

0.523849 1.033051 1.608269

where each number is approximately half of the corresponding number in mabSpec.

# Exploration of first greedy algorithm

Let us implement the greedy algorithm where all the exploration is fully done at the beginning of the iterative process followed by greedy exploitation afterwards. Let us summarise all the variables using our setup:

```
epsilon:0.1;
N:1000;
K:3;
```

where we consider 1000 steps to be performed by the algorithm.

Let us introduce several further variables we need during the lifetime of the algorithm to be preserved across individual iterations: the realised pay-offs, minimum bound for any pay-off in the situation where the bandit’s arm has not been explored yet is to be exploited, the choice of iterations, series of strategies taken, and the multi-armed bandit function itself:

```
payoffs:Kw();
minBound:0.0;
counter:0;
strategy:();
mab::quantQ.mcts.MAB[(1.0;2.0;3.0)];
```