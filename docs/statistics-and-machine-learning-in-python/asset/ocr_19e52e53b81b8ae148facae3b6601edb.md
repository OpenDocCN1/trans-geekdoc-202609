```
```python
import numpy as np
import scipy.stats as stats
import matplotlib.pyplot as plt as plt
import seaborn as sns
%matplotlib inline
%matplotlib qt
np.random.seed(42)
x = np.random.normal(loc=10, scale=1, size=100)
y = x + np.random.normal(loc=-3, scale=3, size=100) # snr = 1/2
# Permutation: simulate the null hypothesis
nperm = 10000
perms = np.zeros(nperm + 1)
perms[0] = np.corrcoef(x, y)[0, 1]
for i in range(1, nperm):
    perms[i] = np.corrcoef(np.random.permutation(x), y)[0, 1]
# Plot
# Re-weight
weights = np.ones(perms.shape[0]) / perms.shape[0]
plt.hist([perms[perms >= perms[0]], perms], histtype='stepfilled',
         bins=100, label=["t>t obs (p-value)", "t<t obs"],
         weights=[weights[perms >= perms[0]], weights])
plt.xlabel("Statistic distribution under null hypothesis")
plt.axvline(x=perms[0], color='blue', linewidth=1, label="observed statistic")
_ = plt.legend(loc="upper left")
# One-tailed empirical p-value
pval_perm = np.sum(perms >= perms[0]) / perms.shape[0]
# Compare with Pearson's correlation test
_, pval_test = stats.pearsonr(x, y)
print("Permutation two tailed p-value=%.5f. Pearson test p-value=%.5f" % (2*pval_perm, pval_test))
```
```

RuntimeWarning: numpy.dtype size changed, may indicate binary incompatibility. Expected 96, got 88

ImportWarning: can't resolve package from __spec__ or __package__, falling back on __name__ and __path__ return f(*args, **kwargs)

Permutation two tailed p-value=0.06959. Pearson test p-value=0.07355