# CHAPTER 8 LOCAL MODEL-AGNOSTIC METHODS

Actual prediction: 2409
Average prediction: 4518
Difference: -2108

![](bbox=[0.185, 0.175, 0.742, 0.439])

Figure 8.21: Shapley values for days 285. With a predicted 2049 rental bikes, this day is -2108 below the average prediction of 4518. The weather situation and humidity had the largest negative contributions. The temperature on this day had a positive contribution. The sum of Shapley values yields the difference of actual and average prediction (-2108).

Can we do the same for any type of model? It would be great to have this as a model-agnostic tool. Since we usually do not have similar weights in other model types, we need a different solution.

Help comes from unexpected places: cooperative game theory. The Shapley value is a solution for computing feature contributions for single predictions for any machine learning model.

# 8.5.3.1 The Shapley Value

The Shapley value is defined via a value function *val* of players in S.

The Shapley value of a feature value is its contribution to the payout, weighted and summed over all possible feature value combinations:

```
$$\phi_j(val) = \sum_{S\subseteq\1,...,p\}\setminus\{j\}} \frac{|S|! (p - |S| - 1)!}{p!} (val(S \cup \{j\}) - val(S))$$
```