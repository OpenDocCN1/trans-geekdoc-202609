# Gene Expression Pattern Discovery 257

```
lines(range(MA$A),c(2,2),lty=3,lwd=2)
```

Figure 6.7 shows a MA plot for the prostate cancer data, where the upregulated DEGs and down-regulated DEGs can be visualised in terms of the biological significance. For instance, the genes above two were upregulated DEGs and the genes below negative two were down-regulated DE DEGs. From this plot, it can be seen that the mean expression variable has a wide distribution though the majority of genes have small mean expressions. Other phenomenon from this plot is the discovered DEGs have a wide range distribution of the mean expression. This means a DEG may have a smaller mean expression or may have a greater mean expression. One major limitation of this MA plot is that it does not involve the use of the statistical significance. Therefore, in addition to the visualisation of the relationship between the differential expression variable and the mean expression variable, it may not be efficient to whether the discovered DEGs have the statistical significance.

![](bbox=[0.297, 0.447, 0.683, 0.611])

Figure 6.7. A MA plot generated for the prostate cancer diagnosis data, where M stands for the differential expression variable and A stands for the mean expression variable.

# 6.2.3 The visualisation of the discovered DEGs using the volcano plot

As aforementioned, the biological significance measurement can indicate whether a gene is up- or down-regulated while the statistical significance measurement can assess the significance of the differential expression between two conditions. Combining both, therefore, can lead to meaningful conclusion for a gene expression pattern discovery project.

The popularly used approach to visualise the discovered DEGs for both biological significance and statistical significance is the volcano plot [Cui and Churchill, 2003]. It has been widely used in gene expression pattern