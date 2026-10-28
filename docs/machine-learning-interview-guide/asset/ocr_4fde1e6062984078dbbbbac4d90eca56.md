are utilized to optimize the current residual before the next iteration starts.

+   6. **Iteration**: Steps 2-5 are performed iteratively for a certain number of iterations or when a certain value of termination condition/criterion is attained. Again, in each iteration, a new tree is created to make a correction to the combined model of the previous iterations.
+   7. **Final prediction**: The last forecast is given by the aggregation of the results of all the tree models of the given ensemble. The features are added gradually in each iteration and, hence it helps the model to predict better results.

Still, gradient-boosting is quite effective for regression and classification problems, and other algorithms are XGBoost, LightGBM, and AdaBoost. The overarching concept is to construct the trees one by one and make them correct the mistakes of the previous trees, thus increasing the model’s efficiency.

# Question 8: What is the relationship between tree depth and model complexity in GBTs?

Answer: In GBTs, tree depth, and model complexity are vital to comprehend the data. Gradient-boosting is a type of ensemble learning wherein a series of trees, each one developed to minimize the loss function of the previous tree’s errors. The tree’s depth is determined by the distance of the farthest node in the tree, particularly starting from the root node, which is zero. The pervasiveness of the tree, the richer the model.

Let us go through some of the advantages and disadvantages for shallow and deep tress, along with some other critical topics: