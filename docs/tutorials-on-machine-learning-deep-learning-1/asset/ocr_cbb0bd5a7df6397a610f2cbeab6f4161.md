# All code at once (practiced version) Principle Component Analysis (PCA)

```
# Library
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
```

```
# Data Extract
dataset = pd.read_csv("Wine.csv")
X = dataset.iloc[:, :13].values
y = dataset.iloc[:, 13].values
```

```
# Data Split
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.20, random_state=0)
```

```
# Feature_Scaling
from sklearn.preprocessing import StandardScaler
# y need not be scaled.
st = StandardScaler()
x_train = st.fit_transform(X_train)
x_test = st.transform(X_test)
```

```
# Applying PCA
from sklearn.decomposition import PCA
dcmpose_pca = PCA(n_components=2)
X_train = dcmpose_pca.fit_transform(X_train)
x_test = dcmpose_pca.transform(X_test)
explained_variance = dcmpose_pca.explained_variance_ratio_
```

```
# Fit dataset to Logistic regression
from sklearn.linear_model import LogisticRegression # class
# train and test classifier
classifier = LogisticRegression(random_state=0) # create object
classifier.fit(X_train, y_train) # fit the dataset
```

```
# Predict
y_pred = classifier.predict(X_test)
# Making the confusion matrix use the function "confusion_matrix"
# Class in capital letters, functions are small letters
from sklearn.confusion_matrix(y_true=y_test, y_pred=y_pred)
# parameters of cm: y_true: Real values, y_pred: Predicted values
```

```
# Visualising the training results
from matplotlib.colors import Colormap
X_set, y_set = X_test, y_test
X1, X2 = np.meshgrid(np.arange(X_set[:,0].min(), X_set[:,0].max() + 0.01, step=0.01), np.arange(X_set[:,1].min(), X_set[:,1].max() + 0.01, step=0.01))
plt.contour(X1, X2, classifier.predict(np.array([X1.ravel(), X2.ravel()]).T).reshape(X1.shape), alpha=0.5, cmap=Colormap(['red', 'orange']))
plt.xlim(X1.min(), X1.max)
plt.ylim(X2.min(), X2.max)
for i, j in enumerate(np.unique(y_set)):
    plt.scatter(X_set[:,0], X_set[:,1], c=Colormap(['red', 'orange'])[i], label=j)
plt.xlabel('PC1')
plt.ylabel('PC2')
plt.legend()
plt.show()
```