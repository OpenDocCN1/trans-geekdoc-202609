![](bbox=[0.12, 0.08, 0.49, 0.24])

Example applications include genealogy research to analyse genetics to understand family relationships, and organizing library resources such as books and journals in a manner that reflects similarity of content based on topics, themes or authors.

In this plot of a family tree, individuals from the same family are grouped closer together first and, as you move up the dendrogram, families start merging based on their similarities (distances).

+   - Hierarchical clustering tree

> **See also**
> 
> Reference the scikit-learn documentation for hierarchical clustering with a dendrogram by searching online for scikit-learn’s "Plot Hierarchical Clustering Dendrogram" (https://scikit-learn.org/stable/auto_examples/cluster/plot_agglomerative_dendrogram.html).

# # DBSCAN clustering

> **Key information**
> 
> DBSCAN stands for Density-Based Spatial Clustering of Applications with Noise.

![](bbox=[0.12, 0.47, 0.49, 0.64])

DBSCAN clustering will group together points that are close to each other based on a distance measurement and a minimum number of points. It is very effective for data with clusters of similar density. Unlike k-means, DBSCAN does not require the number of clusters to be specified. It can find arbitrarily shaped clusters and can handle noise and outliers.

An example application might be to detect fraudulent financial transactions by clustering on similarities of amount, location and time. DBSCAN can identify the dense clusters that are “typical” and then separate out unusual transactions for alerts.

+   - Density-based spatial clustering

> **See also**
> 
> Reference the scikit-learn documentation for DBSCAN by searching online for scikit-learn’s section 2.3.7 “DBSCAN” (https://scikit-learn.org/stable/modules/clustering.html#dbscan).

> **Association rule:**
> a process of finding patterns of co-occurrence in data; this means, given the presence of one item in a record, how likely it is that another item will be present.

# # A4.3.5 Unsupervised learning: association rule

The association rule can be understood as a data mining technique that seeks to find co-occurrences within a data set. It is another form of unsupervised learning. The technique is commonly applied for market analysis, as well as crime analysis, healthcare, web / app behaviour tracking, and more.