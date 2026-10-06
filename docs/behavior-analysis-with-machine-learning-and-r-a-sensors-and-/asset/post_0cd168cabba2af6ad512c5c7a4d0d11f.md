
## Chapter 6

## Discovering Behaviors with Unsupervised Learning

So far, we have been working with supervised learning methods, that is, models for which the training instances have two elements: 1) a set of input values (features) and 2) the expected output (label). As mentioned in chapter 1, there are other types of machine learning methods and one of those is unsupervised learning which is the topic of this chapter. In unsupervised learning the training instances do not have a response variable (e.g., a label). Thus, the objective is to extract knowledge from the available data without any type of guidance (supervision). For example, given a set of variables that characterize a person, we would like to find groups of people with similar behaviors. For physical activity behaviors, this could be done by finding groups of very active people versus groups of people with low physical activity. Those groups can be useful for delivering appropriate suggestions to each group, thus, enhancing and personalizing the user experience.

This chapter starts with one of the most popular unsupervised learning algorithms: kmeans clustering. Then, an example of how this technique can be applied to find groups of students with similar characteristics is presented. Then, association rules are presented which is another type of unsupervised learning. Finally, association rules are used to find criminal patterns in a database.

### 6.1 K-means clustering

```
kmeans_steps.R
```

This is one of the most commonly used unsupervised methods due to its simplicity and efficacy. Its objective is to find groups of points such that points in the same group are similar and points from different groups are as dissimilar as possible. The number of groups k needs to be defined a priori. The method is based on computing distances to centroids. The centroid of a set of points is computed by taking the mean of each its features. The k-means algorithm is as follows:

1. Generate k centroids at random.
2. Repeat until no change or max iterations:
    - Assign each data point to the closest centroid.
    - Update centroids.

Measure the distance between a data point and a centroid, the Euclidean distance is typically used but other distances can be used as well depending on the application. As an example let's cluster user responses from the STUDENTS' MENTAL HEALTH dataset. Demonstrate how k-means works, we choose only two variables to group into 3 disjoint groups. The variables are ToAS (total accumulated stress) and ToSC (total social connectedness). The code that implements the k-means algorithm can be found in the script kmeans_steps.R. The algorithm begins by selecting 3 centroids at random. Figure 6.1 shows a scatterplot of ToAS and ToSC along with the random centroids.

Next, at the first iteration, each point is assigned to the closest centroid. This is depicted in Figure 6.2 (top left). Then, the centroids are updated (moved) based on the new assignments. In the next iteration, the centroids are reassigned to the closest centroids and so on. Figure 6.2 shows the first 4 iterations of the algorithm.

From iteration 1 to 2 the centroids moved considerably. After that, they began to stabilize. Formally, the algorithm tries to minimize the within cluster variation of all clusters. The cluster variation of a single cluster $C_k$ is defined as:

> $W(C_k) = \sum_{x_i \in C_k} (x_i - \mu_k)^2 \quad (6.1)$

where $x_i$ is a data point and $\mu_k$ is the centroid of cluster $C_k$. Thus, the total cluster variation TWCV is:

> $TWCV = \sum_{i=1}^k W(C_i) \quad (6.2)$

#### Initial random centroids

![](img/91c149cc24c3e5af2971580c9dda9d8b_188_0.png)

Figure 6.1: 3 centroids chosen randomly.

that is, the sum of all within-cluster variations across all clusters. The objective is to find the $\mu_k$ centroids that make TWCV minimal. Finding the global optimum is a difficult problem. However, the iterative algorithm described above often produces good approximations.

### 6.1.1 Grouping Student Responses

```
group_students.R
```

In the previous example, we only used two variables to perform the clustering. Let’s now use more variables from the STUDENTS' MENTAL HEALTH dataset to find groups. The full code can be found in `group_students.R`. After removing missing values, one-hot encoding categorical variables, and some additional cleaning, the following 10 variables were selected:

![](img/91c149cc24c3e5af2971580c9dda9d8b_189_0.png)
![](img/91c149cc24c3e5af2971580c9dda9d8b_189_1.png)
![](img/91c149cc24c3e5af2971580c9dda9d8b_189_2.png)
![](img/91c149cc24c3e5af2971580c9dda9d8b_189_3.png)

Figure 6.2: First 4 iterations of k-means.

```
selvars <- c("Stay", "English_cat", "Intimate"
      , "APD", "AHome", "APH", "Afear"
      , "ACS", "AGuilt", "ToAS")
```

Additionally, it is advisable to normalize the data between 0 and 1 since we are dealing with distance computations and we want to put the same weight on each variable. To plot the 10 variables, we can use MDS (described in chapter 4) to project the data into 2 dimensions (Figure 6.3).

Visually, it seems that there are 4 distinct groups of points. Based on this initial guess, we can set k = 4 and use the kmeans() function included in base R to find the groups automatically.

#### Students Responses

![](img/91c149cc24c3e5af2971580c9dda9d8b_190_0.png)

Figure 6.3: Students responses projected into 2D with MDS.

```
clusters <- kmeans(normdf, 4)
```

The first argument of kmeans() is a data frame or matrix and the second argument is the number of clusters. Figure 6.4 shows the resulting clustering. The kmeans() method returns an object that contains several components including cluster that stores the assigned cluster for each data point and centers that stores the centroids. This finds clusters as we intuitively expect. We can check how different the groups are by inspecting some of the variables. For example, by plotting a boxplot of Intimate variable (Figure 6.5). This variable is 1 if the student has a partner or 0 otherwise. Since there are only possible values the boxplot looks flat. This shows that cluster_1 and cluster_3 are different from cluster_2 and cluster_4. Additionally, let's plot the ACS variable which represents the total score. This has a minimum value of 3 and a max value of 13.

#### Students Responses

![](img/91c149cc24c3e5af2971580c9dda9d8b_191_0.png)

Figure 6.4: Students responses when k=4.

![](img/91c149cc24c3e5af2971580c9dda9d8b_191_1.png)

Figure 6.5: Boxplot of Intimate variable.

![](img/91c149cc24c3e5af2971580c9dda9d8b_192_0.png)

clusters which gives an intuitive idea of why those two clusters are different.

So far, the number of groups k has been chosen arbitrarily or by visual inspection. But, is there an automatic way to select the best k? As always, this depends on the task at hand but there is a method called **Silhouette index** that can be used to select the optimal $k$ based on an optimality criterion. This index is presented in the next section.

### 6.2 The Silhouette Index

As opposed to supervised learning, in unsupervised learning there no **ground truth** to validate the results. In clustering, one way to validate the resulting groups is to plot them and explore the clusters' data points and look for similarities/or differences. But sometimes we also want to automate the process and have a quantitative measure to how well the clustering algorithm grouped the points with the given set of parameters. If we had such a method we could do parameter optimization, for example, to find the best k. Well, there is something called the *silhouette index* (Rousseau, 1987) and it can be used to measure the correctness of the clusters.

This index is computed for each data point and tells us how well they are clustered. The total silhouette index is the mean of all points' indices and gives us an idea of how well the points were clustered overall.
