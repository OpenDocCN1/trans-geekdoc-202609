The daily excess portfolio returns (i.e., the difference between the daily return of the portfolio and the three month UK T-bill rate) are regressed on the Fama and French (1993) three factors (i.e., the difference between the FTSE All-Share Index and the three month UK T-bill rate, as well as the daily returns on zero-investment factor-mimicking portfolios for size and B/M. The standard errors are corrected for heteroscedasticity through the Newey–West procedure with 0 lag.

```
matrix b = e(b)
```

The b matrix contains the coefficients from the original regression. This matrix is used to generate the list of independent variables stored in the macro xvars, which is a place where we can hold a piece of text including numeric as well as alphabetic characters, and then to produce/simulate a new dependent variable with the resampled residuals.

```
local icons = colnumb(b, "_cons")
matrix b[1,'icons'] = 0
```

The time-series of pseudo excess returns impose the null hypothesis of zero true performance (α = 0).

```
predict double resid, residuals
histogram resid
simulate _b _se, reps(10000) : bs_resid, res(resid) mat(b)
```

We use the bs_resid.do file to execute the bs_resid.ado file for the corresponding bootstrapping simulation methods. Specifically, _b represents the coefficient on risk factor; _se represents the standard error; reps() specifies the number of replications to be performed, say, 10,000 in this study.

# Appendix 55C: Summary Statistics and Correlations for the Daily Risk Factor Returns

This appendix presents descriptive statistics (in Panel A) and correlation (in Panel B) of the daily risk factor returns in the UK stock market over the period January 1997 to June 2015. Mean and Std.Dev. are the mean and standard deviation of the daily returns; Min and Max are the minimum and maximum of the daily returns; t-statistic is the ratio of the mean return over its standard error. *** stands for the statistical significance at the 1% level. We obtain the daily (R_{m,t} − R_{f,t}), SMB_t, and HML_t in the UK stock market from the Xfi Centre for Finance and Investment at the University