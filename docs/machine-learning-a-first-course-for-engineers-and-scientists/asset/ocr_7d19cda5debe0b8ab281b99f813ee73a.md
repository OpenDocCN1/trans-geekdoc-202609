# 4.4 The bias-variance decomposition of $E_{new}$

![](bbox=[0.188, 0.085, 0.875, 0.348])

**Figure 4.8:** The bias-variance decomposition of $E_{new}$, instead of the training error-generalization decomposition in Figure 4.3. Low model complexity means high bias. The more complicated the model, the more it adapts to (noise) in the training data, and the higher the variance. The irreducible error is independent of the particular choice of model and is therefore constant. The problem of achieving a small $E_{new}$ by selecting a suitable model complexity level is often called the bias–variance tradeoff.

![](bbox=[0.118, 0.466, 0.882, 0.696])

**Figure 4.9:** The typical relationship between bias, variance and the size $n$ of the training dataset. The bias is (approximately) constant, whereas the variance decreases as the size of the training dataset increases. This figure can be compared with Figure 4.6.

The squared bias is more of a property of the model than that of the training dataset, and we may think$^4$ of the bias term as independent highly with $n$. The variance, on the other hand, varies highly with $n$. $E_{new}$ typically decreases as $n$ increases, and the reduction in $E_{new}$ is largely because of the reduction in variance. Intuitively, the more data, the more information we have about the parameters, resulting in a smaller variance. This is summarized by Figure 4.9, which can be compared to Figure 4.6.

> $4$This is not exactly true. The average model $f$ might be different if all datasets (which we average over) contain $n=2$ or $n=100000$ data points, but we neglect that effect here.

This material will be published by Cambridge University Press. This pre-publication version is free to view and download for personal use only. Not for re-distribution, re-sale or use in derivative works.
© Andreas Lindholm, Nicholas Wahlström, Fredrik Edholm, and Thomas B. Schön. 2021.