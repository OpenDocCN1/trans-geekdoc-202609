Thus c_j = X v_j = u_j d_j, for j = 1, … K. Hence u_j is simply the projection of the row vectors of X, i.e., the input predictor vectors, on the direction v_j, scaled by d_j.

c_1 = [ x_{1,1} v_{1,1} + … + x_{1,P} v_{1,P} ; x_{2,1} v_{1,1} + … + x_{2,P} v_{1,P} ; ⋮ ; x_{N,1} v_{1,1} + … + x_{N,P} v_{1,P} ]

+   3. The variance of each component is given by the eigen values λ_k, k = 1, … K. It can be obtained from the singular values:

var(c_k) = 1/(N-1) (X v_k)^2   (10.9)
= 1/(N-1) (u_k d_k)^2   (10.10)
= 1/(N-1) d_k^2   (10.11)

# 10.3.4 Determining the number of PCs

We must choose K* ∈ [1, …, K], the number of required components. This can be done by calculating the explained variance ratio of the K* first components and by choosing K* such that the cumulative explained variance ratio is greater than some given threshold (e.g., ≈ 90%). This is expressed as

cumulative explained variance(c_k) = (∑_{j}^{K*} var(c_k)) / (∑_{j}^{K} var(c_k)).

# 10.3.5 Interpretation and visualization

# PCs

Plot the samples projeted on first the principal components as e.g. PC1 against PC2.

# PC directions

Exploring the loadings associated with a component provides the contribution of each original variable in the component.

Remark: The loadings (PC directions) are the coefficients of multiple regression of PC on original variables:

c = X v   (10.12)
X^T c = X^T X v   (10.13)
(X^T X)^{-1} X^T c = v   (10.14)

Another way to evaluate the contribution of the original variables in each PC can be obtained by computing the correlation between the PCs and the original variables, i.e. columns of X,