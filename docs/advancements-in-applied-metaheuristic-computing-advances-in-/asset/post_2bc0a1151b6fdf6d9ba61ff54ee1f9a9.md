
Voß, S., Martello, S., Osman, I. H., & Roucairol, C. (Eds.). (2012). Meta-heuristic: Advances and trends in local search paradigms for optimization. Springer Science & Business Media.

Yang, X. S. (2010). A new metaheuristic bat-inspired algorithm. Nature inspired cooperative strategies for optimization (NICSO 2010), 65-74.

Zangeneh, D., & Yazdi, M. (2016, May). Automatic segmentation of multiple sclerosis lesions in brain MRI using constrained GMM and genetic algorithm. In Electrical Engineering (ICEE), 2016 24th Iranian Conference on (pp. 832-837). IEEE. doi:10.1109/IranianCEE.2016.7585635

## Section 2

### Genetic Algorithm Applications

## Chapter 9

### Optimized Crossover JumpX in Genetic Algorithm for General Routing Problems: A Crossover Survey and Enhancement

**Hicham El Hassani**
ENSEM Casablanca, Morocco

**Said Benkachcha**
ENSEM Casablanca, Morocco

**Jamal Benhra**
ENSEM Casablanca, Morocco

### ABSTRACT

Inspired by nature, genetic algorithms (GA) are among the greatest meta-heuristics optimization methods that have proved their effectiveness to conventional NP-hard problems, especially the traveling salesman problem (TSP) which is one of the most studied Supply chain management problems. This paper proposes a new crossover operator called Jump Crossover (JMPX) for solving the travelling salesmen problem using a genetic algorithm (GA) for near-optimal solutions, to conclude on its efficiency compared to solutions quality given by other conventional operators to the same problem, namely, Partially matched crossover (PMX), Edge recombination Crossover (ERX) and 2-opt heuristic with consideration of computational overload. We adopt the path representation technique for our chromosome which is the most direct representation and a low mutation rate to isolate the search space exploration ability of each crossover. The experimental results show that in most cases JMPX can remarkably improve the solution quality of the GA compared to the two existing classic crossover approaches and the 2-opt heuristic.

### INTRODUCTION

NP-hard problems generally require exponential time depending on the problem size to find exact optimal solutions. This is why many metaheuristics are used to obtain approximate solutions to problems of such difficulty. To legitimate using metaheuristics to solve an optimization problem, a complexity analysis of a problem can be driven to give an indication on the hardness of the problem. It is also important to know the size of input instances the algorithm is supposed to solve. Even if a problem is NP-hard, small instances or even large-size instances with a specific structure may be solved in optimality by exact approach. Moreover, the required search time to solve a given problem is an important issue in the selection of an optimization algorithm. It is unwise to use metaheuristics to solve problems where efficient exact algorithms are available. For instance, one should not use a metaheuristic to find a minimum spanning tree or a shortest path in a graph. Known polynomial-time exact algorithms exist for those problems.

There are several powerful optimization techniques that are inspired by nature. Evolutionary algorithms (EAs) have been developed based on the principles of natural genetics to perform research and optimization in complex spaces. The most important components of the Evolutionary algorithms family are: Genetic Algorithms, Genetic Programming and Evolutionary Strategies.

Various other bio-inspired research and optimization techniques which was created, developed, hybridized, enhanced and used in numerous fields of optimization, such as Particle Swarm Optimization (PSO) in (Shweta & Kamal, 2014; Soleimani & Kannan, 2015; Wang, Ma, Xu, Liu, & Wang, 2015), Ant Colony Optimization (ACO) in (Ahmed Hamza, Ahmad Taher, & Aboul Ella, 2014), A. Hamza developed a New Heuristic Function, Differential Evolution (DE) in (Zhu, Fang, Tang, Zhang, & Du, 2012), Artificial Bee Colony (ABC) in (Rahul, Senthilnath, Omkar, & Narendra, 2016), Cuckoo Search and Chaotic Flower Pollination optimization algorithm in (Binh, Hanh, Van Quan, & Dey, 2016), (Dey, Samanta, Yang, Das, & Chaudhuri, 2013), (Ashour et al., 2015), Firefly algorithm in (Dey, Samanta, et al., 2014), Neural Networks in (Hore et al., 2017), and Simulated Annealing in (Bouttier et al., 2017), are also classified among the metaheuristics techniques. In (Reza, 2016), a new Meta-heuristic algorithm inspired of the biologic nephron performance for optimization of objective functions in NP-hard problems is introduced (NAO). In (Dey, Chakraborty, & Samanta, 2014) the author is using Particle Swarm Optimization and Genetic Algorithm based techniques and offers MATLAB result sets, tables, flow charts and illustrations to exemplify the complicated concepts discussed in the text.

