# CHAPTER 7 An end-to-end example using XGBoost

algorithms, not just gradient boosting. Ideally, it would be better to have multiple pipelines based on how each model deals with the different features. For instance, in our pipeline, we are going to ordinarily encode a code of categorical features, and such encoding, for tree-based models, doesn't work properly with linear models. However, having unique pipelines can lead to better performance, and it can also become a maintenance nightmare. The human effort required to create and manage multiple pipelines may outweigh the marginal gains achieved by customizing each pipeline for specific models. Therefore it is better to decide on multiple pipelines if you have evidence that it is worth it.

Let's carry on classifying the kinds of features that we will be using into categorical, numeric, binary features:

```
categorical = {
  'room_type',
  'neighbourhood_more_than_30',
  'type_of_accommodation',
  'coordinates'
}\umeric = [
  'minimum_nights',
  'number_of_reviews',
  'days_since_last_review',
  'reviews_per_month',
  'calculated_host_listings_count',
  'availability_365',
  'score',
  'number_of_reviews_ltm',
  'number_of_reviews_ltm_ratio',
  'number_of_bedrooms',
  'number_of_beds',
  'number_of_baths',
  'imperial_palace_distance',
  'nearest_convenience_store',
  'nearest_train_station',
  'nearest_airport',
  'nearest_bus_station',
  'nearest_subway'
]inary = [
  'is_new',
  'is_studio',
  'has_shared_bath',
  'has_half_bath'
]
```

A further inspection of the categorical features is necessary because we need to understand whether to treat them as high cardinality or not. We can understand better what to do after having counted how many unique values each categorical feature has:

```
for feat in categorical:
print(f"{{feat}} has {X[feat].unique()} unique values")
```