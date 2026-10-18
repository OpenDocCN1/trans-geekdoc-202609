+   1. the parameter names
+   2. the ridge regression parameter values
+   3. the lm parameter values

Because I want to exclude the intercepts, I use [-1] to subset all the parameters except the first one (the intercept).

So that we can facet by model, I gather() the data, and then plot it using ggplot(). Because it’s nice to see things in ascending or descending order, I supplied reorder(Coef, Beta) as the x aesthetic, which will use the Coef variable as the x aesthetic, ordered by the Beta variable. By default, geom_bar() tries to plot frequencies, but because we want bars to represent the actual value of each parameter, we set the stat = "identity" argument.

# Listing 11.9 Plotting the model parameters

```
lmCoefs <- coef(lm(Yield ~ ., data = iowaTab))

coefTib <- tibble(Coef = rownames(ridgeCoefs)[-1],
Ridge = as.vector(ridgeCoefs)[-1],
Lm = as.vector(lmCoefs)[-1])

coefUntidy <- gather(coefTib, key = Model, value = Beta, -Coef)

ggplot(coefUntidy, aes(reorder(Coef, Beta), Beta, fill = Model)) +
  geom_bar(stat = "identity", col = "black") +
  facet_wrap(~Model) +
  theme_bw() +
  theme(legend.position = "none")
```

The resulting plot from code listing 11.9 is shown in figure 11.13. In the left facet we have the parameter estimates for the unregularized model, and in the right facet we have the estimates for our ridge regression model. Can you see that most of the ridge regression parameters (though not all) are smaller than those for the unregularized model? This is the effect of regularization.

![](bbox=[0.1, 0.8, 0.8, 0.95])

# Figure 11.13 Comparing the parameter estimates of our ridge regression model to our OLS regression model.