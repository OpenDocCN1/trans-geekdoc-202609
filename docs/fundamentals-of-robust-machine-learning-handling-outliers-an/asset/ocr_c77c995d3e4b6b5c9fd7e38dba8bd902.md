c) Run LC-LASSO with the following code.

```
n_lambdas = 25
beta = np.random.randn(d)/10.
lambdas = np.logspace (-3, 5, n_lambdas)
coefs = []
for lam in lambdas:
    res = minimize(LCLASSO, beta, method='BFGS' )
    beta = res.x
    coefs.append(beta[0:d-1])
```

Plot the results using the code in the previous problem with a change in the title to reflect the use of LC-LASSO. What value of \(\lambda\) reduces the number of variables to 2 for LC-LASSO?

# References

James, G., Witten, D., Hastie, T. et al. (2023). *An Introduction to Statistical Learning with Applications in Python*. Springer.

Saleh, A.K. Md. E., Arashi, M., and Kibria, B.M.G. (2019). *Theory of Ridge Regression Estimation with Applications*. New York: John Wiley and Sons.

Saleh, A.K. Md. E., Arashi, M., Saleh, R., and Norouzirad, M. (2022). *Rank-Based Shrinkage and Selection: With Application to Machine Learning*. New York: John Wiley and Sons.