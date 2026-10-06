
# A Novel Deep Learning Method for Identification of Cancer Genes From Gene Expression Dataset

## Bcluster Extraction for Human Lymphoma Dataset

Table 3.2 summarizes the bclusters for lymphoma cancer dataset after 100 generations. The maximum sized bcluster is identified at MSR=226.43, with coherence index seen minimal and proves the goodness of the identified patterns. The minimum value of CI is 0.0465 with a corresponding size of 4587 being in the Table 1. As mentioned earlier, a lower mean squared residue indicates a maximum coherence of the founded bclusters.

Table 1. Extracted bclusters for lymphoma dataset

| Bcluster | Genes | Conditions | Volume | MSR | Row Variance | CI |
|---|---|---|---|---|---|---|
| BC_ | 208 | 8 | 1664 | 158.53 | 796.90 | 0.0898 |
| BC27 | 304 | 6 | 1824 | 179.84 | 812.16 | 0.0878 |
| BC52 | 372 | 8 | 2976 | 183.16 | 793.77 | 0.0576 |
| BC74 | 389 | 9 | 3501 | 192.36 | 835.75 | 0.0517 |
| BC83 | 417 | 11 | 4587 | 226.43 | 948.02 | 0.0465 |

Figure 3. Gene expression profile of the largest bcluster on lymphoma dataset

![](img/c5cbbc72cd5e7b9be32079eac36d685c_158_0.png)

Figure 3 depicts the gene expression dataset of the sized bcluster, corresponding to MSR=226.43. The gene expression values vary in the range 150 to 350 proves the highly dense profiles of the co-regulated genes having few or no fluctuations under the selected conditions of the bcluster. It has the highest row variance is 948.02 whereas the MSR is 226.43. In terms of fitness, this is the most "interesting" bcluster which has largest volume 4587 with the lowest MSR. Moreover, GCSM tries to find highly-variant busters instead of triclusters.

From Table 2 the fact can be seen that there is no difference between SDAE-Genetic algorithm and other heuristic Algorithm at the time and the number of iterations. But the algorithm will lose space to speed up the algorithm. The maximum number of iteration in this algorithm always reached 1000 to terminate the algorithm.

# A Novel Deep Learning Method for Identification of Cancer Genes From Gene Expression Dataset

Table 2. Number of iterations versus MSR on various

| Fitness Value | CC (Cheng & Church 2000) | CS (Yang, S. Deb.) | CSM (Balamurugan) | SDAE(proposed) |
|---|---|---|---|---|
| Number of Iterations | CC (Cheng & Church 2000) | CS (Yang, S. Deb.) | CSM (Balamurugan) | SDAE(proposed) |
| 1000 | 650 | 653 | 583 | 685 |
| 700 | 492 | 467 | 568 | 590 |
| 500 | 564 | 572 | 536 | 489 |
| 300 | 692 | 642 | 539 | 450 |
| 200 | 269 | 460 | 469 | 226 |

Table 3. Comparison of Average MSR vs No. of Iterations Vs Time Complexity on various Algorithms

| Method | Average MSR | No of Iterations | Iterative value in seconds (Time Complexity) |
|---|---|---|---|
| CC (Cheng & Church 2000) | 204.29 | 543 | 1106 |
| CS (Yang, S. Deb.) | 228.16 | 487 | 998 |
| CSM(Balamurugan) | 176.12 | 351 | 621 |
| SDAE(proposed) | 167.43 | 318 | 486 |

From Table 3 the Experimental results show that the proposed nested based SDAE genetic bicustering of gene expression data, can retrieve more significant marker subset of genes and conditions. It not only find out bclusters having low mean square reduce, but also it takes less number of iterations, whilst the proposed method can control the time complexity

Figure 4. Comparison of Fitness value Vs Algorithm

![](img/c5cbbc72cd5e7b9be32079eac36d685c_159_0.png)

# A Deep Learning Method for Identification of Cancer Genes From Gene Expression Dataset

