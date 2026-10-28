| Interpretability | Provides soft cluster assignments and estimates cluster parameters, offering probabilistic interpretations. | Produces hierarchical structures, providing insights into hierarchical organization but may lack direct interpretability of individual clusters. |

*Table 4.1: GMM versus hierarchical clustering*

In summary, GMM and hierarchical clustering methods differ in their approach to clustering, handling of cluster shape and size, determination of the number of clusters, computational requirements, and interpretability. GMM is probabilistic and models cluster shapes explicitly, while hierarchical clustering produces hierarchical structures and does not require specifying the number of clusters in advance.

# Question 16: What is the impact of outliers on GMM clustering?

**Answer:** The impact of outliers on GMM clustering can be significant and can affect the clustering results in the following ways:

+   - **Distortion of cluster shape**: Any values that exist far from the distribution can also distort the parameters of a combination of Gaussians and thus distort the contours of clusters.
+   - **Influence on parameter estimation**: Such a situation means that large values can affect