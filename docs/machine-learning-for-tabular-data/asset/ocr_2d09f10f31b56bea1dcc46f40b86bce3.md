# 464 APPENDIX B K-nearest neighbors and support vector machines

```
import numpy as np
import pandas as pd
excluding_list = [
    'price', 'id', 'latitude', 'longitude',
    'host_id', 'last_review', 'name', 'host_name'
]
categorical = {
    'neighborhood_group', 'neighbour',
    'room_type'
}
continuous = {
    'minimum_nights', 'number_of_reviews', 'reviews_per_month',
    'Calculated_host_listings_count'
}
data = pd.read_csv('.AB_NYC_2019.csv')
target_median = {
    data['price'] > data['price'].median(0)
}.astype(int)
```

List of column names to be excluded from the analysis

List of columns that likely represent categorical variables in the dataset

List of columns that represent numerical variables in the dataset

A binary balanced target

The code will use your dataset and define features what be excluded from the analysis or considered continuous or categorical for processing purposes.

# B.1 k-NN

Applicable to regression and classification tasks, the k-NN algorithm is considered one of the simplest and intuitive algorithms for making predictions. It finds the k (where k is an integer number) closest examples from the training set and uses their information to make a prediction. For example, if the task is a regression, it will return the average of the k closest examples. If the task is a classification, it will choose the most common class among the k closest examples.

Technically, k-NN is commonly regarded as an instance-based learning algorithm because it memorizes the training examples as they are. It is also regarded as a "lazy algorithm" because, contrary to machine learning algorithms, there is little processing at time. During training, there is some processing of the distances by optimized algorithms and data structures that render it computationally costly afterward to look for the neighboring points near a training example. Most of the computational work is done at testing time (see B.1).

We apply a k-NN classifier to the Airbnb NYC data, in chapter 4, in listing features to be on the same scale, ensuring an equal weight to each dimension in the distance measurement process. If a feature is on a different or smaller scale, it would be over-weighted. To give an idea of the problem, let's consider what happens when we compare distances by kilometers, meters, and centimeters. Even if distances are comparable, meters and centimeters will numerically exceed kilometers measurements. This problem is usually solved by scaling features—for instance, subtracting their mean and dividing by their standard deviation (an operation known as z-score normalization