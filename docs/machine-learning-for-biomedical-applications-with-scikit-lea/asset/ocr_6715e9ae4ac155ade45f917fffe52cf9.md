# Clusters 1&2

# Cluster 3

# Misclassified

![](bbox=[0.199, 0.113, 0.822, 0.266])

**Figure 6.5** Brain MRI of term and preterm babies. Left: average MRI image for babies from cluster 1 and 2. Middle: average MRI image for babies from cluster 3. Right: MRI image of a term baby in cluster 3, which contains mostly preterm babies. Yellow arrows point to enlarged volumes of CSF, which is typical in preterm babies.

a neonatal brain atlas (which may look similar to Fig. 6.5, left), so that all images are in the same orientation, and also of approximately similar global shape. MRI signals are not quantitative, we cannot calculate the Euclidean distance, but we instead calculate normalized cross-correlation (NCC) to measure the similarity between two images. In this example the NCC will always be positive, with a maximum value of 1, because the images are aligned and have similar T2-weighted contrast. We contrast input NCC between each pair of images directly to the affinity matrix **A**. This means we will have a fully connected weighted graph with a single connected component.

We will now apply clustering to brain images of 68 term and preterm neonates. Since the affinity matrix **A** has been precomputed and saved to a file, we can therefore load it using pandas as pd

```
import pandas as pd
d = pd.read_csv('babies.csv', header=None)
A = df.to_numpy()
print(A.shape)
>> (68, 68)
```

Note that the affinity matrix is of size $n 	imes n$, where $n$ is the number of samples. Each element of the matrix gives NCC between a pair of brain MRI images.

We will perform spectral clustering using a 3D Laplacian eigenmap embedding and k-means clustering with three clusters. It is often not obvious the parameters of spectral clustering should be chosen, we selected this setting because it provides stable results with different randomly assigned initial cluster centers in a kmeans algorithm (Sect. 6.1). We implement the clustering in scikit-learn using object `SpectralClustering` with 'precomputed' affinity matrix A:

```
from sklearn.cluster import SpectralClustering
```