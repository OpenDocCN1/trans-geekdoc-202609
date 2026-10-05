# Efficient and socio-aware recommendation approaches 45

modern systems, where recommendations need to be provided for possibly millions
of users and over millions-to-billions of items, further complicating the inevitable
technical challenges.

Content-based approaches originated from the field of information retrieval [5].
in general, they focus on the creation of user profiles by analyzing the features of
the items that a user has rated in the past. Most frequently, these are textual
descriptions of items, e.g., if the item is a film, it could be beside, size, etc., in the form of
annotations accumulating the item. Assuming some known utilities $f(u, i)$ of items,
i$i \ \in I$ assigned by user $u$, the utility $f(u, i')$ of item $i'$, which is similar to items $i_i$, canbe estimated. Methods in this category suggest different ways of performing these
estim.

Contrary to content-based methods which are centered around item-item simil-
arity CF techniques rely on users’ ratings similarity (according to measures
as cosine or Jaccard distance [6]), in order to provide the utility of an item for a
particular user. More specifically, the utility $f(u, i)$ of item $i$ to user $u$ is computedy the utilities $f(u)$, where $U$ are the users who are similar to $u$. Col-
laborative recommendations can be either neighborhood based or model based.
neighborhood-based recommendations, sometimes referred to as memory based, the
user-item ratings, represented alphabetically by a matrix (or user-item utility matrix
in Figure 4.1), are directly used to estimate ratings for unrated items. Similarity-
based approaches are defined either between the users (user-based) or between
the items (item-based), and a weighted average of the corresponding ratings is calcul-
ted [7]. Model-based approaches, in contrast to the neighborhood-based, each
user-item rating patterns build a predictive model of ratings with the use of data
mining and machine-learning techniques (Bayesian network, clustering, association
anysis [7].

To summarize the difference between the above two approaches, the
content-based aims at recommending similar items to users that a user has already cho-
sen, on the other hand, CF approaches provide recommendations by suggesting
to user items that users have selected before.

We should note that both of the aforementioned approaches have sev-
eral limitations, some of which can be found in [6,7], along with more extensive
planations. In general, a content-based system is highly dependent on the avail-
ity of the descriptive data (limited content analysis). In addition, it is susceptible to
o-specialization and exhibits the users’ cold-start problem [3], which also appears
as a drawback along with sparsity and scalability in collaborative systems.
in particular, rating data characteristics such as the size and shape of the rating space
which is defined by the ratio of the number of users to the number of items, as
well the rating density which is the proportion of known ratings among all poss-ible, are shown in [8] to have a significant impact on collaborative systems’
predictive accuracy. Finally, CF systems fail to categorize users who have common
preferences with more than one group of similar users (they belong to the intersection
of the different clusters of users) and by extension to output accurate recom-\mendations, a problem known as the gray sheep problem [9]. Hybrid methods are