\(\beta_1^2 + \beta_2^2 \le c,\) (1.7.11)

where c is a constant. Note that this constraint would form a circular region about the origin, as shown in Figure 1.8. The figure represents the two-dimensional plane of possible \(\beta_1\) and \(\beta_2\) values. The circles represent the constraint \(\beta_1^2 + \beta_2^2 = c\) due to the ridge penalty function for different values of c, as set by \(\lambda\) in the penalty function. The point marked “X” represents the unbiased rank or LS estimates. The contours around the estimates represent lines of equal value of the unpenalized loss function. The largest circle (labeled 0) is associated with \(\lambda = 0\), while the point the origin (where \(\beta_1 = \beta_2 = 0\)) is due to \(\lambda = \infty\).

Starting at the unbiased solution on the circle labeled 0, with \(\lambda_0 = 0\), as we apply the penal function with tuning factor \(\lambda\), the estimates shrink and follow some hypothetical trajectory depicted in the figure until the edge of the circle 1 is reached at \(\lambda = \lambda_1 > 0\). As \(\lambda\) increases to \(\lambda = \lambda_2 > \lambda_1\) ( circle 2), we shrink the estimates by a greater degree. At \(\lambda = \lambda_3 > \lambda_2\), we reach the circle 3. This continues until all estimates reach 0 at \(\lambda = \infty\) at the origin. Essentially, we are shrinking the estimates towards the null hypothesis, \(\boldsymbol{\beta} = 0\). In practice, we seek

![](bbox=[0.256, 0.482, 0.792, 0.868])

**Figure 1.8** Geometric interpretation of ridge.