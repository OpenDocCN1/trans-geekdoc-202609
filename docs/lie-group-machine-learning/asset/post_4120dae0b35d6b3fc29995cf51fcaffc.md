
![](img/456a7a56403cbb2b5f1a261793529a51_357_0.png)

Points as a whole, it would break the local structure and not be useful to find the local characteristic.

Here, we explain this viewpoint by using a simple example. Figure 10.18(a) shows the distribution characteristic of known data points. The region A is null. We process these data points in the overall structure and local structure, respectively. Figure 10.18(b) and 10.18(c) show the results. Figure 10.18(b) and 10.18(c) can be made more explicit to show the internal regularity of the original data.

Each data point corresponds to a weight value $w$ during tensor processing. The unknown data correspond to zero. Figure 10.17 shows tensor $\mathbf{T}_X$ in point $X$. The weight value $\mathbf{w}_B$ represents the extent of the effect of $B$ on $X$. Combined with the previous analysis, we can see that all the data points would be given a new weight value. We can then estimate the cluster data point.

Considering the three points $A$, $B$, and $C$ as well as $\boldsymbol{\xi}_A$ yields the tensor $\mathbf{T}_A$, $\boldsymbol{\xi}_C$ determines the tensor $\mathbf{T}_C$. All these tensors include the information about point $B$. The weight value $w$ of $B$ would be affected by tensor $A$ and tensor $B$, respectively, and we obtain the new weight values $w_1'$ and $w_2'$. The final weight value $w'$ of $B$ would be equal to the mean value of $w_1'$ and $w_2'$, i.e., $w' = w_1' + w_2'/2$.

If one point is affected by its $M$ neighbour points, the environmental information of this point could be represented by an $N$-order tensor $T_{I_1 \times I_2 \times \cdots \times I_N}$. The final weight of point $X$ will be as follows (Figure 10.19):

$$w_X = \frac{1}{M} \sum_{i=1}^{M} T_i \tag{10.44}$$

If the orders of tensor $A$ and tensor $B$ are the same, the result of the tensor addition is $C$. It can be represented by $C_{ijk...} = A_{ijk...} + B_{ijk...}$.

The result of the reconstruction of the tensor field gives us the data distribution characteristics. We can estimate the related information of a point based on the data distribution characteristics. In order to achieve this goal, we have to construct a new tensor $T_{J_1 \times J_2 \times \cdots \times J_N}$ by utilising the entire tensor field, which is also called the discriminant tensor. From the perspective of the classification task, the discriminant tensor is a classifier. The information of the weight values of $\Gamma^{I_1\times I_2\times\cdots\times I_N}$ could yield the classification attributes of the nodes to be considered.

If the cluster of the data object has the $k$ order of $\Gamma$, the $k$-mode vector can describe the cluster characteristics of the data object. We can obtain $\Gamma_{(k)}$ by $k$-mode unfolding. Finally, we assess the cluster characteristics of the data object based on the $k$-mode vector.

![](img/456a7a56403cbb2b5f1a261793529a51_358_0.png)
![](img/456a7a56403cbb2b5f1a261793529a51_358_1.png)
![](img/456a7a56403cbb2b5f1a261793529a51_358_2.png)

**Fig. 10.18:** The global and local processing step.

![](img/456a7a56403cbb2b5f1a261793529a51_358_3.png)

**Fig. 10.19:** The point $B$ is infected by point $A$ and point $C$ at the same time.

### 10.3.4 Classification algorithm based on the tensor field

According to the above analysis, we introduce the tensor field in the classification algorithm. There is a data set $X = \{X_1, X_2, \dots, X_M\}$ and $X_i$ is the sample. Each sample has $N$ attributes, i.e., $X_i = < P_{i1}, P_{i2}, \dots, P_{iN} >$, where $P_{ij}$ represents the $j$-th attribute of each sample. The range of values allowed for $P_j$ is $[U_{Pj}, D_{Pj}]$ and includes $C_j$ possible values.

First, we discuss how to obtain a tensor field model for a known data set. In simple terms, any data object can be described by each attribute in common. Each attribute is a view of the sample, and all the attributes construct a full expression of the sample. Figure 10.20 shows that sample $A$ is described by four attributes.

Therefore, we can construct a tensor, each order of which corresponds to an attribute of samples. The dimension number of the $j$-th order is determined by the neighbour points $\zeta_{X_i}$, and we have $l_j \leq \|U_{P_j} - D_{P_j}\|$. Therefore, we can construct a tensor $T_i^{I_1 \times I_2 \times \cdots \times I_N}$ of each sample $X_i$ based on its high-dimensional linear space.

$T_i^{I_1 \times I_2 \times \cdots \times I_N}$ is the description of the local environmental information, which is also the description of the neighbouring region $\zeta_{X_i}$. Therefore, the value of $T_i^{I_1 \times I_2 \times \cdots \times I_N}$ is determined by $\zeta_{X_i}$. If we have a sample $X_j \in \zeta_{X_i}, X_j$ would have a weight value $w_{ij}$. The component of $T_i^{I_1 \times I_2 \times \cdots \times I_N}$ is:

