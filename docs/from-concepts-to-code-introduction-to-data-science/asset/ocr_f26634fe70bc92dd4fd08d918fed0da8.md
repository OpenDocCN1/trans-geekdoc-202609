# Modeling with Linear Regression

```
from sklearn.datasets import fetch_california_housing
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LinearRegression
from sklearn.metrics import r2_score # R-squared
```

import as pd

housing = fetch_california_housing()

```
['data': array([[41., 6.9841698, ..., 2.5555556,
  [8.3904, 122.123, ..., 2.1904183],
  [6.2381378, 8.2881599, ..., 2.8025989],
  [7.2574, 121.224, ...],
  [1.7, 5.2565473, ..., 2.3253591],
  [1.4672, 5.3295318, ..., 2.12308517],
  [2.0568, 5.25471688, ..., 2.3466813]]]),
 'frame': {
  'target': ['MedHouse'],
  'target_names': ['MedHouse'],
  'HouseAge',
  'Avenue',
  'Population',
  'latitude',
  'longitude'},
 'DESC': '...California Housing Dataset...\nNumber of Attributes: 8, predictive attributes and the target is:\nMedian house value in block group - Information median income in block group
median house age in block group - Avenue average number of
per household - average persons per household - average block location
Population - block group population - Avenue - average number of house'}
```

FIGURE 13.2: California Housing Data Snapshot

Checking the data type with (housing) shows this specialized object: sklearn.utils.Bunch. The object appears to contain key:value pairs, we request the:

```
housing.keys()
```

```
OUT:
dict_keys(['data', 'target', 'frame', 'target_names',
'feature_names', 'DESC'])
```

The key DESCR provides descriptive data about the dataset. The name of the target variable is MedHouseValue, which is the median house value in units of 100K. The first two values are 4.526 and 3.585. Predictors include