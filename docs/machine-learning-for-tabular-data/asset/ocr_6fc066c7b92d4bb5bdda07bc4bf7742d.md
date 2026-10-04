# Preparing and exploring your data

degrees_to_meters. We can verify the results by inspecting the first five rows of the resulting dataset:

```
min_distances.head()
```

Figure 7.5 shows the results, representing the contents from the created min_distances DataFrame.

| listing_id | nearest_convenience_store | nearest_train_station | nearest_airport | nearest_bus_station |
|---|---|---|---|---||
| 0 | 196777 | 475.837692 | 666.488917 | 8326.122756 | 829.211343 |
| 1 | 776070 | 114.974697 | 384.929313 | 5430.623850 | 453.968550 |
| 2 | 3427384 | 410.735809 | 367.589007 | 6343.224450 | 417.734902 |
| 3 | 905944 | 155.409734 | 268.125319 | 2929.393383 | 783.601883 |
| 4 | 3514008 | 160.799537 | 836.808222 | 5532.347474 | 619.141342 |

Figure 7.5 The first five rows of the min_distances DataFrame

Having the minimum distance to our selection of venues for each listing of our dataset, we now proceed with putting together all these new features into a final dataset of predictors and extracting a target series or vector to be used for modeling.

# 7.1.4 Finalizing your data

After creating some additional features, we can finalize our predictive features and their target. In 7.7, we join the summary_listing dataset to the minimum distance to our landmarks (airports, subway, train stations, convenience stores). We rearrange the joined data with respect to our target: the mean price we computed in the price_stats_ordered dataset.

+   7.7 Assembling data

```
summary_listings_features = [
'neighbourhood',
'coordinates',
'room_type',
'minimum_nights', 'number_of_reviews', 'days_since_last_review',
'reviews_per_month', 'calculated_host_listings_count',
'availability_365', 'number_of_reviews_ltm',
'number_of_beds_ltm',
'number_of_bedrooms', 'number_of_baths',
'type_of_accommodation', 'score', 'is_new',
'is_studio', 'has_shared_bath', 'has_half_bath',
'imperial_palace_distance'
]
```

```
summarized = summary_listings[['id']] +
```