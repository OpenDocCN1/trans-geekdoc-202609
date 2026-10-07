Note that we have created the column named ConcatenatedString. We will use the data in this column to create TF-IDF vectors.

The following code forms TF-IDF vectors:

```
from sklearn.feature_extraction.text import TfidfVectorizer
tfidfconverter = TfidfVectorizer(max_features = 90000, ngram_range = (1,1))
arNonNumericTIDF = tfidfconverter.fit_transform(dfNonNumeric)
ConcatenatedString(df) = pd.DataFrame(arrNonNumericTIDF,
columns = tfidfconverter.get_feature_names())
print(dfNonNumericTIDF.shape)
(4706, 53)
```

Note that we now have 53 features.

The following code concatenates the features containing numeric data and the TF-IDF vectors:

```
import pandas as pd
dfFormModel = pd.concat([dfNonNumeric, dfNonNumericTIDF], axis = 1)
import pickle
print(dfFormModel)
pickle.dump(dfFormModel, open(".Columns", 'wb'))
(4706, 2327)
```

Note that we now have 4,706 data points, each containing 2,327 features. The dataset is stored in the variable dfFormModel.

The data frame dfFormModel contains only numeric data. We can use this data frame to balance the data. The following code creates a balanced dataset:

```
import imblearn as ib
```