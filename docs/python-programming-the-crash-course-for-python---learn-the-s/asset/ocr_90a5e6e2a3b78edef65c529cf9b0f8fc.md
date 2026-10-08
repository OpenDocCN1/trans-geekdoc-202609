create one of our own K-Means clustering algorithms, and how to add in some of the soft k-means to any code that you would like to work with. Some of the coding that you need to make this happen includes:

```
import numpy as np
import matplotlib.pyplot as plt
```

```
def d(u, v):
    diff = u - v
    return diff.dot(diff)
```

```
def cost(X, R, M):
    cost = 0
    for k in xrange(len(M)):
        for n in xrange(len(X)):
            cost += R[n,k]*d(M[k], X[n])
return cost
```

After this part, we are going to take the time to define your function so that it is able to run the k-