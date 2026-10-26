```
odds = prob / (1 - prob)
print('Odds %.1f' % odds)
# convert odds to log-odds
logodds = log(odds)
print('Log-Odds %.1f' % logodds)
# convert log-odds to a probability
prob = 1 / (1 + exp(-logodds))
print('Probability %.1f' % prob)
```

Listing 13.3: Example of converting between probability and log odds.

Running the example, we can see that our odds are converted into the log odds of about 1.4 and then correctly converted back into the 0.8 probability of success.

```
Probability 0.8
Odds 4.0
Log-Odds 1.4
Probability 0.8
```

Listing 13.4: Example output from converting between probability and log odds.

Now that we have a handle on the probability calculated by logistic regression, let’s look at maximum likelihood estimation.

# 13.4 Maximum Likelihood Estimation

Maximum Likelihood Estimation, or MLE for short, is a probabilistic framework for estimating the parameters of a model (introduced in Chapter 11). In Maximum Likelihood Estimation, we wish to maximize the conditional probability of observing the data (X) given a specific probability distribution and its parameters (θ), stated formally as:

P(X; θ)  (13.14)

Where X is, in fact, the joint probability distribution of all observations from the problem domain from 1 to n.

P(x₁, x₂, x₃, …, xₙ; θ)  (13.15)

This resulting conditional probability is referred to as the likelihood of observing the data given the model parameters and written using the notation L() to denote the likelihood function. For example:

L(X; θ)  (13.16)

The joint probability distribution can be restated as the multiplication of the conditional probability for observing each example given the distribution parameters. Multiplying many small probabilities together can be unstable; as such, it is common to restate this problem as the sum of the log conditional probability.

∑ᵢ₌₁ⁿ log P(xᵢ; θ)  (13.17)