
[5] As reassignment has taken place, so we will again go to the step-4, which is finding new centroids or K-points.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_143_0.png)

[6] We will repeat the process by finding the center of gravity of centroids, so the new centroids will be as shown in the right-side image:

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_143_1.png)

[7] As we got the new centroids, so again will draw the median line and reassign the data points. So, the image will be:

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_143_2.png)

[8] We can see in the above image; there are no dissimilar data points on either side of the line, which means our model is formed. Consider the below image:

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_143_3.png)

[9] As our model is ready, so we can now remove the assumed centroids, and the two final clusters will be as shown in the below image:

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_143_4.png)

## 4.1.3 K-Means Random Initialization Trap

Consider the following scatterplot. We have two variables represented by the **x** and **y** coordinates. Let's say we're going to choose clusters. It does look like you can pretty spot them here.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_144_0.png)

If we choose K = 3 clusters...

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_144_1.png)

- So this is the end result if we choose the **correct random initialization** at **correct location**.

- However, if we select a **centroid** in **different locations** we will end up with different result. By following the steps of the algorithm we will end up as follows:

STEP 1: Choose the number K of clusters: K = 3

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_144_2.png)

- [1] Draw the median lines
- [2] Group the points

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_144_3.png)

- [3] Find new centroids
- [4] Then assign the centroids to the new positions:
STEP 4: Compute and place the new centroid of each cluster

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_144_4.png)

## True Cluster
## False Cluster

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_145_0.png)

So you can see that the three clusters are different and therefore, the selection of the Centroid is at the very start of the algorithm can potentially dictate the outcome of the algorithm. And that's not a good thing because the centroid is selected at random.

**K-means++**: This is a modification to the **K-means algorithm** that allows you to correctly select the Centroid called the **K-means++**.

**Python Scikit-learn library can handle this automatically:** From above we can see it is obviously a trap. However we need to worry about this because python implementation of this k-means algorithm can automatically handle this kind of "trap" situation. The good news is that **K-means++** algorithm happens in background in either R or Python or whatever tool you're using, [you don't] need to actually implement it.

## 4.1.4 Elbow-Method: Choosing K (Right Number Of Clusters)

The performance of the k-means clustering algorithm depends highly upon efficient clusters it forms. But *choosing the optimal number of clusters* is a big task. There are many different ways to find the *optimal number of clusters*, but here we are discussing the most appropriate method to find the number of clusters or value. The method is given below:

**Elbow Method:** The Elbow method is one of the most popular ways to find the *optimal number of clusters*. This method uses the concept of **WCSS**. **WCSS for Cluster Sum of Squares**, which defines the *total variations* within a cluster. The method to calculate the value of **WCSS (for k clusters)** is given below:

```
WCSS = \sum_{P_i \in Cluster 1} distance(P_i, C_1)^2 + \sum_{P_i \in Cluster 2} distance(P_i, C_2)^2 + \sum_{P_i \in Cluster 3} distance(P_i, C_3)^2
```

Where $P_i$ are data points in **Clustering** and $C_1, C_2, C_3$ are centroids. In the above formula, WCSS is the sum of squares between each data point and its centroid within a Cluster and the same for other terms.

To measure the **distance** between data points and centroid, we can use any method such as *Euclidean distance* or *Manhattan distance*.

To find the optimal value of clusters, the elbow method follows below steps:

- [1]. It executes **K-means** clustering on given dataset for **K values** (ranges from 1-10).
- [2]. For each value of k, it calculates WCSS.
- [3]. Plots a curve between calculated WCSS values and the **number of clusters**.
- [4]. The **sharp point** of bend on the plot looks like an arm, that point is considered as the best value of K.

Since the graph shows a sharp bend which looks like an elbow, hence it is known as the elbow method. The graph for the elbow method looks like the right-side image:

**Maximum number of Clusters**: We can choose the number of clusters to equal given data points. If the number of clusters equals data points, then the value of WCSS becomes zero, and that will be the endpoint of the plot. Actually we can see that for WCSS decreases rapidly and after a certain number it doesn't change.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_146_0.png)

**WCSS value is a metric**: We need a metric so that we can understand or evaluate how a number of clusters compares to different number of clusters (preferably quantifiable).

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_146_1.png)

WCSS = $\sum_{P_i \in Cluster 1} distance(P_i, C_1)^2 \sum_{P_i \in Cluster 2} distance(P_i, C_2)^2 \sum_{P_i \in Cluster 3} distance(P_i, C_3)^2$

Actually it is quite a good metric in terms of understanding the goodness of fit between different K-means clusterings. Let's see how WCSS is going to change as we **increase the number of clusters**.

If we use one centroid in the middle, the distance from each data point is big and the squared distance will be very large.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_146_2.png)

If we have 2 clusters then the squared distance reduces.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_147_0.png)

For 3 clusters we get reduced WCSS. For 4 or 5, more centroids the distance doesn't decrease rapidly (but decreases). The WCSS tends as K reaches the number of data points.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_147_1.png)

WCSS = distance(P1, C1)^2 + distance(P1, C2)^2 + distance(P1, C3)^2

The Elbow method is an approach that can help you decide the number of k (clusters). But at the end, it is your decision.

## 4.1.5 Python Implementation of K-means Clustering

**Problem Description:** We have a dataset of Mall_Customers, which is the data of customers who visit the mall and spend there. In the dataset, we have Customer_Id, Gender, Age, Annual Income ($), and Spending Score (which is the calculated value of how much a customer has spent in the mall; the more, the more he has spent). From this dataset, we need to calculate such patterns as it is an unsupervised method, so we don't know what to calculate exactly.

```python
# Within-Cluster Sum of Square
# K-means Clustering

# Libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Importing data
dataset = pd.read_csv('Mall_Customers.csv')
X = dataset.iloc[:, [3, 4]].values
```

## There is no y for clustering

```python
# Finding optimal number of clusters using elbow method : WCSS
from sklearn.cluster import KMeans
wcss = []
for i in range(1, 11):
    # setting parameters for cluster generator
    cluster_elbow = KMeans(n_clusters=i, init='k-means++', random_state=0, max_iter=300, n_init=10)
    cluster_elbow.inertia_ = cluster_elbow.fit(X) # fit the independent data
    wcss.append(cluster_elbow.inertia_) # capturing wcss data for each
# The inertia : Sum of squared distances to their closest cluster center. It is actually "wcss"
```

```python
# Visualizing the elbow
plt.plot(range(1, 11), wcss)
plt.title("The Elbow Method")
plt.xlabel("Number of Clusters")
plt.ylabel("WCSS")
plt.show()

# Getting optimum number of clusters from elbow-plot
kmeans = KMeans(n_clusters=5, init='k-means++', random_state=0, max_iter=300, n_init=10)
y_kmeans = kmeans.fit_predict(X)
# plotting the clusters
plt.scatter(X[:, 0], X[:, 1], c=y_kmeans, s=50, cmap='viridis')
plt.scatter(kmeans.cluster_centers_[:, 0], kmeans.cluster_centers_[:, 1], s=300, c='red', label='Centroids')
plt.title("Clusters")
plt.xlabel("Annual income")
plt.ylabel("Spending score (1-100)")
plt.legend()
plt.show()
```
