FIGURE 2.10: Fitted residuals from the airquality OLS regression.

The HC standard errors are useful, and you will use them often. There is also an interesting relationship between HC standard errors and the bootstrap. It turns out that, for OLS, the parameter variance estimates you get from the nonparametric bootstrap are actually \textit{approximated} by the HC procedure.\textsuperscript{13} That is, you can use the HC standard errors as a fast alternative to bootstrapping for OLS. This relationship also implies that the assumption of the normal distribution in Equation 2.28 is not especially important for the HC standard errors\u2014they are robust to deviations from Gaussianity in the errors. To illustrate, we can run a quick bootstrap on the \textit{airquality} data.

```
```python
B <- 10000
beta <- vector (length=B)
n <- nrow(airquality)
for (b in 1:B) {
  bs = sample.int (n,n,replace=TRUE)
  bsfit <- lm(Ozone ~., data=airquality, subset=bs)
  beta[b] <- coef(bsfit) ["Wind"]
}
sd(beta)
[1] 0.8753398
```
```

To a first decimal place, the standard error matches that of the HC procedure. The sampling distributions are illustrated in Figure 2.11.

![](bbox=[0.3, 0.62, 0.7, 0.9])