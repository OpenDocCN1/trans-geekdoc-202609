# 18.3.4 Using Software for Partial and Semipartial (or Part) Correlation

Partial correlations are straightforward to calculate in SPSS. Simply select Correl from the Analyze menu, and then choose Partial. Select the variables to correlate (X and Y in Section 18.3.1) and move the variable to be partial (W in the prior equations) to the "controlling" for and click OK. For the 207 female-identifying participants in the Seasons data set with the age, bmi, ic, and height variables, the partial correlation of age with bmi is partial 0.509.

Computing a semi-partial or part correlation in SPSS requires first regressing X on W to obtain the results: Select Regression from the Analyze menu, then Linear. With the regression of X on W, click the "save" bar, and tick the box to save standardized residuals; these will be stored in window data. Finally, compute the correlation of Y with the file name RES_1 (assuming this is the first residual you have saved). Following the steps described in Section 18.3.2, the result will be the semipartial correlation, $r_{XY(W)} = 0.504$.

In R, the [ppcor] package provides functions for partial correlation (pcor or ptest) and semipartial correlation (sportest). For partial correlation, pcor can take a data frame as input (e.g., pcor(dat)), in which case the output will be a matrix of partial correlations of each pair with all the other variables partialed out, as well as a matrix of p-values. To compute a simple partial correlation, pcortest(X, Y) returns $r_{XY}$. For example, if the data described above are saved in a data frame called datWSc, then pcortest(datWSc, dat$age, dat$bmi) = .509. The function sportest(Y, W) returns $r_{XY(W)}$. For example, sportest(datWSc, dat$bmi) = .503. Note that any cases with missing data will be deleted by these functions to work; the na.omit function in the [base] package deletes rows with missing data on any variable.

# 18.3.5 Constraints in Sets of Correlation Coefficients

Given three variables X, Y, and W, there are three correlation coefficients, $r_{XY}$, $r_{XP}$ and $r_{YW}$. The range of possible values taken by any one of these correlations is constrained by the values taken by the other two. As the most extreme example, if W has a perfect linear relationship with both X and Y, then X and Y must have a perfect linear relationship. That is, if $r_{XY} = r_{YW} = 1$, however, what can we say about the possible values of $r_{XY}$ if $r_{X}$ and $r_{YW}$ are both equal to some other value between -1 and .7?

Because $r_{XY}$ is a correlation, it must take on a value between -1 and +1. If we have Equation 18.9 for $r_{XY}$

```
$r_{XY} = r_{XW}r_{YW} + \sqrt{(1-r_{XW}^2)(1-r_{YW}^2)}$
```

Therefore, the value of $r_{XY}$ must lie between

```
$r_{XY} - \sqrt{(1-r_{XW}^2)(1-r_{YW}^2)} = r_{XW}r_{YW} + \sqrt{(1-r_{XW}^2)(1-r_{YW}^2)}$
```

Substituting into these expressions, we see that if $r_{XW} = r_{YW} = .7$, $r_{XY}$ must have a value between -.02 and 1.00. A strong negative correlation between X and Y is not possible if X and Y have large positive correlations with W. Violating these constraints – either