# Genetic Algorithms for Radio Optimization

![](bbox=[0.146, 0.114, 0.824, 0.423])

**Figure 5.4** Performance graph of three knapsack problems. Each curve represents the best chromosome in each generation for the three different problems.

and the size and values of the knapsack problem. The first generation, which was randomly generated, had poor performance but the best member quickly climbed during the first few dozen generations. A “knee” occurs in the early generations and ends around generation 1,000 where the upwards climb slows down. Over the next couple of thousand generations, the fitness of the best member levels off and Though progress slows down, the fitness still climbs every few generations. At the end, the algorithm is still climbing slowly, and it is likely that the best solution from this generation is not the optimal solution to the problem, although it is very close.

In fact, the last point is significant in GA theory. Holland [8] proved that a GA will always converge on the optimal solution; however, it can never guarantee convergence within a certain time limit. Of course, for NP-complete problems, the optimal solution is unknown through anything other than a full search. Similarly, the optimal solution is not necessarily the goal of real-world optimization problems, which may be more interested in quickly optimized solutions that approach the optimal solution.

The idea of suboptimal (but approaching optimal) solutions is true for the waveform optimization problem where the cognitive engine must produce a waveform under real-time constraints. The cognitive engine needs better