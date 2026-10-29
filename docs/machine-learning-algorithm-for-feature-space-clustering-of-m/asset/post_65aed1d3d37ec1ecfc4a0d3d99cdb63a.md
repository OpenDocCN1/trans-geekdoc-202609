
The center of the cluster C_v is symbolized and well-defined as:

Y_v = {y_1^v, y_2^v, ..., y_M^v}, (7)

where the significance at q^th component of Y_v is a likelihood distribution on I_q^v estimated by a kernel orientation approach using equation (5) and is well-defined as:

y_q^v = [P_q^v(I_{1q}^v), P_q^v(I_{2q}^v), ..., P_q^v(I_{|I_q|}^v)] . (8)

The significance of each categorical feature I_{pq}^v (1 ≤ p ≤ |I_q^v|) is computed through equations (4), (5), and (6) as follows:

P_q^v(I_{pq}^v) = { θ_v 1/|I_q^v| + (1 - θ_v) RR_v(I_{pq}^v) if I_{pq}^v ∈ I_q^v ; 0 otherwise } . (9)

## Example 4:
Assume that instances in Table 2 are allocated into the cluster C_1 = {I_1, I_2, I_3, I_5, I_7, I_15}. The smoothing capacity factor is θ_1 = 0.4827. Hence, the center of the cluster of Y_1 for categorical features are computed as F_1 = {u = 0.2069, v = 0.3793, w = 0.2069, x = 0.2069}, F_2 = {u = 0.5, v = 0.5}, F_3 = {w = 0.5, z = 0.5}, F_4 = {x = 0.3275, y = 0.6724}, and numerical features are computed as 0.35556 and 14.1111, respectively.

## Definition 7: Closeness between two categories
The closeness between A and B is computed by the number of facts desirable to state the unity of A and B and the statistics needed to completely define what A and B are. In general, the closeness among A and B is determined as:

CLO(A,B) = log P(common(A,B)) / log P(description(A,B)), (10)

where P(s) is the probability of a statement, and the information contained in s is computed by [-log P(s)].

Let there be two clusters I_{pq} and I'_{pq} taking place in two instances I_p and I_p' at the q^th feature. The closeness amongst the clusters is symbolized and well-defined as:

