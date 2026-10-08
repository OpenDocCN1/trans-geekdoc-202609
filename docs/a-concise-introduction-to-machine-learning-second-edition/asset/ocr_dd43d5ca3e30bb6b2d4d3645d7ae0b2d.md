We can now estimate the mortality for smokers and nonsmokers for each of the age groups. Or in other words the estimated conditional probability of death given the age group and whether they were smokers or nonsmokers, $p(died|Y)$:

| | mortality |
|---|---||
| 18-24 | smokers | 3.6% |
| | nonsmokers | 1.6% |
| 25-34 | smokers | 2.4% |
| | nonsmokers | 3.2% |
| 35-44 | smokers | 12.8% |
| | nonsmokers | 5.8% |
| 45-54 | smokers | 20.8% |
| | nonsmokers | 15.4% |
| 55-64 | smokers | 44.3% |
| | nonsmokers | 33.1% |
| 65-74 | smokers | 80.6% |
| | nonsmokers | 78.3% |
| 75+ | smokers | 100% |
| | nonsmokers | 100% |

Now the mortality reflects the health advice given. In all age groups but one, the mortality of smokers is higher (or equal in the oldest group where no one was still alive). Smokers die younger on average which might in part explain their under-representation in the two oldest age groups.

Simpson's paradox is due to another variable influencing the data, but hiding. This is called confounding. In this case, it is the women in the original study and the distribution of smokers and nonsmokers within the different age groups. Whenever the distributions within a population (the women in the original study) vary for different parts of the population (the different age groups), data analysis has to be done carefully, taking these variations into account.

# 2.2 Probability Densities, Expectation, Variance and Moments

In the previous section, the random variables were discrete. However, one of them, age, is a continuous variable, if it is considered time passed since birth. It was discretized by considering age groups. The choice of how to discretize can influence the interpretation. No discretization at all, leads to the wrong interpretation of mortality with smokers being less likely to die than nonsmokers. On the other hand, the discretization shall not be too fine-grained, because the number of samples in each category becomes