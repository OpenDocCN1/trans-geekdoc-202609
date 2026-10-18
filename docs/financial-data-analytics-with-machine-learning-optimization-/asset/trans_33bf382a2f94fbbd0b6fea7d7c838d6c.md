

## 参考文献

12. Kaufman, L., and Rousseeuw, P. J. (1990). Finding Groups in Data: An Introduction to Cluster Analysis. Wiley.

13. Kendall, M.G. (1938). A new measure of rank correlation. Biometrika, 30(1/2), 81–93.

14. Konishi, S., and Kitagawa, G. (2008). Information Criteria and Statistical Modelling. Springer Science & Business Media.

15. Kullback, S. (1997). Information Theory and Statistics. Courier Corporation.

16. Lehmann, E.L., and Casella, G. Theory of Point Estimation (2nd ed.). Springer.

17. Pearson, K. (1895). Notes on regression and inheritance in the case of two parents. Proceedings of the Royal Society of London, 58, 240–242.

18. Rathi, P., and Arpan, M. (2019). Insurance company dataset. https://www.kaggle.com/datasets/prakharrathi25/insurance-company-dataset (accessed 15 May 2022).

19. Spearman, C. (1904). The proof and measurement of association between two things. The American Journal of Psychology, 15(1), 72–101.

20. Thomas, K. (2021). Bank churn data exploration and churn prediction. https://www.kaggle.com/code/thomaskonstantin/bank-churn-data-exploration-and-churn-prediction/data (accessed 15 May 2022).

21. Witten, I.H., Frank, E., Hall, M.A., and Pal, C.J. (2016). Data Mining: Practical Machine Learning Tools and Techniques (4th ed.). Morgan Kaufmann.

22. Young, G.A., and Smith, R.L. (2005). Essentials of Statistical Inference. Cambridge University Press.

## NOTES

1. 我们首先将值按降序排序，然后用数字 `1, ..., n` 对排序后的值进行索引作为其主要排名。对于每组并列值，即成员具有相同值的情况，该组中所有成员的排名均等于这些值的平均主要排名。

2. 除非引起歧义，否则我们将使用索引集来表示相应的特征集，例如，`{1, 2, 3}` 代表 `{x₁, x₂, x₃}`。

3. 该总数可以通过标准的组合论证得出：我们首先关注 `Xₗ,₁⁽ⁱ⁾` 中具有任意类别标签 `cₖ` 的观测值，那么任何分类都将导致以下三种情形之一：

   * (i) 所有这些观测值都被分类到 `Xₗ₊₁,₁⁽ⁱ⁾`，因此类别 `cₖ` 仅存在于 `Xₗ₊₁,₁⁽ⁱ⁾` 中；
   * (ii) 所有这些观测值都被分类到 `Xₗ₊₁,₂⁽ⁱ⁾`，因此类别 `cₖ` 仅存在于 `Xₗ₊₁,₂⁽ⁱ⁾` 中；以及
   * (iii) 部分观测值被分类到 `Xₗ₊₁,₁⁽ⁱ⁾`，而其他观测值则落入 `Xₗ₊₁,₂⁽ⁱ⁾`，因此类别 `cₖ` 同时存在于两个子集中。

