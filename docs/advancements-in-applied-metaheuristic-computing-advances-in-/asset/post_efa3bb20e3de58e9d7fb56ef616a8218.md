
On the other hand, tool wear and economical estimations related to tool life are among essential issues associated with machining optimization, because in automated manufacturing operations, tool must be removed from the cutting process well before it fails, otherwise the parts produced become out of the allowable tolerance (Devliez, Lesko, & Mozer, 2004). Therefore, tool wear is of great significance in manufacturing since it affects the quality of the components, tool life and machine costs.

Mechanisms responsible for tool failure are abrasive, adhesive and diffusion wear (Devliez et al., 2004). Considering that the chip radius has a direct relation with the form of crater wear and this type of wear is formed due to adhesive and diffusion factors, so it can be resulted that these factors affect chip geometry impressively.

By considering the basic nature of the various wear mechanisms that are generally observed in machining operations, it has been showed that during the progressive tool wear, some major wear parameters contribute to the variation in chip flow, chip curl and chip breakability in metal machining, typically in a turning operations. Figure 1 shows various wear features studied in mentioned research.

To predict the tool crater wear in this work, two independent data sets are obtained on the basis of measurements: training data set and testing data set. Chip radius is used as independent input variable, while crater wear is the dependent output variable. An equation for the tool crater wear is developed on the basis of training data set and the accuracy of obtained model is proved on the testing data set by using fitness functions.

So in this chapter, on the basis of results obtained from practical experiments, the interrelationship between the chip radius and tool crater wear using their geometrical

Figure 1. Major tool wear parameters affecting chip geometry in a turning operation, VB: major flank wear; KT: crater wear depth; KB: crater wear length; KS: wear retract of the cutting edge; KK: crater wear width; N: tool nose wear (Devliez et al., 2004).

![](img/ffe7d4fcc17dbb6c6c08d4db77d800ca_142_0.png)

Figure 2. A schematic overview of the methodology used in present study

- 1. Selecting suitable cutting parameters
- 2. Performing the experiments
- 3. Classifying obtained data to train the GP model, test the GP model and initiate previously presented models
- 4. GP modeling for training data set
- 5. Calculating the fitness function for the output of models according with experimental data
- 6. Comparing the values of fitness functions to evaluate the performance of the GP model

features has been studied and then using GP, a model has been presented to estimate the values of crater wear depth, KT, and crater wear length, KB.

## Genetic Programming (GP)

Genetic algorithms (GA) are generally used as an optimization technique to search the global optimum of a function. However, this is not the only possible use for GA. Other fields of applications where robustness and global optimization are needed could also benefit greatly from GA. The two most important alternative domains applying GA are genetic based machine learning (GBML) and genetic programming (Settea & Boullart, 2001). GP is basically a GA which is applied to a population of members or computer programs, while a GA usually operates on (coded) strings of numbers a GP has to operate on members. GP allows, in comparison with GA, the optimization of much more complicated structures and can therefore be applied to a greater diversity of problems (Koza, 1992). A schematic overview of GP model which shows its different stages is given in Figure 3. The following steps are performed in each stage of programming. The aim of GP is to find out the member or offspring that best solves the problem. Possible solutions in GP are all the possible computer programs that can be composed in a recursive manner from a set of function genes which is as F = {f1, f2 ... , fm}, where m is the number of function genes, and the set of terminal genes T = {a1, a2 ... , an}, where n is the number of terminal genes. Each individual function fi from the set F has a certain number of arguments z(fi). The appropriate number of arguments for function genes from the set F is thus determined with the list {z(f1), z(f2), ..., z(fm)}.

Figure 3. Schematic overview of GP model application (Zadshakoyan & Pourmostaghi, 2013)

![](img/ffe7d4fcc17dbb6c6c08d4db77d800ca_144_0.png)

The set of function genes F can include basic mathematical functions, Boolean functions, relation functions, program flow control functions, functions for recursion, and functions defined with respect to the problem area studied. The set of terminal genes T can include numerical constants, logical constants, variables, etc. Terminal genes are, in fact, function genes without arguments. An example of such a tree using the F and T is given in Figure 4.

The initial population is obtained with the random creation of members by the use of available function genes from the set F and the available terminal genes from the set T. Each member of generation represents a random point in the searching space.

The creation of the initial population is a blind random search for solutions in the huge space of possible solutions. The next step is the calculation of adaptation of individuals to the environment (i.e., calculation of fitness for each member of generation). Fitness is a guideline for modifying the structures undergoing adaptation. In GP, the computer programs change, in particular, with two genetic operations: reproduction and crossover. The reproduction operation gives a higher probability of selection to more successful organisms.

In each generation the best chromosome is copied unchanged into the next generation. The crossover operation ensures the exchange of genetic material between the offsprings. Figure 5 shows the crossover operation of two parents’ chromosomes consisting of several function and terminal genes and mutation operation.

Figure 4. An example tree representation of a member corresponding with the equation (2-x)*(y+5)

![](img/ffe7d4fcc17dbb6c6c08d4db77d800ca_145_0.png)

Figure 5. GP method mathematical operations (Zadshakoyan & Pourmostaghimi, 2013)

![](img/ffe7d4fcc17dbb6c6c08d4db77d800ca_146_0.png)

the computer programs, an iterative repetition of second and third stages follows. After a certain number of generations, the newly born offsprings are usually much better adapted to the environment.

The meaning of the environment depends on the problem dealt with. The evolution is terminated when a termination criterion is fulfilled.

This can be a prescribed number of generations or sufficient quality of the solution. Since evolution is a non-deterministic process, it does not end with a successful solution in each run. In order to obtain a successful solution, the problem must be processed in several independent runs. The number of runs required for the satisfactory solution depends on the difficulty of the problem (Zadshakoyan & Pourmostaghimi, 2013).

In this chapter, for determination of the relationship between crater wear parameters and chip radius a genetic equation with genetic programming has been developed. The genetic equations for the wear characteristics were developed as follows:

$KT = F_1(R)$

(1)

$KB = F_2(R)$

(2)

In which $KT$ is crater wear depth, $KB$ is crater wear length and F1 and F2 are functions which relates chip radius, $R$, to $KT$ and $KB$ respectively. The evolutionary parameters for the determination of the genetic equation are population size (number of chromosomes) Ms=40 and number of generations G=3000. The number of chromosomes is selected 30, that is, a very small population, as it produces very good results for virtually all problems, even for such high dimensional problems as DNA microarrays with more than 25000 variables. The genetic operations, crossover and mutation are used. The mutation rate is P$_m$=0.044 and crossover rate was P$_c$=0.1. Moreover, arithmetic operations, according to the nature of wear mechanism and wear rate, set as follows:

$F = {+, -, \times, Ln, exp}$

(3)

## BACKGROUND

Today's scientific approaches in the area of tool wear monitoring usually measure several process parameters which are indirectly correlated with tool wear (such as force or vibration signals). These signals are measured on-line, i.e. during a cutting process. The process itself is influenced by many cutting conditions such as tool geometry or work material. A detailed description of metal-cutting manufacturing processes can be found in(Milton & Shaw, 1984), for instance. Very often, artificial neural networks (ANN), fuzzy systems, or combinations of both are used to model the non-linear dependencies between features extracted from the measured signals and cutting conditions on the one hand and tool wear or tool fracture on the other hand. A lot of promising research has been performed within the last years. However, particularly due to insufficient generalization capabilities (e.g. the use is restricted to a specific machine tool, only a small range of cutting conditions is allowed, or time-consuming 'teach-in' cycles are needed) or simply a lack of precision even
