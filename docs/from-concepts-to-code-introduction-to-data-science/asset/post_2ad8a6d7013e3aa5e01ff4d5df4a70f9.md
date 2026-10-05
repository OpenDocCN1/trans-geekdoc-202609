
# A Simple Tool for Decision Making

which means somehow aggregating this data into a Go/No decision. This is the hard part. Do we count the number of pros and subtract the number of cons? This would assume that each attribute is equally important. We do say that family is ten times more important than each of the other attributes? Or is the number twenty? One hundred? It appears that some kind of weighting might play a role, or if each item carries an equal weight. At this point, some people change the weighting to make the decision for them. This might be obvious: increase one of the weights to the point where the decision is reached.

Let's recap and reflect on what we have learned. In making a decision, we collected relevant attributes instead of all of them, or risk making the wrong decision. We might have gathered some data and done some research. We might have reflected on past experience, but this was troublesome as our memories could fail us. Additionally, the experiment required us to predict how we would perceive related experiences in a different environment. Experiences vary far back in the past, they might not have been useful. Recency of data is valuable, as the world might have changed from long ago. Lastly, after classifying each attribute under the pros and cons, we follow the decision of how to weigh

I hope you can appreciate how hard this task is. At the same time, I hope you can start to see how machine learning might help. Now, machine learning is not going to tell us what we feel, but it might help us understand our feelings, and in a way that is consistent with our goals. How can we do this? We need to collect data, and we should keep only the data that is relevant. We still need to select the predictors. However, machine learning can be used to determine the optimal weights for any number of predictors. This will require data, a mathematical objective function, an algorithm, and a way for the algorithm to learn from the data. Depending on the algorithm, learning will differ, but in general it follows this path in the supervised learning we will discuss next.

1. Start with some weights, which are perhaps randomly assigned.
2. Using the weights and predictors, combine them to make a prediction. Each predictor might be multiplied by its weight, and then the terms can be summed.
3. Compare each prediction to the correct answer. For example, differences might be computed. This returns errors.
4. Change the weights to reduce a measure of the total error. The measure might be the sum of squared errors, for example.
5. Repeat 2-4 until we run out of permitted iterations or the experiment is marginal.

Now, let us discuss supervised learning in more detail. This is a classic machine learning approach that has wide applicability.

# Supervised Learning

Supervised learning (SL) uses $n$ data pairs $(x_1, y_1), (x_2, y_2), \dots, (x_n, y_n)$ to learn a function that can predict a target $y$ given $x$. We denote the labeled dataset as $\{(x_i, y_i)\}_{i=1}^n$. It is common in classification problems (which we discuss shortly) to refer to target values as *labels* or *ground truth values*. For a given observation $i$, the data pair $(x_i, y_i)$ is associated with a $d$-dimensional vector of predictors $x_i$, associated with the label $y_i$. When each observation has a label, we say that the dataset is labeled.

Taking a step back, we might ask if it is possible to avoid learning a function and take a simpler approach: why not use data as a lookup table? That is, if we were given a new $x$, could we look up the data pair for the right $x$, and return its $y$? There are some problems with this approach. First, the particular value of $x^*$ might not be in the dataset. Second, if $x^*$ is noisy, leading to an erroneous $y$. Third, for a large set of data pairs with possibly high-dimensional $x^*$, this motivates a function to handle the mapping for us. These shortcomings, it motivates us to learn from the data at hand, interpolate for new values of $x^*$, and complete much faster as it avoids lookup.

There are two kinds of supervised learning problems, and this depends on whether $y$ is a continuous– or discrete-valued variable. In the continuous case $y$ takes an uncountable number of values, the problem is a *regression problem*. An example is predicting the price of a house. In the discrete case $y$ takes a countable number of values, the problem is a *classification problem*. A common task is to predict an outcome with two possible values, or classes, such as:

- The patient recovers (positive class) or not (the negative class)
- A bank deposit is fraudulent (positive class) or not (negative class)
- A stock price rises over the next trading day (positive class) or not (negative class)

These examples are called *binary classification problems*. The positive class is assigned to the event of interest; it makes no judgment on good versus bad. Programmatically, the positive class is coded as 1, and the negative class as 0.

In the case the outcome has more than two possible values, it is called a *multiclass classification problem*. Examples might include predicting the fastest runner in a marathon, or the next number rolled on a six-sided die. Coding by numbering each class from zero to the total classes minus one. For the six-sided die, the classes would be 0, 1, $\dots$, 5.

# Unsupervised Learning

Supervised learning is a very powerful method for predicting outcomes, but it has some strong requirements. First, labeled data is required, and it must be accurate. Depending on the problem and the explanatory power of the predictors, the necessary dataset may be massive. Additionally, the labeled data needs to be relevant. Let's think about why this can be challenging. Consider a new product launch, where the task is to predict the number of units in the first month. Since the product is new, there is no data. Consider a product which has been on the market for ten years. There is an abundance of labeled data. Then the world is gripped by a pandemic, and demand surges. The historical database is now irrelevant. For these reasons, supervised learning might not work.

## 12.3 Unsupervised Learning

Unsupervised learning problems aim to understand the structure of data that is not labeled. In this case, we have collected a set of observations $\{X_1, X_2, \dots, X_n\}$ where $X_i$ is again a $d$-dimensional vector of predictors. As shorthand, we will denote the dataset as $\{X_i\}_{i=1}^n$. We can ask questions of this data as:

- Which of these data points are outliers? This can be used for outlier detection to flag suspicious activity, for example.
- If we wanted to group the data points, how should we group them?
- What are the underlying patterns or structures in the data?

Unsupervised learning is often used to find hidden patterns in data. One common method is clustering, which groups data points together based on similarity. Another is dimensionality reduction, which reduces the number of variables under consideration while preserving as much information as possible. A popular algorithm for clustering is $k$-means, which partitions the data into $k$ clusters.

## 12.4 Semi-supervised Learning

Semi-supervised learning (SSL) uses a combination of supervised and unsupervised learning. In some cases, we have a small amount of labeled data and a much larger amount of unlabeled data. SSL uses the unlabeled data to improve the performance of the supervised model. This is particularly useful when labeling data is expensive or time-consuming.

One approach is to use the unlabeled data to learn the structure of the data, and then use that structure to improve the model. Another approach is to use the supervised model to generate pseudo-labels for the unlabeled data, and then use those labels to retrain the model.

TABLE 12.1: Labeling data based on probabilities.

| Data Point | P(neg class) | P(pos class) | Action |
|---|---|---|---|
| 1 | 0.09 | 0.91 | Assign to positive class |
| 2 | 0.96 | 0.04 | Assign to negative class |
| 3 | 0.60 | 0.40 | Low confidence, do not assign |

## 12.5 Reinforcement Learning

In reinforcement learning (RL), an agent must decide on the best sequence of actions to maximize an objective. The agent begins in state $s_0$, takes action $a_1$, receives reward $r_1$, and transitions to the next state $s_1$. This continues until a stopping condition, generating tuples $(s_t, a_{t+1}, r_{t+1}, s_{t+1})$ which can be collected and used for training the system. For actions leading to good outcomes, the reward will be positive, while bad outcomes will produce
