# Scaling

Our data is spread over a wide range with different scales i.e. not suitable to train models. We need to bring our data in a more appropriate scale, we can do so using the MinMaxScaler class and it's fit_transform() method of the scikit-learn library. We can scale our data in the range of 0 to 1 which is the most appropriate range for the algorithms

```
import pandas as pd
from sklearn import preprocessing
dt = pandas.read_csv('trees.csv')
ar = dt.values # array
# Scaler Object
Sclr = preprocessing.MinMaxScaler(feature_range=(0,1))
skl_ar = Sclr.fit_transform(ar) #Scaling
# Scaled data
skl_dt = pandas.DataFrame(skl_ar, columns=['S.No.', 'Height', 'Height', 'Volume'])

skl_dt.round(1).loc[5:10]
```

| S.No. | Height | Height | Volume |
|---|---|---|---||
| 5 | 0.2 | 0.2 | 0.8 | 0.1 |
| 6 | 0.2 | 0.2 | 0.1 | 0.1 |
| 7 | 0.2 | 0.2 | 0.5 | 0.1 |
| 8 | 0.3 | 0.2 | 0.7 | 0.2 |
| 9 | 0.3 | 0.2 | 0.5 | 0.1 |
| 10 | 0.3 | 0.2 | 0.7 | 0.2 |

You can compare the values with the values beside unscaled. If you want to change the range to say 0-100 through the feature_range parameter in MinMaxScaler while the scaler class intialization

| S.No. | Girth | Height | Volume |
|---|---|---|---||
| 5 | 10.7 | 81 | 18.8 |
| 6 | 10.8 | 83 | 19.7 |
| 7 | 7 | 11.0 | 66 | 15.6 |
| 8 | 8 | 11.0 | 75 | 18.2 |
| 9 | 9 | 11.1 | 80 | 22.6 |
| 10 | 10 | 11.2 | 75 | 19.9 |