![](bbox=[0.16, 0.05, 0.86, 0.5])

FIGURE 3.8: Cross-validated lasso for the browser data. The blue dots are mean OOS errors, and the error bars mark ± 1 standard error. CV-min and CV-1se rules are marked with vertical lines.

For most applications, I recommend using the CV-min rule. This is the best choice if you are focused on OOS predictive performance. The CV-1se rule is more *conservative*: it hedges toward a simpler model in a reasonable but ad hoc fashion. This should be used if you are going to put a lot of weight on interpreting the nonzero $\hat{\beta}_k$, for example, as being special or representing some underlying truth. In high dimensions, such interpretation should be done with care anyway because multicollinearity can make it somewhat arbitrary which coefficients end up nonzero. Hence, I focus on predictive performance. However, the CV-1se rule is the default in *glmtr* because it is the default in *glmnet* and we don’t want to rock the boat. You need to add the flag `select="min"` to get the CV-min selection.

When you call *coef* on a fitted *cv.glmtr* object, it automatically does the selection.