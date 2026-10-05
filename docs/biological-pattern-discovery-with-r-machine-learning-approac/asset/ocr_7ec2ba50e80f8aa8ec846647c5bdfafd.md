A sequencing count data set generated to examine how genes contribute to the airway smooth muscle cytokine function [Himes, et al., 2014] was used here to illustrate how the histogram approach worked in R. Table 2.1 shows the data structure.

Table 2.1. A count matrix after the sequencing reads have been mapped to a reference genome for the airway data. Each count represents the times by which a sequencing read hits or mapped to a genome. Gene IDs have been shortened by removing the prefix ENG000000000 and the sample IDs have also been shortened by removing the prefix SRR103955. For instance, the full ID of gene E003 is ENG00000000003 and the full ID of sample S08 is SRR1039508.

| Gene | S08 | S09 | S12 | S13 | S16 | S17 | S20 | S21 |
| E003 | 723 | 486 | 904 | 445 | 1170 | 1097 | 806 | 604 |
| E005 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| E419 | 467 | 523 | 616 | 371 | 582 | 781 | 417 | 509 |
| E457 | 347 | 258 | 364 | 237 | 318 | 447 | 330 | 324 |
| E460 | 96 | 81 | 73 | 66 | 118 | 94 | 102 | 74 |

The code below was used to call hist estimate a density function for the first replica of this data set.

```
hist(log(x[which(x[,1]>0),1]),nclass=50)
```

In the code, x was a prepared count matrix for this data set. A density function was estimated based on only non-zero count values. hence which(x[,1]>0) was used. The bin number was 50. Figure 2.3 shows the histogram of the logarithm-transformed non-negative count data of two samples (SRR1039508 and SRR1039509).

![](bbox=[0.245, 0.693, 0.755, 0.853])

Fig. 2.3. Two histograms of the logarithm-transformed non-zero sequencing counts of the samples SRR1039508 and SRR1039509 for the airway data.