We did our, we gave the list of potential cheaters to the bank, now the bank's side gave the ball. Their analyst will investigate this list of potential cheaters and take priority into the ones got approved to revise the application, and by investigating deeper, they will find out if the customer really created somehow.

# All code at once (practiced)

```
# Self Organizing Maps (SOM)
# importing Libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Data Preprocessing --
# Importing the Data-set
dataset = pd.read_csv("Credit_Card_Applications.csv")
X = dataset.iloc[:, :-1].values
y = dataset.iloc[:, -1].values

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc = MinMaxScaler(feature_range=(0, 1))
X = sc.fit_transform(X)

# training the SOM
from minisom import MiniSom
som = MiniSom(10, 10, input_len=15, sigma=1.0, learning_rate=0.5)
som.random_weights(X.shape[1])nsom.train_random(data=X, num_iteration=100)

# Visualize the result
from pyplot import plt, pcolor, colorbar, plot, show
bone()
npcolor(som.distance_map(som).T)
colorbar()

markers = ['o', 's']
colors = ['r', 'g']
for i, x in enumerate(X):
    w = som.winner(x)
    plot(w[0]+0.5, w[1]+0.5, markers=markers[i],
emarkeredgecolor=colors[i],
emarkeredfacecolor='None',
emarkersize=10,
emarkeredgewidth=2)
how()

# finding the Frauds
mappings = som.win_map(X) != 0 its output "X", capital X
fraud_list_1 = mappings([8, 6])
fraud_list_2 = mappings([1, 7])
frauds = np.concatenate([mappings([8, 6]), mappings([1, 7])], [0], axis=0)
frauds = sc.inverse_transform(frauds)
```

The SOM changes every time, when we built, so the position of outlier nodes also changes. In this case

```
frauds = np.concatenate((mappings([1, 5]), mappings([4, 7])), axis=0)
```

![](bbox=[0.643, 0.805, 0.893, 0.943])