# Figure 5. Performance Comparison of Clustering Implementations

![](bbox=[0.145, 0.135, 0.855, 0.385])

Figure 5 clearly shows that the K-Means algorithm fares well in terms of scalability that is of utmost importance in this application since the number of data points increases rather rapidly. Based on the above results, K-Means clustering is selected as the ideal candidate as the clustering algorithm for the recommender system.

# K-Means Algorithm in Hospital Clustering

+   1. Select k number of clusters.
+   2. Select k number of centroids at random from the data set of hospitals.
+   3. Calculate proximity to each of these centroids from the hospital by determining the Euclidean distance d between them.

```
d=√((s₁-s₂)²+(l₁-l₂)²+(t₁-t₂)²+(a₁-a₂)²+(c₁-c₂)²+(f₁-f₂)²+(r₁-r₂)²)   (1)
```

Here the subscripts (1) represent the values of the centroid and subscript (2) represents the value of attributes for the data point that is the hospital to be clustered.

+   s = Specialization (categorical variable)
+   l = Location
+   t = Threshold Rating
+   a = Average cost of treatment
+   c = Capacity
+   f = Fatalities