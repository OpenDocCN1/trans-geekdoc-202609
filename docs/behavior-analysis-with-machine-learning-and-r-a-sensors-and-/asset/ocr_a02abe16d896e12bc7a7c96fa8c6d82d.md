# Students Responses

![](bbox=[0.163, 0.189, 0.756, 0.413])

Figure 6.3: Students responses projected into 2D with MDS.

```
clusters <- kmeans(normdf, 4)
```

The first argument of kmeans() is a data frame or a matrix and the second argument is the number of clusters. Figure 6.4 shows the resulting clustering. The kmeans() method returns an object that contains several components including cluster that stores the assigned cluster for each data point and centers that stores the centroids.

The k-means algorithm finds the same clusters as we would intuitively expect. We can check how different the groups are by inspecting some of the variables. For example, by plotting a boxplot of the Intimate variable (Figure 6.5). This variable is 1 if the student has an intimate partner or 0 otherwise. Since there are only two possible values the boxplot looks flat. This shows that cluster_1 and cluster_3 are different from cluster_2 and cluster_3.

Additionally, let's plot the ACS variable which represents the total score of cluster shock. This has a minimum value of 3 and a max value of 13.

cluster_2 and cluster_4 were similar based on the Intimate variable but if we take a look at the difference in medians based on ACS, cluster_2 and cluster_4 are the most dissimilar