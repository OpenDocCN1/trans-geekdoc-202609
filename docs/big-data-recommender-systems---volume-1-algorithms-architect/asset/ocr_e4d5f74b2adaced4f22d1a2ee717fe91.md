# Big data recommender systems, volume 1

Table 2.1 Example utility matrix

| | P1 | P2 | P3 | P4 | P5 | P6 | P7 |
|---|---|---|---|---|---|---||
| User A | 4 | | | 5 | 1 | | |
| User B | 5 | 5 | 4 | | | 5 | |
| User C | | | | 2 | 4 | | | |
| User D | | | 3 | | | | 3 |

+   iii. They provide transparency to the user by giving explanation about how this works.

+   iv. They do not need a large amount of memory to store data and compute recommendations.

Poonam et al. [8] also discussed the disadvantages of a content-based RS have. They are as follows:

+   i. It is difficult to extract item features in content domains.

+   ii. They work on the item similarity approach so it suffers from overspecialization problem (later discussed in Section 2.4 of this chapter).

+   iii. It is hard to acquire feedback from the user about a recommendation. Therefore, it is not possible to determine if the recommendation made is correct or not.

+   iv. It is harder to construct user profiles, as users do not provide information about them explicitly or implicitly.

# 2.3.2. CF recommenders

Introduction

CF recommenders are the most popular among other recommendation approaches [8]. They recommend items to the user based on the ratings given to the items by similar users. For example, let us consider User A is similar to User B. So, if User B has liked Item A, then it is likely that User A would also like Item A. In this way, CF recommenders construct a matrix of items and users which represents which user likes what item. This matrix is used to compute similarity among users and predicted ratings of items by a certain user. Table 2.1 shows an example utility matrix. In matrix, Users A–D have rated products P1–P7 on a rating scale of 1–5. Notice, from this utility matrix, we can infer the similarity of users by seeing what ratings they have given products. As an instance, see User A and User B, they seem to like similar products like ‘P1’. So, they could be said similar to each other. Now, see User A and User C, they seem to give opposite ratings to P4 and P5. So, they could be said dissimilar to each other.

However, we do not usually infer the ratings directly by looking at the table. The CF recommenders use different similarity measures to compute similarity among users and items, which we will discuss in the upcoming subsections.