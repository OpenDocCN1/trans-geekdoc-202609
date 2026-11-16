# # 6.1.1 Generating Counterfactual Explanations

A simple and naive approach to generating counterfactual explanations is searching by trial and error. This approach involves randomly changing feature values of the instance of interest and stopping when the desired output is predicted. Like the example where Anna tried to find a version of her apartment for which she could charge more rent. But there are better approaches than trial and error. First, we define a loss function based on the criteria mentioned above. This loss takes as input the instance of interest, a counterfactual and the desired (counterfactual) outcome. Then, we can find the counterfactual explanation that minimizes this loss using an optimization algorithm. Many methods proceed in this way but differ in their definition of the loss function and optimization method.

In the following, we focus on two of them: first, the one by Wachter et. al (2017) who introduced counterfactual explanation as an interpretation method and, second, the one by Dandl et al. (2020) that takes into account all four criteria mentioned above.

# ### 6.1.1.1 Method by Wachter et al.

Wachter et al. suggest minimizing the following loss:

```
\L(x,x^\prime,y^\prime,\lambda)=\lambda\cdot\text{cdot}(\hat{f}(x^\prime)-y^\prime)^2+d(x,x^\prime)
```

The first term is the quadratic distance between the model prediction for the counterfactual x' and the desired outcome y', which the user must define in advance. The second term is the distance d between the instance x to be explained and the counterfactual x'. The loss measures how far the predicted outcome of the counterfactual is from the predefined outcome and how far the counterfactual is from the instance of interest. The distance function d is defined as the Manhattan distance weighted with the inverse median absolute deviation (MAD) of each feature.

```
\d(x,x')=\sum_{j=1}^p |x_j-x'_j| \cdot \{MAD_j\}
```

The total distance is the sum of all p feature-wise distances, that is, the absolute differences of feature values between instance x and counterfactual x'. The feature-wise distances are scaled by the inverse of the median absolute deviation of feature j over the dataset defined as:

```
\MAD\_j=\text{median}\{|x_{1,j}-\text{median}\{|x_{1,j}\}|\}
```

The median of a vector is the value at which half of the vector values are greater and the other half smaller. The MAD is the equivalent of the variance of a feature, but instead of using the mean as the center and summing over the square distances, we use the median as the center and sum over the absolute distances. The proposed distance function has the advantage over the Euclidean distance that it is more robust to outliers. Scaling with the MAD is necessary to bring all the features to the same scale - it should not matter whether you measure the size of an apartment in square meters or square feet.

The parameter \lambda balances the distance in prediction (first term) against the distance in feature values (second term). The loss is solved for a given \lambda and returns a counterfactual x'. A higher value of \lambda means that we prefer counterfactuals with predictions close to the desired outcome y', a lower value means that we prefer counterfactuals x' that are very similar to x in the feature values. If \lambda is very large, the instance with the prediction closest to y' will be selected, regardless how far it is away from x. Ultimately, the user must decide how to balance the requirement that the prediction for the counterfactual matches the desired outcome with the requirement that the counterfactual is similar to x. The authors of the method suggest instead of selecting a value for \lambda to select a tolerance \epsilon for how far away the prediction of the counterfactual instance is allowed to be from y'. This constraint can be written as:

```
|\hat{f}(x') - y'| \leq \epsilon
```