
Current trends in cyber security

![](img/a35f8e852e0ee65e528c95ad0821783b_240_0.png)

# Location recommendation system

Deepali Suraj Attavar, R. Deekshitha, S. Nikhitha & B. Deepthi
Department of Computer Science, PES University, India
ORCID ID: 0000-0007-2998-4954, 0000-0006-8024-5084

P. Evlin Vidyu Latha
PES University, India

ABSTRACT: Recommender System is a Web Application that recommends the best places to visit and around a location. Once the User logs in, his/her location coordinates are obtained and the nearby places are listed down based on the Location-Aware Recommendation model built; the user can do the same for a custom system. The system displays the recommendations along with ratings. The system interface displays these suggestions based on Machine Learning and Data Analysis tools: Recommender system and optimal search algorithm filtering and User-Item-based collaborative filtering algorithm is also used to provide a personalised recommendation.

Keywords: Location Aware Recommender System, Location Coordinates, User Preference, Content Filtering, Hybrid model, User's Content

# 1 INTRODUCTION

In the current world, users have been successfully provided with objects of interest (such as movies, music, books, news, and photos) using recommendation algorithms. On the other hand, the traditional recommendation algorithms, mostly do not consider the location to be an important factor when making these suggestions. Our aim is to design a web application that recommends the best places to visit and around a location. We take Bangalore as the experimental case in this phase of our research. The web application attracts and being a great help to the tourists or the new people to a place in saving time while exploring the places in that location or to visit places of their interest. By providing the ratings, it aids the user to decide better as to which places to choose for instance, historic places, a place for leisure, eatery, shopping, park etc. etc. The user's profile caters in giving a free and personalized recommendation.

# 2 RELATED WORK

In [1], a cloud-based hybrid recommendation framework is used. Multi-level collaborative filtering and scaling optimization are included in the recommender system. It generates Top K recommendations. However, it does not employ multi-agent systems to investigate a user journey pattern in order to develop a context-aware recommender system. Concern about privacy is not addressed [2] talks about a context aware tourist app that includes location, time, weather, social media and penalisation. The perception model with Fuzzy logic and ANN is used; also employs PCA. Although they state that the number of factors increases the complexity. The work that is done in [3] is to provide a survey on location aware recommendation systems in mobile computing. Various concepts like traditional recommendation system, location aware recommendation system (LARS) are discussed here. They [4] created a personalised recommendation system for the web and mobile that will provide recommendations based on relevant location data collected from users (GPS routes and photos). Recommending routes and scoring criteria introduced to the recommendation system require refinement, providing additional obstacles. In [5], the focus is on personalised tourist recommendations using adaptive recommendation and profile modelling. The method allows for the inheritance of features by collecting information on tourist profiles, specialised hobbies, and so on. The "tour box" tourists' trip information. In [6] the primary goal is to propose a framework for a Personalized Location-based Traveller Recommender System for a mobile application. It aims to provide an individualized location-based services (LBS). This software is designed [7] for those who want to visit destinations using their Android devices. It is useful for those who want to visit nearby locations or work on similar projects. The study in [8] is based on a system for recommending tourist destinations. Collaborative Filtering is employed, and Material Based Filtering is used to propose places based on similar content. The machine learning model is trained and picked before being utilised in the front-end, and the data is saved in a MySQL database. Content Based Filtering, Web Scraping, and MySQL are all the terms used in the index.

# 3 PROPOSED METHODOLOGY

- The Approach to the project would begin by clustering the areas in the target location.
- The system displays the recommendations along with ratings.
- The system interface displays these suggestions based on Machine Learning and Data Analysis tools: Recommender system and optimal search algorithm filtering and User-Item-based collaborative filtering algorithm is also used to provide a personalised recommendation.
- The system interface displays these suggestions based on Machine Learning and Data Analysis tools: Recommender system and optimal search algorithm filtering and User-Item-based collaborative filtering algorithm is also used to provide a personalised recommendation.

# 4 DESIGN AND IMPLEMENTATION

## 4.1 Design

### 4.1.1 Models

- Sign-up, Authorization: Registration of a new user.
- User login: Login of user.
- Authentication: Following sign up and login, user data is verified.

## 4.1.2 APIs

- Geolocation API: Geolocation API is used for obtaining user's current location.
- Weather API: Weather API helps in getting details for coordinates from RapidX API.
- Place ID API: Place ID API is used for getting place ID for the coordinates.
- Place Details API: Place Details API helps in getting details such as opening hours, delivery, dine-in from Google.

## 4.1.3 Database

- User DB: User's Login details are stored.
- GPS DB: Stores current position of the users.
- User Feedback DB: User's ratings for the visited places are stored.
- Location Cluster DB: Stores the clustered area data.

## 4.2 Implementation

### 4.2.1 Top K recommender

- Cluster finder: it is used to find the cluster, the location belongs to.
- Main: Main is the Heart of processing modules.
- Top K recommendations: It recommends the Top K nearby places and far off places.
- Collaborative Filtering: It recommends places to users according to their previously visited places.
