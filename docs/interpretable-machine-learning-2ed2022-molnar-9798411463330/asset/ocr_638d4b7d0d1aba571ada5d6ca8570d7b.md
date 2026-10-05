# 4.3 GLM, GAM AND MORE

someone on a certain day, we could model it with a GLM with a Poisson distribution and the natural logarithm as the link function:

```
$$\ln(E_y(y|x)) = x^T\beta$$
```

The logistic regression model is also a GLM that assumes a Bernoulli distribution and uses the log function as the link function. The mean of the binomial distribution used in logistic regression is the probability that y is 1.

```
$x^T\beta = \ln\left(\frac{E_y(y|x)}{1-E_y(y|x)}ight) = \ln\left(\frac{P(y=1|x)}{1-P(y=1|x)}ight)$
```

And if we solve this equation to have P(y=1) we get the logistic regression formula:

```
$P(y=1) = \frac{1}{1+exp(-x^T\beta)}$
```

Each distribution from the exponential family has a canonical link function that can be derived mathematically from the distribution. The GLM framework makes it possible to choose the link function independently of the distribution. How to choose the right link function? There is no perfect recipe. You take into account knowledge about the distribution of your target, also theoretical considerations and how well the model fits your data. For some distributions the canonical link function can lead to values that are ideal for that distribution. In the case of the exponential distribution, the canonical link function is the negative inverse, which can lead to negative predictions that are outside the domain of the exponential distribution. Since you can choose any link function, the simple solution is to choose another function that respects the domain of the distribution.

# Examples

I have simulated a dataset on coffee drinking behavior to highlight the need for GLMs. You have collected data about your daily coffee drinking behavior. If you do not drink coffee, it is about tea. Along with number of cups, you record your current stress level on a scale of 1 to 10, how well you slept before on a scale of 1 to 10 and whether you had to work on day. The goal is to predict the number of coffees given the features stress sleep and work. I simulated data for 200 days. Stress and sleep were drawn uniformly between 1 and 10 and for each day, the number of coffees was drawn from a Poisson distribution, modelling the intensity $\lambda$ (which is also the expected value of the Poisson distribution) as a function of the features sleep, stress and work. You can guess what this story will tell: "Hey, let us model this data with a linear model ... Oh it does not work ... Let us try a GLM with Poisson distribution ... SURPRISE! Now it works! I hope I did not spoil the story too much for you.

Let us look at the distribution of the target variable, the number of coffees on a given day: