the training error rate decreases, but the testing error rate increases after a given number of epochs

reducing the model's complexity improves test performance.

Signs of underfitting include:
- the model performs poorly on both the training and test data sets
- a simple model is used, with minimal features
- there are insufficient features to adequately capture the characteristics of the data
- increasing complexity or adding features improves test performance.

# A4.3.4 Unsupervised learning:
clustering techniques

To review, unsupervised learning is where the data set your model is trained on is unlabelled. That is, you don't supply the correct answer that corresponds with each datum you supply. Rather than looking for data that is similar to known answer values, the features of the unlabelled data are compared for similarities among them all, with the goal of identifying naturally forming clusters in the groupings of data.

Clustering techniques: where data is grouped into clusters based on similarity or proximity to each other without any labels provided to help indicate the correctness of associating any individual datapoint to the cluster assigned.

# K-means clustering

K-nearest neighbours is very commonly used for unsupervised clustering, in addition to the supervised learning approaches already considered.

With the supervised approach, when a new, unlabelled data point is introduced, the algorithm measures the distance (often Euclidean) from the new point to all those in the training set. From there, it identifies the nearest neighbours to assign a predictive label to the new value. With the unsupervised approach, when a new data point is introduced, the algorithm similarly measures distances to other data points to determine its nearest neighbours but, instead of predicting a label, it uses these relationships to identify the groupings, or clusters, within the entire data set.

The main weakness with a KNN approach is that it assumes clusters are spherical and of similar size, making it sensitive to initial centroids and outliers.

![](bbox=[0.285, 0.625, 0.89, 0.735])

K-means clustering with one dimension

In this example, k-means clustering has been used to determine grade boundaries for a cohort of 200 students. Asked to cluster the grades into six buckets, one for each letter grade, the algorithm determined the following boundaries:

+   - A: 83.48 to 100
+   - B: 72.74 to 83.48
+   - C: 64.45 to 72.74
+   - D: 56.30 to 64.45
+   - E: 47.09 to 56.30
+   - F: 0 to 47.09