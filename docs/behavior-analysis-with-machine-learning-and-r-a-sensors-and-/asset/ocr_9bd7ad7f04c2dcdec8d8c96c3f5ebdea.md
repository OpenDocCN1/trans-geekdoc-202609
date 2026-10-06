# 2.7 Summary

This chapter focused on classification models. Classifiers predict a category based on the input features. Here, we showed how classifiers can be used to detect indoor locations, classify activities and had gestures.

+   * *k-nearest neighbors (k-nn)* predicts the class of a test point as the majority class of the *k* nearest neighbors.
* Some classification performance metrics are **recall, specificity, precision, accuracy, F1-score**, etc.
* **Decision trees** are easy-to-interpret classifiers trained recursively based on feature importance (for example, purity).
* **Naive Bayes** is a type of classifier where features are assumed to be independent.
* **Dynamic Time Warping (DTW)** computes the similarity between two timeseries after ‘aligning’ them in time. This can be used for classification for example, in comination with *k*-nn.
* **Dummy models** can help to spot possible errors in the data and can also be used as baselines.