among various nodes and utilize Link Prediction as the downstream task. We specifically obtain the features of user nodes as user bias \( U_b \) from the dynamic graph encoder.

# 3.2 R2GFormer

After acquiring the initial meta and textual features of the nodes, we use the textual features \( N_t \), which include rich information about the nodes, as the initial embeddings \( N_g^{(0)} \) for **R2GFormer**. This graph encoder not only models the complex relations and interactions between users, reviews, and movies but also handles features from different genres of the entire graph and captures remote dependencies. First, we will introduce how we construct the whole graph. Then, we decompose an R2GFormer layer into two parts: RetGAT and Genreformer, which will be introduced respectively.

**Graph Construction.** We first construct a directed graph consisting of three types of nodes: { User, Review, Movie } and the following three types of edges: E1 : Movie — Review We connect a review node to a movie node if the review is about the movie, but not vice versa. This setup allows movie information to influence the review while ensuring that the review information does not affect the movie. E2 : Review — User We connect a review node to a user node if the review is posted by the user. E3 : User — Review We connect a user node to a review node if the user posts the review.

**RetGAT.** Inspired by the work of [9,26,34], we propose RetGAT, which extends the RetNet framework by integrating a global perception into GAT, incorporating explicit exponential decay for nodes within \( k \) hops and truncation for nodes beyond \( k \) hops. This method ensures a broad receptive field while balancing performance and computational complexity by dynamically adjusting the influence of nodes based on their distance, with closer nodes having a higher impact on the final node features.

To achieve this global receptive field, we utilize \( k \) parallel GAT layers to separately aggregate information from \( k \)-hop neighbors. For each layer, node features are aggregated from different \( k \)-hop neighborhoods, applying decay factors to control the influence of information from various hops. Beyond \( k \) hops, the influence of nodes is truncated to maintain computational efficiency and focus on relevant information within the \( k \)-hop range. Note that we correct the algorithm that previous work [1,37] used to compute \( k \)-hop neighbors, and the details are available in the supplementary material.

The decay factor \( \delta_h \) for hop \( h \) (\( h \le k \)) is defined as:

```
\(\delta_h = \exp(-\alpha \cdot h),\) (1)
```