CLO_q(I_{pq}, I'_{pq}) = 2 log RR(I_{pq}, I'_{pq}) / (log RR(I_{pq}) + log RR(I'_{pq})). (11)

and recurrence relation is defined as:

RR(I_{pq}, I'_{pq}) = # (I_{pq}, I'_{pq}) / |X_CAT| , (12)

## Example 5:
Based on Table 2, only complete instances are considered, and thus, the closeness metric of categorical values y and v in the feature F_1 is CLO_q('y''', 'v''') = 2 log R_1 / (log R_1 + log R_1) = 0.4665.

## Definition 8: Closeness metric for numerical features
The instance-cluster closeness amongst numerical features I_p^{NF} and the cluster C_v, p = 1,2,...,N, v = 1,2,...,K is represented as:

CLO(I_p^{NF}, C_v) = exp(-0.5 ||I_p^{NF} - c_v||^2) / sum_{i=1}^k exp(-0.5 ||I_p^{NF} - c_i||^2). (13)

## Definition 9: Closeness metric for categorical features
expressed as follows:

CLO_q(I_{pq}^{CF}, C_v) = sum_{I_{pq} ∈ I_q^v} P_q^v(I_{pq}) CLO_q(I_{pq}, I'_{pq}). (14)

The closeness measure amongst I_p and cluster center Y_v can be expressed as follows:

CLO(I_p^{CF}, Y_v) = sum_{q=1}^M CLO_q(I_{pq}^{CF}, C_v). (15)

## Definition 10: Closeness metric for mixed features
Let the instance-cluster closeness measure amongst the instance I_p and cluster C_v, represented as CLO(I_p, C_v), which is the average closeness measure computed built on every feature. Then,

CLO(I_p, C_v) = 1/F_M [ CLO(I_{p1}^{CF}, C_v) + CLO(I_{p2}^{CF}, C_v) + ... + CLO(I_{pF_c}^{CF}, C_v) + CLO(I_p^{NF}, C_v) ] . (16)

CLO(I_p, C_v) = 1/F_M sum_{q=1}^{F_c} CLO(I_{pq}^{CF}, C_v) + 1/F_M CLO(I_p^{NF}, C_v), (17) where F_M = F_c + 1.

## Definition 11: Imputation Closeness Measure (ICM)
A mixed data set χ = {I_1, I_2, ..., I_N} contains complete and missing information on instances. Let F' = {F'_1, F'_2, ..., F'_M} be the complete features and F'' = {F''_1, F''_2, ..., F''_M'} be the missing information on features such that {F'_M', F''_M'} ⊂ F'_M, M' < M. For all f = {f'_1, f'_2, ..., f'_{M'}} ∈ F'_1 × F'_2 × ... × F'_M and f'' = {f''_1, f''_2, ..., f''_{M'}} ∈ F''_1 × F''_2 × ... × F''_{M'}, the ICM between f' and f'' is defined as:

ICM(f', f'') = Support(f', f'') / sqrt(Support(f') × Support(f'')). (18)

## Definition 12: Missing complete closeness measure (MCCM)
Let the mixed data set χ contain both complete and missing information on instances. The closeness between two categorical values is defined as:

CLO_d^{mis}(I_{pd}, I'_{pd}) = { 2 log RR(I_{pd}, I'_{pd}) / (log RR(I_{pd}) + log RR(I'_{pd})) if I_{pd} ≠ ? and I'_{pd} ≠ ? ; 0 otherwise } (20)

Let I = {I_1, I_2, ..., I_M} be the complete instances and I' = {I'_1, I'_2, ..., I'_{M'}} be the missing information on instances. The MCCM between I and I' defined as:

MCCM(I, I') = sum_{d=1}^M CLO_d^{mis}(I_{pd}, I'_{pd}) (21)

## Example 6:
Table 3 shows complete information that is extracted from Table 2. Let us select the categorical instance I_6^{CF} = {x, v, z, ?} as the missing information. The decision tree uses F_4^{CF} as the class feature that is to be generated for I_6^{CF} on Table 3. The instance I_6^{CF} is then allocated to child 7. The whole information of categorical instances that are associated with I_6^{CF} are {I_1, I_2, I_3, I_5, I_7, I_15}. The complete information of categorical

![](img/4e39085eb98826467f01a93fc8260e3b_6_0.png)

## Fig. 1. The Clustering Process of Molecule Similarity.
features contains $F_1^{CF} = \{v, v, w\}$, $F_2^{CF} = \{u, u, w\}$ and $F_3^{CF} = \{v, u, z\}$. The missing information of categorical feature $F_4^{CF}$ contains $\{y\}$. The likelihood of computed information is the only y. Therefore, the missing information on $I_6^{CF} = \{x, v, z, y\}$.

whole information of categorical instances that are associated with $I_8^{CF}$ are $\{I_5, I_{15}\}$. For the missing information in the feature $F_4^{CF}$ the instance $I_8^{CF}$ is allocated to child 1. The complete information of categorical features $F_1^{CF}$, and $F_2^{CF}$ contains $\{v, v\}$, $\{w, u\}$ and $\{v, u\}$. The missing information of categorical features $F_3^{CF}$ and $F_4^{CF}$ contains $\{w, y\}$, $\{z, x\}$ and $\{z, y\}$.

## Example 7:
Next, Let us select the categorical instance $I_8^{CF} = \{v, u, ?, ?\}$ as the missing information. There are two missing information such as $F_3^{CF}$ and $F_4^{CF}$ in $I_8^{CF}$. Therefore, two decision trees use $F_3^{CF}$ and $F_4^{CF}$ as the class feature that is to be generated for $I_8^{CF}$ on Table 3. For the missing information in the feature $F_3^{CF}$ the instance $I_8^{CF}$ is allocated to child 8. The

The ICM and MCCM measure for every set of categorical information in the complete and missing information are:

![](img/4e39085eb98826467f01a93fc8260e3b_7_0.png)

Fig 2. A Sample Chemoinformatics Datasets.

![](img/4e39085eb98826467f01a93fc8260e3b_7_1.png)

Fig 3. Projection of Data into High-dimensional Feature Space.

ICM{ {v, v}, {w, y} } = 0.5 / sqrt(0.5 × 0.5) = 1, ICM{ {w, u}, {z, x} } = 0.25 / sqrt(0.25 × 0.25) = 1
= 1,

ICM{ {v, u}, {z, y} } = 0.25 / sqrt(0.25 × 0.25) = 1,

MCCM(f₂^CF, f₈^CF) = MCCM(f₅^CF, f₈^CF) = (2 log 0.8)/(log 0.8 + log 0.8) + (2 log 1)/(log 0.4 + log 0.6) + 0 + 0 = 1

MCCM(f₅^CF, f₈^CF) = (2 log 1)/(log 0.8 + log 0.8) + (2 log 0.6)/(log 0.6 + log 0.6) + 0 + 0 = 1

MCCM(f₁₅^CF, f₈^CF) = (2 log 0.8)/(log 0.8 + log 0.8) + (2 log 0.6)/(log 0.6 + log 0.6) + 0 + 0 = 2

The likelihood of computed information of {w,y}, {z,x}, and {z,y}

are 0.2857, 0.2857, and 0.4286, respectively. Therefore, {z,y} has a likelihood of being selected as the actual missing information of f₈^CF.

## 4. Clustering process
The common work for processing clusters is to categorize the specified instances into numerous groups such that the likeness amongst instances in the equivalent set is great while the likeness amongst instances in diverse sets is little. The Clustering process of molecule similarity is shown in Fig. 1. A sample chemoinformatics datasets is presented in Fig. 2. Projection of data into high-dimensional feature space is shown in Fig. 3.

Let χ indicate an extensive set of training vectors χ ≡ {I₁, I₂, …, I_N} into K disjoint groups, where I_f ∈ R^N, such that

## Table 4
### Mixed Dataset Imputation (MDI) algorithm.
Mixed Dataset Imputation (MDI) algorithm

Input:
𝒳 = (I₁, I₂, ..., I_N): a mixed dataset with missing information
Output:
A mixed dataset 𝒳 with complete information
Algorithm:
1. Split into two subsets, 𝒳 = 𝒳₁ (complete set) + 𝒳₂ (missing information set)
2. Extract complete instances in 𝒳₁ into 𝒳₁^NF and 𝒳₁^CF that contain numerical and categorical instances respectively.
3. Extract missing instances in 𝒳₂ into 𝒳₂^NF and 𝒳₂^CF that contain numerical and categorical instances respectively.
4. for each instance 𝒳₂ in 𝒳₂^CF do
5. Compute ICM measure by Eq. (18) for missing categorical features.
6. Compute MCCM measure by Eq. (21) for missing categorical features.
Compute sampling likelihood values based on ICM and MCCM.
7. end for
8. for each instance 𝒳₂ in 𝒳₂^NF do
9. Replace the missing information by mean of numerical values using Eq. (3)
10. end for
11. 𝒳 = Merge 𝒳₁ and 𝒳₂
12. return mixed dataset 𝒳 with complete information.

## Table 5
### Feature Space Clustering of Mixed data with Missing Information Algorithm.
Feature Space Clustering of Mixed data with Missing Information (FSCMMI) Algorithm

Input:
𝒳 = (I₁, I₂, ..., I_N): a mixed dataset with missing information
k: a user-defined number of clusters
Output:
The cluster label vector Y = {y₁, y₂, ..., y_N} and feature cluster weights matrix W
Algorithm:
1. Mixed Dataset 𝒳 = MDI(𝒳)
2. Initialize Y = {0,0,...,0}, Choose K initial instance, and set W_qv = 1/F, one for every cluster
3. Repeat
4. for p = 1 to N do
5. for v = 1 to K do
6. Compute y_p = argmax [Z_pv, CLO_W(I_p, C_v)]
7. Update the cluster y_v, including the rate of recurrence relation of every categorical features and the center of cluster for numerical features
8. end for
9. end for
10. Update W_qv according to the equations (39), (40), (42), and (43).
11. Until the partitions does not change.

![](img/4e39085eb98826467f01a93fc8260e3b_8_0.png)

Fig. 4. A schematic diagram for the computation of feature space clustering of mixed data with missing information.

![](img/4e39085eb98826467f01a93fc8260e3b_8_1.png)

Fig. 5. Tree for the missing feature F₄^CF in T₆^CF.

![](img/4e39085eb98826467f01a93fc8260e3b_8_2.png)

Fig. 6. Tree for the missing feature F₃^CF in T₈^CF.

![](img/4e39085eb98826467f01a93fc8260e3b_8_3.png)

Fig. 7. Tree for the missing feature F₄^CF in T₈^CF.
