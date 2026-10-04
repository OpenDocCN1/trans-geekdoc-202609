# Processing features 201

grid space. The mapping returns a feature presenting over 2,000 distinct values, which makes it a high cardinality categorical feature without any doubt. In 6.3, we first bin latitude and longitude and combine them by summing them in a way that results in a distinct code for every bin of latitude and longitude. Binning is obtained by dividing the range between the feature's minimum and maximum value into equal parts. Also, the code snippet performs binning on two features, resulting in sets of integer values for each feature. The values of one feature are multiplied by a factor of 10, which is larger than the maximum value of the other. This ensures that a unique value is always obtained when the two sets of values are summed, regardless of the specific values used.

# Listing 6.3 Creating a high cardinality categorical feature

```
def bin_2_cat(feature, bins=100):
    min_value = feature.min()
    bin_size = (feature.max() - min_value) / bins
    bin_values = (feature - min_value) / bin_size
    return bin_values.astype(int)

data['coordinates'] = {
    bin_2_cat(data['latitude']) * 1000
    + bin_2_cat(data['longitude'])
}
high_card_categorical += ['coordinates']

print(data['high_card_categorical'].nunique())
```

The code snippet shows by checking the number of unique values for each feature among the high cardinality ones:

neighbour 221
coordinates 2259

With two categorical features considered high cardinality, we can add to our preprocessing pipeline the TargetEncoder from category-encoders.

# Listing 6.4 Using target encoding in the pipeline

```
from category_encoders.target_encoder import TargetEncoder
from XGBoost XGBClassifier
from sklearn.model_selection import KFold, cross_validate
from sklearn.metrics import accuracy_score, make_scorer
ntarget_encoder = TargetEncoder(cols=high_card_categorical, smoothing=0.5)
accuracy = make_scorer(accuracy_score)
cv = KFold(5, shuffle=True, random_state=0)
xgb = XGBClassifier(booster='gtree', objective='reg:logistic', n_estimators=300)
```