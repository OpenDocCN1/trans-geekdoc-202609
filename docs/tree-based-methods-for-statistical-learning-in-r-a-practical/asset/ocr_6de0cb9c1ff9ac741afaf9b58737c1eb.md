| Permutation/order of players | Alex | Brad | Brandon |
|---|---|---|---|
| Alex, Brad, Brandon | $10 | $15 | $5 |
| Alex, Brandon, Brad | $10 | $15 | $5 |
| Brad, Alex, Brandon | $5 | $20 | $5 |
| Brad, Brandon, Alex | $10 | $20 | $0 |
| Brandon, Alex, Brad | $5 | $15 | $10 |
| Brandon, Brad, Alex | $17 | $3 | $10 |
| Shapley contribution: | $9.50 | $14.67 | $5.83 |

TABLE 6.1: Marginal contribution for each permutation of the players/beer drinkers {Alex, Brad, Brandon} (i.e., the order in which they arrive). The Shapley contribution is the average marginal contribution across all permutations. (Notice how each row sums to the total bill of $30.)

+   • the total payout/worth (\(\Delta_S\)) for \(x^*\) is the prediction for \(x^*\) minus the average prediction for all training observations (the latter is referred to as the baseline and denoted \(\bar{f}\)): \(\hat{f}(x^*) - \bar{f}\);

+   • the players are the individual feature values of \(x^*\) that collaborate to receive the payout \(\Delta_S\) (i.e., predict a certain value).

The second point, combined with the efficiency property stated in the previous section, implies that the \(p\) Shapley explanations (or feature contributions) for an observation of interest \(x^*\), denoted \(\{\phi_i(x^*)\}_{i=1}^p\), are inherently standardized since \(\sum_{j=1}^p \phi_i(x^*) = \hat{f}(x^*) - \bar{f}\).

# 6.3.2.1 Tree SHAP

Several methods exist for estimating Shapley values in practice. The most common is arguably Tree SHAP [Lundberg et al., 2020], an efficient implementation of exact Shapley values for decision trees and ensembles thereof.

Tree SHAP is a fast and exact method to estimate Shapley values for tree-based models (including tree ensembles), under several different possible assumptions about feature dependence. The specifics of Tree SHAP are beyond the scope of this book, so I’ll defer to [Lundberg et al., 2020] for the details. It’s implemented in the Python shap module, and embedded in several tree-based modeling packages across several open source languages (like xgboost [Chen et al., 2021] and lightgbm [Shi et al., 2022]). While the details of Tree SHAP are beyond the scope of this book, we’ll see an example of it in action in Section 8.9.4.