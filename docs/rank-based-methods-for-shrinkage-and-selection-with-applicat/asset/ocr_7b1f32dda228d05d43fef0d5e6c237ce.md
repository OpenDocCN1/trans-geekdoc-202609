**Table 11.5** RLR-LASSO estimates vs. $\lambda_1$ with number of correct predictions.

| $\lambda_1$ | $\hat{\beta}_0$ | $\hat{\beta}_1$ | $\hat{\beta}_2$ | $\hat{\beta}_3$ | $\hat{\beta}_4$ | Number correct |
|---|---|---|---|---|---|---|
| 0.0 | -13.1 | 0.32 | 0.41 | 11.7 | 11.3 | 331 |
| 1.0 | -8.3 | -2.6e-04 | 5.1e-04 | 7.5 | 7.2 | 331 |
| 4.0 | -5.4 | 1.1e-03 | -1.0e-03 | 4.9 | 4.7 | 331 |
| 6.0 | 4.7 | 0.006 | -0.006 | 0.002 | 0.002 | 266 |
| 10.0 | 5.2 | -0.02 | -0.012 | -0.006 | -0.006 | 266 |

conclusion is that ridge can act to improve LLR but may not be as useful for RLR in this type of example. The best solution for the RLR-ridge occurs at $\lambda_2 = 0$ so there is no improvement with regularization.

The evolving decision boundaries for several values of $\lambda_2$ during LLR-ridge regularization are shown in Figure 11.9. The boundary first shifts downward as $\lambda_2$ increases and then begins to shrink in size as $\lambda_2$ is increased towards infinity. A similar effect occurs with RLR-ridge (not shown) but the shrinkage occurs much faster than for the LLR-ridge. In fact, the RLR-ridge decision boundary disappears around $\lambda_2 = 30$, whereas this occurs at $\lambda_2 = 80$ for LLR-ridge, as seen in Figure 11.8.

The LASSO penalty function has a similar characteristic as ridge for LLR and RLR. The results improve for LLR-LASSO as $\lambda_1$ increases and then eventually the results degrade beyond the optimal value. For RLR-LASSO, the results remain about the same for small $\lambda_1$ but degrade beyond a certain large value of $\lambda_1$, so it is of no value here. However, subset selection can be carried out using LASSO. In particular, we show the parameter values for a range of values for $\lambda_1$ in Table 11.5. From this table, we can see that a value of $\lambda_1 = 1.0$ produces relatively small values of $\beta_1$ and $\beta_2$, associated with $x_1$ and $x_2$, respectively. These can be set to 0 and a rather compact model can be generated using only $x_1^2$ and $x_2^2$. Therefore, subset selection using LASSO is still appropriate in this example for LLR and RLR whereas ridge is effective for LLR but not effective for RLR in this case. A key lesson is that LASSO (or aLASSO) should be used for selection and ridge for shrinkage with rank methods.

In the previous examples, the outliers were few in number and only existed in one region of the solution space. In our final example, we show the effect of outliers in the both regions of the circular data which is more realistic. That is, there are gray outliers (loan defaults) in the predominantly black dot region (loan repaying customers) and vice versa. The results from LLR ($\lambda_2 = 0.0$, learning rate = 0.02) and RLR ($\lambda_2 = 0.0$, learning rate = 2.0), LLR-ridge ($\lambda_2 = 10.0$, learning rate = 0.02) and SVM (RBF, $C = 1.0$, $\gamma = 1.0$) are shown in Figure 11.10.