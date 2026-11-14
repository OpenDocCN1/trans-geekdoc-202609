
1. Next, we predict the rating that user `a` will give to specific items using the `k` neighbors ratings for same or similar items.

2. Now we look for the item `j` with the best predicted rating.

#### 12.6.5.2 User Based Collaborative Filtering

In user based collaborative filtering, the recommendations are based on preferences of the most similar user (users) to the current user. Cosine similarity and Pearson correlation coefficient are commonly used to find similarity between users as shown subsequently. Let us assume that we want to determine the similarity between two users `U[i]` and `U[j]`. Let `k` be the number of items rated by both `U[i]` and `U[j]` and let `r[i,k]` be the observed rating of user `i` for item `k` and `r[j,k]` the observed rating of user `j` for item `k`. Let `r[i]~` be user `i`’s mean rating and `r[j]~` be user `j`’s mean rating.

Cosine similarity between two users `U[i]` and `U[j]` is given as follows (Equation 12.2):

```
(12.2)
$${sim}\left( U_{i},U_{j} \right) = \cos\left( \left( U_{i},U_{j} \right) = \frac{U_{i},U_{j}}{\left\| U_{i} \right\|\left\| U_{j} \right\|} = \frac{\sum_{k}r_{i,k}r_{j,k}}{\sqrt{\sum_{k}{r_{i,k}}^{2}}\sqrt{\sum_{k}{r_{j,k}}^{2}}} \right.$$
```

Pearson correlation coefficient between two users `U[i]` and `U[j]` is given as follows (Equation 12.3):

```
(12.3)
$${sim}\left( U_{i},U_{j} \right) = \frac{\sum_{k}\left( r_{i,k} - {\widehat{r}}_{i} \right)\left( r_{j,k} - {\widehat{r}}_{j} \right)}{\sqrt{\sum_{k}\left( r_{i,k} - {\widehat{r}}_{i} \right)^{2}}\sqrt{\sum_{k}\left( r_{j,k} - {\widehat{r}}_{j} \right)^{2}}}
```

The next step is to find the predicted rating of user `u` for item `i`. Here we use the similarity calculation to predict rating as shown in [Figure 12.7](#ch12.xhtml#fig12_7).

![Figure 12.7 Calculation of predicted rating—user based collaborative filtering.](images/fig12_7_B.jpg)

[Figure 12.7 Calculation of predicted rating—user based collaborative filtering.](#ch12.xhtml#R_fig12_7)

#### 12.6.5.3 Item Based Collaborative Filtering

In item based collaborative filtering, in order to find whether a user prefers an item, its similarity to other items already rated by the user is determined. In order to find whether a user will buy item B if they had already bought A, we find the missing rating based on the ratings given to the other items by the user.

The Pearson correlation coefficient is commonly used to find similarity between items as shown subsequently. Let us assume that we want to determine the similarity between item `i` and item `j` or the correlation between item `i` and item j. Let `U` be the set of users who have rated both item `i` and item `j`. Let `R[u,i]` be the observed rating of user `u` for item `i` and `R[j]~` be item `j`’s mean rating.

Pearson correlation coefficient between two items `I` and `j` is given as follows (Equation 12.4):

```
(12.4)
$$S\left( i,j \right) = \text{corr}_{\overline{i},\overline{j}} = \frac{\sum_{u \in U}\left( R_{u,i} - {\overline{R}}_{i} \right)\left( R_{u,j} - {\overline{R}}_{i} \right)}{\sqrt{\sum_{u \in U}\left( R_{u,i} - {\overline{R}}_{i} \right)^{2}}\sqrt{\sum_{u \in U}\left( R_{u,j} - {\overline{R}}_{i} \right)^{2}}}
```

The next step is to find the predicted rating of user `u` for item `i` based on the past ratings for similar items as shown in [Figure 12.9](#ch12.xhtml#fig12_9).

![Figure 12.9 Calculation of predicted rating—item based collaborative filtering.](images/fig12_9_B.jpg)

[Figure 12.9 Calculation of predicted rating—item based collaborative filtering.](#ch12.xhtml#R_fig12_9)

#### 12.6.5.4 Advantages and Disadvantages of Collaborative Based Filtering

One important advantage of collaborative filtering is that no domain knowledge is necessary. This method works for any kind of item, and no feature selection is required. Essentially users and items are considered as symbols without any internal structure or characteristics. Another important aspect is that it allows serendipity; that is, collaborative filtering can help users discover new items by recommending items because similar users recommended those items.

However, collaborative filtering also has some disadvantages. Collaborative filtering is based on previous ratings and hence cannot recommend items that have previously not been rated or if enough users are not present in the system—called the **cold start problem**. **Sparsity** is another issue, where if the user–item matrix is sparse it is difficult to find users who have rated the same items. In user based collaborative filtering similarity between users is dynamic; precomputing user neighborhood can lead to poor predictions, but in item based collaborative filtering similarity between items is static and enables precomputing of item–item similarity, and prediction requires only a table lookup. Further these systems cannot recommend items to users who have unique tastes since they tend to recommend popular items. Moreover, it is assumed that items are standardized and that prior choices determine current choices without considering contextual knowledge.

### 12.6.6 Content Based Recommendation

In a content based model, recommendations are based on the content of items and not on the ratings of other users. Machine learning is used to learn a profile of the users’ preferences from examples based on description of content based on features. The idea is to recommend items to users that are similar to previous items that were highly rated by the same user. An example is recommendation of movies with the same features such as actor, genre, director, and so on. Now we need to explain what we mean by content of an item. The content can be an explicit attribute of the item such as genre (action/thriller), action (Vijay), or year (2015). The content can also be characterized by textual content where techniques can be used to compute the distance between two textual descriptions or natural language processing can be used to extract features. The content may be in the form of audio or image and then can be extracted from the signal. After the features from the content of the item are extracted, an item profile is created, which is essentially a vector of features. A user profile is created as an weighted average of rated item profiles. Now given the user profile `x` and an item profile `i`, the estimate of the rating `u` of user `x` for item `i` is given as in Equation (12.5):

```
(12.5)
$$u\left( x,i \right) = \cos\left( x,i \right) = \frac{x \cdot i}{\left\| x \right\|\left\| i \right\|}
```

#### 12.6.6.1 Advantages and Disadvantages of Content Based Recommendation

The major advantage of content based recommendation is that there is no need of data about other users, which in turn means that there is no cold-start or sparsity problem. Moreover, the model is able to recommend to users with unique tastes and also recommend new and unpopular items. Another important advantage is that recommendations can come with explanations listing content features that resulted in the recommendation can be given.

The major disadvantage is that the content must be amenable to being encoded as meaningful features and user interest must be represented as a learnable function of these features. Another disadvantage is that we are unable to exploit the quality judgements of other users unless we are able to encode these judgements as content features.

## 12.7 Context Aware Recommendations
