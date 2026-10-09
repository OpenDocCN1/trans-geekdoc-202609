# **10.3.4 Classification algorithm based on the tensor field**

According to the above analysis, we introduce the tensor field in the classification algorithm. There is a data set $X = \{X_1, X_2, \dots, X_M\}$ and $X_i$ is the sample. Each sample has $N$ attributes, i.e., $X_i = < P_{i1}, P_{i2}, \dots, P_{iN} >$, where $P_{ij}$ represents the $j$-th attribute of each sample. The range of values allowed for $P_j$ is $[U_{Pj}, D_{Pj}]$ and includes $C_j$ possible values.

First, we discuss how to obtain a tensor field model for a known data set. In simple terms, any data object can be described by each attribute in common. Each attribute is a view of the sample, and all the attributes construct a full expression of the sample. Figure 10.20 shows that sample $A$ is described by four attributes.

Therefore, we can construct a tensor, each order of which corresponds to an attribute of samples. The dimension number of the $j$-th order is determined by the neighbour points $\zeta_{X_i}$, and we have $l_j \leq \|U_{P_j} - D_{P_j}\|$. Therefore, we can construct a tensor $T_i^{I_1 \times I_2 \times \cdots \times I_N}$ of each sample $X_i$ based on its high-dimensional linear space.

$T_i^{I_1 \times I_2 \times \cdots \times I_N}$ is the description of the local environmental information, which is also the description of the neighbouring region $\zeta_{X_i}$. Therefore, the value of $T_i^{I_1 \times I_2 \times \cdots \times I_N}$ is determined by $\zeta_{X_i}$. If we have a sample $X_j \in \zeta_{X_i}, X_j$ would have a weight value $w_{ij}$. The component of $T_i^{I_1 \times I_2 \times \cdots \times I_N}$ is:

```
$$ T_i^{i_1 \times i_2 \times \cdots \times i_N} = w_{ij} X_j, \, X_j = (P_{i1}, P_{i2}, \dots, P_{iN}) \in \zeta_{X_i} \quad (10.45) $$
```

Here, each point of the linear space determines a tensor. Then, the data set $X$ can determine a tensor field $\Phi(X)$.

We reconstruct the tensor field $\forall T_i \in \Phi(X)$ and decompose $T_i$ by high-order singular value decomposition to

```
$$ T_i = S_i \times_1 U^{(1)} \times_2 U^{(2)} \times \cdots \times_N U^{(N)} \quad (10.46) $$
```

Here, $T_i, S_i \in R^{I_1 \times I_2 \times \cdots \times I_N}$ and $U^{(i)}$ is a $I_N \times I_N$ square matrix. Setting $K = \{K_1, K_2, \dots, K_N\}$, it is the reduction dimension of $S(\zeta_{X_i}) = \{l_1, l_2, \dots, l_N\}$.

```
$$ \tilde{T}_i = \tilde{S}_i \times_1 \tilde{U}^{(1)} \times_2 \tilde{U}^{(2)} \times \cdots \times_N \tilde{U}^{(N)} \quad (10.47) $$
```

which is the tensor after the reconstruction, and $\tilde{T}_i \in R^{\tilde{I}_1 \times \tilde{I}_2 \times \cdots \times \tilde{I}_N}, \tilde{S}_i \in R^{K_1 \times K_2 \times \cdots \times K_N}, \tilde{U}^{(n)} \in R^{I_n \times K_n}.$

![](bbox=[0.18, 0.79, 0.8, 0.9])