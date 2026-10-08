```
plt.subplot(grid_width, grid_height, i+1)
plt.scatter(X[:,:0], X[:,:1], c=colors)
```

```
# step 1: determine assignments / responsibilities
# is this inefficient?
for k in xrange(K):
  for n in xrange(N):
    R[n,k] = np.exp(-beta*d(M[k], X[n])) / 
np.sum(np.exp(-beta*d(M[j], X[n])) for j in xrange(K))
```

```
# step 2: recalculate means
for k in xrange(K):
  M[k] = R[:,k].dot(X) / R[:,k].sum()
```

```
costs[i] = cost(X, R, M)
if i > 0:
  if np.abs(costs[i] - costs[i-1]) < 10e-5:
    break
```

```
plt.show()
```

```
def main():
```