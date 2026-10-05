# CHAPTER 7. DUALITY, NEARESET NEIGHBORS, SPARSITY

# 7.3 Nearest Neighbor Classification

In classification, it is reasonable to conjecture that data points that are sufficiently close to one another should be of the same class. For example, in fruit classification, perturbing a few pixels in an image of a banana should still result in something that looks like a banana. The k-nearest neighbors (k-NN) classifier is based on this observation. Assuming that there is no preprocessing of the training data, the training time for k-NN is effectively O(1). To train this classifier, we simply store our training data for future reference. For this reason, k-NN is sometimes referred to as “lazy learning”. The major work of k-NN is done at test time: to predict on a test data z we compute the k closest training points to z, where “closeness” can be quantified in some distance function such as Euclidean distance - these are k nearest neighbors to z. We then find the most common y among these k neighbors and classify z as y (that is, we perform a majority vote). For binary classification, k is usually chosen to be odd so we can break ties cleanly. Note that k-NN can also be applied to regression tasks — in that case k-NN would return the average label of the k nearest points.

![](bbox=[0.179, 0.413, 0.821, 0.616])

(a) 1-NN on 3 classes  (b) 2-NN on 5 classes

Figure 7.1: Voronoi diagram for k-NN. Points in a region shaded a certain color will be classified as that color. Test points in a region shaded with a combination of 2 colors have those colors as their 2 nearest neighbors.

# Choosing k

Nearest neighbors can produce very complex decision functions, and its behavior is highly dependent on the choice of k.

> ¹Sometimes we store the data in a specialized structure called a k-d tree. This data structure is out of scope for this course, but it usually allows for faster (average-case O(log n)) nearest neighbors queries.