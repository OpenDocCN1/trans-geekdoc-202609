
| | The Big Short | Finding Nemo | The Blind Side | Black Panther | Wonder Woman | Moneyball | Coco | Guardians of the Galaxy |
|---|---|---|---|---|---|---|---|---|
| User 1 | 4 | | 4 | 3 | | 4 | | 5 |
| User 2 | | | | | | | 4 | 1 |
| User 3 | 3 | | 1 | | 5 | | | |
| User 4 | | | | | 4 | 4 | | |

Table 4: Original dataset

These eight movies can be reclassified into the following categories:
**Michael Lewis Adaptation:** The Big Short, The Blind Side, Moneyball
**Family:** Finding Nemo, Coco
**Superhero-Action:** Black Panther, Wonder Woman, Guardians of the Galaxy
User ratings for individual movies are then summed and averaged to populate category rating values.

| | Michael Lewis Adaptation | Family | Superhero-Action |
|---|---|---|---|
| User 1 | 4 | | 4 |
| User 2 | | 4 | 1 |
| User 3 | 2 | | 5 |
| User 4 | 4 | | 4 |

Table 5: Recreated dataset

This transformation captures the information using fewer variables and reduces the number of variables from eight to three. The downside of this transformation is there is now less information regarding specific relationships between individual movies. Thus, rather than recommending movies to users based on other movies, recommendations are formed according to movie categories.

This method is admittedly crude and overtly manual for the purpose of developing sophisticated recommender systems. This is why descending dimension algorithms are a more effective methodology for implementing dimension reduction, as we'll uncover next.

## Principal Component Analysis

One of the most popular descending dimension algorithm techniques is principal component analysis (PCA). Known also as *general factor analysis*, PCA examines interrelations among a set of variables and removes components that have the least impact on data variability. This helps to reveal hidden and simplified structures in the data and is often used as a pre-processing step before applying another algorithm, which will now run faster on a compressed dataset (less bloated by matrix sparsity).

As with other descending dimension algorithms, PCA is useful for reducing data complexity and visualizing multidimensional data using fewer variables by synthesizing variables into components. The algorithm allows one to take a dataset with a high number of variables, such as 20-30 variables, and find the principal components that have the most impact on data variability. Components are identified through the statistical application of an orthogonal line perpendicular (at a right angle) to the regression hyperplane. The orthogonal line then takes the role of the new y-axis.

![](img/a19c36b1869b7a68ada55e0c3c42a30d_33_0.png)

In Figure 8 are four horizontal axes. The first two axes relate the x and y values denoted in the original data plot. The third and fourth axes measure the distance from the new x and y values with the orthogonal line taking the place of the original y-axis. The new x-axis is Principal Component 1 (PC 1), and the new y-axis is Principal Component 2 (PC 2).

Under the new PC1 and PC2 axes (the third and fourth axis), we can see a change in variance amongst the data points. The variance in PC1 has expanded in comparison to the original x values (seen in the first axis). Meanwhile, the variance in PC2 has shrunk significantly as all data points are virtually stacked on top of each other, close to zero.

As PC2 contributes the least to overall variance, we can focus our attention on studying the variance along PC1. While PC1 doesn’t contain 100% of the original information, it captures the data points that have the most impact on data patterns and improves computational performance.

In this example we divided the dataset into two principal components before selecting one principal component. In other scenarios, you might select two or three principal components that contain 75% of the information from a total of ten components. (Of course, insisting on 100% of the information would defeat the purpose of data reduction and maximizing performance.)

![](img/a19c36b1869b7a68ada55e0c3c42a30d_35_0.png)

Figure 9: Example of PCA after the isolation of 2 principal components from 7 original features

Like compressing an image to a smaller file format such as JPEG, dimension reduction techniques including PCA do cause some information loss. Thus, although dimension reduction helps to summarize the variability of high-dimensional data and speed up training, it may result in a slight sacrifice to accuracy.

In the next exercise we will use another descending dimension algorithm called singular-value decomposition to compress data to represent generalized user tastes.

## COLLABORATIVE FILTERING PART 1

As you’ll recall from Chapter 2, recommender systems are not a specific algorithm but rather an application of machine learning and data mining techniques. The two primary architectures for recommending items are content-based filtering and collaborative filtering. This chapter examines collaborative filtering.

Collaborative filtering recommends items to a user based on analysis of similar users and their preferences, past purchases, ratings or other general behavior. Collaborative filtering can also be split into two methods.

The first method is user-based collaborative filtering, which generates recommendations to a target user based on the historical preferences of similar users. Another way of expressing this is people similar to you who buy x also buy y.

In practice, like-minded users are first identified, and their ratings or preferences are then collected and grouped to produce a weighted average. The group’s general preferences are used to recommend items to individual users based on the ratings and preferences of their peers. For instance, if a user has never seen a given film or TV series which their peers watched and rated positively, the system will recommend this content item to the user based on peer observation.

The second method is item-based collaborative filtering, which rather than finding users with similar preferences, finds a set of items similar to the target item based on user preferences. For example, Star Wars movies rated highly by a similar audience of users will be matched together as a set and then recommended to other users that like and rate one of the movies in the set. Item-based filtering can therefore be thought of as people who buy x also buy y.

The main distinction between the two methods lies in the selection of input. Item-based filtering first takes a given item, finds users who liked that item, and then retrieves other items that those users liked. Conversely, user-based filtering first takes a selected user, finds users similar to that user based on similar ratings, and then recommends items that the similar users also liked. In reality, item-based and user-based collaborative filtering tend to produce similar item recommendations, but user-based filtering can be more accurate for datasets that have a large number of users with esoteric interests. Datasets that have less information regarding user characteristics and tastes, though, are generally more compatible with item-based collaborative filtering.

Let's now review the advantages and drawbacks of collaborative filtering.

### Advantages

- **1) Low knowledge of item characteristics**

  A major advantage of collaborative filtering is that it doesn’t rely on a sophisticated understanding of items and their specific attributes. This saves upfront effort as you don’t need to spend time meticulously documenting items. This is especially convenient for online video and audio content items that are generated daily and time-consuming to review and classify.

- **2) Flexible over the long-term**

  As collaborative filtering responds directly to user behavior and trends, this technique is generally more flexible than content-based filtering at reacting to changes in user/consumer behavior. Sudden short-term changes in fashion, pop culture, and other trends, though, can be difficult to respond to —at least initially—depending on when the data is collected.

- **3) Discoverability**

  Collaborative filtering enables discoverability of items outside the user’s standard periphery as it synthesizes preferences from users they’ve never met but who share similar interests.

### Disadvantages

- **1) Large-scale user data**

  A challenge and potential drawback of collaborative filtering is the significant amount of upfront information that is needed to document user preferences. Without this information, collaborative filtering is largely ineffective. Amazon and Netflix have enough user data to ride out sparsity problems in the data, but new entrants without an established user base are handicapped. Obtaining or acquiring data from a comparable platform, as Amazon did via its data partnership with AOL, is one strategy to overcome the cold-start problem.

  Also, note that the scalability of collaborative systems can be computationally expensive for platforms with a massive number of users.
