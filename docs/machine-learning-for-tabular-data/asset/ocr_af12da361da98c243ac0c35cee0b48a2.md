# Pathologies and remedies

decide which feature to keep. Again, domain knowledge can help you make decisions. Data analysis can also contribute with hints based on the association with the target and the data quality of the features at hand, using a of fewer features, fewer missing data, and fewer outliers. Keeping the feature most associated with the target or the one with the highest quality is the best choice.

# Listing 2.3 Finding multicolinear numeric features

Adds more correlated features to the dataset: we pick the first five features, and we duplicate them at the end of the dataset after adding some noise, so they are not the same as the original ones.

Creates a synthetic dataset: the make_classification command will create a sample dataset of slightly correlated features (https://mng.bz/eynqo)

```
import numpy as np
from sklearn.datasets import make_classification
from statsmodels.outliers.influence import variance_inflation_factor

np.random.seed(0)
X, _ = make_classification(n_redundant=0, n_repeated=0, random_state=0)
X = np.hstack([X, X[:, :5] + np.random.random((X.shape[0], 5))])
```

Sets the seed for reproducibility

```
vif = [variance_inflation_factor(X, i) for i in range(X.shape[1])]

for a in range(X.shape[1]):
    for b in range(X.shape[1]):
        if a < b:
            r = np.corrcoef(X[:, a], X[:, b])[0][1]
            if np.abs(r) > 0.90:
                print(f"feature {a} and {b} have r={r:0.3f}")
```

The threshold to report collinearity is in absolute value (correlation will be negative if a feature is reversed). In addition, depending on the stage of the analysis, you can select 0.90, 0.95, or 0.99.

The correlation coefficient is computed using the NumPy function np.corrcoef (https://mng.bz/80hw).

Checking for correlated features by iterating through a correlation matrix, we compute only the coefficients of the lower triangle of the matrix.

Computes the variance inflation factor to spot the features that have the least unique contribution

In the previous example, we deal with highly collinear numeric features in a synthetic dataset. We use two approaches: the variance inflation factor and the Pearson correlation coefficient. The variance inflation factor (VIF) is a typical analysis preparatory