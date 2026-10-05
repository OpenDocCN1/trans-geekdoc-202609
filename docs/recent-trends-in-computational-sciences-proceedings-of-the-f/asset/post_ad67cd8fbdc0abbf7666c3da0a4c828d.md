
## 3.2 Proposed solution

Users can waste a lot of time scrolling through hundreds, if not thousands, of anime without discovering something they enjoy. Our goal is to fill the gap in the existing research and construct a recommendation system that proposes anime to viewers based on their preferences and needs, resulting in a better streaming experience that increases income and time spent. In this effort, the System can be implemented in multiple ways. We intend to address Popularity Based Recommendation System, Collaborative Filtering using KNN.

## 3.3 Dataset description

We worked with two datasets. The first is Anime, while the second is Rating. These two datasets were collected from the website, Kaggle. This data collection contains choices for 12,299 anime from a total of 73,516 users. The ratings in this set are a collection of them. The first anime dataset has 12299 rows and 7 columns. The second rating dataset has 781376 rows and 3 columns. Each user may rate and add it to their finished list. Anime.csv and Rating.

Next step is Data Preprocessing which is a technique to clean the raw data and make it suitable for classification models. This will make the data to be easily parsed by the machine and additionally improve the quality of the results. Real-world datasets are highly prone to inconsistent, noisy, or missing data. If the data mining algorithms are applied on such a dataset, they will not get quality results as they will not be able to identify patterns effectively. Hence, data preprocessing is a crucial step to improve the data quality before applying any algorithm to it.

## 3.4 Algorithms

### 3.4.1 Popularity-based

It's a type of recommendation system that works on the basis of popularity or anything that's currently hot or popular among customers and promote them right away [6]. For Example If a product is regularly purchased by the majority of people, for example, the system will learn that it is the most popular and will promote it to every new user who has joined up, increasing the possibility that the new user would purchase it as well.

### 3.4.2 Collaborative-based filtering

There are probably of people who rate a product that the user intended. This comparable trend of their ratings with the user serves as the basis for collaborative filtering [5]. The foundation of collaborative filtering is the idea of making product recommendations based on the tastes of others with similar interests.

### 3.4.3 K-nearest neighbour for collaborative filtering

KNN is a type of algorithm that may be used to solve issues in classification and regression [14]. Based on a provided distance measure as cosine, Euclidean, Jaccard similarity, minkowski, or custom distance measures, K-nearest neighbor determines the k most similar objects to a single instance.

In our model, we employed the cosine similarity to discover the k-nearest neighbors [19].

## 4 RESULTS AND DISCUSSION

This section summarizes the outcomes of the strategies to obtain similar anime and ratings.

## 4.1 Popularity algorithm

The Figure 2 shows the top 15 most popular shows based on given by the users. In the graph given below, the Y-axis represents different Animes and on the X-axis, the corresponding popularity score is from 0-10.

Based on our recommendation system, we have obtained the top 15 most popular anime, according to people's ratings. The Table 2 is drawn, with columns Name, Average Ratings and the Score based on the 15 most popular Animes.

Table 2. Fifteen most popular shows.

| Name | Average Ratings | Score |
|---|---|---|
| Fullmetal Alchemist Brotherhood | 9.26 | 9.1292697 |
| SteinsGate | 9.17 | 9.62223918 |
| Clannad After Story | 9.06 | 8.89006859 |
| Code Geass Hangaku no Lelouch R | 8.98 | 8.843128568 |
| Hunter x Hunter 2011 | 9.13 | 8.626378505 |
| Sen to Chihiro no Kamikushi | 8.93 | 8.76503438 |
| Code Geass Hangaku no Lelouch | 8.83 | 8.714967667 |
| Shigatumi kimi no Uso | 8.92 | 8.663781234 |
| Death Note | 8.71 | 8.636635884 |
| One Punch Man | 8.82 | 8.634727359 |

### 4.1.1 KNN

We obtained the following result using the KNN. The Table 3 represents the top 5 recommended anime (similar genre/ratings), based on a given anime i.e., Anime 0. This is effective to club anime based on specific taste.

Table 3. Top 5 recommended anime based on Anime 0.

| Anime0 | Anime1 | Anime2 | Anime3 | Anime4 | Anime5 |
|---|---|---|---|---|---|---|
| Choisui | Princess Tutu Recaps | Paizuri Cheerld vs Sakunyu Oendan | 09 Recgyord | PerePero Teacher | Please Me | Osaru no Sankiuchi Boukuse n Xmen |
| Gekigre r 3 Movie | Ookiku Furutta but spell | | Gundam Build Fighters Try Idol Wars Jetsu TV | Avengers Confident at Black Widow to Punisher | Koishima Miyu OVA Onake Ashita to | |

## 4.2 Collaborative-based filtering

There are probably of people who rate a product that the user intended. This comparable trend of their ratings with the user serves as the basis for collaborative filtering [5]. The foundation of collaborative filtering is the idea of making product recommendations based on the tastes of others with similar interests.

The Figure 2 shows the top 15 most popular shows based on given by the users. In the graph given below, the Y-axis represents different Animes and on the X-axis, the corresponding popularity score is from 0-10.

Based on our recommendation system, we have obtained the top 15 most popular anime, according to people's ratings. The Table 2 is drawn, with columns Name, Average Ratings and the Score based on the 15 most popular Animes.

![](img/a3f8e852e0ee65e528c95ad0821783b91.png)

## 4.3 KNN

KNN is a type of algorithm that may be used to solve issues in classification and regression [14]. Based on a provided distance measure as cosine, Euclidean, Jaccard similarity, minkowski, or custom distance measures, K-nearest neighbor determines the k most similar objects to a single instance.

In our model, we employed the cosine similarity to discover the k-nearest neighbors [19].

## 5 CONCLUSION AND FUTURE WORK

Anime is a vast class of entertainment that consists of a huge variety of genres and topics to attract a huge variety of viewers. The animation enterprise provides 430 firms. To cope with this problem, we evolved private recommendations into a hard task. To cope after a good deal of thought, the results have been created through our algorithms on the customers’ various hobbies. Collaborative filtering techniques based on recognition, content material, and reminiscence have all been used. Online companies have to now assist clients via means of providing tailormade ideas, content material, and services. Hybrid models arises while the user’s looking records are considered. Excessive degree of accuracy is needed for real-time superior advice systems. A sort of machine learning algorithm can assist those real-time systems. We wish to examine the other algorithms to look if they’ll assist to enhance the precision even further.

# REFERENCES

+   [1] Tiwari, Anand Shanker, Ajay Kumar, and Asim Gopal Rahman. “Book Recommendation System Based on Combining Features of Content Based Filtering, Collaborative Filtering and Association Rule Mining.” In 2014 IEEE International Advanced Computing Conference (IACC), pp. 500–503. IEEE,2014.
[2] Saadati, Mojdeh, Seyed Shihab, and Mohammed Shiqur Rahman. “Movie Recommender Systems: Implementation and Performance Evaluation.” arXiv preprint:1909.12749 (2019).
