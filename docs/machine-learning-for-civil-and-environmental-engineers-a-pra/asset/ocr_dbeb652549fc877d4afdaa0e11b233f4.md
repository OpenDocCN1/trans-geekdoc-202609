![](bbox=[0.105, 0.085, 0.575, 0.255])

(a) A dendrogram example for HC algorithm

![](bbox=[0.1, 0.33, 0.345, 0.69])

(b) Flowchart

Figure 4.28 Flowchart of HC algorithm.

# Python Package:

```
import scipy.cluster.hierarchy as sch
model = sch.dendrogram()
```

# R Package:

```
>install.packages (''fastcluster'')
>library(fastcluster)
>hclust (d, method="complete", members=NULL)
```