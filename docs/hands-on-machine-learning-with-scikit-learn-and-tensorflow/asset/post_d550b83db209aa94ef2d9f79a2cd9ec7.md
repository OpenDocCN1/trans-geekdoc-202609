
```
[[ 0.68809572, 0.79608475],
[ 0.79608475, 1.122341415]]
```

Great, it worked fine! The weights that were used to generate the data were 0.2, 0.4 and 0.4, and similarly, the means and covariance matrices were very close to those found by the algorithm. But how? This class relies on the Expectation-Maximization (EM) algorithm, which has many similarities with the K-Means algorithm: it initializes the cluster parameters, then repeats two steps until convergence, assigning instances to clusters (this is called the expectation step) updating the clusters (this is called the maximization step). Sounds familiar? Indeed, in the context of clustering you can think of EM as a generalization of K-Means which not only finds the cluster centers ($\mu^{(i)}$ to $\mu^{(i)}$), but also their size, orientation ($\phi^{(i)}$ to $\phi^{(i)}$). Unlike K-Means, EM uses soft clustering rather than hard assignments: for each instance during the expectation step, the algorithm estimates the probability that it belongs to cluster (based on the current cluster parameters). During the maximization step, each cluster is updated using all the instances in the dataset, with each instance weighted by the estimated probability that it belongs to that cluster. These probabilities are called the responsibilities of the clusters for the instances. During the maximization step, each cluster's update will mostly be impacted by the instances it is most probable.

![](img/0684d2da98e09085c0a622d4fd69aaad_288_0.png)

Unfortunately, just like K-Means, EM can end converging to poor solutions, so it needs to be run several times, keeping only the best solution. This is why we set n_init to 10. Be careful: by default n_init is only set to 1.

You can check whether or not the algorithm converged and how many iterations it took:

```python
>>> gm.converged_
True
>>> gm.n_iter_
3
```

Okay now that you have an estimate of the location, size, orientation and relative weight of each cluster, the model can easily assign each instance to the most likely cluster (hard clustering) or estimate the probability that it belongs to a particular cluster (soft clustering). For this, use the predict() method for hard clustering, or the predict_proba() method for soft clustering:

```python
>>> gm.predict(X)
array([2, 2, 1, ..., 0, 0])
>>> gm.predict_proba(X)
array([[2.23289467e-02, 7.76379850e-07, 9.76603766e-01],
[1.64856092e-02, 9.82856078e-01, 1.51333333e-02]])
```

[2.01535336e-01, 9.99923053e-01, 7.49319577e-05],
...
9.9999571e-01, 2.9546075e-26, 4.28788333e-07,
1.0000000e+00, 1.46454409e-01, 5.12451716e-01,
1.0000000e+00, 8.02806365e-04, 2.27262328e-15]]

It is a generative model, meaning you can actually sample new instances from it (note that they are ordered by cluster index):

```python
>>> X_new, y_new = gm.sample(6)
>>> X_new
array([[2.95400315, 2.63808992,
 -1.1665475, 1.62792705,
 -1.394771225, 1.48511338,
 0.27221525, 0.690366],
 0.54095936, 0.48591934,
 -0.30860465, -0.56240465]])
```

```python
>>> y_new
array([0, 1, 2, 2, 2, 2])
```

It is also possible to estimate the score_samples() method: for each instance it is given, this method estimates the log of the probability density function (PDF) at that location. The greater the score, the higher the density:

```python
>>> gm.score_samples(X)
array([-2.68782346, -3.57186041, -3.33003479, ..., -3.51352783,
 -4.39802535, -3.80743853]])
```

If you compute the exponential of these scores, you get the value of the PDF at the location of the instances. These are not probabilities, but probability densities: they can take any positive value, not just between 0 and 1. To estimate the probability that an instance will fall within a particular region, you would have to integrate the PDF over that region (if you do so over the entire space of possible instance locations, the result will be 1).

