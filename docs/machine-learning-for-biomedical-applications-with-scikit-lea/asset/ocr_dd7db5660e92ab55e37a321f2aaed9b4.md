```
@plot original 2D data
ax = ax.scatter(X_m[:], X_m[:,1], c=X_m[:,1], marker='o')
```

Consider XD_m as the (underlying) degrees of freedom. Think of the 3D x as the high-dimensional data we have measured.25

+   1. First, implement PCA to embed x in 2D. The transformed data. Check if your result results shown in Fig. 5.14c (allowing for differences in the distribution of the data).
2. Now, implement Laplacian using np.zeros(N,N):
   i. Initialize A using np.zeros(N,N);
   ii. Calculate the sum of square distances between all points—insert l at the location of the closest points for each row of A;
   iii. Symmetrize A (hint: use np.maximum(...));
   iv. Calculate D as D=Σ (This will output a vector and use np.diag(...) to turn this into a matrix);
   v. Estimate L;
   vi. Use np.eigigh(1,2) to return the eigenvectors corresponding to the two smallest nonzero eigenvalues.26
   vii the Laplacian embedding.27
3. Compare your implementation with the result obtained using scikit-learn. Remember that scikit-learn will not return the same result as the 'from-scratch' implementation due to the use of the normalized graph Laplacian.
4. (optionally) Try editing your scikit-learn implementation to make use of affinity='rbf'.
5. (optionally) Try some of the alternative manifold learning methods offered by scikit-learn, such as t-distributed stochastic neighbor embedding (t-sne) [47] or Isomap [46].

25 Skeleton code and solution is available from github.com/MachineLearningBiomedicalApplications/notebook.

26 Where we here assume that you have only 1 nonzero eigenvector; in fact, this will depend on the connectivity of your adjacency matrix, which in turn depends on the tuning of k—we suggest using a relatively high number, e.g., k=20.

27 Reminder: This is given by the eigenvectors of the Laplacian.