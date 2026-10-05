![](bbox=[0.198, 0.068, 0.802, 0.258])

Figure 1. Workflow diagram.

+   - Cluster finder: it is used to find the cluster, the location coordinate belongs to.
- Main: Main is the Heart of processing modules.
- Top K recommendations: It recommends the Top K nearby places and far off places for a location.
- Collaborative Filtering: It recommends places to users according to their previously visited places and ratings using user-item-based collaborative filtering.

# ## 4.1.2 APIs

+   - Geolocation API: Geolocation API is used for obtaining user's current location.
- Weather API: Weather API helps in getting details for coordinates from RapidX API.
- Place ID API: Place ID API is used for getting place ID for the coordinates.
- Place Details API: Place Details API helps in getting details such as opening hours, delivery, dine-in from Google API.

# ## 4.1.3 Database

+   - User DB: User's Login details are stored.
- GPS DB: Stores current position of the users.
- User Feedback DB: User's ratings for the visited places are stored.
- Location Cluster DB: Stores the clustered area data.

# ## 4.2 Implementation

# ### 4.2.1 Top K recommender

For Top K recommender, k-means Clustering is done. Various clusters are formed. The cluster to which the user's current location belongs is found; to which recommendations are given accordingly. Two types of recommendations are made: 1) Nearby Top K recommendations 2) Slightly Far Top K recommendations. In Far away and Nearby Top K recommender, the number of clusters considered is different from each other as the radius of the distance taken into consideration varies. Based on Elbow curve method, for the Nearby Top K recommender the number of clusters considered is 5 whereas for Slightly Far Top K recommender the number of clusters considered is 3.

# ### 4.2.2 Collaborative filtering

Collaborative filtering is used to give a personalised recommendation based on the user's history of visited places and their ratings. User-Item-based is used for the same. The