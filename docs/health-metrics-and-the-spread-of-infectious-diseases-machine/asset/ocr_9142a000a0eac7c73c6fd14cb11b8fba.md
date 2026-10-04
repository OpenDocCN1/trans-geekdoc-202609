# The Steps of Building a Model

paste("RMSE", rmse)
# [1] "RMSE": 4.25017352277781

```
augmented %>%
gpgplot(aes(I, .pred)) +
geom_point() +
geom_abline() +
labs(
  title = "Prediction of Infections for Epidemic X",
  subtitle = "Simulate Data",
  x = "Infections", y = "Predicted values")
augmented %>%
gpgplot(aes(x = time)) +
gpgplot_point(aes(y = I)) +
gpgom_line(aes(y = .pred), color = "navy") +
labs(
  title = "Prediction of Infections for Epidemic X",
  subtitle = "Simulate Data",
  x = "Time (Day)", y = "Obsesrvd vs Estimated values")
```

![](bbox=[0.105, 0.433, 0.894, 0.597])

(a) Prediction of Infections for Epidemic X
(b) Observed vs Estimated values

Figure 6.9 Prediction of Infections for Epidemic X

# 6.3.3 Example: Epidemic Y

# 6.3.3.1 INLA: An Empirical Bayes Approach to GAMs

In this example is a simulation of an epidemic in 100 days based on temperature level and number of cases simulated with a random poisson distribution.

The model uses the INLA - integrated nested Laplace approximation⁸ model, an excellent choice for applications requiring repeated model fitting. The INLA approach is particularly useful for fitting complex models, as Generalised additive models (GAMs), which involve non-linear relationships between predictors and the response variable.

> ⁸Approximate Bayesian Inference for Latent Gaussian Models by Using Integrated Laplace Approximations - Rue - 2009 - Journal of the Royal Statistical Society: Series b (Statistical Methodology) - Wiley Online Library, n.d., https://rss.onlinelibrary.wiley.com/doi/full/10.1111/j.1467-9868.2008.00700.x.