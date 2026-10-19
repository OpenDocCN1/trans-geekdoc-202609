# 3.1. Weighted Parameter Combination Selection Method

By taking a weighted average of the performance of each parameter combination and its neighboring parameter combinations, where neighboring parameter combinations are defined as those within one to three circles of expansion. The design of the weighting ratios adopts the concept of “inverse distance weighting”, using the reciprocal of the distance between parameter combinations as weights (Equation (5)). The weight of the central parameter combination is 1. After weighting, parameter combinations that are farther away have a smaller influence.

$$w_i = \frac{1}{\sqrt{(x_i - x_{center})^2 + (y_i - y_{center})^2}}, \qquad (5)$$

+   - $w_i$: Weight of parameter combination $i$
+   - $x_i$, $y_i$: Position of parameter combination $i$
+   - $x_{center}$, $y_{center}$: Position of the central parameter combination
+   - $x_i \neq x_{center}$ and $y_i \neq y_{center}$

If $x_i$, $y_i$ are the central points, the formula’s result would be infinite; in this study, the weight for this case is set to 1.

# 3.2. Standard Deviation Parameter Selection Method

The Standard Deviation Parameter Selection Method is used to identify parameter combinations within the in-sample dataset that exhibit relatively stable performance compared to their neighboring parameter combinations. This method begins by filtering out parameter combinations for each period in the in-sample dataset where the net profit is greater than the average net profit of all parameter combinations. It then calculates the standard deviation for each parameter combination concerning its neighboring parameter combinations. The standard deviation indicates the level of variation between the parameter combination and its neighbors; a higher standard deviation implies greater variation, while a lower standard deviation implies less variation. Finally, the method selects the parameter combination with the lowest standard deviation from all parameter combinations as the recommended parameter and evaluates its performance on the out-of-sample data. The formula for standard deviation is given by Equation (6).

$$\sigma_i = \sqrt{\frac{1}{N}\sum_{i=1}^{N}\left(Ind_i - \overline{Ind}\right)^2}, \qquad (6)$$

+   - $\sigma_i$: The standard deviation of the performance (net profit, MDD, MAR) of parameter combination $i$ and its neighbors within two circles.
+   - $Ind_i$: The performance value of parameter combination $i$ (net profit, MDD, MAR).
+   - $\overline{Ind}$: The mean of parameter combination $i$ and its neighboring parameter combinations.
+   - $N$: The number of parameter combinations $i$ and its neighbors.

# 3.3. Island Area Parameter Selection Method

This method can be likened to comparing benchmark performance to sea level as illustrated in Figure 2. It examines the areas occupied by different islands located at sea level and selects the parameter point with the best performance from the largest island as the parameter choice. Regarding benchmark performance, we arranged the performance of all parameter combinations within the in-sample dataset from smallest to largest for each period. Subsequently, benchmark performance was determined by percentile ranks (PR). In this study, PR values were set at 90, 95, and 99.