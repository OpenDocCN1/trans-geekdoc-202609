# ## 4.1.1.8 Genetic Programming (GP)*

Genetic programming (GP) is a modern variant and a special case of GA and can be further grouped under linear genetic programming (LGP) and genetic expression programming (GEP) [23, 24]. Unlike GA, which is made of expressions (or simple strings of formulas), GP creates computer programs in the form of a tree-like structure (as in codes48) [25]. John Koza is credited for his invention of GP in 1988.49

# ### 4.1.1.8.1 Programming This Algorithm

The Python and R codes for the GP algorithm are provided below:

Python Package:

```
#Use package DEAP from https://pypi.org/project/deap/ [26]
pip install deap
import random
from deap import creator, base, tools, algorithms
```

R Package:

```
>install.packages("grp")
>library("grp")
>geneticProgramming(fitnessFunction, stopCondition=makeTimeStopCondition(5),
population, populationSize=100, eliteSize=ceiling(0.1 * populationSize),
elite=list(), functionSet=mathFunctionSet
```

# ## 4.1.1.9 Gradient Boosted Trees (GBTs)

GBTs are simple tree-like models. In their simplest form, they use the first model's error as a feature to build successive models. Focusing on errors obtained from a feature when building successive models reduces the overall error in the model. There are variants to GBT, most notably the Extreme Gradient Boosting (XGBoost), the Light Gradient Boosting Machine (LightGBM), and the CatBoost50 algorithm.

*How do these algorithms work?*

The XGboost brings two techniques to improve the performance of a GBT; a weighted quantile sketch by means of an approximation algorithm that can determine how to make splits candidates in a tree and the sparsity-aware split finding technique. The XGboost uses a pre-sorted algorithm and a histogram-based algorithm for computing the best split. This algorithm was created by Chen and Guestrin [27] and can be found at [28, 29]. This algorithm does not use any weighted sampling techniques.

```
$$Y = \sum_{k=1}^M f_k(x_i), f_k \in F = \Big\{f_x = w_{q(x)} \cdot q: R^p \rightarrow T, w \in R^T\Big\}$$
```

where M is additive functions, T is the number of leaves in the tree, w is a leaf weights vector, wi is a score on i-th leaf, and q(x) represents the structure of each tree that maps an observation to the corresponding leaf index [30].

On the other hand, the LightGBM algorithm, created by Microsoft [31], also introduces two new techniques to improve the performance of a GBT. These techniques are gradient-based one-side sampling51 and exclusive feature bundling52 to accelerate the processing time within this algorithm. Finally, the CatBoost algorithm is the latest of the discussed algorithms and was developed by Yandex in 2017. This algorithm adopts the minimal variance sampling techniques in which it weighs sampling at the tree-level to maximize the accuracy of split scoring.