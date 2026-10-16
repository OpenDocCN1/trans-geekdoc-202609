
Optimization of the fermentation process contains multiple constraints such as expense, more labour work, open-ended and time-consuming processes that include multiple steps. Continuously, new strains and mutants are introduced in bioprocess industries and, therefore, there is the need to perform optimized experiments (`[Stanbury et al. 2013](#ch6.xhtml#ref6_67)`). As the fermentation process speeds, there will be a need for techniques to obtain high yield end-product generation at low cost which will compete with the conventional methods of fermentation processes. Currently, GAs which are non-statistical optimization techniques are used to optimize the fermentation process. The Genetic Algorithm is a stochastic optimization model that can be used to find an optimal or near-optimal solution by simulating natural evolution (`[Adeyemo and Enitan 2011](#ch6.xhtml#ref6_1)`). GAs are the compelling stochastic search algorithm associated with the theory of probability. The concept behind GA is genetics and the process of natural selection, where the historical information is used to take the algorithm to the best level. GAs are based on the “survival of the fittest” principle that means after repeated steps of mutation only the best individual will exist. For the identification of the ideal or best-fit solution set, the algorithm mimics the causes of evolution as in any natural population. At a single step, from the current population GAs randomly choose parents (some individual solutions) to reproduce the offspring for the next generation. As the repeat of the consecutive generation increases, the population evolves toward the most suitable solution. Likewise, GAs are responsible for the production of high yield products or solutions for optimization of fermentation using evolutionary biology, probability theory, and search algorithms. A detailed schematic workflow in GA is provided in [`Figure 6.3`](#ch6.xhtml#fig6_3).

``` 
![Figure 6.3 Workflow and steps involved in the application of genetic algorithm (GA) for parameter optimization in the fermentation process.](images/fig6_3_B.jpg)
```

[Figure 6.3 Workflow and steps involved in the application of genetic algorithm (GA) for parameter optimization in the fermentation process.](#ch6.xhtml#R_fig6_3)

In GA, the initial solution set can be understood as an individual (with a specific chromosome) of a population. Two sets of chromosomes are selected as parents, and the offspring population is derived via the processes of recombination and mutation (`[Vasant and Barsoum 2009](#ch6.xhtml#ref6_70)`). Each chromosome consists of several genes that define a particular parameter, and each bit in a gene describes the value imparted to the parameter. The three processes that determine the next generation are “Selection”, “Crossover”, and “Mutation”. Selection selects the parent chromosomes, and crossover combines them together to form the offspring as it happens in nature via recombination. Mutation introduces random changes in the chromosomes during each cycle (`V. [Singh et al. 2017](#ch6.xhtml#ref6_61)`). Selection usually occurs based on the fitness of the chromosomes defined by a fitness factor (`[Doganis et al. 2006](#ch6.xhtml#ref6_16)`). GA comes with several advantages over conventional optimization techniques. It is capable of solving complex problem statements and can run them in parallel. GA can deal with various optimization methods, whose fitness (or objective) function can be of various types, viz. with random noise, linear/ nonlinear, stationary/non-stationary (that change over time), and continuous/discontinuous. Because multiple offspring in a population act like independent agents, the sample group (or population) can parallelly explore the search (or solution) space in multiple directions. Because of this feature, GA makes the process for finding optimal solution faster via parallelizing the algorithms. Furthermore, GAs are capable of manipulating multiple parameters and different groups of encoded strings simultaneously (`Table 6.1`).

``` 
Table 6.1 Microbial Sources of Various Enzymes and Their Optimization Using Conventional Optimization Techniques 

| Microbial Source  || Enzyme || Applications || Optimization Method || Reference |
| --- | --- | --- | --- | --- |
| *Bacillus subtilis JK-79* || L-glutaminase || Therapeutic enzyme || PBD and RSM || [`Kiruthika and Murugesan (2020)`](#ch6.xhtml#ref6_33) |
| --- | --- | --- | --- | --- |
| *Aeromonas veronii* || L-glutaminase || Anti-cancer enzyme || PBD and CCD || [`Jesuraj et al. (2017)`](#ch6.xhtml#ref6_31) |
| *Alcaligenes faecalis KLU102* || L-glutaminase || Anti-cancer enzyme || RSM || [`Pandian et al. (2014)`](#ch6.xhtml#ref6_45) |
| *Trichoderma reesei QM9414* || Cellulases || Cellulolytic enzyme || CCRD || [`Sirohi et al. (2019)`](#ch6.xhtml#ref6_64) |
| *Penicillium citrinum YL-1* || Alkaline protease || Proteolytic || PBD and RSM || [`Xiao et al. (2015)`](#ch6.xhtml#ref6_73) |
| *Streptomyces griseoloalbus* || α-galactosi-dase || Glycoside hydrolase enzyme || RSM || [`Anisha et al. (2008)`](#ch6.xhtml#ref6_3) |
| *Bacillus subtilis RSP-GLU MTCC 9727* || L-glutaminase || Deamidation/aminohydrolase enzyme || RSM || [`Sathish et al. (2018)`](#ch6.xhtml#ref6_56) |
| *Serratia marcescens NCIM 2919* || L-asparagi-nase || Therapeutic enzyme || RSM || [`Ghosh et al. (2013)`](#ch6.xhtml#ref6_23) |
| *Enterobacter aerogenes MTCC111* || L-asparagi-nase || Therapeutic enzyme || RSM || [`Erva et al. (2017)`](#ch6.xhtml#ref6_19) |
| *Bacillus* sp. *VUVD101* || Lactase || Lignocellulolytic enzyme || PBD || [`Karlapudi et al. (2018)`](#ch6.xhtml#ref6_32) |
| Abbreviations: CCD – Central composite design, RSM – Response surface methodology, PBD – Plakett–Burman design |
| --- |
### 6.4.1 History of GA
