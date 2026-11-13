# Example no. 3 [Python, Clustering]: Grouping fire-exposed RC columns.

This example replicates Example no. 3 from the BigML section.

To recap, the compiled database contains the following features from 144 RC columns: column width, W (mm), steel reinforcement ratio, r (mm), column length, L (mm), concrete compressive strength,fc (MPa), steel yield strength,fy (MPa), restraint conditions by means of effective length factor, concrete cover to reinforcement, C (mm), eccentricity in applied loading in the main axes, ex (mm), the magnitude of applied loading, P (kN), and fire resistance, FR (min).

Here is the Python code83 for you to try. I am using the K-Means algorithm here, which I am importing from the sklearn. cluster package. I will also provide scripts for the FCM and DBSCAN algorithms.

```
#Importing libraries
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
from sklearn.preprocessing import StandardScaler
import seaborn as sns
```

#Importing dataset

```
dataset = pd.read_excel('Fire-exposed RC columns.xlsx')
X = dataset.iloc[:, :9].values
pd.plotting.scatter_matrix(dataset, alpha = 0.3, figsize = (26,20), diagonal = 'kde');
```

![](bbox=[0.098, 0.38, 0.82, 0.81])

```
from sklearn.cluster import KMeans
from sklearn.metrics import silhouette_samples, silhouette_score
import matplotlib.cm as cm
range_n_clusters = range( 2, 6 )
for n_clusters in range_n_clusters:
```