Figure 9-17 shows the cluster means, the decision boundaries (dashed lines), and the density contours of this model:

![](img/0684d2da98e09085c0a622d4fd69aaad_290_0.png)

Figure 9-17. Cluster means, decision boundaries and density contours of a trained Gaussian mixture model

Nice! The algorithm clearly found an excellent solution. Of course, we made this task easy by generating the data using a set of 2D Gaussian distributions (unfortunately, real data is not always so Gaussian and low-dimensional), and we also gave the algorithm the correct number of clusters. When there are many dimensions, or many clusters, EM can struggle to converge to the optimal solution. You might need to reduce the difficulty of the task by limiting the number of parameters that the algorithm has to learn: one way to do this is to limit the range of shapes and orientations that the clusters can have. This be achieved by imposing constraints on the covariance matrices. To do this, just set the covariance_type parameter to one of the following values:

- "spherical": all clusters are spherical, but they can have different diameters (i.e., different variances).
- "diag": clusters can take on any ellipsoidal shape of any size, but the ellipsoid axes must be parallel to the coordinate axes (i.e., the covariance matrices must be diagonal).
- "tied": all clusters must have the same ellipsoidal shape, size and orientation (i.e., all clusters share the same covariance matrix).

By default, covariance_type is equal to "full", which means that each cluster can take on any shape, size and orientation (it has its own unconstrained covariance matrix). Figure 9-18 plots the solutions found by the EM algorithm when covariance_type is set to "tied" or "spherical".

![](img/0684d2da98e09085c0a622d4fd69aaad_291_0.png)

Figure 9-18. Cluster means, decision boundaries and density contours of a trained Gaussian mixture model

The computational complexity of training a Gaussian mixture depends on the number of instances $m$, the number of dimensions $n$, the number of clusters $k$, and the constraints on the covariance matrices. If\_type="spherical" or "diag", it is $O(kmn)$. If\_type="tied" or "full", it is $O(kn^2)$, so it will not scale to large numbers of features.

# Anomaly Detection

Anomaly detection (also called outlier detection) is the task of detecting instances that deviate from the norm. These instances are called *anomalies* or *outliers*, while the normal instances are called inliers. Anomaly detection is very useful in a variety of applications, for example in fraud detection, or detecting defective products in manufacturing. Using a mixture model for anomaly detection is quite simple: any instance located in a low-density region can be considered an anomaly. You must define what density threshold you want to use. For example, if you notice that you get too many false positives (i.e., perfectly good products that are flagged as defective), you can lower the threshold. Conversely, if you have too many false negatives (i.e., defective products that the system does not flag), you can increase the threshold. This is the usual precision/recall tradeoff (Chapter 3). Here is how you would identify the outliers using the 4th percentile:

```python
densities = gm.score_samples(X)
density_threshold = np.percentile(densities, 4)
anomalies = X[densities < density_threshold]
```

These anomalies are represented as stars on [Figure 9-19].

![](img/0684d2da98e09085c0a622d4fd69aaad_292_0.png)

Figure 9-19. Anomaly detection using a Gaussian model

A closely related task is novelty detection: it differs from anomaly detection in that the alg is assumed to be trained on a "clean" dataset, uncontaminated by outliers, whereas anomaly detection does not make this assumption. Indeed, outlier detection is often precisely used to clean up a dataset.

> Gaussian mixture models try to fill all the data, including the outliers if you have too many of them, this will bias the model's view of "normality": some outliers may wrongly be considered as normal. If this happens, you can try to fill the model once, use it to detect and remove the most extreme outliers, then fit the model again on the cleaned dataset. Another approach is to use robust covariance estimation methods (the EllipticEnvelope class).

# Selecting the Number of Clusters

With K-Means, you could use the inertia or the silhouette score to select the appropriate number of clusters, but with Gaussian mixtures, it is not possible to use these metrics because they are not reliable when the clusters are not spherical or have different sizes. Instead, you can try to find the model that minimizes a theoretical in-
