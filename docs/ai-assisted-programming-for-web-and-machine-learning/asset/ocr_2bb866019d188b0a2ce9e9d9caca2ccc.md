+   - **Hierarchical clustering**: Builds a tree of clusters for nested grouping and dendrogram visualization.
- **Density-based spatial clustering of applications with noise (DBSCAN)**: Effective for identifying arbitrarily shaped clusters and noise points.

We also highlight how AI-assisted programming tools such as GitHub Copilot and ChatGPT can significantly enhance the clustering workflow. These tools:

+   - Acceleration implementation by suggesting complete code blocks and parameter-tuning strategies.
- Reduce boilerplate and setup time by predicting common import statements, initializations, and plotting logic.
- Improve understanding by explaining clustering algorithms, when to use them, and how to interpret the results.

Whether new to clustering or refining a real-world unsupervised learning pipeline, this section demonstrates how automation and AI-guided support can elevate your approach, from faster prototyping to clearer insights.

# K-means clustering in practice

One of the most popular clustering algorithms in unsupervised learning is k-means. It works by partitioning data into $k$ distinct clusters based on similarity, minimizing the variance within each group. K-means is particularly effective when the dataset consists of well-separated, compact clusters.

Let us walk through a practical example using an employee dataset. In this dataset, we cluster individuals based on salary and experience.

# Traditional approach