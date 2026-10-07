```
# mega case study : Make a Hybrid Deep Learning model

# importing libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Data Preprocessing
# importing the Data-set
dataset = pd.read_csv("Credit_Card_Applications.csv")
X = dataset.iloc[:, :-1].values
Y = dataset.iloc[:, -1].values

# Feature scaling
from sklearn.preprocessing import MinMaxScaler
sc = MinMaxScaler(feature_range=(0, 1))
X_scaled = sc.fit_transform(X)

# part 2 : Identify the frauds using Self Organizing Maps (SOM)
# Training the SOM
from minisom import MiniSom
som = MiniSom(x=10, y=10, input_len=15, sigma=1.0, learning_rate=0.5)
som.random_weights_init(X)
som.train_random(X, num_iteration=100)

# Visualize the result
from matplotlib.pyplot as pcolor, colorbar, plt
bone = plt.pcolor(som.distance_map(X).T)
colorbar(bone)

markers = ['o', 's']
colors = ['r', 'g']
for i, x in enumerate(X):
    w = som.winner(x)
    plot(w[0]+0.5, w[1]+0.5, markers[y[i]], colors[y[i]],
emarkercolor='None', markersize=10, markeredgewidth=2)
how()

# Finding the Frauds
mappings = som.map(X) # not 'x' its outside the dataset "X"
fraud_list_1 = mappings([5, 5])
fraud_list_2 = mappings([6, 4])
frauds = np.concatenate((mappings([5, 5]), mappings([6, 4])), axis=0)
frauds = sc.inverse_transform(frauds)

# Saving the list to a csv
# save numpy array as csv file
from numpy import saveetxt
# import data
# define data
data = frauds
# save to csv file
savesetxt('frauds.csv', data, delimiter=',')

# part 2 : Going from Unsupervised to Supervised Deep Learning

# creating the matrix of features
```