Figure 4 shows the results of the proposed method that are compared with CC (Cheng & Church 2000), CS(Yang, S. Deb.) and CSM(Balamurugan) on Colon tumor dataset. The high value of MSR depicts that the cluster is weakly coherent while a low value MSR shows that it is highly coherent (SDAE). CS employs a heuristic approach to find clusters of limited size. It is based on the initial choice of seeds. Similarly CC algorithm gives a small size of clusters because random inference is involved. SDAE is able to locate large clusters for minimum MSR compared with CS. The cluster found by GCS is indent; however, it returns very small size of cluster for average MSR of 206.17. CS returns clusters with large MSR. Next CS method returns largest cluster, however average MSR of CS is larger than all other methods. In the case of SDAE, average MSR is better than the all other algorithms. Even so volume of cluster is better than the other algorithms. Thus, it can find significant cluster while maintaining the maximum size of cluster with low MSR.

# CONCLUSION AND FUTURE WORK

In this work SDAE algorithms for clustering gene expression data are proposed to speed up the convergence rate of CS algorithm. It focuses on finding coherent cluster with lower MSR and higher variance. In CSM uses the mutation operator instead of 말이 to generate a new solution. The proposed method improves the global search ability and prevents the CS algorithm into a local optimum. It increases the solution convergence easily. Moreover, the SDAE preserves the balanced exploitation and exploration via the process of mutation shuffling in the solution of search space respectively. In particular the SDAE shows a high convergence to the true global even problem at multi-dimensions. The proposed clustering method is applied to two gene expression data sets. The clusters obtained using the proposed method reveal good biological meanings. Biological assessment of the identified genes within the clusters are provided by publicly available GO consortium. This experimental study shows that SDAE algorithm competes satisfactorily compared to other popular clustering algorithms to detect the clusters

# REFERENCES

Adabor, Acquaah-Mensah, & Oduro. (2015). SAGA: A hybrid search algorithm for Bayesian Network structure learning of transcriptional regulatory networks. Journal of Biomedical Informatics, Elsevier, 53, 27–35. doi:10.1016/j.j.2014.08.010

American Cancer Society. (2019). Cancer Factors & 2019.

Androulakis, I., Yang, E., & Almon, R. (2007). Analysis of time-series gene expression: Methods, opportunities. Annual Review of Biomedical, 9.

Angellini & Ricciardo. (2016). Deep learning to Approach. Computer Science and Information Systems, 7.

Ayadi, W., & Hao, J. (2012). Pattern-Driven gene expression. Bioinformatics, 13.

Ayadi, W., Elloumi, M., & Yahia, S. (2017). Mining Negative Clusters from Gene Expression using Generic Association Rules. Procedia Computer Science, 112.

Balamurugan. (2016). A Cuckoo Algorithm for parameter optimization. Neurocom, 14.

Bhat, H. (2017). Evaluating SVM for gene detection. International Journal of Applied Engineering, 12.

Cheng, Y., & Chung, G. (2000). Clustering of Expression. Proceedings of the Eighth International Conference on Intelligent.

Khedidja. (2015). Multiobjective optimization for clustering microarray data. Applied Software Computing, 33, 239–249.

Kourou, K., Exarchos, T. P., Exarchos, K. P., Karamouzis, M., & Fotiadis, D. I. (2015). Machine learning applications in cancer prognosis and prediction. Computational and Biotechnology Journal, Elsevier, 13, 8–17.

Li, Y., Liu, W., Jia, Y., & Dong, H. (2016). A Weighted Mutual Information Bustering Algorithm for Gene Expression Data. Computer Science and Information Systems, 14(3), 643–660.

Huang, Z., Duan, H., & Li, H. (2015). Identification of Gene Pattern Related to Breast Cancer Using Integrated TCGA Datasets. BioMed Research International, 1–10.

Huang, Q., Tao, D., Li, X., & Wien. (2012). Parallelized evolutionary learning for detection of clusters in gene expression. IEEE/ACM Transactions on Computational Biology and Bioinformatics, 9(1), 560–570.

Jauhari, S., & Rizvi, S. A. M. (2014). Gene Expression Clustering for Cancer Therapies: A Digest. IEEE/ACM Transactions on Computational Biology and Bioinformatics, 11(3), 53. doi:10.1109/TCBB.2014.231200
