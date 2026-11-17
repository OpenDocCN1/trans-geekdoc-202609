```
betaAvg += betaRidge/numfolds
interceptAvg += intter/numfolds

mse_avg = np.mean(mse)
x_test = np.array(test.drop(["Fertility", \\
    "Examination"],axis=1))
y_test = test["Fertility"]]
yhatt = interceptAvg+np.matmul(x_test, betaAvg)
msetest = np.mean((yhatt-y_test)**2)
msesests.append(msetest)
mses.append(mse_avg)

plt.figure(figsize=(8, 6))
ax = plt.gca()
ax.plot(lambdas, mses, color='red')
ax.plot(lambdas, msetests,color='green')
ax.set_xscale('log')
plt.xlabel('lambda')
plt.ylabel('test MSE')
plt.title('CV (red) and Test MSE (green) as ' \\
    'a function of lambda')
plt.axis('tight')
plt.show()
```

6.5 (Advanced Project) Using the given code above, convert it to run LC-ridge. To do this, you need to replace the LS-ridge statements above with the corresponding LC-ridge statements and then run the minimizer. You will need the code given in the Problems section of Chapter 5.

# References

James, G., Witten, D., Hastie, T. et al. (2023). *An Introduction to Statistical Learning with Applications in Python*. Springer.

Montgomery, D.C., Peck, E.A., and Vining G.G. (2012). *Introduction to Linear Regression Analysis*, 4e. Wiley.

Saleh A.K. Md. E., Arashi, M., and Kibria, B.M.G. (2019). *Theory of Ridge Regression Estimation with Applications*. New York: John Wiley and Sons.

Saleh, A.K. Md. E., Arashi, M., Saleh, R., and Norouzirad, M. (2022). *Rank-Based Shrinkage and Selection: With Application to Machine Learning*. New York: John Wiley and Sons.