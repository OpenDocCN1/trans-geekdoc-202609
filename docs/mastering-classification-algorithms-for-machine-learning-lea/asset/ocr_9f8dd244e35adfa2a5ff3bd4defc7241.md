times, the chance of obtaining tails is 4,900 times. Notice that our conclusion is clearly distinguished as we increase the number of times we toss the coin.

Ensembles work in the same way. Suppose we have several classifiers that produce better results than the random guess. Then, when we create ensembles with sufficient data points using these classifiers and take the majority from the results, the ensembles generally provide more than 75% accuracy. The critical point to note is that we need to have sufficient data points. In statistics, this is called the Law of large numbers.

# Different types of Ensemble models

There are many types of ensemble models. We will focus on four types of ensemble models, that is, Voting, Bagging, Boosting, and Stacking.

# Voting ensemble models

In the Voting ensemble model, we subject the same data to several models built using different algorithms. Then, we make predictions from each model separately and take the decision provided by the maximum number of models.

In Figure 6.2, we see how Voting ensemble models work. We can build 3 different models on the same input data:

![](bbox=[0.137, 0.565, 0.863, 0.833])

> "Class A" got 2 votes and "Class B" got 1 vote and thus choose "Class A" as our decision.

Figure 6.2: Simplified example of Voting ensemble