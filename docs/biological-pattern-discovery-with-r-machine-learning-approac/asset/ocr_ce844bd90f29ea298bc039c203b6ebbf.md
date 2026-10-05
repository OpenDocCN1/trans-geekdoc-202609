# Biological Pattern Discovery with R

![](bbox=[0.277, 0.096, 0.722, 0.373])

Fig. 2.26. Four K-means models for a data toy of three clusters. A, B and C stand for three raw cluster labels. The circle, the triangles and the diamonds stand for the resulting cluster labels assigned by the K-means models.

![](bbox=[0.3, 0.455, 0.699, 0.693])

Fig. 2.27. Four K-means cluster models constructed for the amino acid data using two, three, four and five clusters. Different clusters are represented by different enclosing patterns for the amino acids.

The issue associated with the K-means algorithm is how to determine a proper cluster number for a data set. This is because an accurate cluster number is critically important to the performance of a constructed cluster model for a data set. In the kmeans function, the parameter centers is used for the user to design a cluster number. For a real-world data set, no a priori knowledge about the exact cluster number