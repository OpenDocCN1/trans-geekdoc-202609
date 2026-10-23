# 8.1. Bayesian decision theory

|   | 0                  | 1                          |
| Truth |                    |                            |
| 0   | TN/N=TNR=Spec      | FP/N=FPR=Type I = Fallout  |
| 1   | FN/P=FNR=Miss=Type II | TP/P=TPR=Sens=Recall     |

|   | 0              | 1                  |
| Truth |                |                    |
| 0   | TN/Ñ=NPV       | FP/ P =FDR         |
| 1   | FN/Ñ=FOR       | TP/ P =Prec=PPV    |



For any fixed threshold τ, we consider the following decision rule:

ŷ_τ(x) = I(p(y = 1|x) ≥ 1 - τ)

(8.14)

We can compute the empirical number of false positives (FP) that arise from using this policy on a set of N labeled examples as follows:

FP_τ = ∑_{n=1}^N I(ŷ_τ(x_n) = 1, y_n = 0)

(8.15)

Similarly, we can compute the empirical number of false negatives (FN), true positives (TP), and true negatives (TN). We can store these results in a 2 × 2 class confusion matrix C, where C_{ij} is the number of times an item with true class label i was (mis)classified as having label j. In the case of binary classification problems, the resulting matrix will look like Table 8.1.

From this table, we can compute p(ŷ|y) and p(y|ŷ), depending on whether we normalize across the rows or columns. We derive various summary statistics from these distributions, as summarized in Table 8.2 and Table 8.3. For example, the true positive rate (TPR), also known as the sensitivity, recall or hit rate, is defined as

TPR_τ = p(ŷ = 1|y = 1, τ) = TP_τ / (TP_τ + FN_τ)

(8.16)

and the false positive rate (FPR), also called the false alarm rate, or the type I error rate, is defined as

FPR_τ = p(ŷ = 1|y = 0, τ) = FP_τ / (FP_τ + TN_τ)

(8.17)

> Do not distribute without permission from Kevin P. Murphy and MIT Press.