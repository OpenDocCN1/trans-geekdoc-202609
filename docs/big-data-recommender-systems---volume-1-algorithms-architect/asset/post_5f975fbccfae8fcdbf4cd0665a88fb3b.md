
# Spatiotemporal recommendation with big geo-social networking data 197

## 9.2 Preliminaries about SAGE

Our proposed model is inspired by the SAGE model [17]. SAGE is an effective generative mixture model in the situation where a variable is affected by several factors as it does not need explicit switching variables and has been widely used in many existing work [20–23]. The key technical difference from traditional mixture models is that the mixture occurs in the natural parameters of the exponential family instead of distributions. Such a model is robust given limited training data as it does not have to infer a complex variable to distinguish the set of cases.

To provide a clearer explanation of SAGE, we compare it with a traditional probabilistic mixture model, LCA-LDA [16], as an illustrative example. LCA-LDA is a location-content-aware model which aims to mimic the process of decision-making when visiting spots. There are two factors affecting users' decision-making in checking in spots: the user’s personal interest $\theta_{user}^c$ and the influence of local preference $\theta_{row}^c$ (note that, it does not distinguish between native preference and tourist preference). LCA-LDA combines the two factors in a unified manner. Specifically, in this traditional probabilistic mixture generative model, by querying a user $u$ at a target location $l$, the likelihood that $u$ will prefer item $v$ is computed by combining the two factors through a linear combination as follows:

```
$P(v|\theta_{user^c,row^c}) = \lambda_u P(v|\theta_{user^c}) + (1 - \lambda_u)P(v|\theta_{row^c})$  (9.1)
```

where $\lambda_u$ is the “switching” variable and obviously it needs to be trained for each user. For each record, other than the latent topic, we also need to sample the switching variable. Thus, the complexity is doubled. Unlike the increased complexity, when the data is sparse, it cannot be inferred as the training data for each individual user even sparser. In contrast, SAGE combines the two generative facets through simple addition in log space, as shown in (9.2). Clearly, SAGE avoids the computation for latent switching variables.

```
$P(v|\theta_{user^c,row^c}) = P(v|\theta_{user^c} + \theta_{row^c}) = \frac{\exp(\theta_{u,v}^{user^c} + \theta_{row^c})}{\sum_{v'} \exp(\theta_{u,v'}^{user^c} + \theta_{row^c})}$ (9.2)
```

## 9.3 Spatial–temporal SAGE model

In this section, we first formulated the problem definition and then propose our ST-SAGE model.

### 9.3.1 Problem definitions

We first define the data structures used in this chapter and then introduce the research method. For ease of reference, the involved notations in this part is summarized in Table 9.2.

Table 9.2 Notations of the input data

| Variable | Interpretation |
| --- | --- |
| $U, V, R, T$ | The set of users, spatial items, locations and time slices |
| $W$ | The vocabulary set |
| $D_u$ | User $u$'s profile |
| $v_{u,i}$ | The spatial item of $i$th record in $D_u$ |
| $l_{u,i}$ | The location of spatial item $v_{u,i}$ |
| $l_u$ | The home location of user $u$ |
| $W_{u,i}$ | The set of words describing spatial item $v_{u,i}$ |
| $w_{u,i,n}$ | The $n$th word describing spatial item $v_{u,i}$ |
| $s_{u,i}$ | A Boolean value indicating whether the user $u$ is a local or tourist on location $l_{u,i}$ |
| $t_{u,i}$ | The occurrence time of $i$th record in $D_u$ |

**Definition 9.1. (Spatial item)** A spatial item is an item associated with a geographical location (e.g., a hotel or a scenic spot).

A spatial item in world has three attributes: identifier, location and content, represented by $v$, $l$, and $W$, respectively. The content associated with the spatial items refers to the set of words describing the item, such as tags and categories. The location information for each spatial item $v$ in the collected raw datasets is in form of the (latitude, longitude) pair. A spatial pyramid [13,24,25] is adopted to partition and index the entire geographic area, and then index of the area containing this location as the identifier $l_v$ of this location. The granularities range from cities to streets, depending on the nature of the applications. The details of the spatial pyramid are described in Section 9.3.4.

**Definition 9.2. (User home location)** Given a user $u$, following the recent work of [26], define the user's home location as the place where he/she lives, denoted as $l_u$.

Due to the privacy problem, user home locations are not always available. For a user whose home location is not explicitly given, the method proposed in [27] is adopted to infer the user's home location as the cell in the spatial pyramid containing most of his/her check-ins.

**Definition 9.3. (Time)** $t$ is an ordinal variable and $u$ to index the $i$th time slice which corresponds to a specific time period.

The time information available for each record in the collected raw datasets is in form of the (latitude, longitude) pair. A spatial pyramid [13,24,25] is adopted to partition and index the entire geographic area, and then index of the area containing this location as the identifier $l_v$ of this location. The granularities range from cities to streets, depending on the nature of the applications. The details of the spatial pyramid are described in Section 9.3.4.

**Definition 9.4. (User activity)** A user activity consists of $(u, v, l, t, s)$.

# Spatiotemporal recommendation with big geo-social networking data 199

A user activity indicates that the user $u$ visits $v$, located at $l$ and described as $W$, at time $t$. If $s=0$, the user is recognized as local. If $s=1$, the user plays the role of tourist.

**Definition 9.5. (User profile)** For each user $u$, we create a user profile $D_u$, which is a set of user activities associated with $u$.

**Problem 9.1. (Spatial item recommendation)** Given a dataset $D$, a target user $u$ with current location $l$ and querying time $t$ (i.e., $q=(u, l, t)$), our goal is to recommend $k$ spatial items that the target user would be most interested in. Given a distance $d$, the problem becomes **out-of-town recommendation** if the distance between $u$'s current location and home location $|l-l_h|$ is greater than $d$. Otherwise, the problem is hometown recommendation.

We set $d=100$ km in following related studies [7,30–32]. A distance around 100 km is the typical radius of human “reach” as it usually takes 1–2 h to drive such distance.

## 9.3.2 Model description

In this chapter, we propose an ST-STAGE to model users activities in LBSNs. The graphical representation of ST-STAGE is demonstrated in Figure 9.1. The notations of our model are summarized in Table 9.3. The shaded circles in Figure 9.1 model the observed random variables.

**User interest modeling.** Intuitively, a user chooses a spatial item at a given location and a specific time by matching his/her interests with the content of that item. Inspired by the early work of user interest modeling [16,20,33], ST-STAGE also adopts latent topics to characterize users’ interests. We infer an individual user’s interest vector over a set of topics according to his/visited spatial items and their associated contents, denoted as $\theta^{user}$. As the content of spatial items can be the medium through which user preferences from their hometown can be transferred to out-of-town regions, our proposed model is able to alleviate the locality problem for out-of-town recommendation. Moreover, beyond $\theta^{user}$, we also introduce a background vector over topics $\theta^b$.

**Spatial dynamic modeling.** To adapt to spatial dynamics of user behavior, we exploit the preferences of crowds who share the same role as the target user $u$. For example, the preferences of the tourists will be leveraged if the target user is currently
