

Say you want to predict the price of a house based on its features, such as number of bedrooms, square feet area, and so on.

You start by assuming a value for K. Usually, this value for K is obtained through trial and error. You need to learn some metrics, such as utility and distance, to measure the distance between the actual houses in the dataset and the new house for which you need to make a prediction.

Once you identify the five closest houses, you can take the average price to come up with a new prediction. Of course, this prediction assumes that houses with similar features will have similar pricing.

When the value of K is small, it's possible that your price is susceptible to the outliers and noise in the dataset. If you choose a higher value for K, the outcome may be influenced by houses dissimilar to your new house.

In practice, KNN is an excellent algorithm to be chosen for applications such as product recommendations, image classification, and anomaly detection.

KNN is a good candidate under the following conditions:

| CONDITION DESCRIPTION | EXAMPLE | ALTERNATIVES |
|---|---|---|
| Labeled, structured data<br>The dataset should be labeled and ideally have structured data. | Ideal for datasets where each instance is tagged with a label | Unsupervised learning algorithms for unlabeled data |
| Small and medium sized datasets<br>Works best with small to medium-sized datasets; larger datasets can become computationally intensive. | Not recommended for very large datasets due to high computational cost | Decision tree, random forest, or gradient boosting for large datasets |
| Classification and regression only<br>Suitable for problems that involve classification or regression. | Not suitable for problems that don't involve classification or regression tasks | Deep learning or reinforcement learning for complex tasks |
| Not for real-time inference<br>Suitable for situations where you can train offline and deploy it online. If real-time online performance is essential, other models should be explored. | Not ideal for situations requiring real-time predictions | Random forests or gradient boosting machines (GBMs) for real-time predictions |
| Explainability<br>A good model when explainability is required, as predictions can be easily traced. | Helpful when it's necessary to explain the decision-making process | Decision tree, logistic regression for explainability |

> **TIP** Use KNN in classification or regression tasks for small to medium-sized, structured, and labeled datasets. It is essential to select an appropriate value for K to balance between noise sensitivity and the included dissimilar data points.

## Data Analysis and Predictive Modeling Using Neural Networks

Here are the conditions under which neural networks are recommended:

| CONDITION | DESCRIPTION | EXAMPLE |
|---|---|---|
| Large data | Suitable for very large amounts of data | Data-intensive fields like genomic research or social network analysis |
| Complex pattern analysis | Particularly well suited to analyze complex patterns in data | Image or speech recognition tasks |
| Predictive modeling | Well suited for predictive modeling to make accurate predictions based on historical data | Predictive maintenance or forecasting sales |
| Real-time CNN use cases | Can be used for convolutional neural network (CNN) use cases that require real-time decisions | Autonomous vehicles or real-time financial trading |
| Large-scale cloud AI | Well suited for large-scale enterprise cloud AI implementations | Allows workload distribution across multiple servers and GPUs for speedier training and inference |

Refer to the section “Deep Learning” in this chapter for more details.

> **TIP** Consider using neural networks for large datasets, complex pattern analysis, predictive modeling, real-time CNN tasks, or large-scale cloud AI deployments.

## Using Unsupervised Learning to Discover Patterns in Unlabeled Data

Next is unsupervised learning, where the data is not labeled, and therefore, it is up to the algorithm to find common patterns, as shown in Figure 16.13.

Machine discovers and creates the labels itself.

![](img/1490b3cf638678afadc8c48abc1698d5_423_0.png)

FIGURE 16.13: How unsupervised learning works

There are two types of unsupervised learning applications: clustering and anomaly detection.

### Clustering

An excellent example of a clustering application is when you have a large amount of customer data. You use this algorithm to break the data into multiple segments based on buying patterns and other attributes. You could then analyze those different segments and identify one of those as college students or moms, and so on, and then tailor your products and services based on which customer segments you are marketing to.

Another example of clustering applications is topic modeling. For example, you can feed the content from multiple books into this algorithm, generate topics, and classify those books into different categories.

### Anomaly Detection

Anomaly detection is used to detect anomalies in data. In other words, look for patterns that do not conform to expected behavior. It is of great use in the case of fraud detection in customer transactions, such as an unusually large number of purchases in a foreign country or abnormal patient readings indicating a potentially serious health condition.

The following table summarizes the different types of unsupervised learning algorithms:

| UNSUPERVISED LEARNING APPLICATION | DESCRIPTION | EXAMPLE |
|---|---|---|
| Clustering | Clustering algorithms divide a dataset into groups or clusters, based on similarity in the data features. | Customer segmentation or topic modeling |
| Anomaly detection | Anomaly detection algorithms identify outliers in the data that do not conform to the expected patterns. | Fraud detection or abnormal patient readings in healthcare |

> **TIP** Use unsupervised learning when dealing with unlabeled data to discover hidden patterns. Clustering helps with grouping similar data, while anomaly detection uncovers outliers useful in fraud detection or health diagnostics.

## Segmentation Using K-Means Clustering

K-means clustering is an unsupervised algorithm that groups data points into clusters, as shown in Figure 16.14.

## K-Means Clusters

![](img/1490b3cf638678afadc8c48abc1698d5_425_0.png)

**FIGURE 16.14:** K-means clusters created from an Iris flower dataset

Source: Wikipedia

The algorithm starts by randomly assigning K cluster centers and then attaching the remaining data points to one of the clusters closer to it. Then the cluster centers are recomputed by calculating the mean of all the data points attached to that cluster center. The process is then repeated until the cluster centers do not change anymore.

K-means clustering is helpful for image segmentation, customer segmentation, fraud detection, and anomaly detection.

These are the conditions under which K-means clustering can be adopted:

| SITUATION | DESCRIPTION | USE CASE EXAMPLE |
|---|---|---|
| Large data | You have a large amount of data to be processed. | Analyzing massive user datasets in social media platforms |
| Unlabeled data | The data is not labeled. | Segmenting a database of consumer details without pre-established categories |
| Pattern analysis | When you want to identify patterns in the data. | Identifying common buying patterns in retail consumer data |
| Segmentation use cases | There is a need for segmentation of customers, products, or any other entity. | Segmenting customers into distinct groups based on purchasing behavior |
| Process optimization | You want to optimize processes by identifying inefficiencies or areas of improvement. | Identifying inefficient processes in a manufacturing line |
| Uncorrelated data | Useful when the data is not highly correlated. | Clustering unrelated blog posts based on topics |
| Unknown number of clusters | Ideally, the number of clusters is not known. | Organizing news articles into categories without pre-established groups |

> **TIP** Use K-means clustering for large, unlabeled datasets where the number of clusters is unknown and the data is not highly correlated. It's useful for tasks like customer segmentation and process optimization.

## Reducing Dimensions Using Principal Component Analysis

Principal component analysis reduces the dimensionality of a large dataset by identifying the underlying patterns and reducing the number of features. It does this by transforming the original features into a new set of uncorrelated variables called principal components. And it does this without losing much of the original information in the dataset. Since it deals with data that does not have labeled examples or explicit target variables, it is appropriate for exploratory data analysis and feature extraction.

> **NOTE** Given that PCA doesn't use labels, it is considered an unsupervised learning technique.

Say you have product data served with a lot of information, such as sales history and specifications of the product, such as its color, size, shape, and so on. Each row represents a product, and each column is an attribute of the product. However, the dataset is so large that making any sense of that data is becoming difficult. Follow these steps to use PCA:

| STEP | DESCRIPTION | USE CASE EXAMPLE |
| :--- | :--- | :--- |

