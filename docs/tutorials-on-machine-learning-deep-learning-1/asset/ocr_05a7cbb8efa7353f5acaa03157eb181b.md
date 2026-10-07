![](bbox=[0.094, 0.215, 0.905, 0.225])

# # All code at once (instructor version)

```
# PCA

# Importing the libraries
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

# Importing the dataset
dataset = pd.read_csv("Wine.csv")
X = dataset.iloc[:, 0:13].values
y = dataset.iloc[:, 13].values

# Splitting the dataset into the Training and Test set
from sklearn.model_selection import train_split
X_train, X_test, y_train, y_test = train_split(X, y, test_size=0.2, random_state=0)

# Feature Scaling
from sklearn.preprocessing import StandardScaler
sc = StandardScaler()
X_train = sc.fit_transform(X_train)
X_test = sc.transform(X_test)

# Applying PCA
from sklearn.decomposition import PCA
pca = PCA(components=2)
X_train = pca.fit_transform(X_train)
X_test = pca.transform(X_test)
explained_variance = pca.explained_variance_ratio_

# Fitting Logistic Regression to the Training set
from sklearn.linear_model import LogisticRegression
classifier = LogisticRegression(random_state=0)
classifier.fit(X_train, y_train)

# Predicting the Test results
y_pred = classifier.predict(X_test)

# Making the Confusion Matrix
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(y_test, y_pred)

# Visualising the results
from matplotlib.colors.colors import ListedColormap
X_set, y_set = np.vstack((X_train, X_test)), np.vstack((y_train, y_test))
X1, X2 = np.arange(X_set[:, 0].min(), X_set[:, 0].max() + 1, 0.01), 
np.arange(X_set[:, 1].min(), X_set[:, 1].max() + 1, 0.01)
plt.contour(X1, X2, classifier.predict_np(X1.ravel(), X2.ravel())).reshape(X1.shape),
alpha=0.3, cmap=ListedColormap(('red','green', 'orange'))
plt.xlim(X1.min(), X1.max())
plt.ylim(X2.min(), X2.max())
for i, j in enumerate(y_set):
    plt.scatter(X_set[y_set == j, 0], j,
                c=ListedColormap(('red', 'green', 'orange'))(i), label = j)
```