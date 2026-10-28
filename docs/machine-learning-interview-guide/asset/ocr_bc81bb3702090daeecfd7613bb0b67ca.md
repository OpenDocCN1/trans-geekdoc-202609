parameter estimation and even move or stretch certain clusters towards them.

+   - Incorrect cluster assignments: Outliers can distort the centroids positions and inaccurately assign clusters, that are distant from the really existing ones, so clusters will not be grouped correctly in relation to the distribution of data.
+   - Impact on model selection: Outlier can have an influence on determining the most suitable number of clusters which may include in the overestimate of the number of clusters and splitting of genuine clusters.
+   - Increased sensitivity: It should be noted that GMM is less robust as compared to other robust clustering algorithms like in this problem, where it could be easily disrupted in the estimation process.

In summary, outliers are a major concern in most applications in GMM clustering since they alter the clusters shapes and robustness, skew the parameters and results, cause incorrect allocation of data points to clusters, affect model selection and make the algorithm highly sensitive.



Assessing the quality of GMM clustering results can be done using the following metrics and techniques:

+   - Silhouette score: This test reveals how clustered measures are and how separated alike measures are. That higher the value, the better the defined clusters are.
+   - BIC or AIC: It is the evaluation of the models on the basis of the fitness criteria. Conversely, the lowest scores represent the improvement of the models.