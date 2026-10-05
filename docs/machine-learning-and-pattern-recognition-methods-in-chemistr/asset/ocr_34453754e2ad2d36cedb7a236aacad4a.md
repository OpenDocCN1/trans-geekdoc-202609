# K-means Clustering

![](bbox=[0.218, 0.123, 0.79, 0.353])

**A.3** The obtained clusters of the k_means algorithm on the IRIS dataset.

```
plt.scatter(data_reduced[idx,0],data_reduced[idx,1],color='red')
idx = np.where(kmeans.labels_==2)
plt.scatter(data_reduced[idx,0],data_reduced[idx,1],
color='purple')
plt.gca().settitle="K-means Clusterig",
xlabel='Feature1', ylabel='Feature2')
plt.legend()
plt.show()
```

where the "kmeans.labels_" shows the assigned cluster numbers to each data. The result of the above code is shown in Fig. A.3.

By comparing Fig. A.1 with Fig. A.3, it is concluded that k_means clustering is reliable on this dataset.

In Chapter 3, machine learning and pattern recognition methods in chemistry from multivariate and data-driven modeling are investigated. Also, many algorithms including linear regression, logistic regression, SVM, random forest, neural network (both for classification and for regression), and deep convolutional neural network (both for classification and for regression) are implemented on molecular property prediction by using DeepChem and scikit-learn (i.e., sklearn) packages. In the following, codes of these algorithms are given, and for each part of code, there are useful comments that explain the function of that part of code.