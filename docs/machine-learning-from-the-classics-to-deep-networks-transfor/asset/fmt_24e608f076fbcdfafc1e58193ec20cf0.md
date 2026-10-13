
The previous minimum error interpretation paves the way to build around PCA an efficient searching procedure in identifying similar patterns in large databases. Assume that a number `N` of prototypes are represented in terms of `l` features, giving rise to feature vectors, `x[n] ∈ ℝ^l, n = 1, 2, …, N`, which are stored in a database. Given an unknown object, which is represented by a feature vector `x`, the task is to identify to which one among the prototypes this pattern is most similar. Similarity is measured in terms of the Euclidean distance `||x − x[n]||²`. If `N` and `l` are large, searching for the minimum Euclidean distance can be computationally very expensive. The idea is to keep in the database the components `z[n]^(m) := [z[n1], …, z[nm]]^T` (see Eq. [(20.12)](#Chp020_1103-1179_B9780443292385000263.xhtml#deq13)) that describe the projections of the `N` prototypes in `span{u[1], …, u[m]}`, instead of the original `l`-dimensional feature vectors. Assuming that `m` is large enough to capture most of the variability of the original data (i.e., the intrinsic dimensionality of the data is `m` to a good approximation), then `z[n]^(m)` is a good feature vector description because we know that in this case `x̂_n ≈ x_n`. Given now an unknown pattern, `x`, we first project it onto `span{u[1], …, u[m]}`, resulting in

```
x̂ = ∑_{i=1}^m (u_i^T x) u_i := ∑_{i=1}^m z_i u_i.
``` (20.13)

Then we have
