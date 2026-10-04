# 216 CHAPTER 6 Advanced feature processing methods

```
n_estimators=300,
max_depth=4,
min_child_samples=3)
```

boruta_selector = BorutaPy(estimators=lgbm, n_estimators='auto', verbose=2)
boruta_selector.fit(X, target_median)
selected_features = boruta_selector.support_
selected_data = column_transform.get_feature_names_out() [selected_features]
print(selected_data)

The result is reached after 9 iterations, and this time, we have an increased number of rejected features:

+   - Iteration: 9 / 100
- Confirmed: 8
- Tentative: 0
- Rejected: 6

```
[['low_card_categories_neighbourhood_group_Manhattan',
'low_card_categories_neighbourhood_room_type_Entire_home/apt',
'high_card_categories_neighbourhood_numeric_minimum_nights',
'numeric_number_of_reviews_numeric_reviews_per_month',
'numeric_calibrated_host_listings_count_numeric_availability_365']]
```

LightGBM not only converges quickly, but it splits in leaves, allowing the creation of a performing model with many more features than XGBoost.

In our example we have trained on all the available data. Still, you can consolidate the dataset by using all the selected features in folds or by those selected a minimum number of times across the folds.

# 6.2.3 Forward and backward selection

One limitation of Boruta is that it selects all the relevant features for your problem but not the essential ones. This means you might end up with a list with redundant and highly correlated features that can be cut to a shorter selection. After applying Boruta, we suggest resorting to a feature selection procedure, as implemented in the Scikit-learn SequentialFeatureSelector. This procedure performs forward selection or removes by backward elimination from your selection based on their performance on the prediction in a greedy fashion—that is, always picking up the best-performing choice, based on cross-validation score, in terms of addition or discard. The technique rely on the learning algorithm and its objective function. Hence, selection will always be the best possible. Since it is a greedy procedure, there is always the risk of choosing a local optimum set.

Sequential selection is a very effective procedure in reducing the number of features you have to deal with. Still, it is quite time-consuming because the algorithm has to evaluate all the candidates at each round. In the forward procedure, this will turn slower and slower as you proceed because, despite having fewer candidates to evaluate, the increasing number of features used will slow down the training. However,