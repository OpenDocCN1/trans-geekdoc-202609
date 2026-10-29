# Table 2

An example mixed numerical and categorical dataset with missing values.

| Instances (I) | F1 | F2 | F3 | F4 | F5 | F6 |
|---|---|---|---|---|---|---|
| I1 | x | v | z | y | 7 | 14 |
| I2 | v | v | w | y | 6 | 13 |
| I3 | v | v | w | y | 2 | 13 |
| I4 | u | v | u | v | 5 | 13 |
| I5 | w | u | z | x | 2 | 14 |
| I6 | x | v | z | ? | ? | 14 |
| I7 | u | u | w | y | 1 | 14 |
| I8 | v | u | ? | ? | ? | 12 |
| I9 | w | v | u | w | 5 | 14 |
| I10 | v | ? | x | y | 5 | 7 |
| I11 | x | u | x | w | 10 | 13 |
| I12 | x | v | x | x | 3 | 12 |
| I13 | ? | v | u | y | 2 | ? |
| I14 | u | u | x | x | 2 | 18 |
| I15 | v | u | z | y | 2 | 14 |

# Table 3

The complete categorical features.

| Instances (I) | F1^CF | F2^CF | F3^CF | F4^CF |
|---|---|---|---|---|
| I1^CF | x | v | z | y |
| I2^CF | v | v | w | y |
| I3^CF | v | v | w | y |
| I4^CF | u | v | u | v |
| I5^CF | w | u | z | x |
| I7^CF | u | u | w | y |
| I9^CF | w | v | u | w |
| I11^CF | x | u | x | w |
| I12^CF | x | v | x | x |
| I14^CF | u | u | x | x |
| I15^CF | v | u | z | y |

observation of the clustering process (i.e. Fc categorical features and 1 numerical vector (FM = Fc + 1)). Table 1 shows the list of notations used in this paper. Table 2 shows an example mixed numerical and categorical dataset with missing values. Table 3 shows the complete categorical features.

# Definition 1: Clusters

A mixed data set χ = {I1, I2, ..., IN} is defined for the clustering problem. Let C = {C1, C2, ..., CK} be a cluster of K individual subclusters. Cv is defined as a cluster of χ if and only if Cv ∩ Cv' = ∅ ∀ v ≠ v' and χ = ∪v=1^K Cv

# Example 1:

Assume that the specified instances be located in three subsets of: C1 = {I1, I2, I3, I5, I7, I15}, C2 = {I4, I6, I8, I9, I10, I11, I12, I13, I14} and C3 = {I1, I2, I3}. At that point, {C1, C2} belongs to clusters of, while {C1, C3}, {C2, C3} and {C1, C2, C3} are not.

# Definition 2: Recurrence Relation

The recurrence relation is computed for the given categorical data set χCAT of the set Ipq at the qth feature of χCAT is symbolized and well-defined as: RR(Ipq) = # (Ipq) / N

RRv(Ipq^v) = #v(Ipq^v) / Nv

where #v(Ipq^v) is the number of instances that contain Ipq^v in Cv at the qth feature.

# Example 2:

In Table 2, suppose if the cluster C1 = {I1, I2, I3, I5, I7, I15}, then the recurrence relation of categorical value “v” in the feature F1 is RRv(v) = 3/6 = 0.5.

# Definition 3: Mean of Numerical Features

Let the numerical features are INFp = (INFp1, INFp2, ..., INFpN)^T that belongs to the cluster Cv and Yv is the center of the cluster Cv. The mean of every feature Fd^NF in the cluster is determined as follows: Yd^NF = 1/N sum p=1^N I'pq.

# Example 3:

In Table 2, suppose if the cluster C1 = {I1, I2, I3, I5, I7, I15}, then the mean value of the feature is F6 is Y6^NF = (14+13+13+14+14+14)/6 = 13.67.

# Definition 4: Kernel orientation approach

Let Iq^v and p(Iq^v) represent an indiscriminate parameter related to annotations I_pq (1 ≤ p ≤ Nv) taking place in the cluster Cv at the qth feature and likelihood of concreteness, respectively.

# Definition 5: Smoothing capacity factor

Given a cluster Cv, a smoothing capacity factor is used to reduce the overall errors of the consequential evaluation over instances in this cluster. The peak smoothing factor for Cv is symbolized and well-defined as: θv = 1/(Nv-1) * sum...

# Definition 6: Cluster Center