want to define a bucket for each mode, placing the boundaries between the peaks. Whether you use the percentiles or the modes, you need to analyze the distribution of your idea ahead of time, just like we had to measure the mean and standard deviation ahead of time to normalize the housing_median_age column.

# Categorical Features

For categorical features such as ocean_proximity, there are several options. If it is already represented as a category ID (i.e., an integer from 0 to the max ID), then you can use the categorical_column_with_identity() function (specifying the max ID). If not, and you know the list of all possible categories, then you can use categorical_column_with_vocabulary_list():

```
ocean_prox_vocab = ['IE OCEAN', 'INLAND', 'ISLAND', 'NEAR BAY', 'NEAR OCEAN']
ocean_proximity = tf.feature_column.categorical_column_with_vocabulary_list(
    'ocean_proximity', ocean_prox_vocab)
```

If you prefer to have TensorFlow load the vocabulary from a file, you can call categorical_column_with_vocabulary_file() instead. As you expect, these two functions will simply map each category to its index in the vocabulary (e.g., NEAR BAY will be mapped to 3), and unknown categories will be mapped to -1.

For categorical columns with a large vocabulary (e.g., for zipcodes, cities, words, products, users, etc.), it may not be convenient to get the full list of possible categories, or perhaps categories may be added or removed so frequently that using indices would be too unreliable. In this case, you may prefer to use a categorical_column_with_hash_bucket(). If we had a "city" feature in the dataset, we could encode it like:

```
city_hash = tf.feature_column.categorical_column_with_hash_bucket(
    'city', hash_bucket_size=1000)
```

This feature will compute a hash for each category (i.e., for each city), modulo the number of hash buckets (hash_bucket_size). You must set the number of buckets high enough to avoid too many collisions (i.e., different categories ending up in the same bucket), but the higher you set, the more RAM will be used (by the embedding table, as we will see shortly).

# Crossed Categorical Features

If you suspect that two (or) categorical features are more meaningful when used jointly, then you can create a crossed column. For example, suppose people are particularly found of old houses inland and new houses near the ocean, it might help to