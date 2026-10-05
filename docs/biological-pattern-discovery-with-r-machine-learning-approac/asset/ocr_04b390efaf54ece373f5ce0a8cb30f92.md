# Gene Expression Pattern Discovery

Based on the constructed edgeR model, decideTestsDGE was called to discover DEGs.

```
sig=decideTestsDGE(model)
```

The object contained information of DEGs. For instance the following code was used to show the statistic. When sig was 0, the figure shows the number of non-DEGs. When sig was -1, the figure shows the number of down-regulated DEGs. When sig was +1, the figure shows the number of up-regulated DEGs.

```
> sum(sig==0)
[1] 37943
> sum(sig==-1)
[1] 351
> sum(sig==1)
[1] 400
```

These statistics can also be obtained by calling the summary function

```
> summary(sig)
experiment-control
Down 351
NotSig 37943
Up 400
```

Figure 6.12 shows the six-panel volcano for the edgeR model for the data. In total, 146 down-regulated DEGs and 158 up-regulated DEGs were identified for a critical p value 0.01 and a critical fold change value two.

![](bbox=[0.198, 0.646, 0.762, 0.856])

Fig. 6.12. A six-panel volcano plot for an edgeR model for the airway data.