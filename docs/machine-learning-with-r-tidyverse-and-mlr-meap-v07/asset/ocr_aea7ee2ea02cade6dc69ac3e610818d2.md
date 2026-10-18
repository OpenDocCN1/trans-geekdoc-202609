our learner is a wrapper function, we need to supply an additional argument more.unwrap = TRUE to tell mlr that it needs to go all the way down through the wrappers, to extract the base model information.



```
library(parallel)
library(parallelMap)
parallelStartSocket(cpus = detectCores())
gamModel <- train(gamFeatSelWrapper, gamTask)
parallelStop()
gamModelData <- getLearnerModel(gamModel, more.unwrap = TRUE)
```

Now, let’s understand our model a little better by plotting the functions it learned for each of the predictor variables. This is as easy as calling plot() on our model information. We can also look at the residuals from the model by extracting them with the resid() function. This allows us to plot the predicted values (by extracting the $fitted() component) against their residuals to look for patterns that suggest a poor fit. We can also plot the quantiles of the residuals against the quantiles of a theoretical normal distribution, using qqnorm() and qqline(), to see if they are normally distributed.



As we’re about to create a subplot for every predictor, and two for the residuals, I first divide the plotting device into 9 using the mfrow argument of the par() function. I set this back again using the same function.



```
par(mfrow = c(3, 3))
plot(gamModelData, type = "l")
plot(gamModelData$fitted(), resid(gamModelData))
qqnorm(resid(gamModelData))
qqline(resid(gamModelData))
par(mfrow = c(1, 1))
```

The resulting plot from code listing 10.5 is shown in figure 10.7. For each predictor we get a plot of its value, against how much that predictor contributes to the ozone estimate across its values. Lines show the shape of the functions learned by the algorithm, and we can see that they are all non-linear.