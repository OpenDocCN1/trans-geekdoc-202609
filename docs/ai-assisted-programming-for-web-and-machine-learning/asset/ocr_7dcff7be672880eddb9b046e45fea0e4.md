spherical clusters.

**complete':** Uses the maximum distance between points; better for well-separated clusters.

**'average':** Calculates the average distance between all pairs of points across clusters.

Let us look at an example:

# Prompt: How to choose between 'ward' and 'complete' linkage in hierarchical clustering?

**ChatGPT insight: Use ward when you are looking for compact, similar clusters. Opt for complete if your clusters are more irregular and clearly separated.

By combining automation and expert guidance, AI tools make it easier for people new to the concept to experiment with different linkage methods, interpret dendrograms, and apply hierarchical clustering confidently.

# Density-based clustering with DBSCAN

DBSCAN is a powerful clustering algorithm that identifies clusters of varying shapes and sizes, even in noisy, complex datasets. Unlike k-means, DBSCAN does not require you to specify the number of clusters beforehand. Instead, it groups data points that are closely packed and labels the rest as outliers.

This makes DBSCAN especially effective for real-world applications involving non-spherical clusters, anomaly detection, or spatial data analysis.

> Note: Similar to hierarchical clustering, DBSCAN determines clusters without a fixed k value, but it uses parameters like eps (neighborhood radius) and min_samples to control cluster formation based on density.

By relying on density rather than distance to centroids or linkage trees, DBSCAN provides more flexibility in scenarios with irregular patterns or when the data contains noise.