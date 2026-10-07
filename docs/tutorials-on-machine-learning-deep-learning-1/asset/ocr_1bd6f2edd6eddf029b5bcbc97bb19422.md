```
print(old_x)
from sklearn.preprocessing import LabelEncoder, OneHotEncoder
from sklearn.compose import ColumnTransformer
```

```
# Encode Count Column
t = ColumnTransformer(transformers=[('Encoding', OneHotEncoder(), [0])], remainder = 'passthrough')
# remainder='passthrough' for remaining columns to be unchanged
old_x = ct.fit_transform(old_x) # convert this to NumPy Array
print(old_x)
old_x = np.array(old_x)
print(old_x)
```

```
# Encode dependent vector Column
label_encode = LabelEncoder()
old_y = label_encode.fit_transform(old_y)
print(old_y)
```

```
# ---------------- Feature Scaling
from sklearn.preprocessing import StandardScaler
sc = StandardScaler()
old_x = sc.fit_transform(old_x)
print(old_x)
```

```
# ---------------- Splitting the Data and Test
from sklearn.model_selection import train_test_split
x_train, x_test, y_train, y_test = train_test_split(old_x, old_y, test_size = 0.2, random_state = 0)
print(x_train)
print(y_train)
print(x_test)
print(y_test)
```

```
#### List listing #####
# # Initialize List
# List = [50, 70, 30, 20, 90, 10, 50]
```

```
# # Display list
# print(List[:])
```

```
# # Index -1 represents the last element of the List(considering n as the length of the List). Lists can also be manipulated using negative indexes also.
```

```
# # Initialize List
# List = [50, 70, 30, 20, 90, 10, 50]
```

```
# # Display list
# print(List[-7::1])
```

```
# # Display list
# print(List[1:5])
```

```
# python prcts_dt_prep.py
```

# Current codes

```
# Data Preprocessing Tools
# Importing the libraries
import numpy as np
import matplotlib.pyplot as plt
```