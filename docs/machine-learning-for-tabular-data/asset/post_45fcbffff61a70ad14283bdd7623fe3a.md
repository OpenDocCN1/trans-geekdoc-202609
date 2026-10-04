
## Introduction to tree-based methods

also becomes evident that specific partitions have been carved out just to fit examples in a certain position in the space. There are a few partitions containing only one example case. Any new example risks being incorrectly classified if it doesn't perfectly fit the training distribution (an overfitting situation).

![](img/def89cc476fa39f4c54bd34e78d91674_159_0.png)

Figure 5.2 How a fully grown decision tree branching can also be interpreted as a series of dataset splits

Figure 5.3 shows the same problem visualized with fewer splits—two for every feature. You can achieve this by pruning the previous tree splits backward, removing the ones enclosing too few training examples, or you accomplish that by limiting in the first place the tree's growth—for instance, by imposing a maximum number of splits to be created. If you use fewer partitions, the tree may not fit the training data as perfectly as before. However, a simpler approach provides more confidence that new instances will likely be classified correctly, as the solution depends explicitly on single points in the training set.

![](img/def89cc476fa39f4c54bd34e78d91674_159_1.png)

Figure 5.3 The problem handled by a simpler decision tree, obtained by pruning or by limiting its growth

# CHAPTER 5 Decision trees and gradient boosting

Thinking of this algorithm in terms of underfitting and overfitting, it is a high-variance algorithm because its complexity tends to exceed what should be given the problem and data. It is not easy to find its sweet spot. In fact, the best way to use decision trees to achieve more accurate predictions is not as single models but as an ensemble of models. In subsequent subsections, we will explore methods such as bagging, random forests, and gradient boosting, an advanced method based on decision trees.

In this chapter, we will return to the Airbnb NYC dataset to illustrate the core gradient-boosted decision tree implementations and how the technique works. The code in the following listing represents the data and some key functions and classes we previously used to illustrate other classical machine learning algorithms.

# Listing 5.1 Reprining the Airbnb NYC dataset

```python
import numpy as np
import pandas as pd
from sklearn.preprocessing import HotEncoder
from sklearn.compose import ColumnTransformer
from sklearn.impute import SimpleImputer
```

List of high-cardinality categorical features to be ordinarily encoded

```python
data = pd.read_csv('./AB_NYC_2019.csv')
excluding_list = ['price', 'id', 'latitude', 'longitude', 'host_id', 'last_review', 'name', 'host_name']
low_categorical = ['neighborhood_group', 'room_type']
high_categorical = ['neighborhood']
continuous = ['min_minutes', 'number_of_reviews', 'reviews_per_month', 'calculated_host_listings_count', 'availability_365']
```

List of low-cardinality categorical features to be one-hot encoded

```python
target_mean = (data['price'] > data['price'].median())
  .astype(int)
target_median = (data['price'] > data['price'].median())
  .astype(int)
target_multiclass = pd.qcut(data['price'], q=5, labels=False)
target_regression = data['price']
categorical_onehot_encoding = OneHotEncoder(handle_unknown='ignore')
categorical_ord_encoding = OrdinalEncoder(handle_unknown='encoded_value', unknown_value=np.nan)
numeric_passthrough = SimpleImputer(strategy='constant', fill_value=0)
```

List of features to be excluded from processing

Creates a binary target indicating whether the price is above the median (balanced binary target)

```python
column_transformer = ColumnTransformer(
  ['low_card_categories', categorical_onehot_encoding, low_categorical),
  ('high_card_categories', categorical_ord_encoding, high_categorical),
```

Sets the target for regression as the price column

Creates a binary target indicating whether the price is above the median (balanced binary target)

Creates a multiclass target by quantile binning the price into five classes

```python
high_card_categorical),
('numeric',
numeric_passthrough,
continuous),
nremainder='drop',
verbose_feature_names_out=False,
sparse_threshold=0.0);
```

![](img/def89cc476fa39f4c54bd34e78d91674_161_0.png)

- different types:
- excluding_list—A list of features that should be excluded from the analysis, such as unique identifiers and text features
- low_card_categorical—A subset of categorical features that have a low cardinality (few unique values) and will be one-hot encoded
- high_card_categorical—A subset of categorical features that have a high cardinality (many unique values) and will be encoded using an ordinal encoding
- continuous—A list of numerical features that will be standardized for analysis

The code reads a CSV file containing data related to Airbnb listings in New York City in 2019 using the pandas library. It then defines several lists that categorize the features of the data in different types:

- The code creates several target variables based on the Price feature of the data:
- target_mean—A binary variable indicating whether the price is higher than the mean price of all listings
- target_median—A binary variable indicating whether the price is higher than the median price
- target_multiclass—A multiclass target by quantile binning the price into five classes
- target_regression—The actual price values

Creates a binary target indicating whether the price is above the median (balanced binary target)

The code reads a CSV file containing data related to Airbnb listings in New York City in 2019 using the pandas library. It then defines several lists that categorize the features of the data in different types:

- The code creates several target variables based on the Price feature of the data:
- target_mean—A binary variable indicating whether the price is higher than the mean price of all listings
- target_median—A binary variable indicating whether the price is higher than the median price
- target_multiclass—A multiclass target by quantile binning the price into five classes
- target_regression—The actual price values

## CHAPTER 5 Decision trees and gradient boosting

Finally, the code sets up a ColumnTransformer object that will apply different transformations to each subset. It applies one-encoding to low-cardinality categorical features and passes through continuous features. The sparse_threshold is set to zero to ensure the transformer returns dense arrays.

Listing 5.2 shows how a standard decision tree model is implemented to our example. As the examples seen in the previous chapter, we import the necessary modules from Scikit-learn, define a custom scoring metric based on accuracy, and set up a five-fold cross-validation. Then we define a ColumnTransformer named column_transform, which orchestrates data preprocessing. It involves:

- Transforming categorical variables using a function_onehot_encoding for specific low-cardinality categorical columns
- Passing through numeric features with a function numeric_passthrough
- Dropping any remaining columns (remainder='drop')
- Setting options like suppressing feature names and not applying sparse representation

At this point, a pipeline combining the ColumnTransformer with a decision tree classifier is tested using cross-validation, with accuracy scores along with the average time and score time.

Under the hood of the cross-validation procedure and the data pipelining, the dataset is separated multiple times by the decision tree classifier during the training based on a splitting value from a feature. The procedure can be algorithmically explained as "greedy" because the decision tree picks the best split at each step without questioning whether alternatives could lead to a better result. Despite such a simple approach, decision trees are effective machine learning algorithms. The process goes until there are no more splits that improve the training, as shown in the following
