# Gene Expression Pattern Discovery 247

$F_g = \frac{\mu_{g,A}}{\mu_{g,B}} \quad (6.1)$

The base two logarithm fold change is defined as below,

$\log_2(F_g) = \log_2\left(\frac{\mu_{g,A}}{\mu_{g,B}}\right) = \log_2(\mu_{g,A}) - \log_2(\mu_{g,B}) \quad (6.2)$

When a fold change is two, the base two logarithm fold change is one, meaning that the case expression is the double of the control mean expression. When a fold change is half, the base two logarithm fold change is negative, meaning that the control mean is double of the case mean expression. For short, the base two logarithm fold change is expressed as the fold change in the following discussions. A gene with a negative fold change is called a down-regulated gene and a gene with a positive fold change is called an up-regulated gene. The gene regulation direction is from a control to a case condition. If the fold change of a down-regulated DEG is less than a pre-defined negative threshold, the gene is named as a down-regulated DEG. If the fold change of an up-regulated gene expression is missing in the fold change space, the gene is named as an up-regulated DEG.

Figure 6.1 shows the distribution of the fold changes of all genes in a microarray gene expression data, in which the letorole drug was used to treat the breast cancer patients [Miller, et al., 2007; Miller, et al., 2010]. The data set is composed of two conditions, i.e., before and after using the drug. The condition population was named as baseline before using the drug. The fold change threshold was one, 22 down-regulated DEGs and six up-regulated DEGs were identified. All the down-regulated DEGs were on the left side of the estimated density function of the fold change. Meanwhile, all the up-regulated DEGs were on the right side of the estimated density function of the fold change.

However, the fold change may have little information regarding the statistical significance. For instance, it has no statistical significance to compare a gene with a fold change 2.5 with a gene with a fold change 2.1. Therefore, the statistical significance is missing in the fold change space.