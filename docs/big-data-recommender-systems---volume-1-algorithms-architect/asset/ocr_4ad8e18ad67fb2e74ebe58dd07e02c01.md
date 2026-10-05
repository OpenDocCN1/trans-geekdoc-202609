# 52 Big recommender systems, volume 1

connected items $i_a, i_b$ is defined as $\psi_{rab}(r_{za}, r_{zb}) = (1/Z_{ab})\exp(-(r_{za}-r_{zb})^2/\sigma_{ab}^2)$, where $\sigma_{ab}$ is adjusted by item similarity, penalizing the incompatible rating from connected items if they deviate from each other. The authors employ a probabilistic message passing (in the form of BP) algorithm over the defined PMRF and the observed beliefs (expectations of the marginal probability distributions) corresponding to the desired ratings are exact if the PMF has no loops, otherwise they constitute approximations of the desired ratings (Figure 4.4). The approach was evaluated in [21] on the 100K MovieLens dataset using the mean absolute error and root mean square error metrics, demonstrating comparative performance with the state of the art at the time and linear complexity per user ever. Further, it can update the recommendations for each user instantaneously, using the most recent rating, without needing to solve the marginal distributions for all users. The results indicate that such approaches can scale well in bigdata environments and efficient implementations.

# 4.3.2.2 Preference networks

The work in [22] suggests preference networks (PNs), a probabilistic model for combining content-based with CF into a hybrid recommendation approach. The goal of PNs is again to estimating the user to item ratings of the utility (preference) matrix for only a limited set of items for each user (top-N ranking), as a user is typically interested in a moderate number of items.
In PNs, each vertex of the undirected directed graph $G(V, E)$ corresponds to a rating $r_{ui}$ of user $u$ for item $i$ and each edge captures a relation between two ratings, either of item-item or user-item. Specifically, there is an edge between two ratings by the same user, and an edge between two ratings on the same item (Figure 4.5). The resulting network is typically very connected. The PN is a conditional MRF that defines a distribution over the graph, $P(X|\mathbf{o}) = (1/Z(\mathbf{o}))\Psi(X, \mathbf{o}) = \prod_{u \in V} \psi_u(r_{ui}) \prod_{(i,j) \in E} \psi_{ij}(r_{ui}, r_{uj})$, where $\mathbf{o}$ is the vector of all user and item features combined, $\psi$ is the potential function, and $\psi_u(r_u, \mathbf{o})$ encodes information associated with rating $r_u$, and $\psi_{ij}$ captures correlations between two

To other users/items

![](bbox=[0.318, 0.712, 0.682, 0.843])

Figure 4.5 Example of a preference network, where the associations between user-user, item-item and user-item are shown