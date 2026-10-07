```
'batch_size': [24],
epochs': [5],
toptmizer': ['adam', 'rmsprop']
}

grid_sch = GridSearchCV(
    estimator=ann_classifier_for_tune,
    param_grid=params_dic,
    scoring='accuracy',
cv=5
)

grid_sch = grid_sch.fit(X_train, y_train)
best_parameters = grid_sch.best_params_
best_accuracy = grid_sch.best_score_
print(f'\n{best_parameters} \nAccuracy = {best_accuracy}')

# python prct_ANN_lmry_Drpg_grid_sch.py
```

**Execute-by (do not execute all-code)** Since we're not gonna execute previous ANN-part-2 with Dropout-regularization and Evaluations-part (k-Fold):

+   **[1].** First need to import the data and run the data processing phase;
**[2].** Finally execute the **last section, parameter tuning**, we have the whole tuning.

# All code at once (processed, Used small values in parameter tuning)

```
# Artificial Neural Network
# Install: Tensorflow, Keras and Libraries.

import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# -------------------------------------- Part 1 : Data Preprocessing ---------------------------------------
# Data Extract
dataset = pd.read_csv('Churn_Modelling.csv') # This can be used
X = dataset.iloc[:, 3:-1] # all columns from index 3, excluding 1 indexed column
y = dataset.iloc[:, 0] # values which is the target column

# -------------------------------------- Categorical Data -----------------------------------------------------
from sklearn.preprocessing import LabelEncoder, OneEncoder
from sklearn.compose import ColumnTransformer

# Encode 'Gender' using LabelEncoder
 'Gender' is in 3rd-column, X[:,2]
label_encoder = LabelEncoder().fit_transform(dataset['Gender'])
X = np.array(X) # X.values is needed if X is not an array. ."values" not applied
X = label_encoder.fit_transform(X[:,2])
print(X)

# For a data-set we can still encode "Key" using Columns
# Encode 'Geography' using OneEncoder. "Geography" is in 2nd-column, X[:,1]
t = ColumnTransformer(transformers=[('encoding', OneEncoder(), [[1]])], remainder='passthrough')
ct = transformer.fit_transform(X) # for remaining columns to be unchanged
X = ct.fit_transform(X)
X = np.array(X) # convert this to Numpy array
print(X)
X = X[:, :1] # Excluding 0-indexed column to avoid dummy-variable type

# ------------------------------------------------------Data Split -----------------------------------------------------
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state = 0)
```