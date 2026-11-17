
Remember, your testing data must follow the same data distribution as your training data, and you are very likely to find all (or at least most) of the categories (of a categorical feature) either in the training or testing sets. Furthermore, if you are facing overfitting issues (doing well in the training, but poorly in the testing set) and, at the same time, you realize that your categorical encoders are transforming a lot of unknown values in the test set, guess what? It's likely that your training and testing samples are not following the same distribution, invalidating your model entirely.

As you can see, slowly, you are getting there. You are learning about bias and investigation strategies in fine-grained detail – that is so exciting! Now, move on and look at performing transformations on numerical features. Yes, each type of data matters and drives your decisions.

## Dealing with numerical features

In terms of numerical features (discrete and continuous), you can think of transformations that rely on the training data and others that rely purely on the (individual) observation being transformed.

Those who rely on the training data will use the training set to learn the necessary parameters during fit, and then use them to transform any test or new data. The logic is pretty much the same as what you just learned for categorical features; however, this time, the encoder will learn different parameters.

On the other hand, those that rely purely on (individual) observations do not depend on training or testing sets. They will simply perform a mathematical computation on top of an individual value. For example, you could apply an exponential transformation to a particular variable by squaring its value. There is no dependency on learned parameters from anywhere – just get the value and square it.

At this point, you might be thinking about dozens of available transformations for numerical features! Indeed, there are so many options, and you will not learn all of them here. However, you are not supposed to know all of them for the AWS Machine Learning Specialty exam. You will learn the most important ones (for the exam), but you should not limit your modeling skills: take a moment to think about the unlimited options you have by creating custom transformations according to your use case.

## Data normalization

Applying data normalization means changing the scale of the data. For example, your feature may store employee salaries that range between 20,000 and 200,000 dollars/year and you want to put this data in the range of 0 and 1; where 20,000 (the minimum observed value) will be transformed as 0; and 200,000 (the maximum observed value) will be transformed as 1.

This type of technique is especially important when you want to fit your training data on top of certain types of algorithms that are impacted by the scale/magnitude of the underlying data. For instance, you can think about those algorithms that use the dot product of the input variables (such as neural networks or linear regression) and those algorithms that rely on distance measures (such as k-nearest neighbors (KNN) or k-means).

On the other hand, applying data normalization will not result in performance improvements for rule-based algorithms, such as decision trees, since they will be able to check the predictive power of the features (either via entropy or information gain analysis), regardless of the scale of the data.

## IMPORTANT NOTE

You will learn about these algorithms, along with the appropriate details, in the later chapters of this book. For instance, you can look at entropy and information gain as two types of metrics used by decision trees to check feature importance. Knowing the predictive power of each feature helps the algorithm define the optimal root, intermediaries, and leaf nodes of the tree.

Take a moment and use the following example to understand why data normalization will help those types of algorithms. You already know that the goal of a clustering algorithm is to find groups or clusters in your data, and one of the most used clustering algorithms is known as k-means.

Figure 4.2 shows how different scales of the variable could change the hyper plan's projection of k-means clustering:

![](img/87c29232224b00f5a8bba6a66a391700_100_0.png)

Figure 4.2 – Plotting data of different scales in a hyper plan

On the left-hand side of Figure 4.2, you can see a single data point plotted in a hyper plan that has three dimensions (x, y, and z). All three dimensions (also known as features) were normalized to the scale of 0 and 1. On the right-hand side, you can see the same data point, but this time, the x dimension was not normalized. You can clearly see that the hyper plan has changed.

In a real scenario, you would have far more dimensions and data points. The difference in the scale of the data would change the centroids of each cluster and could potentially change the assigned clusters of some points. This same problem will happen on other algorithms that rely on distance calculation, such as KNN.

Other algorithms, such as neural networks and linear regression, will compute weighted sums using your input data. Usually, these types of algorithms will perform operations such as W1*X1 + W2*X2 + Wi*Xi, where Xi and Wi refer to a particular feature value and its weight, respectively. Again, you will learn details of neural networks and linear models later, but can you see the data scaling problem by just looking at the calculations that were just described? It can easily come up with very large values if X (feature) and W (weight) are large numbers. That will make the algorithm's optimizations much more complex. In neural networks, this problem is known as gradient exploding.

You now have a very good understanding of the reasons you should apply data normalization (and when you should not). Data normalization is often implemented in ML libraries as Min Max Scaler. If you find this term in the exam, then remember that it is the same as data normalization.

Additionally, data normalization does not necessarily need to transform your feature into a range between 0 and 1. In reality, you can transform the feature into any range you want. Figure 4.3 shows how normalization is formally defined.

![](img/87c29232224b00f5a8bba6a66a391700_101_0.png)

Figure 4.3 – Normalization formula

Here, Xmin and Xmax are the lower and upper values of the range; X is the value of the feature. Apart from data normalization, there is another very important technique regarding numerical transformations that you must be aware of, not only for the exam but also for your data science career. You'll look at this in the next section.

## Data standardization

Data standardization is another scaling method that transforms the distribution of the data, so that the mean will become 0 and the standard deviation will become 1. Figure 4.4 formally describes this scaling technique, where X represents the value to be transformed, μ refers to the mean of X, and σ is the standard deviation of X:

![](img/87c29232224b00f5a8bba6a66a391700_101_1.png)

Figure 4.4 – Standardization formula

Unlike normalization, data standardization will *not* result in a predefined range of values. Instead, it will transform your data into a standard Gaussian distribution, where your transformed values will represent the number of standard deviations of each value to the mean of the distribution.

## IMPORTANT NOTE

*The Gaussian distribution, also known as the normal distribution, is one of the most used distributions in statistical models. This is a continuous distribution with two main controlled parameters: μ (mean) and σ (standard deviation). Normal distributions are symmetric around the mean. In other words, most of the values will be close to the mean of the distribution.*

Data standardization is often referred to as the zscore and is widely used to identify outliers on your variable, which you will see later in this chapter. For the sake of demonstration, Table 4.7 simulates the data standardization of a small dataset. The input value is shown in the Age column, while the scaled value is shown in the Zscore column:

| Age | Mean | Standard deviation | Zscore |
| --- | --- | --- | --- |
| 5 | 31.83 | 25.47 | -1.05 |
| 20 | 31.83 | 25.47 | -0.46 |
| 24 | 31.83 | 25.47 | -0.31 |
| 32 | 31.83 | 25.47 | 0.01 |
| 30 | 31.83 | 25.47 | -0.07 |
| 80 | 31.83 | 25.47 | 1.89 |

Table 4.7 – Data standardization in action

Make sure you are confident when applying normalization and standardization by hand in the AWS Machine Learning Specialty exam. They might provide a list of values, as well as mean and standard deviation, and ask you for the scaled value of each element in the list.

## Applying binning and discretization

**Binning** is a technique where you can group a set of values into a bucket or bin – for example, grouping people between 0 and 14 years old into a bucket named “children,” another group of people between 15 and 18 years old into a bucket named “teenager,” and so on.
