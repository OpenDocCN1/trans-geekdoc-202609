currently used to cross, and f represents the fitness value of the individual which needs to perform mutation operation. The improved adaptive genetic algorithm mainly makes the P_r, P_m of the optimal individual in the early stage of evolution not zero, and it is not easy to fall into the local optimal solution, as shown in Figure 7:

![](bbox=[0.18, 0.24, 0.85, 0.38])

Figure 7. Improved adaptive crossover probability and mutation probability.

Because adaptive adjustment may cause the population to fall into a local optimal solution, we adopt an improved method to improve P_r, P_m so that the optimal individuals P_r, P_m in the early evolution stage are not zero. The specific improvement process is to increase the population’s maximum fitness value P_r to P_r1 and P_m to P_m1. As shown in Figure 6, this will make the individual with the largest fitness value in the initial stage of evolution in a constant state, and check and mutate according to the size of P_r1, P_m1.

The above five steps are an UAV trajectory planning algorithm process of Problem 1. The overall algorithm flow can be expressed in Figure 8.

![](bbox=[0.15, 0.58, 0.9, 0.72])

Figure 8. Flow chart of an UAV trajectory planning algorithm based on an improved genetic algorithm.

Figure 8 shows the combination of genetic algorithm and trajectory planning and the entire planning process. In Problem 1, we used the real number coding method to transform the trajectory planning problem into a genetic algorithm chromosome problem. Under multiple constraints and driven by the fitness function, the evolution operation of each generation is completed through operations such as genetic crossover and mutation, and finally decoded to obtain the required track node and complete the solution of the optimal solution for the trajectory planning.

# 3.3. Simulation Results and Analysis of the Trajectory Planning Algorithm for the Problem 1

According to the above algorithm, the results of the Problem 1 are calculated by using the data set. For the parameters of the data set, the vertical error and horizontal error will increase by δ dedicated units for each flight of 1 m; when a UAV reaches the ending point, the vertical error and