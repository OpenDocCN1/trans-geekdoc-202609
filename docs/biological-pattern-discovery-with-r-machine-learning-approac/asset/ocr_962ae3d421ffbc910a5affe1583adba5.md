by weighting the insertions according to their insertion sites in a gene. An ESSENTIALS statistic $S_g^E$ for gene $g$ is shown below, where $z_{g,i}$ stands for the transposon insertions at the $i^{th}$ insertion site and $n_g$ is the total number of insertion sites in the gene $g$,

```
$S_g^E = \sum_{i=1}^{n_g} Z_{g,i} \quad (2.30)$
```

The TraDIS statistic $S_g^T = n_g$. The MF statistic is defined as below, $0 < w_i < 1 $(\sum_{i=1}^{n_g} w_i = 1)$ is a weight for the $i^{th}$ insertion site,

```
$S_g^M = \sum_{i=1}^{n_g} w_i Z_{g,i} \quad (2.31)$
```

First, it is obvious that $S_g^M < S_g^E$ if insertions are equally distributed within a gene. If all insertions are distributed in the distal regions of a gene, $S_g^M \ll S_g^E$. If all insertions are distributed in the centre of a gene, $S_g^M \approx S_g^E$. In most cases, $S_g^M > S_g^T$. However, if all insertions are distributed in the distal regions of a gene, $S_g^M \ll S_g^T$. It can be seen that the introduction of the mutation feature statistic has pressed down the transposon statistic values of the essential genes. This therefore increases the bimodality of the density of the transposon statistic such as the mutation feature statistic.

Figure 2.44 shows the density estimated based on MF for the first replicate of the Francisella Tularensis species. This density shows a better bimodality, which may make essential gene identification easier and more robust.

![](bbox=[0.283, 0.719, 0.683, 0.846])

Fig. 2.44. The density estimated based on the MF statistic for the first replicate of Francisella Tularensis.