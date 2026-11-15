In the process of training, in order to maintain the numerical stability, these matrices are normalized such that the square sum of the entries of each matrix becomes unity. At the beginning, the weights are selected randomly from the set [-1, +1]. An algorithm similar to backpropagation is used, however, here adjustment of weights is not possible. In the back propagation the output is known beforehand, but in this net the relative values of the output are important. Instead here a Genetic algorithm is used as a suitable tool, described briefly in the next section.

For a collection of examples used for training, ordering of the nodes can be performed using any available technique. One can for example use the Sloan's method. Now the orders of the nodes for each case and the corresponding wavefront F$_{rms}$ are available. The graphs used for ordering, can be a single one or a group of graphs with similar topological properties.

# 14.5.4 Genetic Algorithm for Evaluation of Weights

Genetic algorithm (GA) is one of the strategic randomized search technique which is well-known for its robustness in finding the optimal or near optimal solution, Goldberg [10]. This approach uses and manipulates a population of potential solutions to find optimal solutions. The individuals (chromosomes or string) in the population will be better adapted to the environment, as they have to in order to survive in the generations to come. In GA, environment is defined as the fitness function for a specific optimization problem. In GA fitter individuals in the population will survive and weaker ones will be eliminated from one generation to the next.

GA operates through simple stages of cycle:

+   (a) Creation of population of strings,
+   (b) Fitness evaluation of each string,
+   (c) Selection of a pair of strings,
+   (d) Genetic operations.

The evaluation of the suitable weights is an optimization problem in which the fitness function is the wavefront and the variables are the weights. The vector of variables is in the form of a string having 17 real variables corresponding to the weights of the neural network.

```
X = | X$_1$ | X$_2$ | $\cdots$ | X$_{16}$ | X$_{17}$ |
```

For this optimization problem a simple Genetic algorithm is employed, reference [10]. For a specific case, the chromosome X is considered and using the weights of the net, ordering of the nodes is performed. Comparing the corresponding wavefront with the previous F$_{rms}$, the optimality of the response is evaluated, and using GA the initial population is selected and gradually improved.