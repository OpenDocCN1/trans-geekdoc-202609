# Unsupervised Learning

Supervised learning is a very powerful method for predicting outcomes, but it has some strong requirements. First, labeled data is required, and it must be accurate. Depending on the problem and the explanatory power of the predictors, the necessary dataset may be massive. Additionally, the labeled data needs to be relevant. Let's think about why this can be challenging. Consider a new product launch, where the task is to predict the number of units in the first month. Since the product is new, there is no data. Consider a product which has been on the market for ten years. There is an abundance of labeled data. Then the world is gripped by a pandemic, and demand surges. The historical database is now irrelevant. For these reasons, supervised learning might not work.

# 12.3 Unsupervised Learning

Unsupervised learning problems aim to understand the structure of data that is not labeled. In this case, we have collected a set of observations $\{X_1, X_2, \dots, X_n\}$ where $X_i$ is again a $d$-dimensional vector of predictors. As shorthand, we will denote the dataset as $\{X_i\}_{i=1}^n$. We can ask questions of this data as:

+   - Which of these data points are outliers? This can be used for outlier detection to flag suspicious activity, for example.
- If we wanted to group the data points according to some distance metric, how should they best grouped? This can help discover substructure to understand different persons in the data, for example.
- For a new data point, which group provides the best fit? For example, in an ideal case, we might find that bank transactions form two groups: fraudulent transactions and non-fraudulent transactions. The new data point, based on the values of the predictors, might clearly belong to the non-fraudulent group.

Unsupervised learning can often be an iterative procedure, as algorithms require parameters such as the number of groups which often are unknown in advance. In some cases, the grouping can be used as a new variable in analysis. The most popular algorithm for unsupervised learning is $k$-means, and we will discuss this in detail later.