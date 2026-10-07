# Steps of K-means Algorithm: The working of the K-means algorithm is explained in the below steps:

**1. Step-1** (choose the number K of clusters): Select the K to determine the number of clusters. Let's imagine that we've agreed on a number of clusters for a challenge scenario, say 2 or 5 clusters. Once you've done that you may proceed to *step 2*

> > We'll talk about how to select the **Optimal Number Of Clusters**.

> > As you have a Scatterplot, we could select some points in Scatterplot. The points **don't have to be of the observations**, we can then random x and y values on your Scatterplot. (As long as you select a **certain number of centroids** that are going to equate to the number of clusters that you have decided)

+   - Centroid is a kind of vague term, it depends on what kind of distance you are measuring (is it Euclidean distances? Or some other sort of distance)?
- For the purposes of simplicity, we're going to talk about Euclidean distances (that is basically geometrical distances).

**3. Step-3:** Assign the *Variance* and place *a new centroid* of each cluster.

**4. Step-4:** Repeat the *3rd steps*, which means reassign each point to the Newest Centroid of CLUSTER.

**5. Step-5:** If any reassignment occurs, then there go to step-4 else to FINISH.

# 4.1.2 K-Means Clustering Example

Now we do these steps manually to understand the whole process:

+   - This is our *scatterplot*. We can't visually identify the **clusters**, although it is **two-dimensional** but it's pretty tough.
- Now imagine how complex a situation would be if we had **three or more variables**!! We won't even be able to plot a *five dimensional scatterplot* like that.
- So that's where it came in clustering comes into play and that's where this algorithm will help simplify the process.
- In this case we are actually going to perform the same k-means clustering algorithm (later we will do this in python/R).

+   - [1] Let's take number K of clusters, i.e., **K2**, to identify the dataset and put it into different clusters. It means we will try to group these datasets into **two clusters**
- We need to choose **random k points** or *centroid* to form the cluster.
- These points can be either the **points from the dataset** or **any other point**. So, here we are selecting the two points as k points (in the right-side figure), which are not the part of our dataset. Consider the right-side image:

![](bbox=[0.58, 0.53, 0.81, 0.89])

**Now we will assign each data point** of the scatter plot to its closest **K-point or centroid**. We will compute it by applying **mathematics** that we have studied to calculate the distance between two points. So, we will draw a *median* between both the