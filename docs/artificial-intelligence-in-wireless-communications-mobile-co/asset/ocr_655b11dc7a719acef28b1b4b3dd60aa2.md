A genetic algorithm encodes a set of input parameters that represent possible solutions into a chromosome. The evaluation stage calculates a ranking metric of fitness for each individual, which then determines their survival to the next generation. Optimization progresses through finding genes that provide higher fitness for the chromosome in which it is found. The fitness calculation is often done through some absolute metric such as cost, weight, or value by which the algorithm can rank the success of an individual. Selection is the technique by which fit individuals are chosen to survive and reproduce for the next generation while less fit chromosomes are killed off. An algorithm terminates when it reaches a desired level of fitness in the population, a single member exceeds a fitness, the fitness plateaus for a number of generations, or through a simple criteria based on a maximum number of generations. The algorithm then takes the most fit individual of the last generation as the solution.

To understand each of these concepts clearly, we describe a genetic algorithm that solves the knapsack problem.

# 5.2 Simple Example: The Knapsack Problem

To explain the operation of a simple GA, we examine the knapsack problem [6], which is a classic NP-complete problem [7] and also called the subset problem (SSP). The knapsack problem takes a set of items, each with a weight and profit, and tries to fit as many of these items into the knapsack to maximize the profit without exceeding the maximum weight the knapsack can hold. Mathematically, the knapsack problem is represented by (5.1) where the goal is to maximize the profit, $P$, of items in the knapsack. The problem statement includes $K$ as the maximum weight the knapsack can hold and $N_s$ as the number of items in the set, $S$. Items in the knapsack have a weight vector, $\vec{w}$, a profit vector, $\vec{p}$, and the vector $\vec{x}$ is used to show whether an item is present or not in the knapsack. The values $w_i$ represent the weight and profit of item $i$, and the knapsack vector $x_i$ is a 1 if the item is included in the knapsack and a 0 if not.

```
$P = \max_{i=1}^{N} x_i p_i \quad (5.1)$
```

```
subject to: $\sum_{i=1}^{N} x_i w_i \leq K$
```

Chromosome: The problem consists of choosing the right set of items to place in the knapsack, so the chromosome represents the vector $x$ and consists