Over the past years, hybridization of metaheuristics has become an important issue, to the point that all the different metaheuristics that we have cited, and other techniques, are now seen as starting points for the development of new optimization algorithms. In (A. Meryem & Salim, 2016), authors present a new approach based on the cooperation of many variants of metaheuristics in order to solve the large existing benchmark instances of the capacitated vehicle routing problem (CVRP). (Amal Mahmoud & Sawsan, 2015) propose a new variation of ABC that uses multi-parent crossover named multi parent crossover operator artificial bee colony (MPCO-ABC). In the proposed technique the crossover operator is used to generate three new parents based on memory.

Also, Harmony search algorithm (HSA) which is a recent evolutionary algorithm used to solve several optimization problems. The algorithm mimics the improvisation behavior of a group of musicians to find a good harmony. Several variations of HSA have been proposed to enhance its performance. In (Iyad Abu, Faisal, Eslam Al, Mohammed Azmi, & Basima Hani, 2013), a new variation of HSA that uses multi-parent crossover is proposed (HSA-MPC). In (B. Meryem & Abdelmadjid, 2016), the authors present a new Quantum Inspired Harmony Search algorithm with Variable Population Size QIHSVPS for a complex variant of vehicle routing problem (VRP), called HVRPMBTW (Vehicle Routing Problem with Heterogeneous fleet, Mixed Backhauls and Time Windows). In (B. Meryem & Abdelmadjid, 2015), the author deals with a variant of the famous NP-hard (Laporte, 1992) vehicle routing problem called the Vehicle Routing Problem with Simultaneous Pickup and Delivery VRPSPD.

Genetic algorithms are stochastic search methods which mimic the natural biological evolution. They are widely used in NP-hard problems optimization (Mohammad & Mohammad Hassan, 2016).

Genetic algorithms were developed by John Holland of the University of Michigan in the early 1970s (Holland, 1975) and since then, the GAs continue to prove theoretically and empirically their efficiency and robustness to provide good solutions in complexes areas (David Edward Goldberg, 1989).

GA operates on a population (group of individuals) of possible solutions applying the principle of survival of the fittest, to generate new and improved estimates. In every generation, a new set of approximate solutions is created by the process of selecting individuals according to their fitness (objective) and the use of genetic operators inspired by natural genetics. This approach guarantees the evolution towards better populations (Eiben, Hinterding, & Michalewicz, 1999).

In the following, a description of the main genetic operators is given, namely: selection, crossover, mutation, and replacement. The emphasis here is on presenting a functional description of the principles, rather than giving a complete overview of the concepts of these operators; however, the focusing this work is on crossovers operators.

The selection mechanism is one of the main components of research in evolutionary algorithms. The overall principle of parent selection is that their probability of being chosen grows with their fitness. Such selection pressure will lead the population towards better solutions. However, the worst individuals should not be rejected and they have a chance to be selected. This can lead to useful genetic material. After the selection process, the crossing operator is applied to each parent pair (P1, P2) with a probability Pc (predetermined) and generates the child pair (E1, E2). The mutation operators are unary operators that act on a single individual and whose main action is the modification of an individual genotype and thus allow a better exploration of the solutions space. Finally, the replacement phase concerns the selection of survivors from the parents generation to maintain the size of population.

Evolutionary algorithms have shown their efficiency in solving optimization problems, but given their stochastic nature, these algorithms alone may sometimes not retain the correct solutions encountered during their execution until the end of the algorithm. The notion of elitism which advocates that the best individuals of the actual population will be saved in the next generation is then necessary. In (Kanungo, Janmenjoy, Bighnaraj, & Behera, 2016), an effort has been made with a recently developed population based metaheuristic called Elitist based teaching learning based optimization (ETLBO) for data clustering. The ETLBO has been hybridized with K-means algorithm (ETLBO-K-means) to get the optimal cluster centers and effective fitness values.

The TSP is one of the most famous combinatorial optimization problems (NP-hard for large size), it was treated by a large number of metaheuristic and approximate methods (Yong, 2015) and particularly genetic algorithms (Abdoun & Abouchabaka, 2011; Bontoux, Artigues, & Feillet, 2010; Dwivedi, Chauhan, Saxena, & Agrawal, 2012; Yuan, Skinner, Huang, & Liu, 2013).

Researchers have proposed several versions of genetic operators for this kind of ordered problems such as order based crossover (OBX) and uniform order based crossover (UOBX) chapter 1 pages 1–101 (L. D. Davis, 1991), partially mapped crossover (PMX) (David E. Goldberg & Lingle, 1985) and many others that we cite afterwards.

Here, we propose a new crossover called Jump crossover (JMPX) then we compare it with some pretty powerful and classic methods.

This paper is organized into 4 sections. The first deals with some basic concepts of genetic algorithms and a brief description of the benchmark operators and methods. In the second section, we describe the proposed crossover operator. The third section presents the results and discussions in comparison with the benchmark, while the fourth section discusses the conclusions reached.
