
# Data Preprocessing and Clustering Analysis

Before we can apply clustering algorithms, we need to prepare our data. The first step in this process is to preprocess our sequences and segments. This involves two key steps: padding our sequences to ensure they are uniform in length, and standardizing our segments to prevent any individual feature from dominating the analysis. We will begin by applying padding to our sequences.

## Sequence Padding

In the context of sequence data, padding refers to the process of adding extra values to a sequence to make it a uniform length. This is often necessary when working with sequences of varying lengths, as many machine learning algorithms require fixed-length input data. Without padding, sequences of varying lengths would not be compatible with these algorithms. Furthermore, if sequences have different lengths, the model may be biased towards the longer sequences, which could lead to inaccurate results.

The following is the code to standardize (`pad_sequences`) the input segments (`seqs` is a list of sequences), ensuring they are all of uniform length[10](#chap09.xhtml#footnote-053):

```python
from keras.preprocessing.sequence import pad_sequences

padded_seqs = pad_sequences(seqs, padding='post', dtype='float32')
```

After ensuring uniform length, we need to standardize the input segments statistically. To achieve this, we apply a standard scaler (`StandardScaler()` function), which transforms all inputs to have a similar scale, characterized by a zero mean and unit standard deviation.

This step (`scaler.fit_transform`) enables the machine learning algorithm to more easily compare the different sequences, facilitating the discovery of recurring patterns:

```python
from sklearn.preprocessing import StandardScaler

# padded_seqs: array of padded sequences
scaler = StandardScaler()

# Standardize the sequences
seqs_scaled = scaler.fit_transform(padded_seqs.reshape(len(padded_seqs), -1))
```

## Dimensionality Reduction with UMAP

Before clustering, we apply a critical preprocessing step: dimensionality reduction. Experience shows that this improves the analysis of complex financial data. We will use the Uniform Manifold Approximation and Projection algorithm (UMAP), which is known for preserving local data structure while reducing dimensionality.

### Applying UMAP

With our data now standardized, we could move on to clustering. However, from my experience with financial data analysis, I know that it is often necessary to refine the data to make it more analyzable. To do this, we will use a dimensionality reduction technique that preserves the local structure of the data called UMAP[11](#chap09.xhtml#footnote-052). We have already introduced this algorithm in [Chapter 6](#chap06.xhtml), Improving Model Capability with Features. By applying UMAP, we can distill complex, high-dimensional data into a more manageable, lower-dimensional representation called projection (typically one or two dimensions). The algorithm ensures that the relationships between neighboring data points are preserved during the projection step, so that data points that were originally close together remain close together.

This step simplifies the data and preserves its inherent characteristics, a feat that UMAP accomplishes with remarkable precision:

```python
from umap import UMAP

trsf = UMAP(n_neighbors=2, min_dist=0.1, n_components=2)
seqs_reduced = trsf.fit_transform(seqs_scaled)
```

With UMAP reducing dimensionality, we can now group similar sequences. Using kMeans, we will identify patterns and structure within the data.

## Clustering Sequences with KMeans

The UMAP-transformed data are fed into the clustering algorithm, which groups similar data points together. In essence, we are not analyzing the original data, but rather the UMAP-transformed data, which allow for more effective pattern recognition and clustering.

The heavy lifting is done by UMAP, which projects the complex data into a lower-dimensional space while preserving its essential characteristics. This sets the stage for the k-Means clustering algorithm to group the points based on their proximity to each other.

In short, k-Means is an unsupervised algorithm that groups data points into clusters based on their similarities, allowing us to identify natural families within the data. It works by iteratively refining the cluster assignments until the data points are grouped into coherent clusters that share common characteristics.

By doing so, k-Means provides a way to uncover hidden patterns and structures in the data, allowing us to better understand and describe the underlying relationships between the data points:

```python
# CLUSTERING
n_clusters = 4
clst = KMeans(n_clusters=n_clusters, n_init='auto')
clusters = clst.fit_predict(seqs_reduced)
```

The following graph illustrates the result of applying k-Means clustering to the data that has been transformed by UMAP, showing the resulting groupings into four distinct clusters.

We annotate the points with their label based on their order in the original list and highlight the last (most recent one) subsequence with a distinct color and label (16), as follows:

![](images/fig-9-6.png)

This graph shows the categorization of sequences into their inherent groups, with each group represented by a different color. For example, the initial two sequences (0 and 1) and the latest one ('last sequence') are clustered together, as indicated by the orange color assigned to this group.

While this scatter plot of clustered sequences provides a useful visualization of how they interact with each other, it lacks a critical dimension: time. To fully capture the dynamics of these sequences, we need to incorporate the temporal aspect into our graph. Instead of positioning the sequences relative to each other, we will reorder them according to their appearance in time.

In the following figure, we will display each sequence, labeled by the clustering algorithm, in its correct position on the time scale, providing a more comprehensive understanding of their relationships:

![](images/fig-9-7.png)

The graph shows the closing prices for copper futures segmented into four clusters, each indicated by a different color: `['orange': labeled '0', 'purple': labeled '1', 'green': labeled '2', 'blue': labeled '3']`. The algorithm identifies each cluster as a distinct regime characterized by its own unique dynamics and behavior.

## Interpreting Clustering

The clusters identified by the algorithm reveal a complex dynamic that will permit us to guide our interpretation and analysis of the market's dynamic.

Specifically, we need to undertake the following steps:

1. Characterize each cluster in terms of its underlying dynamics, revealing the unique patterns and behaviors that define each regime.
2. Examine the chronological arrangement of the sequences, seeking to understand whether there is a specific order in which each type of sequence emerges in relation to others.
3. Finally, we will explore whether the insights gained from this analysis can be used to predict the next type of sequence that is likely to occur, following the last observed sequence (labeled 'orange', numbered 16, cluster '0').

Let us start with the first step[12](#chap09.xhtml#footnote-051) which is to characterize each cluster in terms of its underlying dynamics. We can observe the following facts:

- **'orange' zones (labeled '0')**: These segments generally represent periods of relative stability or minor fluctuation in copper prices.
- **'purple' zones (labeled '1')**: These periods show a trend of increasing volatility or rising prices.
- **'green' zones (labeled '2')**: These segments are characterized by significant fluctuations, possibly indicating periods of market uncertainty or correction phases.
- **'blue' zones (labeled '3')**: These periods also display volatility with noticeable peaks, possibly suggesting reactionary movements to external market influences or speculative trading. These periods are also clearly characterized by a downward trend.
