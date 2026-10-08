# 198 ■ Concise Introduction to Machine Learning

```
import numpy as np
import matplotlib.pyplot as plt
import tensorflow as tf
from sklearn.decomposition import PCA
import skimage.util

# Load data.
(x, train, y, test) = tf.keras.datasets.mnist.load_data()

# Restrict data to a subset of digits and show examples.
k = 25
data, label = train[k], y[np.random.choice(train.shape[0], k)]
montage = skimage.util.montage(data)
plt.imshow(montage, cmap='Grays')
ax = plt.figure()
ax.get_axes()[0].set_ticks([])
ax.get_axes()[0].set_yticks([])

# Reshape images into arrays
train = np.reshape(data, (data.shape[0], 
    data.shape[1]*data.shape[2]))

# Initialize Principal Component Analysis
ncommp = 3
pca = PCA(n_components=ncomp)
subspace = pca.transform(train)

# Find the principal components and transform data to this
# Display data points.
colors = [(1,0,0), (0,1,0), (0,0,1), (1,1,0), (0,1,1)]
fig = plt.figure()
if ncomp == 2:
    for i in range(0,k):
        plt.scatter(X[data.label == i], Y[data.label == i],
                    facecors='none', edgecolors=colors[i],
                    s=10)
else:
    ax = plt.figure(projection='3d')
    for i in range(0,k):
        ax.scatter(X[data.label == i], Y[data.label == i], Z[data.label == i],
                    facecors='none', edgecolors=colors[i],
                    s=10)
plt.show()

# Reconstruct examples.
rec = pca.inverse_transform(subspace[choice])
rec_digits = rec.reshape(data.shape[1], data.shape[2])
montage = skimage.util.montage(rec_digits)
plt.imshow(montage, cmap='Gray')
ax = plt.figure()
ax.get_axes()[0].set_ticks([])
ax.get_axes()[0].set_yticks([])
```

Listing 7.1: PCA separating digits in Python. For MALAB go to https://github.com/ACFaul/Dimensionality-Reduction-Matlab.