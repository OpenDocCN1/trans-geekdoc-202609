
library(randomForest)

# Fit a bagged tree ensemble
set.seed(1452) # for reproducibility
(iris.bag <- randomForest(Species ~ ., data = iris, mtry = 4))

#>
#> Call:
#> randomForest(formula = Species ~ ., data = iris, mtry = 4)
#>  Type of random forest: classification
#>  Number of trees: 500
#> No. of variables tried at each split: 4
#>
#>   OOB estimate of  error rate: 4.67%
#> Confusion matrix:

| | setosa | versicolor | virginica | class.error |
|---|---|---|---|---|
| setosa | 50 | 0 | 0 | 0.00 |
| versicolor | 0 | 47 | 3 | 0.06 |
| virginica | 0 | 4 | 46 | 0.08 |

Next, I plot the partial dependence of Species on Petal.Width for each of the three classes using the pdp package. The code chunk below exploits a simple trick to computing partial dependence with partial() for several classes simultaneously. The results are displayed in Figure 6.5. Here, you can clearly see the average effect petal width has on the probability of belonging to each species.

```
library(pdp)
library(ggplot2)
```

```
# Prediction wrapper that returns average prediction for each class
pfun <- function(object, newdata) {
  colMeans(predict(object, newdata = newdata, type = "prob"))
}
```

```
# Partial dependence of probability for each class on petal width
p <- partial(iris.bag, pred.var = "Petal.Width", pred.fun = pfun)
ggplot(p, aes(Petal.Width, yhat, color = as.factor(yhat.id))) +
  geom_line() +
  theme(legend.title = element_blank(),
        legend.position = "top")
```

Note that without the aid of a user-supplied prediction function (via the pred.fun argument), pdp's partial() function can only compute partial dependence in regards to a single class; see Greenwell [2017] for more details on the use of this package.

![](img/2c227bfb3620dc3d159fa5e6598afa30_233_0.png)

FIGURE 6.5: Partial dependence of species probability on petal width for each of the three iris species using a bagged tree ensemble.

## 6.3 Feature contributions

In general, a _local feature contribution_ is the worth assigned to a feature's value that is proportional to the feature's share in the model's prediction for a particular observation. You can think of feature contributions as a directional variable importance at the individual prediction level. While there are a wide variety of feature contribution methodologies, the next section briefly covers one of the most popular methods in current use: _Shapley values_ (or _Shapley explanations_). Shapley values necessarily involve a lot of mathematical notation, but I will try to avoid as much as possible while trying to convey the main concepts. For more details, start with Štrumbelj and Kononenko [2014] and Lundberg and Lee [2017].

### 6.3.1 Shapley values

The Shapley value [Shapley, 2016] is an idea from coalitional/cooperative game theory. In a coalitional game, assume there are _p_ players that form a grand coalition (_S_) worth a certain payout (\(\Delta_S\)). Suppose it is also known how much any smaller coalition (\(Q \subseteq S\)) (i.e., any subset of _p_ players) is worth (\(\Delta_Q\)). The goal is to distribute the total payout \(\Delta_S\) to the individual _p_ players in a “fair” way; that is, so that each player receives their “fair” share. The Shapley value is one such solution and the only one that uniquely satisfies a particular set of “fairness properties.”

Let $v$ be a characteristic function that assigns a value to each subset of players; in particular, $v : 2^p \rightarrow \mathbb{R}$, where $v(S) = \Delta_S$ and $v(\emptyset) = 0$, with $\emptyset$ denoting the empty set (i.e., zero players). Let $\phi_i(v)$ be the contribution (or portion of the total payout) attributed to player $i$ in a particular game with total payout $v(S) = \Delta_S$. The Shapley value satisfies the following properties:

- efficiency: $\sum_{i=1}^p \phi_i(v) = \Delta_S$;
- null player: $\forall W \subseteq S \setminus \{i\} : \Delta_W = \Delta_{W \cup \{i\}} \implies \phi_i(v) = 0$;
- symmetry: $\forall W \subseteq S \setminus \{i, j\} : \Delta_{W \cup \{i\}} = \Delta_{W \cup \{j\}} \implies \phi_i(v) = \phi_j(v)$;
- linearity: If $v$ and $w$ are functions describing two coalitional games, then $\phi_i(v + w) = \phi_i(v) + \phi_i(w)$.

The above properties can be interpreted as follows:

- the individual player contributions sum to the total payout, hence, are implicitly normalized;
- if a player does not contribute to the coalition, they receive a payout of zero;
- if two players have the same impact across all coalitions, they receive equal payout;
- the local contributions are additive across different games.

Shapley [2016] showed that the unique solution satisfying the above properties is given by

```
\(\phi_i(v) = \frac{1}{p!} \sum_{\mathcal{O} \in \pi(p)} \left[ v \left( S^{\mathcal{O}} \cup i \right) - v \left( S^{\mathcal{O}} \right) \right], \quad i = 1, 2, \dots, p, \quad (6.5)\)
```

where $\mathcal{O}$ is a specific permutation of the player indices $\{1, 2, \dots, p\}$, $\pi(p)$ is the set of all such permutations of size $p$, and $S^{\mathcal{O}}$ is the set of players joining the coalition before player $i$.

In other words, the Shapley value is the average marginal contribution of a player across all possible coalitions in a game. Another way to interpret (6.5) is as follows. Imagine the coalitions (subsets of players) being formed one player at a time (which can happen in different orders), with the $i$-th player demanding a fair contribution/payout of $v \left( S^{\mathcal{O}} \cup i \right) - v \left( S^{\mathcal{O}} \right)$. The Shapley value for player $i$ is given by the average of this contribution over all possible permutations in which the coalition can be formed.

A simple example may help clarify the main ideas. Suppose three friends (players)—Alex, Brad, and Brandon—decide to go out for drinks after work (the game). They shared a few pitchers of beer, but nobody paid attention to how much each person drank (collaborated). What’s a fair way to split the tab (total payout)?

Suppose we knew the following information, perhaps based on historical happy hours:

- if Alex drank alone, he’d only pay $10;
- if Brad drank alone, he’d only pay $20;
- if Brandon drank alone, he’d only pay $10;
- if Alex and Brad drank together, they’d only pay $25;
- if Alex and Brandon drank together, they’d only pay $15;
- if Brad and Brandon drank together, they’d only pay $13;
- if Alex, Brad, and Brandon drank together, they’d only pay $30.

With only three players, we can enumerate all possible coalitions. In Table 6.1, I list all possible permutations of the three players and list the marginal contribution of each. Take the first row, for example. In this particular permutation, we start with Alex. We know that if Alex drinks alone, he’d spend $10, so his marginal contribution by entering first is $10. Next, we assume Brad enters the coalition. We know that if Alex and Brad drank together, they’d pay a total of $25, leaving $15 left over for Brad’s marginal contribution. Similarly, if Brandon joins the party last, his marginal contribution would be only $5 (the difference between $30 and $25). The Shapley value for each player is the average across all six possible permutations (these are the column averages reported in the last row). In this case, Brandon would get away with the smallest payout (i.e., have to pay the smallest portion of the total tab). The next time the bartender asks how you want to split the tab, whip out a pencil, and do the math!

## 6.3.2 Explaining predictions with Shapley values

From this section forward, let $\{x_i\}_{i=1}^p$ represent the $p$ feature values comprising $x^*$, the observation whose prediction we want to try to explain. Štrumbelj and Kononenko [2014] suggested using the Shapley value (6.5) to help explain predictions from a supervised learning model. In the context of statistical and machine learning,

- a game is represented by the prediction task for a single observation $x^*$;
