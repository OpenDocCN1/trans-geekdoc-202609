# Selecting features

n_estimators hyperparameter, which can be empty, set to an integer, or set to "auto"
where the number of trees is decided upon the size of the dataset. Other important
parameters in Boruta are max_iter, the number of rounds of testing, usually set to 100,
an the alpha threshold for the binomial test, which can be increased from 0.05 to allow
features to be retained or decreased for more features to be discarded.

# Listing 6.10 Boruta selection

```
from XGBoost import XGBClassifier
from boruta import BorutaPy
xgb = XGBClassifier(booster='gtree',
objective='logistic',
n_estimators=300,
max_depth=4,
min_child_weight=3)

X = column_transform.fit_transform(data, target_median)
boruta_selector = BorutaPy(estimator=xgb, n_estimators='auto')
boruta_selector.fit(X, target_median)
selected_features = boruta_selector.support_
selected_data = column_transform.get_feature_names()[selected_features]
print(selected_data)
```

Initializes a BorutaPy feature
selection object using an
XGBClassifier

Transforms the input data,
performing any necessary
preprocessing steps

Retrieves a Boolean mask of features
determined by the Boruta feature selector

Fits the Boruta feature selector

After a few iterations, you should get the results of only a single feature discarded asnnot relevant to the problem:

```
Iteration: 50 / 100
Confirmed: 13
Tentative: 0
Rejected: 0
[low_categories = neighborhood_group_Bronx]
[low_categories = neighborhood_group_Brooklyn]
[low_categories = neighborhood_group_Manhattan]
[low_categories = neighborhood_group_Queens]
[low_categories = room_type_Entire_home/apt]
[low_categories = room_type_Private_room]
[low_categories = room_type_shared_room]
[high_card_categories = numeric_minimum_nights]
[numeric_number_of_reviews = 'numeric_reviews_per_month']
[numeric_calculated_host_listings_count = 'numeric_availability_365']
```

The same procedure can be executed using LightGBM as predictor, instead of
XGBoost:

```
from lightgbm import LGBMClassifier
lgbm = LGBMClassifier(boosting_type='gbdt',
```