+   - The **subspace clustering methods** find all clusters in all subspaces of the entire data space. A data object may belong to zero, one, or multiple clusters simultaneously. Clusters may also substantially overlap in different subspaces. A representative method in this group is CLIQUE, which is briefly introduced in Section 8.4.3 as a grid-based method.

+   - The **projected clustering methods** partition a given data set into nonoverlapping subsets. In other words, a data object belongs to exactly one cluster. For each cluster, the methods search for the corresponding subspace. PROCLUS is a pioneering and representative projected clustering method.

+   - The **bi-clustering methods** cluster attributes and objects simultaneously. In other works, attributes and objects are treated in a symmetric manner in bi-clustering methods. This group of methods have been extensively used in biological data analysis and recommender systems. We will introduce bi-clustering in Section 9.3.

The second category is the **dimensionality-reduction methods**. As we discussed, in a high-dimensional data set, the intrinsic dimensionality may be much lower than the embedding dimensionality. Thus the dimension-reduction methods construct new attributes to approach the intrinsic dimensions and transform the objects from the original embedding data space to a constructed space of much lower dimensionality. Clustering analysis is then conducted in the constructed space. Dimensionality-reduction methods for clustering analysis will be discussed in Section 9.4.

# ## 9.2.2 Axis-parallel subspace approaches

Now, let us look at some representative subspace clustering methods and projected clustering methods. We use three methods, CLIQUE, PROCLUS, and LAC, to illustrate the essential ideas.

# ### CLIQUE: a subspace clustering method

Subspace clustering methods find all clusters in all subspaces of the entire data space. CLIQUE is a representative. Recall that we introduce CLIQUE in Section 8.4.3 as a grid-based method. Let us recap the two major ideas in CLIQUE tackling high-dimensional data.

First, CLIQUE adopts a **bottom-up strategy**. It starts from low-dimensional subspaces and searches higher-dimensional subspaces only when there may be clusters in those higher-dimensional subspaces. Various pruning techniques are explored to reduce the number of higher-dimensional subspaces that need to be searched.

Second, CLIQUE allows overlaps among clusters in different subspaces. For example, in Fig. 8.22, the dense cell of salary $30,000–40,000, age 35–40, and vacation 2–3 weeks in the 3-D subspace (salary, age, vacation) also belongs to the dense cell of salary $30,000–40,000 and age 35–40, and the one of age 35–40 and vacation 2–3 weeks in the corresponding subspaces, and thus in turn belongs to the two clusters in the two subspaces. Every object in the 3-D dense cell also belongs to the two clusters.

# ### PROCLUS: a projected clustering method

**PROCLUS** is a _k_-medoid–like method for projected clustering on high-dimensional data. PROCLUS works in three phases.

+   - In the **initialization phase**, PROCLUS generates _k_ potential cluster centers, that is, medoids, using a greedy sample of the data set.