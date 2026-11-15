

operation. In the end, each user can upload their bucket number to blockchain. The pseudocode of Min-Hash algorithm is shown in Algorithm 1.

```
Algorithm 1: Min-Hash Based LSH
Input:
M: Sparse matrix of raw data
U_s: Random seed set by each user
P: Row permutation times
Nban: The number of bands in the signature matrix
Nrow: The number of lines in each band
Nbuc: The number of buckets that can be mapped
Output:
B: Bucket number set
1: initialize matrix s with 0
2: for each i ∈ P do
3: generate seed with U_s
4: row_order ← permutation rows
5: M ← M[row_order, :]
6: get the first row number of '1' in M's each column
7: s[i] ← first row number
8: end
9: current_row ← 0, initialize array buckets
10: for each b ∈ Nban do
11: band ← s[current_row: Nrow + current_row, :]
12: current_row ← current_row + Nrow
13: ids ← ravel_multi_index(band, band.max()(1)+1)
14: buckets ← ids
15: end
16: initialize array B
17: for each item ∈ buckets do
18: get crc32_value of item
19: hash_bucket ← crc32_value mod Nbuc
20: B ← hash_bucket
21: end
22: return B
```

### C. PCMS Based Local Differential Privacy

The pseudocode of this method is shown in Algorithm 2. Each user perturbs raw data locally and sends the results to IPFS, then upload received IPFS hash to blockchain. Then users needing recommendations can obtain overall data features and rank the results in descending order. In the end, the algorithm provides these users with TOP-N items.

## IV. EXPERIMENTAL STUDIES

We conducted enough experiments to verify the effectiveness of the proposed mechanism on two real datasets. We first describe the environment and datasets used in the experiments, and subsequently explain the evaluation metrics. Finally, we show the performance of the mechanism under different parameter settings.

### A. Experiment Setup and Datasets

All the experiments are implemented in multiple Ubuntu 16.04 virtual machines running in two personal computers, one is configured with 12GB RAM, Intel i5-6300HQ CPU and the other is with 32GB RAM, Intel i9-9880H CPU. Each virtual machine is allocated at least 6G RAM to support the experiments. The packages and tools used are Python 2.7.17, tensorflow 2.1.0, numpy 1.16.6 and graphlab 2.1. Ethereum chain is used to record the required information during recommendation. We evaluate the mechanism on Movielens datasets¹ provided by GroupLens, the smaller dataset is termed as ML_100K, for the larger one, only half of the items are used, termed as ML_20M. The datasets containing the watched movies of each user and the rating value ranging from 0.5 to 5. The metadata of the two datasets is shown in Table I.

¹ https://grouplens.org/datasets/movielens/latest/

```
Algorithm 2: PCMS Based Local Differential Privacy
Input:
D: Raw dataset of users
D_t: All user data domain
ε: Differential privacy budget
k: The number of hash function
m: The mod of hash function
Functions:
PerturbData(): perturbs users' data
ComputerSketchMatrix(): generates sketch matrix for recommendation
GetFrequencyStatistics(): obtain frequency statistics
Output:
F (f(d): d ∈ D_t): Frequency statistics of each element in dataset domain
1: select a set H = {h1, ..., hk} randomly, mapping D to [m]
2: for each d(i) ∈ D do
3: (v(i), j(i)) ← PerturbData (d(i), ε, H)
4: end
5: sketch M ← ComputerSketchMatrix ((v(i), j(i))), ..., ((v(n), j(n))), ε, k, m)
6: for each d ∈ D_t do
7: f(d) ← GetFrequencyStatistics(d_t, M, ε, H)
8: end
9: return F (f(d): d ∈ D_t)
```

| | Users | Movies | Ratings | Average | Density |
|---|---|---|---|---|---|
| ML_100K | 610 | 9742 | 100836 | 3.2549 | 1.70% |
| ML_20M | 110000 | 27278 | 1590140 | 3.4964 | 1.85% |

### B. Evaluation Metrics

To evaluate the recommendation accuracy, we use the metrics: Precision P, Recall R, and F1-Measure F1. The definitions of them are as follows:

```
P = \frac{\Sigma_{u \in U} |S(u) \cap T(u)|}{\Sigma_{u \in U} |S(u)|} \quad (2)
```

```
R = \frac{\Sigma_{u \in U} |S(u) \cap T(u)|}{\Sigma_{u \in U} |T(u)|} \quad (3)
```

