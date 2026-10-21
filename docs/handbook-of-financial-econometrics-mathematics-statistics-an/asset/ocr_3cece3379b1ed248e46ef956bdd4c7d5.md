pricing models (e.g., McCulloch and Rossi, 1991; Geweke and Zhou, 1996; Ang and Chen, 2007; and Cederburg and O’Doherty, 2015).

Cederburg and O’Doherty (2015) introduce a hierarchical Bayesian approach and uses US firm level data to reexamine financial anomalies under capital asset pricing model. The Bayesian approach can estimate all parameters simultaneously in one step and effectively avoid the errors-in-variables problem on the estimators induced from two-pass capital asset pricing test. Their empirical finding shows that the economic importance of CAPM anomalies is overstated.

Cederburg and O’Doherty (2015) uses a Bayesian approach to simultaneously estimate coefficients of the following three equation system.

```
r_{i,t,y} = α_{i,y} + β_{i,y} r_{m,t,y} + ε_{i,t,y}, where ε_{i,t,y} ~ N(0, σ²_{r_{i,y}}), (37.52)
α_{i,y} = X_{i,y} + η_{i,y}, where η_{i,y} ~ N(0, σ²_{α,i,y}) and (37.53)
δ_y = \bar{δ} + ν_y, where ν_y ~ MVN(0, V), (37.54)
```

where r_{i,t,y} is firm i’s excess return in month t during the time period y, and r_{m,t,y} denotes the monthly excess return for firm i during the time period y. α_{i,y} and δ_y are latent variables. X_{i,y} is a vector including a constant and firm characteristics observable during the time period y. The model allows firm-level βs to vary over each time period, y.

In addition to dealing with errors-in-variables problem, there are several advantages using the Bayesian approach to test the capital asset pricing model. First, the Bayesian approach allows βs to vary over time periods and firms and controls the inherent uncertainty associated with firm-level βs. Second, the Bayesian approach can modify the distribution assumptions in stock returns and market returns. Third, the Bayesian inference is free from the use of asymptotic approximations and therefore can be used under finite sample. Fourth, the Bayesian approach takes parameter uncertainty associated with all the model parameters into account.

# 37.4 Applications of Errors-in-Variables Models in Finance Research

For the last four and a half decades, alternative EIV methods have been used to correct estimation bias associated with empirical results in cost of capital, asset pricing model, and capital structure research. Here we review these four kinds of research, cost of capital, asset pricing models, capital structure, and investment equation. EIV models used in finance research will be discussed