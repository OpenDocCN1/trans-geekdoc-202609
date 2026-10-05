# Biological Pattern Discovery with R

Therefore low extreme outlier very likely caused a missed DEG, i.e., a Type II error. When examining the whole data set, it was found that this data set was composed of 162 likely missing DEGs and the Type II errors due to the low extreme outliers occurred in the cancer replicates.

![](bbox=[0.296, 0.203, 0.703, 0.345])

Fig. 6.14. A low extreme outlier in gene 218765_at at GDS3139 caused a Type II error.

In 6.15, a high extreme outlier presented in the cancer replicates. Because of this outlier, the mean expression of the cancer replicates were pushed up. This certainly helped enlace the mean difference between two populations. Therefore the raw p value was 0.0098 if the outlier was not removed. If the outlier was removed, the new p value became 0.018. This shows that the occurrence of a high extreme outlier in the cancer replicates caused a false DEG, a Type I error. If this high extreme outlier was removed, the gene becomes a non-DEG. The investigation into the whole data set found 26 false DEGs (the Type I errors) in total due to the high extreme outliers presented in the cancer replicates.

![](bbox=[0.296, 0.642, 0.703, 0.784])

Fig. 6.15. A high extreme outlier in gene 212954_at at GDS3139 caused a false DEG.

A missing DEG or a Type II error may happen due to a high extreme outlier occurred in the cancer replicates as shown in Figure 6.16. This high extreme outlier was far away from the cluster of the rest cancer replicates and was above the control expression cluster. The raw p value was 0.1188