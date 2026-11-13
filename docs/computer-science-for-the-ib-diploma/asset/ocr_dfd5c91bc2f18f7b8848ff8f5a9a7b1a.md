+   Once a new generation of offspring has been generated, they become the current generation, and the process of calculating fitness, selection, reproduction and mutation repeats itself.

+   The process repeats until whatever termination criteria you determine is satisfied. This might be to iterate for a given number of generations, or to iterate until a fitness score of a minimum threshold has been reached.

Genetic algorithms are used for problems where it is not essential to identify the most perfect, optimal solution, but where there is a degree of “close enough is good enough” flexibility.

Common example applications of genetic algorithms include:

+   Route planning, such as the travelling salesperson problem. Consider the scenario of a salesperson who has 50 cities to visit. Rather than crisscrossing the countryside, genetic algorithms can find a close-to-optimal route to minimize the distance travelled. In the context of a long journey to 50 cities, it is not necessary to find the most perfect solution, so long as the solution is good enough. Put another way, if the algorithm can find a good solution in a few minutes, is it really worth hours or days of additional processing to find a solution that might be only 1 per cent better? At some point, the route is good enough to use.

+   Timetabling, such as allocating students to their preferred classes where there are constraints on the number of teachers, rooms and classes available.

+   Civil and mechanical engineering to help optimize design of structures such as bridges or buildings, and vehicle designs to make choices of materials based on durability, strength and cost.

+   Control systems and robotics use genetic algorithms to optimize the controller for better stability and performance.

+   Finance applications use genetic algorithms to help optimize a trade-off between risk and reward in selection of an investment portfolio.

+   Within machine learning, a genetic algorithm can help select a subset of relevant features from a larger data set to improve model accuracy and reduce overfitting.

+   In some types of machine learning problems, it is possible to use genetic algorithms for the training of an artificial neural network as an alternative approach to backpropagation (see later in this section).

![](bbox=[0.108, 0.602, 0.477, 0.856])

Roulette wheel selection

# Selection functions

Selecting pairs of values for reproduction relies on the concept of weighted randomization. It is weighted in the sense that those with higher fitness scores should be more likely to be chosen for reproduction. Randomization is still important, however, to ensure that the algorithm doesn’t become trapped in a local maximum.

One of the most commonly used approaches is the concept of a roulette wheel, where the portion of the wheel allocated is determined by the fitness function score.