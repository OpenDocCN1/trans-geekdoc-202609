# # Chapter 9 More Regression Methods

```
assert (X.min() < self.cut_points[0] and
self.cut_points[-1] < X.max())

recorded_X = self._recode(X)
# even though the _inner_ model is fit without an intercept,
# our piecewise model *does* have a constant term (but see notes)
self.coeffs_ = (linear_model.LinearRegression(fit_intercept=False)
.fit(recorded_X, y).coef_)

def _recode(self, X):
    cp = self.cut_points
    npieces = len(cp) + 1
    recorded_X = np.eye(npieces)[np.searchsorted(cp, X.flatten())]
    return recorded_X

def predict(self, X):
    check_is_fitted(self, 'coeffs_')
    X = check_array(X)
    recorded_X = self._recode(X)
    return rdot(self.coeffs_, recorded_X)
```

![](bbox=[0.2, 0.49, 0.8, 0.65])

To test and demonstrate that code, let's generate a simple example dataset we can train on.

```
In [24]:
fr = np.random.randint(0,10,(100,1)).astype(np.float64)
cp = np.array([3,7])
tgt = np.searchsorted(cp, fr.flat) + 1
fig, ax = plt.subplots(1,1,figsize=(4,3))
ax.plot(fr, tgt, '.');
```

![](bbox=[0.2, 0.91, 0.8, 1.0])