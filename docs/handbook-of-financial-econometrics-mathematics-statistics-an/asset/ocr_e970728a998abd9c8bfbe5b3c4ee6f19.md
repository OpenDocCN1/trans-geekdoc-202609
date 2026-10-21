Now let “ε” be a set of error terms that are i.i.d. (but not necessarily normal) with zero mean and finite variance. Finally, assume that E(x_t ε_t) = 0 for all periods, so all we assume now is GM “5(b)-ii”; so for the first time we are thinking about dropping GM “5(b)-i”.

The Mann–Wald theorem states that under these conditions:

$$p\lim\left(\frac{X'_n\varepsilon}{n}\right)=0,\qquad(115.13)$$

$$\frac{X'_n\varepsilon_n}{\sqrt{n}}\xrightarrow{d}N[0,\sigma^2Q].\qquad(115.14)$$

# 115.4 The Distribution of the OLS Estimator

We are now in a position to work out the properties of the OLS estimator when “X_n” is stochastic and related to the errors with some lags or leads, but not contemporaneously. This section states the distribution of the OLS estimators when GM conditions “5(a)” and “5(b)-i” do not hold but “5(b)-ii” does. We start by revisiting the deviation of the estimator from the true value, for a sample of size “n”:

$$(\hat{\beta}_n-\beta)=(X'_nX_n)^{-1}X'_n\varepsilon_n.\qquad(115.15)$$

Now, by the Mann–Wald theorem, the last product on the RHS has the limiting distribution:

$$\frac{X'_n\varepsilon_n}{\sqrt{n}}\xrightarrow{d}N(0,\sigma^2Q).\qquad(115.16)$$

The LHS here is now going to play the role of “ψ_n” in Cramers theorem. Note that the Mann–Wald theorem requires $$p\lim\left(\frac{X'_nX_n}{n}\right)^{-1}=Q^{-1}.\qquad(115.17)$$ Applying Cramer's theorem we get $$\sqrt{n}(\hat{\beta}-\beta)=\left(\frac{X'_nX_n}{n}\right)^{-1}\frac{X'_n\varepsilon_n}{\sqrt{n}},\qquad(115.18)$$ $$\sqrt{n}(\hat{\beta}-\beta)\xrightarrow{d}N\left(0,Q^{-1}(\sigma^2Q)Q^{-1}\right).\qquad(115.19)$$ Therefore, the asymptotic distribution is $$\hat{\beta}-\beta\sim AN[0,\sigma^2Q^{-1}].\qquad(115.20)$$