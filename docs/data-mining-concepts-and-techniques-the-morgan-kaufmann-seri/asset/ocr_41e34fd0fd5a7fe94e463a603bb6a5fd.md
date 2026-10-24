# # Cluster analysis: advanced methods

9

You learned the fundamentals of cluster analysis in Chapter 8. In this chapter, we discuss advanced topics of cluster analysis. Specifically, we investigate four major perspectives:

+   * **Probabilistic model-based clustering**: Section 9.1 introduces a general framework and a method for deriving clusters where each object is assigned a probability of belonging to a cluster. Probabilistic model-based clustering is widely used in many data mining applications, such as text mining and natural language processing.

+   * **Clustering high-dimensional data**: When the dimensionality is high, conventional distance measures can be dominated by noise. Cluster analysis on high-dimensional data is an important area. This chapter introduces the general principles and some fundamental methods. Section 9.2 introduces the basic framework for cluster analysis on high-dimensional data. Section 9.3 discusses biclustering, which clusters objects and attributes simultaneously and enjoys many applications, such as bioinformatics and recommender systems. Section 9.4 discusses dimensionality reduction methods for clustering.

+   * **Clustering graph and network data**: Graph and network data is increasingly popular in applications such as online social networks, the World Wide Web, and digital libraries. In Section 9.5, you will study the key issues in clustering graph and network data, including similarity measurement and clustering methods.

+   * **Semisupervised clustering**: In our discussion so far, we do not assume any user knowledge in clustering. In some applications, however, various user knowledge may be available, which can be used to strengthen cluster analysis. For example, a user may provide useful constraints risen from background knowledge or spatial distribution of the objects to be clustered. Semisupervised clustering provides a general framework to accommodate such background knowledge. You will learn how to conduct semisupervised clustering in Section 9.6.

By the end of this chapter, you will have a good grasp of the issues and techniques regarding advanced cluster analysis.

In this chapter, we write a variable of an object in italic if we do not involve the vector representation of the object. If vector representations and matrix operations are involved, then variables in boldface are used.

# ## 9.1 Probabilistic model-based clustering

In most of the cluster analysis methods we have discussed so far, each data object can be assigned to only one of a number of clusters. This kind of strict cluster assignments are required in some applica-