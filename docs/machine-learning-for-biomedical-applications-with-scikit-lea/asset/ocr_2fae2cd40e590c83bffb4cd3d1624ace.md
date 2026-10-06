# # or simultaneously fit the model
# and use it to transform the data
projected_data=model.fit_transform(random_data)

Key attributes that can be returned from the PCA model include:
model.explained_variance_ratio_, which returns explained variance (lambdas) as a
proportion of total variance;model.singular_values_, which returns the singular values
and model.components_, which returns the PCA components.

# ## 5.4.8 PCA exercises

+   1. Estimate on the eigenvalues and unit eigenvectors of the matrices
   a. $A = \left(\begin{matrix} \lambda_1 \ \lambda_2 \end{matrix}\right)$
   b. $A = \left(\begin{matrix} v_1 \ v_2 \end{matrix}\right)$

+   2. Using data from "GA-structure-volumes-preterm.csv",12 implement from scratch
t covariance and SVD methods for PCA decomposition (see 5.4.5):
   a. First load the data; we suggest slicing the first ten features initially to make
it easier to debug

```python
import pandas as pd

# first load data
df = pd.read_csv("GA-structure-volumes-preterm.csv",header=None)
structure_volumes = df.values
# Load first 10 features
Features = structure_volumes[:,1:11]
# load labels
Labels = structure_volumes[:,]
```

+   b. Mean the data.
   c. Implement the covariance method:
      (i) estimate the data covariance matrix.
      (ii) evaluate the eigenvectors and values of the covariance matrix.
      (iii) sort eigenvalues and eigenvectors in descending order.
      (iv) project all data onto the PCA eigenspace.
   d. Implement the SVD method:
      (i) return the singular vectors and values of the mean centered data matrix.
      (ii) project all data onto the correct singular vectors.

12 This dataset, skeleton code and solutions for exercises 2–4 are available from github.com/MachineLearning-ingBiomedicalApplications/notebooks.