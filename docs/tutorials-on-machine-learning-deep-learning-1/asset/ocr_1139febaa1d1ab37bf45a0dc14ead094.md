Encode "Geography" columns using OneHotEncoder to create 3 dummy variables.

Avoiding dummy variable: To avoid dummy variable, we exclude the first column (index 0)

```
X = X[:,1]
```

```
ct = ColumnTransformer(transformers = [['encoding', OneHotEncoder(), [1]]], remainder = 'passthrough')
ct = ct.fit_transform(X)
X = np.array(X) # convert this output to numpy array
X = X[:,1] # excluding index column to avoid dummy-variable trap
```

**Data-Split: We use test_size = 0.2** because of oversampling, so 8000 for training and 2000 for testing.

```
# Data Split
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=0)
```

**Feature-Scaling:** In ANN and deep learning need feature scaling. It is thoroughly compulsory and because there is going to be a lot of computation and all parallel computations So we need to apply feature-scaling to ease of these calculations.

+   And we don't want to have one dominant variable anchoring.

```
from sklearn.preprocessing import StandardScaler
y = dependent variable, need not to be scaled: categorical variable, and or 1
st = StandardScaler()
X_train = st.fit_transform(X_train)
X_test = st.transform(X_test)
```

# Data-Preprocessing All at once

```
# Artificial Neural Network
# Install: TensorFlow, Keras and Theano Libraries.

import lib
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
```

```
# Data Extract
dataset = pd.read_csv("Churn_Modeling.csv") # this can be used
X = dataset.iloc[:, 3:-1] # all columns from index 3, excluding indexed column
y = dataset.iloc[:, 13] # values The last column
```

```
# Encoding Categorical
from sklearn.preprocessing import LabelEncoder, OneHotEncoder
from sklearn.compose import ColumnTransformer
```

```
# Encoding "Gender" using OneHotEncoder. "Geography" is in "3rd-column", X[:, 2]
label_encode = LabelEncoder()
y = np.array(y) # if X = "dataset.loc[:, 3:13]" then it is needed if X is not an array. I.e. "values" not applied
X[:, 2] = label_encode.fit_transform(X[:, 2])
print(X)
```

```
# Encoding "Geography" using OneHotEncoder. "Geography" is in "2nd-column", handle
ct = ColumnTransformer(transformers = [['encoding', OneHotEncoder(), [1]]], remainder = 'passthrough')
remainder = 'passthrough' for remaining columns be unchanged
ct = ct.fit_transform(X)
X = np.array(X) # convert this output to numpy array
print(X)
X = X[:,1] # excluding index column to avoid dummy-variable trap
```

```
# Data Split
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=0)
```

```
# Feature-Scaling after Data Split
```