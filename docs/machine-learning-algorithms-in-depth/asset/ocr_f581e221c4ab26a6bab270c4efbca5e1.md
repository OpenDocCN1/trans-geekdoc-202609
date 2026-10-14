```
1: class perceptron
2: function fit(X, y):
3: k = 1
4: for epoch = 1, 2, ..., num_epochs
5:   for i = 1, 2, ..., N
6:     if y_i (θ · x_i + θ0) ≤ 0
7:       η = 1/(k+1) → Updates the learning rate
8:       k += 1
9:       θ = θ + η y_i x_i
10:      θ0 = θ0 + η y_i → Updates the theta
11:    end if
12:  end for
13: end for
14: return θ, θ0
15: function predict(X):
16: ŷ = sign (θ · X + θ0)
17: return ŷ
```

Figure 5.5 Perceptron algorithm pseudo-code

We now have all the tools to implement the perceptron algorithm from scratch! In the following code listing, we classify irises by training the perceptron algorithm on the training feature data and making a prediction based on the test data.

# Listing 5.1 Perceptron algorithm

```
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

from scipy.stats import randint
from sklearn.datasets import load_iris
from sklearn.metrics import confusion_matrix
from sklearn.model_selection import train_test_split

class perceptron:
    def __init__(self, num_epochs, dim):
        self.num_epochs = num_epochs
        self.theta0 = 0
        self.theta = np.zeros(dim)

    def fit(self, X_train, y_train):
        n = X_train.shape[0]
        dim = X_train.shape[1]

        k = 1
        for epoch in range(self.num_epochs):
            for i in range(n):
                idx = randint.rvs(0, n-1, size=1)[0] ← Samples random point
                if (y_train[idx] * (np.dot(self.theta, X_train[idx,:]) + self.theta0) <= 0): ← Hinge loss
                    eta = pow(k+1, -1) ← Updates learning rate
                    k += 1
```