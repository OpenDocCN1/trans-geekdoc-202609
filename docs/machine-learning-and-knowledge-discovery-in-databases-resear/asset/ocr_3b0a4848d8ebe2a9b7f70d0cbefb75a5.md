was demonstrated by Ma et al. [22] in their PointMLP framework, which achieved excellent performance using lightweight geometric affine modules within a residual structure, emphasizing that complex architectures are not always necessary for effective geometric reasoning. Inspired by these advancements, we propose leveraging multi-scale fusion and local feature learning techniques from point cloud processing to enhance mesh node downsampling and improve local information capture.

![](bbox=[0.132, 0.228, 0.895, 0.502])

**Fig. 2.** A model overview of the Multi-Scale Point-Based GNN(MPG) framework. The top panel illustrates the initial mesh partitioning into dense and sparse regions, followed by constrained Delaunay reconstruction for topology preservation. The bottom panel depicts the hierarchical feature extraction and reconstruction process, utilizing lightweight residual MLPs and KNN-based interpolation for efficient multi-scale processing.

# ## 3 Multi-scale Graph Constructing

In this section, we will introduce the hierarchical density-based sampling strategy, constrained Delaunay reconstruction, and the corresponding neighborhood definition for local feature aggregation in Sect. 4. All algorithms and preprocessing steps here are completed in one pass, and we can flexibly adjust the sampling ratio of each layer, the proportion between different density regions, and the fixed sizes of neighbor nodes for different physical simulations scenarios.

# ### 3.1 Problem Formulation

Multi-scale graph construction aims to generate hierarchical representations of complex systems while preserving essential distribution characteristics and topological structure. For non-uniform meshes, this process involves node selection,