# Security threats and their mitigation in big data recommender systems 249

# Random attack detection

Random attack is similar to Partitioning attack, but in Random attack filler ratings are selected randomly as the average is gained from the overall system for all items. In average attack, different partitions can be examined by choosing different targets and calculating a measurement for each selection partition. The correlation between the average rating for each item and the profile is used in this model. We expect low correlation between filler items and individual ratings because of random ratings [30].

# 11.5.2 Enhanced hybrid collaborative recommender systems

We want to discuss a knowledge-based collaborative hybrid recommendation algorithm, which we believe, represents a potential solution to the injection attack problem. The reason this algorithm is more robust against such attacks is that it relies not on user profiles, but also on semantic knowledge of the domain and items to be able to predict. So, profile injection attack may have less affect into the system [13].

# 11.5.2.1 Hybrid recommendation algorithm

Our semantically enhanced collaborative recommendation algorithm is a hybrid algorithm that uses semantic information and item-based collaborative recommender together [17,33]. Item-based recommendation relies on the similarity of ratings between items. This approach combines the item-based similarity with content-based similarity. This algorithm calculates the similarities using semantic knowledge of items. To simplify these calculations, we need to convert class instances into a vector representation.

# 11.5.2.2 Push attacks against enhanced hybrid algorithm

We call item-based collaborative recommendation extension as the hybrid algorithm. We want to test and compare the robustness of the hybrid algorithm with the robustness of item-based algorithm. For example, an agent extracts samples of movies from Internet Movie Database. For each movie semantic attributes are, title of the movie, release year of the movie, director(s), movie cast, genre and plot. We use these attributes to create a binary attribute vector. We use the single value decomposition to decrease the attribute dimensions. Experiments were done in same situation using the same target items and same users that are Segment attack and average attack with 100% of filler sizes.

We examined the hybrid effective. Figure 11.5 shows that enhanced hybrid decreases the effect of Segment and average attacks. Also, the result show that Segment attack effect reduces using semantic information. Segment attack can be effective against item-based algorithms by increasing the similarity between a pushed item and a group of items that are used by some users. Figure 11.5 shows that enhanced hybrid effectively reduces an attacker ability to change the similarity between target movies and segment moves [13].

To protect completely from ratings attacks, we can use semantic similarity. For improving accuracy using ratings data and selecting α > 0 is recommended. By