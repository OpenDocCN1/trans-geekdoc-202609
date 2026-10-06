In [1]: import pandas
from sklearn.tree import DecisionTreeClassifier
from sklearn.preprocessing import LabelEncoder
from sklearn.metrics import classification_report
from sklearn.model_selection import train_test_split
dt = pandas.read_csv('play_stats.csv')

| Temperature | Humidity% | Rain | Play |
|---|---|---|---||
| 0 | 34 | 74.2 | Yes | No |
| 1 | 19 | 68.2 | No | No |
| 2 | 28 | 67.2 | Yes | Yes |
| 3 | 29 | 66.6 | Yes | No |
| 4 | 26 | 57.9 | Yes | Yes |
| ... | ... | ... | ... | ... |
| 996 | 28 | 62.0 | Yes | Yes |
| 997 | 27 | 71.4 | Yes | No |
| 998 | 19 | 54.1 | No | Yes |
| 999 | 32 | 57.4 | Yes | No |
| 1000 | 24 | 61.4 | Yes | No |

1001 rows × 4 columns

We need to encode the Rain and Play labels so create an encoder and encode the labels

```
In [2]: Enc = LabelEncoder()
Enc.fit(['Yes', 'No'])
for col in ['Rain', 'Play']:
 dt[col] = Enc.transform(dt[col])
```

We simply created a Enc encoder using the LabelEncoder and then fitted the 'Yes' and 'No' values. Then using a loop and the transform() we encoded the labels
Note that you may get an error if you re-run the cell because the labels are encoded so the transform() will recieve numbers this time