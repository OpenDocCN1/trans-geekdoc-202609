
# Introduction to python

(consists of composition, transition, and distribution features), conjoint triad quasi-sequence order sequence sequence (consists of order coupling number and quasi-sequence order descriptors), and pseudo-amino acid composition (consists of pseudo-amino acid composition and pseudo-amino acid composition features). Also, it computes 13 feature groups for small molecules, including the constitution, topology, connectivity, E-state, kappa, burden, information, autocorrelation, charge, property, MOE type, and fingerprints. Also, there are respectively, three and two methods to construct the interaction descriptor for protein-protein and protein-ligand interaction networks.

# 4. pyMCR

Camp Jr (2019) has introduced a python library for multivariate curve resolution with alternating regression, which is called pyMCR. This software library, written in Python, enables users to perform multivariate curve resolution (MCR) analysis, which lets users choose the error functions for minimization, constraints, and regressors.

# 5. DeepChem

DeepChem is an open-source framework, which is first created by Bharath Ramsdumar at Stanford University. Now, it is developed by a group of developers; however, anyone could join and contribute. This project uses TensorFlow to create deep learning models. It is developed to facilitate the researchers to develop new deep learning-based algorithms in drug discovery, biology, and life science. DeepChem provides many useful APIs to develop algorithms. These APIs include:

(1) data (for handling data)
(2) features: extract features from input data to feed into machine learning models. DeepChem provides both data-driven approaches like graph convolution feature and non-data-driven approaches like CircularFingerprint, PubChemFingerprint, Mol2Fingerprint, and RDKDescriptors.
(3) Scikit-learn models,
(4) Keras models,
(5) PyTorch models,
(6) Transformers: provide transformer object to adapt the mechanism of attention by weighting each part of the input data to emphasize the important parts,
(7) hyperparameter tuning, and
(8) reinforcement learning: reinforcement learning is a powerful technique in machine learning: DeepChem provides a useful framework to use it to solve computational biology problems. Also, there are many other beneficial APIs and the suitable documentation about them is available in https://deepchem.readdocs.io/en/latest/.

# 6. Scikit-learn

Scikit-learn is a machine learning package in python, which is open source and commercially usable under the BSD license. This package contains many useful objects, including preprocessing, classification, regression, dimensionality reduction, clustering, and model selection. The last version of this package is scikit-learn 1.0.1, which is released in October 2021. It is built on NumPy, SciPy, and matplotlib and provides many useful tools for visualizing data.

# 7. Examples

In this section, three examples (dimensionality reduction, partial least-squares (PLS), and clustering analysis) are provided using the “sklearn” package.

# 7.1 Dimensionality reduction

In this section, dimensionality reduction using principal component analysis (PCA) is explained. In dimensionality reduction, the main goal is to project the input data into a new space with low dimensions such that it preserves the most important knowledge of the input data. Dimensionality reduction approaches are divided into two categories: feature selection and feature projection (i.e., feature extraction). There are many algorithms. In this section, PCA from the feature projection category is practically explained. In this end, a toy dataset is selected, and then, the steps of how PCA is applied to it to reduce the dimension are explained.

In python, at the first step, you should import the necessary libraries to run the code. In this, we need “numpy,” “sklearn” (to use PCA and load one of the machine learning toy datasets), and “matplotlib” (to show the results) libraries.

```python
import numpy as np
from sklearn import datasets
from sklearn.decomposition import PCA
import matplotlib.pyplot as plt
```

In the next step, choose the toy dataset that you want to apply the PCA on. In this section, we select the IRIS dataset that contains three classes of 150 samples with four features.

```python
from sklearn.datasets import load_iris
data = load_iris()
```

Next, a PCA object is created and it is fit on data by the following commands:

```python
from sklearn.decomposition import PCA
pca = PCA(n_components=2)
data_reduced = pca.fit_transform(data.data)
```

It should be noted that PCA class gets an argument "n_components", which determines the dimension of the new data space. Now, to evaluate how it is performed on data, the projected data is visualized by "matplotlib" package.

```python
import matplotlib.pyplot as plt
idx = np.arg.where(data.target==0)
plt.scatter(data_reduced[idx,0],data_reduced[idx,1],color='blue')
idx = np.arg.where(data.target==1)
plt.scatter(data_reduced[idx,0],data_reduced[idx,1],color='red')
idx = np.arg.where(data.target==2)
plt.scatter(data_reduced[idx,0],data_reduced[idx,1],color='purple')
plt.gca().set(title="PCA on IRIS Dataset",xlabel='Feature1', ylabel='Feature2')
plt.legend()
plt.show()
```

By running this code, Fig. A.1 appears.

![](img/1aed977a858463e62fc6af1793e4677c_183_0.png)
Fig. A.1 PCA on IRIS Dataset.

# 7.2 Partial least-squares

Partial-squares (PLS) is a well-known technique in regression when the number of correlated variables is high. In this section, an example for PLS is given. To use this, we need to download and read the data. In the first step, the necessary libraries should be imported as follows:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.preprocessing import scale
from sklearn.model_selection import RepeatedFold
from sklearn.decomposition import PLSRegression
```

Next, the data is read:

```python
data_url = "https://archive.ics.uci.edu/ml/databases/026/CASP.csv"
raw_df = pd.read_csv(data_url, header=None)
data = raw_df.values[1::10]
data = data.astype(float)
target = raw_df.values[1::0]
target = target.astype(float)
```

In this case, “data” variable is a 45730 × 9 matrix and the “target” variable is 45730 × 1 matrix where 45730 is the number of instances. The nine predictors (namely, total surface area, non-polar exposed area, fractional area of residue, molecular mass-weighted exposed area, average deviation from the standard, secondary structure penalty, spatial distribution constraints).

The number of PLS components should be determined. To this end, for the different number of PLS components, the PLS model is fit, and then its MSE is computed. To do so, the following part of the code is used:

```python
cv = KFold(n_splits=5) # Note: original text had RepeatedFold, likely KFold or RepeatedKFold
cv = RepeatedKFold(n_splits=5)
mse=[]
for i in np.arange(1, 9):
    pls = PLSRegression(n_components=i)
    score = -1*model_selection.cross_val_score(pls, scale(data), target, cv=cv, scoring='neg_mean_squared_error').mean()
    mse.append(score)
#plot number of PLS components vs. MSE
plt.plot(mse)
plt.xlabel('Number of PLS Components')
plt.ylabel('MSE')
```

The output of the above code is given in Fig. A.2.

![](img/1aed977a858463e62fc6af1793e4677c_185_0.png)
Fig. A.2 The effect of the number of PLS components vs. MSE on physicochemical properties of protein tertiary structure dataset.

# 7.3 Cluster analysis

In cluster analysis, the unlabeled data is divided into the number of groups such that samples in each group are similar to each other. In literature, there are many clustering algorithms (Mouton, Ferreira, & Helberg, 2020; Xu & Tian, 2015). In this section, an example for clustering is given and k-means is used as a clustering algorithm. Hence, an unlabeled dataset is needed to fit
