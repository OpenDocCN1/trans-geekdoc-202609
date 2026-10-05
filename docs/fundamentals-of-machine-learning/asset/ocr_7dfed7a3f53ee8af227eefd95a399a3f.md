# Basic probability theory

knowledge into account which should bias our prediction downwards because it is less likely to rain than to rain. To apply Bayes, we also need to know how the meteorologist performs no rain, and let's assume that she is slightly better at predicting when it is not raining as she gets this 95 per cent of the times. That is

```
p(Y = \hat{f}|X = \hat{f}) = 0.95.
```

The last equations also implies that she rains in 5 per cent of the cases when it does not rain,

```
p(Y = r|X = \hat{f}) = 0.05.
```

We have all the components we need to find a solution to the above question using Bayes theorem,

Thus, we see that the actual probability that it is not raining if the meteorologist predicts it is less than we might have thought.

Taking the prior into account is an essential part in Bayesian reasoning. This will become clear in classification. For example, if we have a binary classification problem in which the positive is highly likely, 99 per cent, then always predicting the positive outcome would give us an accuracy of 0.99. Even though that seems good, a real success of a prediction system could considerable outperform this naive prediction.

This is an example of Bayesian modeling. We have made a model of two Bernoulli random variables

```
P(X = r) = p_{xr} and P(Y = r) = p_{yr}.
```

and the conditional distributions

```
P(X = r|Y = r) = p_{xyr} and P(X = r|Y = f) = p_{xyrf}.
```

and estimated parameters p_{xr}, p_{yr}, p_{xyrf} from data. Estimating the parameters for the learning part, and we will derive the procedure of using the ratio of previous values that is appropriate for this model. We then used this model with the rules of probability theory, specifically Bayes rule and the rule of total probability, to make predictions. This last step is sometimes called a statistical inference. We will formalize the process of how to learn the parameters of the model in the next chapter, and we will discuss the process of Bayesian modeling with associated tools in Chapter 8.

Let us consider a second example that should help us appreciate the usefulness and difficulty with Bayes rule. Let us assume we have a robot for which we want to estimate the distance to a wall from sensor readings. For example, we might know from the integration of our previous path that we are a distance of x away from a wall