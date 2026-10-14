
The use of deep learning with cloud will surely produce better outcomes in comparison to the traditional approaches. The above algorithms are classified according to their objectives and the way of working. The basic functionality is to give input with some weight and a threshold point, and pass it to the hidden layer which will process the input with activation function and then produce output. Each layer will have their own bias point.

## 5.3 INTRODUCTION TO THE GENETIC ALGORITHM

This algorithm is a search-based heuristic algorithm that selects the object on a fitness criterion for further processing. The GA consists of five phases:

### 1. Initial population

This is the set of the possible solutions of the given problem. Every element of the set is characterized with some parameters. While deciding the initial population, the diversity and population size should be kept in mind. The population size is a random vector. The initialization can be done in two ways:

1. **Random initialization**: Where the solution is given randomly without prior knowledge.
2. **Heuristic initialization**: The solutions are given on some prior known factors; this may cause similarity and less diversity in the solution.

We are using random initialization in our case.

```
VM_list = { mV1, mV2, mV3, ..., mVn }
Pn = { P1, P2, P3, ..., Pn }
```

Figure 5.4 is a single solution; we will generate a set of `n` solutions from the population.

```
Sn = { [ Vm[List]1, P[n]1 ], [ Vm[List]2, P[n]2 ], ..., [ Vm[List]i, P[n]j ] }
S = { S1, S2, S3, ..., Sn }
```

**FIGURE 5.4** Random allocations of VMs to the population vector.

Where:
- `Vm` is an array of virtual machines.
- `P` is the population set.
- `Sn` is the set of solutions.

After the initial population is determined, a predefined fitness function is applied to the initial population.

### 2. Fitness function

This is a predefined function that determines the fitness of individual elements of the initial population set. The selection of the individual is based on the fitness score. The fitness function should be fast enough to calculate the fitness of the given solution as we may have to repeat it multiple times until an optimal solution is found. Fitness may be exact or approximate depending on the case.

After the fitness function is applied, we will get the list of fit solutions determined by the fitness function (Figure 5.5).

```
Fn = { S1, S3, ..., Sn }
```

`Fn` is the set of fit solutions.

**FIGURE 5.5** Generating fit solution set after fitness function is applied.

### 3. Parent selection

Selection is a crucial part of a genetic algorithm as, if we select the fittest possible solution, it may take upon the entire population hence resulting in **premature convergence**. Good diversity maintenance is necessary for successful GA. There are various ways to select the solution.

#### a. Fitness proportionate selection

In this, every solution can become a parent with the probability proportional to its fitness. Hence the fitter solutions will have higher chances of selection. There are two possible models for this type of selection:

1. **Roulette wheel selection**: A fixed point is defined on the circumference of the wheel. After the rotation, whichever region stops in front of the point is elected as parent. The greater fitness solution will cover a large region and hence have a high chance of selection.
2. **Stochastic universal sampling**: We will have multiple fixed points; therefore all the parents will be chosen in one spin.

#### b. Tournament selection

In `n`-way tournament selection, `n` individual solutions are selected from the population. The process is repeated until the fittest parent is selected. This method can work with negative values too.

#### c. Rank selection

When the fitness of the individuals is very close to each other. In this, the fitness value is almost not considerable as all the sets have the same fitness value. The higher ranked is preferred.

### 4. Crossover

In this, more than one parent is selected and one or more set is generated having the parent attributes. The crossover is applied with a high probability. There are various ways to perform a crossover.

#### a. One-point crossover

Here the random point is selected from the parent(s), and a new solution is generated with the swapping process.

#### b. Multi-point crossover

It is advanced to the one-point crossover; in this we will have multiple random points to generate a new solution.

#### c. Uniform crossover

In this there is no random point. We decide whether the property of parent will be selected or not by flipping a coin.

#### d. Whole arithmetic recombination

This takes a weighted average of two parents by the formulae:

```
Child1 = a × x + (1 - a) × y
Child2 = a × x + (1 - a) × y
```

#### e. Davis’s order crossover (OX1)

This is a permutation-based crossover that transmits relative information to the new solutions. It works as follows:

1. Define two random points in the parent and copy the segment between points and move it to the first new solution.
2. Now from the second point in the second parent copy the unused content and move to the first solution.
3. Repeat for the second solution in reverse parent manner.

### 5. Mutation

This process makes a random small change in the parent solution to generate a new solution. This occurs to maintain the diversity in the initial population set and works on low probability. The most commonly used mutations are:

#### a. Bit flip mutation

We select some random bits and flip them to get a new solution. Mostly used in binary encoded GA.

#### b. Random setting

In this a random integer value is assigned to a randomly selected solution.

#### c. Swap mutation

This combination-based encoding selects two random points from the parent and swaps them to generate a new solution.

#### d. Scramble mutation

In this a subset of the solution is selected and scrambled/shuffled to generate a new solution.

#### e. Inversion mutation

Similar to the scramble selection mutation, we choose a subset but instead of shuffling we invert the list to generate a new solution.

### 6. Termination condition

When the genetic algorithm provides a set of solutions, the algorithm is terminated. In the start the GA tends to be very fast, but at later stages it comes to a saturation point where the improvements are very small. Termination is usually done when we are very close to optimal solution. Usually, the following points should be considered at termination:

1. When there are no improvements for `n` iterations.
2. If we reach an absolute number of generations.
3. When the solution has reached the predefined criteria.

## 5.4 PROPOSED MODEL 1 (A HYBRID GA AND NAÏVE BAYES MODEL FOR OPTIMIZATION)

Our aim is to merge these two algorithms into one to generate a hybrid algorithm that will save the total execution time of a task as well as improve the prediction that will help into proper resource optimization while saving the execution time (Figure 5.6).

At first, we will generate a random list from all the available VMs and
