+   b) Read in the data file (which you should already have in your directory using the data provided in Chapter 3).

```
```python
swiss = pd.read_csv("swiss.csv")
swiss['ones'] = 1
X = np.array(swiss.drop(["Fertility"], axis=1))
Y = np.array(swiss["Fertility"])
x = X - np.mean(X, axis=0)
y = Y - np.mean(Y)
colnames = swiss.columns
```
```

+   c) Run ridge regression from λ = 10^0 to 10^7.

```
```python
n_lambdas = 200
lambdas = np.logspace(0, 7, n_lambdas)
coefs = []
d = X.shape[1]
for a in lambdas:
    ridge = Ridge(alpha=a)
    ridge.fit(X, Y)
    coefs.append(ridge.coef_[0:d-1])
```
```

+   d) Plot the ridge traces.

```
```python
plt.figure(figsize=(10, 8))
ax = plt.gca()
ax.plot(lambdas, coefs)
ax.set_xscale('log')
plt.xlabel('lambda')
plt.ylabel('beta 1-5')
plt.title('LS-ridge coefficients as a function of lambda')
betal = coefs[0]
pos = np.zeros(len(betal))
for i in range(len(betal)):
    plt.annotate(xy=[lambdas[0], betal[i] + pos[i]], text=colnames[i+1])
plt.axis('tight')
plt.show()
```
```

+   e) Replace the ridge code segment above with LASSO:

```
```python
n_lambdas = 200
lambdas = np.logspace(-2, 3, n_lambdas)
coefs = []
d = X.shape[1]
for a in lambdas:
```
```