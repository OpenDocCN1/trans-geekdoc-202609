The calculations to obtain \(D_n(\beta)\) are reported in Table 1.6. We show column values for x, y, R, \(a_n\) and \(D_n\) as defined in the caption. There is one row in this table for each data point in the telephone data set. The \(D_n\) column is to be summed for each of the \(\beta^{(0)}\), \(\beta^{(1)}\), and \(\beta^{(2)}\) cases, as required by Eq. (1.6.5). Thus, among these three values, the solution, i.e. \(\hat{\beta}_n^R\), is the one that gives the minimum value of "sum" in the last row of Table 1.6. In this example, \(\hat{\beta}_n^R = \beta^{(1)} = 0.145\) which will be confirmed later. But, more generally, determining the value of \(\beta\) by hand to find a global solution to the optimization problem is not an easy task and, as mentioned before, we need to use software to numerically find the minimum value. The detailed step-by-step procedure given here is meant to solidify our understanding of Eq. (1.6.5).

Equivalently, instead of the dispersion function, \(D_n(\beta)\), one can use the root of its derivative, \(L_n(\beta)\), Eq. (1.6.8), as

\(\hat{\beta}_n^R = \left\{ \beta : L_n(\beta) = -\frac{1}{\sqrt{n}} \sum_{i=1}^n x_i \sqrt{12} \left( \frac{R_{n_i}(\beta)}{n+1} - \frac{1}{2} \right) = 0 \right\}.\)

The function `uniroot.all` from package `rootSolve` in R can be used here. We provide the required values in Table 1.6 in the column labeled \(L_n\). Here we seek the “sum” that is closest to zero. Again, the zero-crossing occurs at \(\hat{\beta}^R = \beta^{(1)} = 0.145\).

We have shown two methods for R-estimation of \(\beta\). Typically, we use \(D_n(\beta)\) to compute the estimate, and \(L_n(\beta)\) for hypothesis testing. It is instructive to examine a graphical equivalent of the procedure outlined above. This is shown in Figure 1.6. Consider the two panels on the left. The top panel shows the graph of \(D_n(\beta)\) which is clearly a convex function of \(\beta\). We note that the minimum is shown to be at 0.145. Similarly, the bottom panel is the function \(L_n(\beta)\). We see the zero crossing of this function at 0.145 also, with 276 steps, one for each slope. The values of these two graphs can be matched with the data for \(\beta^{(0)}\), \(\beta^{(1)}\), and \(\beta^{(2)}\) in Table 1.6.

Now we turn to the rank estimation of \(\theta\) using Eq. (1.6.10). In this regard, based on the related Wilcoxon score in Eq. (1.6.20), it can be estimated as

\(\hat{\theta}_n^R = \text{argmin} \left\{ \sum_{i=1}^n |y_i - (\theta + \hat{\beta}_n^R x_i)| \sqrt{3} \left( \frac{R_{n_i}^+(\theta)}{n+1} \right) \right\},\)

where

\(R_{n_i}^+(\theta) = R_{n_i}(|y_i - (\theta + \hat{\beta}_n^R x_i)|).\)

Here, we are given that \(\hat{\beta}_n^R = 0.145\) for the telephone data set so the only unknown is \(\theta\).