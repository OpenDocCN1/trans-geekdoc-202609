+   b) Load the dataset and define the **X** and **y** values.

```
from sklearn.datasets import load_diabetes
diabetes_dataset = load_diabetes()

diabetes = pd.DataFrame(diabetes_dataset.data, \\
    columns=diabetes_dataset.feature_names)
diabetes['Y'] = diabetes_dataset.target
diabetes["ones"] = 1
X = np.array(diabetes.drop(["Y"],axis=1))
Y = np.array(diabetes["Y"])
```

+   c) Define the needed function for the log-cosh loss (reuse the code given in the previous problem).

+   d) Implement the iterative IQR code.

```
n = X.shape[0]
d = X.shape[1]
outliers = n
num_outliers = 0
Ifactor = 1.5
while (outliers > 0) :
    initbetaLC = np.random.randn(d) / 10.
    result = minimize(LC,initbetaLC,method='BFGS')
    betaLC = result.x
    r1 = Y-np.matmul(X,betaLC)

    quantiles = np.percentile(r1,[25, 50, 75])
    m = quantiles[1]
    IQR = quantiles[2]-quantiles[0]
    IQR_upper = quantiles[2]+Ifactor*(IQR)
    IQR_lower = quantiles[0]-Ifactor*(IQR)

    outliers = np.sum(r1 < IQR_lower) + \\
        np.sum(r1 > IQR_upper)

num_outliers += outliers
Ifactor += 50/n
if (outliers > 0):
    k = 0
    outliers = np.sum(r1 > IQR_upper) + \\
        np.sum(r1 < IQR_lower)
    rows_to_delete = np.zeros(outliers)
    for i in range(X.shape[0]) :
        if(r1[i] \\
```