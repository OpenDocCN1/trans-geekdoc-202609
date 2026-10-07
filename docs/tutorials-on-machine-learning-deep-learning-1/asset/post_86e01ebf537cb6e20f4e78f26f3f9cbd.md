
CAP curve and ROC curve are not the same: Note that CAP means Cumulative Accuracy Profile. There is a ROC-curve which is Receiver Operating Characteristic

# CAP = Cumulative Accuracy Profile

# ROC = Receiver Operating Characteristic

How to Analyse: So now we have, three lines. One the CAP-Curve (Red line), the Blue line is the random line, and the Gray line which is the perfect model.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_138_0.png)

The closer your Red line to the Gray line the better you are, the closer to the Blue line the worse. So how we quantify this effect? Will there be a standard approach to Calculate The Accuracy Ratio and to calculate accuracy ratios: you take the area under the perfect model or the perfect line which is in Gray here and it's $a_P$. Notice the following figure

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_138_1.png)

And then you need to take area under the Red line which is colored in Red here is $a_R$ is $a_P$ and you need to divide one by the other. This ratio is between 0 and 1.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_138_2.png)

The closer this ratio is to 1 the better, the further it is away from 1 and close to 0 the worse your model.

**Other way:** Now let's get rid of areas and instead of looking the area where you can do is look at the 50% line on the horizontal axis (X-axis) and where it crosses your model-curve and project that point on the vertical axis (Y-axis).

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_139_0.png)

And there are some rules for the X% on the Y-axis projected value:

- *X < 60%*: Rubbish model
- *60% < X < 70%*: Poor model
- *70% < X < 80%*: Good model
- *80% < X < 90%*: Very Good model
- *90% < X < 100%*: That's odd !! This model is so good !! Need to check that there is **OVERFITTING**.

**OVERFITTING is bad:** So Remember the OVERFITTING. It could Ruin your model.

# Chapter 4 : Part 1

# K-Means Clustering

## 4.1.1 K-Means Clustering

K-Means Clustering is an algorithm that allows you to Cluster your data. K-Means Clustering is an unsupervised learning algorithm that is used to solve the clustering problems in machine learning or data science.

- K-Means Clustering is an Unsupervised Learning algorithm, which groups the unlabeled dataset into different clusters. Here K defines the number of pre-defined clusters that need to be created, as if K=2 there will be two clusters, and for K=3 there will be three clusters, and so on.
- It is an iterative algorithm that divides the unlabeled dataset into k different clusters in a way that has each dataset belongs only one group into similar properties.
- It allows us to cluster the data into different groups and a convenient way to discover the categories of groups in the unlabeled dataset on its own without any training.
- It is a centroid-based algorithm where each cluster is associated with a centroid. The main aim of this algorithm is to minimize the sum of distances between the data-point and their corresponding clusters (centroid).

The algorithm takes the unlabeled dataset as input, divides the dataset into k-number of clusters, and repeats the process until it does not find the best clusters. The value of k should be predetermined in this algorithm.

- The k-means clustering algorithm mainly performs the following tasks:
- Determines the best value for K-center points or centroids by an iterative process.
- Assigns each data-point to its k-center. Those data points which are near to the k-center, create a cluster.
- Hence each cluster has data-points with some commonalities, and it is away from other clusters.

The below diagram explains the working of the K-Means Clustering Algorithm:

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_140_0.png)

It is a very convenient tool for discovering categories or groups in your data-set.

Let's imagine we've got two variables in our data set and we decided to plot those two variables on X and Y axes. The question is:

- How our observations are configured according to these variables?
- Can we identify groups among all variables?

What the K-Means does for you: it takes the complexity from this decision making process and allows you to very easily identify those clusters (actually called clusters of data points) in your data-set.

## Steps of K-means Algorithm: The working of the k-means algorithm is explained in the below steps:

**1. Step-1** (choose the number K of clusters): Select the K to determine the number of clusters. Let's imagine that we've agreed on a number of clusters for a challenge scenario, say 2 or 5 clusters. Once you've done that you may proceed to *step 2*

> We'll talk about how to select the **Optimal Number Of Clusters**.

> As you have a Scatterplot, we could select some points in Scatterplot. The points **don't have to be of the observations**, we can then random x and y values on your Scatterplot. (As long as you select a **certain number of centroids** that are going to equate to the number of clusters that you have decided)

- Centroid is a kind of vague term, it depends on what kind of distance you are measuring (is it Euclidean distances? Or some other sort of distance)?
- For the purposes of simplicity, we're going to talk about Euclidean distances (that is basically geometrical distances).

**3. Step-3:** Assign the *Variance* and place *a new centroid* of each cluster.

**4. Step-4:** Repeat the *3rd steps*, which means reassign each point to the Newest Centroid of CLUSTER.

**5. Step-5:** If any reassignment occurs, then there go to step-4 else to FINISH.

## 4.1.2 K-Means Clustering Example

Now we do these steps manually to understand the whole process:

- This is our *scatterplot*. We can't visually identify the **clusters**, although it is **two-dimensional** but it's pretty tough.
- Now imagine how complex a situation would be if we had **three or more variables**!! We won't even be able to plot a *five dimensional scatterplot* like that.
- So that's where it came in clustering comes into play and that's where this algorithm will help simplify the process.
- In this case we are actually going to perform the same k-means clustering algorithm (later we will do this in python/R).

- [1] Let's take number K of clusters, i.e., **K2**, to identify the dataset and put it into different clusters. It means we will try to group these datasets into **two clusters**
- We need to choose **random k points** or *centroid* to form the cluster.
- These points can be either the **points from the dataset** or **any other point**. So, here we are selecting the two points as k points (in the right-side figure), which are not the part of our dataset. Consider the right-side image:

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_141_0.png)

**Now we will assign each data point** of the scatter plot to its closest **K-point or centroid**. We will compute it by applying **mathematics** that we have studied to calculate the distance between two points. So, we will draw a *median* between both the

From the above image, it is clear that points left side of the line is near to the K1 or blue centroid, and points to the right of the line are close to the yellow centroid. Let's color them as blue and yellow for clear visualization.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_142_0.png)

As need to find the closest cluster, so we will repeat the process by choosing a new centroid. To choose the new centroids, we will compute the center of gravity of these centroids, and will find new centroids as below:

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_142_1.png)

Next, we will reassign each datapoint to the new centroid. For this, we will repeat the same process of finding a median line. The median will be like right - image:

> From the beside image, we can see, one yellow point is on the left side of the line, and two blue points are right to the line. So, these three points will be assigned to new centroids.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_142_2.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_142_3.png)
