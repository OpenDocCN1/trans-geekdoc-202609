
Where `x` is a natural number showcasing the population size, i.e., the number of tasks. `λ` is the rate of requests arriving which is usually greater than zero. In this phase, `p` populations are initialized with random VMs being allocated to the task. The populations finally constitute a predefined set of randomly generated tasks and each in a population is initialized with random VM IDs. After this phase, the fitness value for each population is initialized which defines the performance and quality of service of each schedule.

### 2.3.7.2 Phase 2: Fitness Evaluation

This phase starts with the evaluation of the fitness value of each population as given below. Fitness plays an important role in identifying whether the schedule will take part in the next generation of evolution or not. Fitness in BB–BC is also referred to as the mass of the schedule. In the proposed algorithm the fitness function is defined as follows:

Fitness value `i` is defined as the fitness of the `i` th population, where the fitness function is the sum of cost and execution of each task over a VM where `j` states the number of tasks.

Where `α` + `β` = 1.

`j = n`

```
fitness_value_i = Σ (a * Network_cost_tj + b * Completion_time_j) + g * (1 / Failure_rate_i)
j=1
```

The task completion time variable is measured using Equation 2.6 in which `Task_Length` is the number of instructions of a task, `VM_MIPS` is the millions of instructions per second (MIPS) of VM and `PE` is the processor count.

```
Network_cost_i = Network_delay_i
```

```
Failure_rate_i = Task_failed_count_i / T_D
```

The simulation of failure depends on the probabilistic distribution function. `Task_failed_count` concerns measures over a period of time `ΔT`.

Equation 2.7 defines the cost of resources used during the execution of a task at a specific VM. In this phase, the mass of all the schedules is evaluated and then evolution takes place. Evolution is a set of steps repeated in every evolution which include selection, crossover, mutation and the big crunch phase.

### 2.3.7.3 Phase 3: Crossover/Center of Mass and Mutation

In this phase two best solutions are selected. The first solution is the one with the least cost, and the second solution is the one with the fitness value near to the center of mass of all the solutions, where the center of mass is evaluated using Equation 2.9. The center of mass refers to the average solution or the mean position in the solution which is considered to be the most stable as compared to the best and worst solutions. The center of mass is referred to as `xc`.

```
xc = (Σ (1/fi) * xi) / (Σ (1/fi))
i=1 to N
```

`xc` is a point in n-dimensional space where `N` is the number of populations. `fi` is the `i` th solution in `N`-dimensional space. The second fittest solution is the solution nearest to the center of mass, i.e., the solution having a fitness value near to the center of mass.

#### 2.3.7.3.1 Crossover

This phase takes two best solutions from the selection phase and a multi-point crossover is performed in which the swapping of a random point between two solutions selected is done. This phase aims to design a better solution from the two best solutions.

#### 2.3.7.3.2 Mutation

In this phase, the third-best solution discovered spreads its diversity in other populations using swapping-based mutation of the candidate solution in a search space with other solutions.

![Image 12](index-39_1.png)

### 2.3.7.4 Phase 4: Big Crunch

This phase plays an important role by removing the population with the worst fitness value, i.e., the highest fitness value. Repeat phases 2, 3 and 4 until one best solution is left.

Figure 2.3 presents the flow diagram of the proposed model.

## 2.4 EXPERIMENTAL RESULT

In this work, we focus on performance enhancement using an astronomy-aware and human brain-inspired approach. In this section, the performance evaluation of the proposed model is performed. Many criteria are used for task scheduling evaluation. Many of the Metrics are given below:

- Average start Time (millisecond).
- Total execution time/makespan (millisecond).
- Average finish time (millisecond).
- Network delay (millisecond).

### 2.4.1 Results Using Fabricated Data

This subsection illustrates the results with scaling load to study the performance in underloaded and overloaded conditions. Figures 2.2(a) and (b) show the comparisons of the variations of the execution time with scaling tasks and resources. The astronomy-aware and human brain-inspired BB–BC ANN performs better than state-of-the-art approaches. Figures 2.3(a) and (b) show the BB–BC ANN with variations of the average start time with scaling tasks and resources.

FIGURE 2.2 (a) Comparison of execution time with five virtual machines. (b) Comparison of execution time with ten virtual machines.

![Image 13](index-40_1.jpg)
![Image 14](index-40_2.png)

FIGURE 2.3 (a) Comparison of average start time vs scaling tasks with five virtual machines. (b) Comparison of average start time vs scaling tasks with ten virtual machine.

Figures 2.4(a) and (b) show the study of the task failure count on increasing the user tasks with five and ten virtual machines. Figures 2.5(a) and (b) show the study of the task completed count on increasing the user tasks with five and ten virtual machines. Figures 2.4 and 2.5 show that the proposed algorithm performs better in a fault environment with more tasks completed as compared to existing algorithms.

Figures 2.6(a) and (b) exhibit the results which are computed with increasing task load and scaling the resources in terms of a virtual machine. The proposed algorithm performs better as compared to existing approaches to in-network and fault-aware environments.

FIGURE 2.4 (a) Task failure count with five virtual machines. (b) Task failure count with ten virtual machines.

![Image 15](index-41_1.jpg)
![Image 16](index-41_2.png)

FIGURE 2.5 (a) Task completed count with five virtual machines. (b) Task completed count with ten virtual machines.

FIGURE 2.6 (a) Comparison of network delay with five virtual machines. (b) Comparison of network delay with ten virtual machines.

### 2.4.2 Experimental Results Using Real Datasets

In this section, the simulation is performed using a real dataset from a parallel workload using datasets. All the simulations listed below are performed with scaling five and ten machines. The performance is evaluated with increasing load, i.e., the number of tasks. The comparison is carried out with existing BB–BC cost, and two other variants of the genetic approach. Figures 2.7(a) and (b) exhibit that the tasks are submitted on virtual machines using the proposed BB–BC ANN, BB–BC cost and two other variants of the genetic approach. The performance is measured using the average start time. Figures 2.8(a) and (b) exhibit the variations of the average finish time using the proposed BB—BC ANN and state-of-the-art existing approaches. The average finish time acts as a performance metric.

Figures 2.9(a) and (b) show the comparative results over execution time

![Image 17](index-42_1.png)
![Image 18](index-42_2.png)
![Image 19](index-42_3.png)
