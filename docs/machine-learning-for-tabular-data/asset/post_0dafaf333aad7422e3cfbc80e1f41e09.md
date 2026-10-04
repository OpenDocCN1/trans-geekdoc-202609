
# CHAPTER 7 An end-to-end example using XGBoost

- Euclidean distance is based on the straight-line distance between two points in an Euclidean space. It assumes a direct path between the points and can be more suitable when considering physical distances. You may also hear it is referred to as the L2 norm, instead is a mathematical concept referring to the vector and the origin of the vector space. Since the L2 norm is based on the Euclidean distance formula, it is used interchangeably because it is a closely related mathematical concept.

- Manhattan distance, also known as city block distance or taxab distance, measures the distance between two points by adding up the absolute differences between their coordinates. It considers horizontal and vertical movements and disregards diagonal paths. Similarly to the Euclidean distance, you may hear the Manhattan distance referred to as the L1 norm when operating with vectors and vector spaces.

Manhattan distance can be more appropriate when considering the actual movement or navigation within a city, travel often occurs along streets and road networks. Considering that coordinates are inside a city, where the road structure and navigation along streets matter, Manhattan distance might be more suitable for capturing the movement and accessibility between locations. It aligns with the concept of following roads and making right-angle turns.

After calculating the imperial_palace_distance feature, we can examine its average value, expressed in meters, using the following code:

```
summary_listings.imperial_palace_distance.mean()
```

The result shows that the average distance to the Imperial Palace is around 7.9 kilometers.

Next, we can identify the listing that is located near the Imperial Palace. To achieve this, we use the idxmin() function to find the index of the listing with the minimum distance and then access its corresponding details:

```
{summary_listings[
  ['id', 'name', 'neighbourhood', 'imperial_palace_distance']
].iloc[np.argmin(summary_listings['imperial_palace_distance'])]}
```

The result is, which is a bit surprising:

```
id                              874407152426725982
name                            Home in Shibuya City ★New 3 bedrooms...
neighbourhood                   Chiyoda Ku
imper_palace_distance          137.394271
Name: 10255, dtype: object
```

Indeed, the listing is not situated close the Imperial Palace, which emphasizes the presence of potentially misleading errors in the geolocation of listings. It is uncommon to encounter similar problems in datasets, no matter how carefully they are curated.

# Preparing and exploring your data

As discussed in chapter 2, from a general point of view, after some quality checks where you look for consistency among features and marking likely inexact values, we have a few options, listed here in descending order of effort from more to less demanding:

- Geocoding (from address to coordinate) and reverse geocoding (from coordinates to address)—To figure out location information matches the provided latitude and decides whether to trust the provided address or coordinates
- Data imputation—Imputing the dubious values as they were missing, using the coordinates of a default location
- Listwise deletion—Removing all rows that have some dubious values
- Leave it to XGBoost—Tree-based methods to be less affected by erroneous and dubious values being robust to outliers and noise in the data

In our example, we decided to leave the situation to to XGBoost because our model is not so critical as require a thorough quality check. It could be different with your project, and you may evaluate a solution requiring more data-cleaning efforts. Distances from landmarks and services work well as features in real estate modeling. We do not limit ourselves to computing the distance from the Imperial Palace, the center of Tokyo. In the paper “Modeling User Activity Preference by Leveraging User Spatial Temporal Characteristics in LBSNS” by Dingqi Zhang, Vincent W. Zheng, Zhiyong Yu (IEEE Transactions, on Systems, and Cybernetics: Systems, 45(1), 129-142, 2015), the authors collected from Foursquare check-ins in New York City and Tokyo with their geographical coordinates and the type of location they refer to; we can access the data from Kaggle datasets (https://mng.bz/4dDj)

Foursquare is a social network based on geospatial. To its mobile app, it allows users to discover nearby venues to visit, such as restaurants and stores, means of transportation and share information about the places they visit. Another characteristic of the app is check-ins, which happens when using the platform at a venue. Check-ins refer to the presence of a user at a specific location. When a user enters Tokyo into a place, they share their posting with their Foursquare friends, and they may have the option to post about their visit to other social media platforms like Facebook and X. To make the value of a listing in terms of convenience, we have available airports, bus, train, and subway stations among commonly checked-in venues. Together with convenience stores, a type of retail store that mainly sells a wide selection of everyday items and products for their convenience, the proximity of such venues can add value to an accommodation.

Hence, to enrich our dataset, we first extracted the GPS locations directly from Kaggle. The code and the extracted dataset are available at https://mng.bz/QDQV, and you can download the processed file into your working directory from the page https://mng.bz/XxNa you can get the file relevant_spots_Tokyo.csv. The file contains information about 3,560 convenience store, 1,878 bus stations and stops, 439 subway stations, and 264 locations associated with airports. Then, using 7.6, we can compare the location of our Airbnb Tokyo listings with each of these venues and report the nearest distance of each. Our idea is that the closer it is to a convenience store, and more of transportation, the higher the expected price.

In 7.6 we do not compare accommodation with all the possible venues we gathered that would take too much time and computation. Instead, we utilize the k-dimensional tree (KDTree) data structure from Scikit-learn, an optimized algorithm designed to efficiently find the nearest point among many points for a given location. Scikit-learn is used for algorithms such as K-nearest neighbors in situations when you have to find the most similar examples to a test sample in the training set. in our case, the training set is the set of venues, and the algorithm is trained to find the nearest venue to a given location based on Manhattan distance.

# Listing 7.6 Finding the nearest facilities and transportation

```python
from sklearn.neighbors import KDTree

relevant_spots = pd.read_csv('relevant_spots_Tokyo.csv')

venue_categories = ['Convenience Store', 'Train Station',
    'Airport', 'Bus Station', 'Subway']
min_distances = ['listing_id', summary_listings['id']]

for venue in venue_categories:
    venue_filter = relevant_spots['venueCategory'] == venue
    venues = venue_filter[
        ['latitude', 'longitude']]
    tree = KDTree(venues, metric='manhattan')
    distance, index = tree.query(
        summary_listings[['latitude', 'longitude']],
        k=1)
    min_distances[
        'nearest_' + +
        venue.lower().replace(" ", "__")
    ] = degrees_to_meters(
        np.ravel(distance),
        summary_listings['latitude']
    )
min_distances = pd.DataFrame(min_distances)
```

- Stores the minimum distances in a dictionary

- Filters the relevant venue locations

- Creates a KDTree using the filtered venues using The Manhattan metric for fast nearest-neighbor searches

- Queries the KDTree to find the nearest point and its distance to each Airbnb listing (k=1 returns the nearest one)

- The dictionary of the minimum distances for each type of venue is converted into a DataFrame.