```
F_1 = \frac{2*P*R}{P+R} \quad (4)
```

Where U denotes the user set, u represents a certain user (u ∈ U). S(u) is the item set recommended to the user, T(u) is the user behavior item set. |S(u)| and |T(u)| represent the number of elements in S(u) and T(u) respectively.

### C. Experimental Results and Analysis

- 1) LSH clustering based on Min-Hash: We conduct experiments with different bucket numbers to find the optimal one for subsequent experiments. Since the two datasets have the same structure, some data-processing-related parameters are kept the same. The permutation times, the number of bands in signature matrix, and the random seed are set to 100, 25, and 19248 respectively. The only parameter different between the two datasets is the bucket number b. Several metrics are introduced to evaluate the performance, as shown in Table II and Table III. Table II K denotes the number of neighbors of certain user. When K < 3, K - 1 users can easily collude to infer privacy information of other users [4], that is the situation we need to avoid. K̄ represents the average number of neighbors of each user. Utilization rate U reveals the percentage of buckets where the number of users is greater than 1. In the scenario where only one user in some buckets, the process to find the similar users will be costly. LSH algorithm can greatly reduce the computation load, R refers to the percentage of new computation load to the old one, 1 - R represents the computation load reduced.

Therefore, for ML_100K, when bucket number b is set to 1536, the utilization rate of all buckets is 100%, and 96.28% of computation load is reduced. Meanwhile, a desirable privacy protection level can be maintained when K < 3. Similarly, we choose b = 24576 as the optimal bucket number for ML_20M.

TABLE II. EXPERIMENTAL RESULTS OF ML_100K

| Bucket number(b) | Neighbors per user (K̄) | Users whose K<3 | Utilization rate(U) | Relative computation cost (R) |
|---|---|---|---|---|
| 512 | 41.23 | 0 | 100.00% | 6.76% |
| 1024 | 27.15 | 0 | 100.00% | 4.45% |
| 1536 | 22.71 | 1 | 100.00% | 3.72% |
| 2048 | 20.16 | 7 | 99.95% | 3.30% |
| 2560 | 18.84 | 17 | 99.53% | 3.09% |
| 3072 | 17.81 | 37 | 98.77% | 2.92% |
| 3584 | 17.31 | 60 | 98.10% | 2.84% |

TABLE III. EXPERIMENTAL RESULTS OF ML_20M

| Bucket number(b) | Neighbors per user (K̄) | Users whose K<3 | Utilization rate(U) | Relative computation cost (R) |
|---|---|---|---|---|
| 8192 | 775.12 | 0 | 100.00% | 0.68% |
| 12288 | 668.43 | 0 | 100.00% | 0.61% |
| 16384 | 559.11 | 0 | 100.00% | 0.51% |
| 20480 | 499.39 | 0 | 100.00% | 0.45% |
| 24576 | 444.56 | 5 | 100.00% | 0.40% |
| 28672 | 401.47 | 64 | 99.83% | 0.36% |
| 32768 | 334.51 | 215 | 98.90% | 0.30% |

- 2) LSH clustering based on Min-Hash:

![](img/ba6405dd3b4100239a8087f4ac628bd3_3_0.png)

![](img/ba6405dd3b4100239a8087f4ac628bd3_3_1.png)

Before local differential privacy is performed, each user needs to reconstruct the dataset via the following rules. For a movie with a rating of N, the record of that movie will be copied for N times. In this way, N + 1 records of the movie will be in the dataset. For the unrated movies, only one record is generated for each of them and appended into the new dataset.

We consider the rated movies and corresponding ratings as the privacy information of users, and analyze the potential privacy attacks for choosing the suitable privacy budget parameter ε. Suppose the attackers attempt to recover the obfuscated data of a certain user to infer the watched movies and ratings. Let N and N' be the correct and recovered rating respectively, and the difference between them is defined as d = |N - N'|. We argue that the privacy is well preserved if d >= 2, otherwise, there is a high risk for privacy disclosure. Let DR denotes the degree of privacy disclosure, whose value is decided by the percentage of data with d < 2 after perturbation. We conduct experiments on ML_100K and ML_20M when ε takes value from 0.1, 0.2, 0.3, 0.4, 0.5, 0.75, and 0.9. As results shown in Fig. 2, the larger the value of ε, the more likely the privacy is disclosed.

