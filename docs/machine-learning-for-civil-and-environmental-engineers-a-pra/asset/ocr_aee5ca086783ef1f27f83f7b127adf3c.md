![](bbox=[0.09, 0.085, 0.895, 0.54])

Figure 7.16 Explainable tree for hierarchical clustering.

Figure 7.16 shows the explainable tree for the hierarchical clustering algorithm. In this tree, the first split occurs for columns with a smaller cover thickness (less than 39 mm) as these join cluster no. 2, and the rest join cluster no. 3. Columns in cluster no. 2 continue to be analyzed based on their cover thickness, and the rest of the columns in this track are examined against their other features. In cluster no. 3, columns of 3.86 m in length move to cluster no. 3, and columns receiving loads of less than 1650 kN are moved to cluster no. 1, and so on.

# 7.4.3.1 Polar Line Plots

Figure 7.17 shows the polar line plots from the K-Means and hierarchical clustering models. This figure shows similar trends between clusters.84 For example, clusters no. 1 and 3 in both clusters are almost identical. On the other hand, cluster no. 2 in K-Means is equivalent to cluster no. 4, and vice versa. The same figure shows that cluster no. 1 of the K-Means is primarily influenced by strength (fc) and loading (P), while the same cluster no. 2 is influenced by the yield strength and stability/restraint conditions (K).85 In other words, these features drive the models' decision toward clustering the RC columns.

84 Despite having similar trends, the numbering of the clusters is not identical.
85 I trust that you can get the explanations for the other clusters! For example, cluster no. 4 in both models I governed by the collected features about equally – with a bit of sensitivity toward concrete cover.