$$ T_i^{i_1 \times i_2 \times \cdots \times i_N} = w_{ij} X_j, \, X_j = (P_{i1}, P_{i2}, \dots, P_{iN}) \in \zeta_{X_i} \quad (10.45) $$

Here, each point of the linear space determines a tensor. Then, the data set $X$ can determine a tensor field $\Phi(X)$.

We reconstruct the tensor field $\forall T_i \in \Phi(X)$ and decompose $T_i$ by high-order singular value decomposition to

$$ T_i = S_i \times_1 U^{(1)} \times_2 U^{(2)} \times \cdots \times_N U^{(N)} \quad (10.46) $$

Here, $T_i, S_i \in R^{I_1 \times I_2 \times \cdots \times I_N}$ and $U^{(i)}$ is a $I_N \times I_N$ square matrix. Setting $K = \{K_1, K_2, \dots, K_N\}$, it is the reduction dimension of $S(\zeta_{X_i}) = \{l_1, l_2, \dots, l_N\}$.

$$ \tilde{T}_i = \tilde{S}_i \times_1 \tilde{U}^{(1)} \times_2 \tilde{U}^{(2)} \times \cdots \times_N \tilde{U}^{(N)} \quad (10.47) $$

which is the tensor after the reconstruction, and $\tilde{T}_i \in R^{\tilde{I}_1 \times \tilde{I}_2 \times \cdots \times \tilde{I}_N}, \tilde{S}_i \in R^{K_1 \times K_2 \times \cdots \times K_N}, \tilde{U}^{(n)} \in R^{I_n \times K_n}.$

![](img/456a7a56403cbb2b5f1a261793529a51_359_0.png)

**Tab. 10.3:** The continuous attribute values of data set wine.

| No. | class | Alcohol | Malic acid | Ash | Alkalinity of ash | Magnesium | ... |
|---|---|---|---|---|---|---|---|
| 1 | 1 | 14.23 | 1.71 | 2.43 | 15.6 | 127.0 | |
| 2 | 1 | 13.2 | 1.78 | 2.14 | 11.2 | 100.0 | |
| 3 | 1 | 13.16 | 2.36 | 2.67 | 18.6 | 101.0 | |
| 4 | 1 | 14.37 | 1.95 | 2.5 | 16.8 | 113.0 | |
| 5 | 1 | 13.24 | 2.59 | 2.87 | 21 | 118.0 | |
| ... | ... | ... | ... | ... | ... | ... | ... |

In the above algorithm, the attribute values of data are required to be discrete. For continuous attribute values, we need to discretise them. The continuous attribute values are discretised to set some divide point within the range. The discretisation reduces the system's demand for storage space and increases the release of storage space. Table 10.3 shows the Wine data set of UCI, and its condition attributes are all continuous values. From the previous section, we require $\mathrm{I}_{1}$, $\mathrm{I}_{2}$, $\dots$, $\mathrm{I}_{N}$ to be natural numbers for building a series of tensors $T_{i}^{I_{1} \times I_{2} \times \dots \times I_{N}}$. Therefore, we need to project every real attribute value of the data set Wine into the integer attribute values (Table 10.4).

The discretisation should boil down to partitioning of the space, which is achieved by the condition attributes. We divide the space with $N$ dimensions into several regions. Each decision value of the objects in each region is the same. The process of choosing a breakpoint is also a process of merging attribute values. It can reduce the number of attribute values and reduce the problem complexity by merging the attribute values.

At present, the discretisation methods include two categories; one is the unsupervised discretisation method, e.g., the fixed-pitch interval method and equal frequency interval method, and the other is the supervised discretisation method, e.g., the discretisation method based on entropy and the discretisation method based on statistics [13]. The latter approach considers the dependency relationship between the condition attribute and the decision attribute during the processing step. Therefore, this article employs two algorithms to preprocess the data; one is based on the entropy,

**Tab. 10.4:** The discretization of the continuous attribute values.

| No. | class | Alcohol | Malic acid | Ash | Alkalinity of ash | Magnesium | ... |
|---|---|---|---|---|---|---|---|
| 1 | 1 | (14.07~14.45) | (1.246~1.752) | (2.295~2.482) | (14.48~16.42) | (125.2~134.4) | |
| 2 | 1 | (12.93~13.31) | (1.752~2.258) | (2.108~2.295) | (~$\infty$~12.54) | (97.6~106.8) | |
| 3 | 1 | (12.93~13.31) | (2.258~2.764) | (2.669~2.856) | (18.36~20.3) | (97.6~106.8) | |
| 4 | 1 | (14.07~14.45) | (1.752~2.258) | (2.482~2.669) | (16.42~18.36) | (106.8~116) | |
| 5 | 1 | (12.93~13.31) | (2.258~2.764) | (2.856~3.043) | (20.3~22.24) | (116~125.2) | |
| ... | ... | ... | ... | ... | ... | ... | ... |
