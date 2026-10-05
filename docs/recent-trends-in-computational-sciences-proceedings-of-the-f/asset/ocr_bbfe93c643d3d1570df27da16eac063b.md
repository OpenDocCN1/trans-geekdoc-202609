# 3.2 Proposed solution

Users can waste a lot of time scrolling through hundreds, if not thousands, of anime without discovering something they enjoy. Our goal is to fill the gap in the existing research and construct a recommendation system that proposes anime to viewers based on their preferences and needs, resulting in a better streaming experience that increases income and time spent. In this effort, the System can be implemented in multiple ways. We intend to address Popularity Based Recommendation System, Collaborative Filtering using KNN.

# 3.3 Dataset description

We worked with two datasets. The first is Anime, while the second is Rating. These two datasets were collected from the website, Kaggle. This data collection contains choices for 12,299 anime from a total of 73,516 users. The ratings in this set are a collection of them. The first anime dataset has 12299 rows and 7 columns. The second rating dataset has 781376 rows and 3 columns. Each user may rate and add it to their finished list.Anime.csv and Rating.

Next step is Data Preprocessing which is a technique to clean the raw data and make it suitable for classification models. This will make the data to be easily parsed by the machine and additionally improve the quality of the results. Real-world datasets are highly prone to inconsistent, noisy, or missing data. If the data mining algorithms are applied on such a dataset, they will not get quality results as they will not be able to identify patterns effectively. Hence, data preprocessing is a crucial step to improve the data quality before applying any algorithm to it.

# 3.4 Algorithms

# 3.4.1 Popularity-based

It's a type of recommendation system that works on the basis of popularity or anything that's currently hot or popular among customers and promote them right away [6]. For Example If a product is regularly purchased by the majority of people, for example, the system will learn that it is the most popular and will promote it to every new user who has joined up, increasing the possibility that the new user would purchase it as well.

# 3.4.2 Collaborative-based filtering

There are probably of people who rate a product that the user intended. This comparable trend of their ratings with the user serves as the basis for collaborative filtering [5]. The foundation of collaborative filtering is the idea of making product recommendations based on the tastes of others with similar interests.

# 3.4.3 K-nearest neighbour for collaborative filtering

KNN is a type of algorithm that may be used to solve issues in classification and regression [14]. Based on a provided distance measure as cosine, Euclidean, Jaccard similarity, minkowski, or custom distance measures, K-nearest neighbor determines the k most similar objects to a single instance.

In our model, we employed the cosine similarity to discover the k-nearest neighbors [19].

# 4 RESULTS AND DISCUSSION

This section summarizes the outcomes of the strategies to obtain similar anime and ratings.