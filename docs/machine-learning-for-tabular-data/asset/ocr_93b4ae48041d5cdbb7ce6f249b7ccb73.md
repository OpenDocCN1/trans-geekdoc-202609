# CHAPTER 7 An end-to-end example using XGBoost

controlling for the effect of location. Although similar to K-fold cross-validation, there is a key difference in stratified K-fold cross-validation: the class distribution of a feature of our choice in the dataset is preserved in each fold. Such stratified sampling allows to have a similar mix of territories as the complete dataset. However, it is important to check beforehand some territories are difficult to split among neighborhoods because of their low numeracy. If we count the neighborhoods represented in the data, we get a long list with many locations, some showcasing a considerable of listings and others a limited few:

```
X['neighbourhood'].value_counts()
```

Clearly you cannot accept all the neighborhoods having less than a certain number of examples because, if you are going to split the data into folds, you will hardly have them well represented. Since areas are spatially distributed, gathering them into an extra class would potentially mix very different distributions of areas quite far from each other. In listing 7.11, we solve this by aggregating areas with less than 30 examples (implying about 6 examples for each fold if we use a five-validation split) with their nearest neighbor neighborhood. To achieve this, we use a KDTree structure. Then we can match each area with less than 30 accommodations with its nearest area more than 30:

+   Listing 7.11 Aggregating nearby neighborhood areas

```
neighborhoods = {
mary_listings[
    'neighbourhood', 'latitude', 'longitude'
]
groupby('neighbourhood')
agg({'latitude': 'mean',
'longitude': 'mean',
'neighbourhood': 'count'})
}
nless_than_30 = {
neighborhoods[neighborhoods['neighbourhood'] < 30]
nmore_than_30 = {
neighborhoods[neighborhoods['neighbourhood'] > 30]
}

ktree = KDTree(
more_than_30['latitude', 'longitude']
)
change_list = {}

for i in range(len(less_than_30)):
    row = less_than_30.iloc[[i]]
    idx = kdtree.query(['latitude', 'longitude'])
```

> Calculates the mean latitude,
mean longitude, and the count
of listings in each neighborhood

> Separates the neighborhoods into
two groups based on
the number of listings

> Creates a KDTree using the mean latitude\and longitude values of neighborhoods
with counts greater than 30

> Initializes an empty dictionary
to store the mappings of the
neighborhoods