$S_i^+ = \sqrt{\sum_{j=1}^{n} (v_j^+ - v_{ij})^2},\, i=1,...,m;\ j=1,...,n \quad (15.16)$

Similarly, the separation measurement relative to the negative ideal alternative is performed by calculating the distance between each alternative in $V$ and the negative ideal alternative $A^-$ using Euclidean distance as illustrated in Equation 15.17.

$S_i^- = \sqrt{\sum_{j=1}^{n} (v_j^- - v_{ij})^2},\, i=1,...,m;\ j=1,...,n \quad (15.17)$

# Step 5: Calculating the relative closeness to the ideal solution $C_i^+$

In this step, the closeness of $A_i$ to the positive ideal solution $A^+$ is calculated using Equation 15.18.

$C_i^+ = \frac{S_i^-}{S_i^+ + S_i^-},\, i=1,...,m;\ 0 < C_i^+ < 1 \quad (15.18)$

In this case, $C_i^+ = 1$ if $V_i = A^+$ and $C_i^+ = 0$ if $V_i = A^-$. Afterward, a set of alternatives can be ranked in preference order according to the descending order of $C_i^+$. Then, the alternative with $C_i^+$ closest to 1 indicates the best alternative with highest performance.

# 15.3 Intelligent Systems Based Image Watermarking

Decision making for multimedia data watermarking is another multi-criteria problem. Many perspectives in using MCDM in the field of multimedia data watermarking require to consider it as subject of interest for the interested researchers.

For the purpose of comparative study between the proposed image watermarking model based on MCDM method and other intelligent systems based image watermarking, this section presents some of these systems.

The authors of [6] proposed a semi-blind image watermarking approach that combined frequent pattern mining and digital watermarking to provide a significant contribution in images authentication. The proposed approach is based on extracting the maximal frequent pattern among all frequent patterns of the host image. The frequent patterns are defined through features including DC, skewness, kurtosis and entropy, which are used to discriminate between the robust blocks and the fragile blocks. Initially, the host image is partitioned into 8 × 8 blocks, then all of these blocks are represented in a transaction database, where each block is represented as one transaction. The transaction database combines the features values