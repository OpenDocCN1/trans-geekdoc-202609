# # Maximizing similarity: *t*-SNE and UMAP

+   **This chapter covers:**
+   - What is non-linear dimension reduction and why is it important?
+   - What is t-SNE?
+   - What is UMAP?

In the last chapter, I introduced you to PCA as our first dimension reduction technique. While PCA is a linear dimension reduction algorithm (it finds linear combinations of the original variables), sometimes the information in a set of variables can’t be extracted as a linear combination of these variables. In such situations, there are a number of non-linear dimension reduction algorithms we can turn to, such as *t-distributed stochastic neighbor embedding* (t-SNE), and *uniform manifold approximation and projection* (UMAP).

The t-SNE is one of the most popular non-linear dimension reduction algorithms. t-SNE measures the distance between each observation in the dataset, to every other observation, then randomizes the observations across (usually) two new axes. The observations are then iteratively shuffled around these new axes until their distances to each other in this two-dimensional space are as similar to the distances in the original high dimensional space as possible.

UMAP is another non-linear dimension reduction algorithm that overcomes some of the limitations of t-SNE. It works in a similar way to t-SNE (finds distances in high-dimensional space, then tries to reproduce these distances in low-dimensional space), but differs in the way it measures distances.

By the end of this chapter, I hope you’ll understand what non-linear dimension reduction is and why it can be beneficial compared to linear dimension reduction. I will show you how the t-SNE, and UMAP algorithms work, how they’re different from each other, and we’ll apply each of