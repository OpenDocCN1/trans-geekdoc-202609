Say you want to predict the price of a house based on its features, such as number of bedrooms, square feet area, and so on.

You start by assuming a value for K. Usually, this value for K is obtained through trial and error. You need to learn some metrics, such as utility and distance, to measure the distance between the actual houses in the dataset and the new house for which you need to make a prediction.

Once you identify the five closest houses, you can take the average price to come up with a new prediction. Of course, this prediction assumes that houses with similar features will have similar pricing.

When the value of K is small, it's possible that your price is susceptible to the outliers and noise in the dataset. If you choose a higher value for K, the outcome may be influenced by houses dissimilar to your new house.

In practice, KNN is an excellent algorithm to be chosen for applications such as product recommendations, image classification, and anomaly detection.

KNN is a good candidate under the following conditions:

| CONDITION DESCRIPTION | EXAMPLE | ALTERNATIVES |
|---|---|---|
| Labeled, structured data
The dataset should be labeled and ideally have structured data. | Ideal for datasets where each instance is tagged with a label | Unsupervised learning algorithms for unlabeled data |
| Small and medium sized datasets
Works best with small to medium-sized datasets; larger datasets can become computationally intensive. | Not recommended for very large datasets due to high computational cost | Decision tree, random forest, or gradient boosting for large datasets |
| Classification and regression only
Suitable for problems that involve classification or regression. | Not suitable for problems that don't involve classification or regression tasks | Deep learning or reinforcement learning for complex tasks |
| Not for real-time inference
Suitable for situations where you can train offline and deploy it online. If real-time online performance is essential, other models should be explored. | Not ideal for situations requiring real-time predictions | Random forests or gradient boosting machines (GBMs) for real-time predictions |
| Explainability
A good model when explainability is required, as predictions can be easily traced. | Helpful when it's necessary to explain the decision-making process | Decision tree, logistic regression for explainability |