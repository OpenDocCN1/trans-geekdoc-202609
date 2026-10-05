# A Simple Tool for Decision Making

which means somehow aggregating this data into a Go/No decision. This is the hard part. Do we count the number of pros and subtract the number of cons? This would assume that each attribute is equally important. We do say that family is ten times more important than each of the other attributes? Or is the number twenty? One hundred? It appears that some kind of weighting might play a role, or if each item carries an equal weight. At this point, some people change the weighting to make the decision for them. This might be obvious. increase one of the weights to the point where the decision is reached.

Let's recap and reflect on what we have learned. In making a decision, we collected relevant attributes instead all of them, or risk making the wrong decision. We might have gathered some data and done some research. We might have reflected on past experience, but this was troublesome as our memories could us. Additionally, the experiment required us to predict how we would perceive related experiences in a different environment. Experiences vary far back in the past, they might not have been useful. Recency of data is valuable, as the world might have changed from long ago. Lastly, after classifying each attribute under the pros and cons, we follow the decision of how to weigh

I hope you can appreciate how hard this task is. At the same time, I hope you can start to see how machine learning might help. Now, machine learning is not going to tell us what we feel, but it might help us understand our feelings, and in a way that is consistent with our goals. How can we do this? We need to collect data, and we should keep only the data that is relevant. We still need to select the predictors. However, machine learning can be used to determine the optimal weights for any number of predictors. This will require data, a mathematical objective function, an algorithm, and a way for the algorithm to learn from the data. Depending on the algorithm, learning will differ, but in general it follows this path in the supervised learning we will discuss next.

+   1. Start with some weights, which are perhaps randomly assigned
2. Using the weights and predictors, combine them to make a prediction. Each predictor might be multiplied by its weight, and then the terms can be summed.
3. Compare each prediction to the correct answer. For example, differences might be computed. This returns errors.
4. Change the weights to reduce a measure of the total error. The measure might be the sum of squared errors, for example.
5. Repeat 2-4 until we run out of permitted iterations or the experiment is marginal

Now, let us discuss supervised learning in more detail. This is classic machine learning approach that has wide applicability.