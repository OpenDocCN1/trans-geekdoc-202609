
The selection of sensitivity-pheromone was applied in between the present solution 𝑖 and its other solution. Other solutions were applied if it is better than the present solution, i.e., the probability conditions.

2. Onlooker bees

Food source selection by sensitivity-pheromone

For every onlooker bee, each source of food generates a new solution and updates the length of steps

Iter = Iter + 1

Selection applied to the sensitivity-pheromone to current solutions. But the existing resolution is better than the others. Otherwise, increasing its experimental counter-optimal solution should be memorized.

3. Scout bee’s phase

The food source determination of the trial counter should exceed the “limit” value, or in each interaction, only one scout bee was acceptable.

The scout bee used for random Food Number search ≥ max iteration returns to the optimal solution at the end.

## 9.8 Effect of Different Parameters in ABC of Enzyme Optimization

ABC algorithm should be more productive in terms of the scout bee’s food source number (*N*), food source amount (*M*), elected food source number, dispatched bee’s number to the elected food source (Nre), the bee’s dispatched number to another source of food (Nsp), search area radius (Ngh), and iteration number (*I*[max]) ([Zhang et al. 2010](#ch9.xhtml#ref9_54)). Initial food source locations with the conditions are represented within the well-defined problem for this algorithm.

(9.3)  

*X*[*i**j*] = *X*[*j*]^(min) + *r**a**n* (0,1)(*X*[*j*]^(min)−*X*[*j*]^(min))  

where *i* = 1, …, *N* and *j* = 1, …, *j* are ranges in the equation. *N* is the number of parameters. In every area, subsequently, the new solutions created during ABC algorithm *V*[*jk*] within *X*[*k*] are demonstrated in Equation (9.4):

(9.4)  

*V*[*j**k**](*t*+1) = *X*[*j**k**](*t*) + *φ*[*j**k**](*t*)(*X*[*j**k**](*t*)−*X*[*w**k**](*t*))  

*K* = int  (*r**a**n**d* *X* *N*) + 1  

where *ø*[*jk*] and *X*[*jk*] represent the random numbers uniform distribution and the *j*th solution from among the solution set of the *k*th parameter. Though, the *ø*[*jk*] area and parameter *k* are selected casually from the domains \[1 and −1\] and \[1 and *N*\], respectively.Beyond these situations, the explanation for each problem in a suitable way is replaced by the earlier one. The earlier solution is replaced if the new solution is more adaptable. After that, solutions for each bee are selected by the scout bees ([Liu et al. 2018](#ch9.xhtml#ref9_35)).

## 9.9 Control Parameters in ABC for Optimization

ABC optimization/adjustment of parameters are designed, after which the analysis was performed using the most appropriate design for the optimization of parameters. ABC algorithm can deliver the best parameters after the optimization of the process. The earlier ABC version was most efficient for basic functions. Although the performance of the ABC algorithm convergence was not that much effective when working with composite and non-separable constrained related problems and functions ([Karaboga et al. 2014](#ch9.xhtml#ref9_27); [Sonmez 2011](#ch9.xhtml#ref9_48)). The convergence rate and improvement ([Karaboga and Basturk 2007](#ch9.xhtml#ref9_26)) were analyzed by the effect rate of perturbation which controls frequency change parameters; this method is commonly known as the scaling factor which determines the magnitude of parameters by changing neighboring solutions and the parameter limit by ABC performance; the modified version is proposed for solving efficient optimized problems for real parameter. Common modifications in the Artificial Bee Colony Algorithm (ABCA) are made in the perturbation process for controlling the frequency of perturbation. Frequency is fixed in the basic version of ABC while producing the new solution, with slow rate of convergence in only one parameter; this is the parent solution for the expected outcomes. But in the proposed ABCA ([Mohapatra et al. 2017](#ch9.xhtml#ref9_39)), a new control parameter – the modification rate (MR) – was introduced.

## 9.10 ABC Algorithm Modifications

Presents changes in the ABC subsection may cause the variations which are observed by different researchers in the relationships with modified tuning in the parameter, for enhancement or performance improvements. For tackling the constrained problems related to optimization, in the ABC selection procedure, the worker bees generally used Deb’s rules to regulate the strategy in the procedure, instead of the greedy procedure for selection. The ABC’s new variant performance was linked with two methods, i.e., PSO and DE, wherein the results are comparable and the ABC performance was clearly observed. For large-scale problems’ solutions, the ABC is applied ([Karaboga and Basturk 2007](#ch9.xhtml#ref9_26)). The limited handling techniques were applied to the selection phase of ABC so that the feasible area of the whole search space could be reached. To choose the onlooker and employed bees, Deb’s rules were incorporated. Three strategies were carried out for the selection and modification of the ABC. The modification in the three strategies selection in ABC was reported by [Zhu and Kwong (2010)](#ch9.xhtml#ref9_57) for numerical benchmark optimization. Modification in food source selection was carried out by onlooker bees for the prevention of premature convergence and population diversity increases. These strategies include selection based on rank selection-based selection (RABC), tournament selection (TABC), and disruptive selection of (DABC). Modified ABC performance is mainly associated with the results of basic and modified ABC as demonstrated by three selection strategies, and are used for population diversity improvement and convergence prevention.

## 9.11 Summary of ABC

1. Foraging behavior generally inspired by honey bees in ABC

2. For optimization purposes, ABC is used globally

3. Numerical optimization initially is proposed ([Karaboga and Basturk 2007](#ch9.xhtml#ref9_26))

4. Combinatorial problems are analyzed for the optimization process ([Pan et al. 2011](#ch9.xhtml#ref9_42))

5. It is also used for unconstrained and constrained problems related to optimization ([Djaballah and Nouibat 2022](#ch9.xhtml#ref9_13); [Karaboga et al. 2014](#ch9.xhtml#ref9_27); [Kasihmuddin et al. 2021](#ch9.xhtml#ref9_29))

6. The user predetermines the employed control parameters (i.e., population size, number of maximum cycles, and limit)

7. It is comparatively simple, flexible, and robust ([Rao et al. 2008](#ch9.xhtml#ref9_43); [Singh 2009](#ch9.xhtml#ref9_47); [Lin et al. 2021](#ch9.xhtml#ref9_34))

## 9.12 Application of ABC

The ABC has become the most common because of its ease of application and robustness. Researchers successfully applied the solution to complications in many different areas. First, the ABC applied to the mathematical problems by [Karaboga et al. (2014)](#ch9.xhtml#ref9_27) was extended to constrained optimization problems, and were then applied to neural networks of the brain ([Karaboga and Basturk 2007](#ch9.xhtml#ref9_26)), classification to the medical patterns, and clustering problems ([Table 9.2](#ch9.xhtml#table9_2)) ([Seyman and Taşpınar, 2013](#ch9.xhtml#ref9_58); [Ilie and Bǎdicǎ 2013](#ch9.xhtml#ref9_24)).

[Table 9.2 Applications of ABC in Different Fields](#ch9.xhtml#R_table9_2)

| S. No. || Application of ABC || Reference |
| --- | --- | --- |
| 1 || ABC is used for training the multilayer perceptron neural network for classifying the acoustic emission signal toward their particular source || [Omkar and Senthilnath (2009)](#ch9.xhtml#ref9_40) |
| 2 || Investigation of the comparison of the RBF neural network training algorithms in inertial sensor-based terrain classification || [Kurban and Beşdok (2009)](#ch9.xhtml#ref9_30) |
