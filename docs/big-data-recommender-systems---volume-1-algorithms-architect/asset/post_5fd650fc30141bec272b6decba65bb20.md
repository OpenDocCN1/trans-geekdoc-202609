
# 208 Big data recommender systems, volume 1

With this two-step parallel processing using the GraphLab framework and the PPSG framework, respectively, our inference implementation achieves satisfying efficiency and scalability on large data, as shown in the empirical study.

## 9.4 Spatial item recommendation using ST-SAGE

Once we have estimated the model parameter set $\theta$, given a querying user $u_q$, the querying time $t_q$ and location $l_q$, we first incur the role of target user $s_q$ according to the distance between his/her location $l_q$ and the querying location $l_q$. Then, we compute the probability of $u_q$ choosing each unvisited item $v$ based on the new query $q = (u_q, t_q, l_q, s_q)$ as follows:

```
$P(v, W_v|u_q, l_q, s_q, t_q, \theta) = \sum_{z=1}^K P(v, W_v, z|u_q, l_q, s_q, t_q)$
= \sum_{z=1}^K P(z|u_q, s_q, t_q, \phi_{topic}) P(v|z, \psi_{topic}, \theta_{topic}) (1/|W_v|)$
= \sum_{z=1}^K \alpha_{u_q t_q l_q s_q} \prod_{n=1}^{|W_v|} \beta_{z,n} Y_{z,v}$ (15)
```

where $W_v$ is the number of content words associated with each spatial item describing $v$. We note that the reason is why we use the geometric mean $(\prod_{n=1}^{|W_v|} \beta_{z,n})^{1/|W_v|}$ instead of the product $\prod_{n=1}^{|W_v|} \beta_{z,n}$ for the probability of topic $z$ generating the word set $W_v$. As we know, $\beta_{z,n}$ is a distribution over all content words, thus $\beta_{z,n}$ is a value in $(0,1]$. As a result, $1/|W_v|$ spatial items with more content words tend to have lower scores as the product of $\beta_{z,n}$ is always less than 1.

As we know, the efficiency of online recommendation is quite critical as users would not be willing to wait for a long time for recommendation results. To accelerate the online recommendation process, we first propose a ranking framework (16) which accelerates the modeling from online to maximum:

```
$S(q,v) = \sum_{z=1}^K F(z,v)W(q,z)$
$F(z,v) = \prod_{n=1}^{|W_v|} \beta_{z,n} Y_{z,v}$
$W(q,z) = \alpha_{u_q t_q l_q s_q}$ (16)
```

where $F(z,v)$ denotes the score of spatial items $v$ with respect to topic $z$, which is computed. This part is computed offline since it is independent from the query $q = (u_q, t_q, l_q, s_q)$. On the other hand, $W(q, z)$ denotes the part we need to compute online, representing the preference of query $q$ on topic $z$. Note that the principal time-consuming components of $W(q,z)$ are also computed offline (e.g., $\theta^{user}$, $\theta^{native}$ and $\theta^{interest}$). This design enables the maximum separation of the online computation from the offline calculation, which in turn reduces the query time.

Note that, even after the maximum separation of online computation from the offline calculation, a straightforward method of generating the top-k recommendation is still expensive in the situation where the item corpus is large, and it still needs to compute the ranking scores for all items according to (16) and select top-k ones. To improve the online recommendation efficiency, we adopt the TA-based query processing technique for top-k recommendation developed in [41], inspired by the observation that a query usually has a sparse preference over a small number of attributes (say 5-latent dimensions) and the query weights are extremely small. Since $W(q,z)$ is non-negative, the proposed ranking function in (16) is monotonically increasing given a query $q$, which meets the requirement of the TA-based query processing. This technology has the nice property of finding top-k results correctly by examining the minimum number of items without scanning all, which enables the ST-SAGE model scalable to large-scale datasets with large item corpus.

## 9.5 Experiments

In this section, we first describe the experimental settings including the datasets, comparative approaches and the evaluation method. We then demonstrate the experimental results.

### 9.5.1 Experimental settings

#### 9.5.1.1 Datasets

Our experiments are conducted on two real large-scale LBSN datasets: Foursquare and Twitter. The detailed information about the two datasets is described as follows.

**Foursquare**. This dataset contains the check-in history of 4,163 users living in California, USA, with 111,833 spatial items from 2009 to July 2013. For each user, it contains his/her social tags, visiting POI IDs, each check-in POI in terms of latitude and longitude, check-in time and the contents associated with each visited POI. Each check-in is stored as *user-ID*, *POI-ID*, *POI-location*, *check-in time*, *POI-content*. Each record in social networks is stored as *user-ID*, *friend-ID* and the total number of social relationship is 32,512.

**Twitter**. This dataset is based on the publicly available Twitter dataset [42]. Twitter supports the third-party location sharing services like Foursquare and Gowalla, where users of these services opt in to share their check-ins on Twitter. But the original data on Twitter does not contain the content information about spatial items. So, we crawled the category and tag information associated with each spatial item from Foursquare with the help of the publicly available API supplied by Foursquare. The final dataset used in our experiments contains 114,058 users, 62,547 spatial items and 1,434,668 check-in activities from Sep 2010 to Jan 2011. Each check-in record has the same format as aforementioned Foursquare except that dataset does not contain user social information. To make the experiments repeatable, we will make the datasets and our codes publicly available.

#### 9.5.1.2 Comparative approaches

We compare our ST-SAGE model with the following five methods representing the state-of-the-art recommendation techniques.

- **JIM**. JIM [29] is a joint probabilistic model which integrates the content-effect, geographical-social influence, temporal effect and word-of-mouth effect. The word-of-mouth effect refers to the scenario that, a target region, the popularity of a spatial item has a large effect on the probability of a user visiting that item.
- **LCA-LDA**. LCA-LDA is a location-content aware model which has recently developed to support spatial item recommendation for out-of-town users [16]. This model takes into account both personal interests and local preferences of each location by exploiting both item co-visiting patterns and content of spatial items. Compared with ST-SAGE, LCA-LDA is a traditional mixture model which ignores the rules of users and does not consider tourist and native preference. Moreover, LCA-LDA has not integrated temporal information.
- **UTE+SE**. UTE+SE [9] is a collaborative recommendation model which incorporates both the temporal and spatial information. Given a user and his/her querying time, this model first finds the users sharing similar temporal preference with him/her and produces the time-aware recommendations based on these similar users' historical records.
- **CKNN**. CKNN, proposed in [1], projects a user's activity history into the query space and models user preference using a weighted category hierarchy. When receiving a query, CKNN retrieves all items and users in the querying location then applies a user-based CF method to predict the rating of a querying user on an unvisited item. That the similarity between two users in CKNN is computed according to weights in the category hierarchy, CKNN is a hybrid recommendation method.
- **UPS-CF**. UPS-CF [7] is a collaborative recommendation framework which is specifically designed for out-of-town users. This framework integrates user-based collaborative filtering and social-based collaborative filtering. That is, it recommends spatial items to a target user according to the activity records of both his/her friends and similar users.
