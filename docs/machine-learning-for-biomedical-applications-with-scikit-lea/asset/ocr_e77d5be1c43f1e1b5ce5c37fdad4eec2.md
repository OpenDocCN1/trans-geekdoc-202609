and convert it to a feature vector. The function to create a feature matrix is provided
next. We can see that we have 4,005 features after processing.

```
import numpy as np

def ConvertMatrices(matrices):
    @ dimensions
    n = matrices.shape[0]
    m = matrices.shape[1]
    D = round(m*m/2)

    @ create feature matrix
    X=np.zeros([n,D])
    for i in range(n):
        index=0
        for j in range(m):
            for k in range(j):
                X[i,index]=matrices[i,j,k]
            index+=1
    return X
```

X = ConvertMatrices(matrices)
print('Feature matrix: ', X.shape)
>>> Feature matrix: (341, 4005)

We would like to predict the age at scan, so we need to extract it from the information
sheet:

```
y = subject_info['age'].to_numpy()
```

The final preprocessing steps are scaling and converting the data into PyTorch tensors.
We will scale the feature matrix X and target vector y to make the convergence\easier for the stochastic gradient-descent optimizer. The PyTorch tensors need to be 2D
and of type float.

```
from sklearn.preprocessing import StandardScaler
import torch
```

```
# Scale the features
scaler = StandardScaler()
X = scaler.fit_transform(X)
```

```
# Scale the targets
```