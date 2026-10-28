for the decreased perplexity values that are more indicative of local relationships. One must note that perplexity dramatically influences the interpretation of the t-SNE plot; it controls the scale and spread of the clusters and the overall organization of the plot.

# Question 8: What are the limitations of t-SNE in clustering?

Answer: The limitations of t-SNE in clustering include:

+   - **Non-deterministic**: It is stochastic to perform. Hence, different runs with the same data and parameters can produce different results, making it difficult to get consistent clustering results.
+   - **Computational complexity**: t-SNE can be computationally intensive and therefore, is not suitable for any real-time or large-scale clustering endeavors.
+   - **Sensitive to parameters**: Measuring the perplexity, learning rate and number of iterations, t-SNE is highly dependent on those parameters and easy to overfit as well. Choosing the right parameters is not easy, and it often may take a few attempts.
+   - **Difficulty in interpreting distances**: One of the main issues when using t-SNE is that distances between points in the plot are not necessarily good representations of distances in the initial high-dimensional space which makes reading clusters separations troublesome.
+   - **Overfitting**: t-SNE can get over-fitted specially when perplexity is chosen to be high or the number of iterations is chosen to be quite large. This may lead to the generation of pseudo clusters or the distortion of the structure of the dataset.