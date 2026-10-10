
| Kumar et al. [[6]](#ch13.xhtml#r085) | Firefly optimization + fuzzy clustering | CT/MR image segmentation | Enhanced image segmentation by combining firefly optimization with fuzzy clustering to improve clarity |
| Rajabioun [[7]](#ch13.xhtml#r086) | Cuckoo optimization algorithm | Medical image processing | Applied cuckoo optimization for efficient processing of high-dimensional medical images |
| Karaboga and Basturk [[8]](#ch13.xhtml#r087) | Artificial bee colony (ABC) | Functional optimization, control systems | Highlighted ABC’s effectiveness in solving nonlinear optimization problems in control systems |
| Kennedy and Eberhart [[14]](#ch13.xhtml#r093) | Particle swarm optimization (PSO) | Image optimization | Demonstrated PSO’s ability to optimize image processing tasks with fewer parameters than other techniques |
| Karaboga [[13]](#ch13.xhtml#r092) | Artificial bee colony (ABC) | Image optimization | Proposed ABC for handling high-dimensional image data with promising results in image contrast enhancement |

## 3.3 Genetic algorithm

GAs are fundamentally inspired by Charles Darwin’s natural selection process, where they accept input and generate output by selecting from various potential solutions. GAs were initially employed by John Holland [[15]](#ch13.xhtml#r094). The GAs are intended to mimic natural system processes that are required for evolution. To find the best answers, GA searches efficiently in global spaces. GA is more successful at enhancing contrast and generates natural-looking photos. A GA is a search technique inspired by the principles of natural selection mechanism and genetic system. These algorithms are highly parallel and flexible, merging the concept of “survival of the fittest” in string structures with a systematic yet random exchange of information. This approach results in a search strategy that mimics some of the creativity found in human problem-solving. They effectively use previous data to predict and explore new search areas with projected improved outcomes, iteratively applying genetically inspired operators to probable solutions.

### Algorithm 1: Pseudo of the Genetic Algorithm

```
g = 0 /*Initialize Generation counter*/
P = Initialize population/*Random generation of p individuals */
Repeat UNTIL end condition

F = Reproduction(P)/*Selection of p parents through a roulette*/

S = Crossover(F)

M = Mutation (S)/*Alteration of the individual bits with probability mc*/

P = Update population(M)/*M is copied to P(P=M)*/

g = g + 1/*Increment of the Generation counter*/
```

Unlike traditional search strategies, GAs deal with numerous points at once rather than a single point. GAs have been shown to give reliable search in complex spaces both theoretically and experimentally. Pattern recognition and image processing present numerous challenges that require executing efficient searches within complex spaces to identify the optimal solution. GAs use three fundamental procedures on a restricted number of strings to discover the global near-optimal answer. Reproduction/selection, cross-over, and mutation are the three operators.

### 3.3.1 Parent selection strategies

#### 3.3.1.1 Tournament selection

One of the selection strategies used in GAs is tournament Selection. In this, the top candidates are selected from the present generation. After this, the selected best candidates are advanced to the following generation. In a K-way tournament selection, top k-individuals are selected and they compete against each other [[16]](#ch13.xhtml#r095). Among the selected candidates only the best candidate is selected and passed on to the next generation. Numerous tournaments are conducted, allowing us to finalize the pick of candidates, those will advance to the following generation.

This selection strategy has a feature called selection pressure, that provides a probabilistic evaluation of a candidate’s chance of being chosen for a tournament. If the tournament size is large, weaker candidates will have less likelihood of selection, as they must compete against stronger opponents. The pace of convergence of the GA is determined by the selection pressure parameter. The higher the selection pressure, the higher the rate of convergence. Over a wide range of selection pressures, GAs can uncover best or near-best solutions.

#### 3.3.1.2 Roulette wheel selection

In roulette wheel selection, the circular wheel is divided into segments representing individuals. Where each segment size is proportional to the fitness of the individual, as represented in [Figure 3.2](#ch13.xhtml#f5). The wheel is rotated and a specific point on the perimeter of the wheel is selected as indicated in the figure. The segments that comes in front of that specific point is chosen as a parent [[17]](#ch13.xhtml#r096). Similar process is followed for choosing the next parent. When the wheel is revolved, an individual with better fitness will have more probability of stopping in front of the designated point, as it has the larger segment on the wheel. Hence, likelihood of selecting an individual is directly related to his fitness value.

![Figure 3.2 Roulette wheel selection diagram.](html/images/9781032942346_C003_002.jpg)

**Figure 3.2** Roulette wheel selection diagram.

#### 3.3.1.3 Ranking selection

In rank selection, the population is first ranked, and then each chromosome’s fitness is assigned based on its position in that ranking. The worst chromosome receives a fitness value of 1, the second-worst gets a fitness of 2, and so forth, with the best chromosome receiving a fitness value equal to N, where N is the total number of chromosomes in the population [[18]](#ch13.xhtml#r097). Following that, all chromosomes have a chance to be chosen. Premature convergence can be avoided using rank-based selection techniques. However, because it sorts the populations based on fitness value, it can be computationally expensive. However, because the best chromosomes do not differ as much from the others, this strategy may result in slower convergence.

### 3.3.2 Crossover

Crossover is a genetic characteristic that involves the joining of two chromosomes (also known as parents) to form a new chromosome (also called offspring). If the new chromosome inherits the best qualities from both parents, the result of crossover may be better than both parents [[19]](#ch13.xhtml#r098) as shown in [Figure 3.3](#ch13.xhtml#f6). During evolution, crossover happens according to a user-defined crossover probability. The new offspring will inherit certain characteristics from one parent and others from the other. Assume first parent is `10001011` and second parent is `10011111`; after completing the crossover, the outcome can be `10011111`, which has some part of the first parent and some part of the second parent.

![Figure 3.3 Crossover.](html/images/9781032942346_C003_003.jpg)

**Figure 3.3** Crossover.

### 3.3.3 Mutation
