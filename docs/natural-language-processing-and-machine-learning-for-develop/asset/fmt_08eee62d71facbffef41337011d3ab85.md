
If the dimension of `U` and `V` are the same and equal `n`, then a linear transformation `T` can be represented as an `nxn` invertible matrix (i.e., it has an inverse). If the dimension of `V` is lower than the dimension of `U`, then the linear transformation `T` involves a `projection`. If the dimension of `V` is higher than the dimension of `U`, then the transformation `T` involves an `embedding`.

For example, if `T` doubles the size of the components of vectors in two-dimensional Euclidean space, then `T` can be represented by the following matrix:

![image](images/585-01.jpg)

If `T` halves the first component and triples the second component of vectors in two-dimensional space, then `T` can be represented by the following matrix:

![image](images/585-02.jpg)

If `T` maps the vector of the form `(x,y,z)` to a vector of the form `(x,y,0)`, then `T` is a `projection`, and `T` can be represented by the following matrix:

![image](images/585-03.jpg)

Based on the definition of a linear transformation that you saw in the beginning of this section, `PCA` is a `linear` dimensionality reduction algorithm, whereas `kernel PCA` is a `non-linear` dimensionality reduction algorithm.

`Linear` reduction involves computing a linear combination of features or performing a linear transformation. An example of the latter transforming a spanning set of vectors by a non-singular matrix. Specifically, suppose that the set `B` of vectors {`v1`, `v2`, . . . , `vn`} are orthogonal and they form a basis for an `n`-dimensional vector space `V`. In addition, suppose that `M` is an `nxn` non-singular matrix. (Its determinant is non-zero). Then {`Mv1`, `Mv2`, `Mvn`} is a linear transformation of the basis `B` that also spans the vector space `V`.

By contrast, `nonlinear (NL)` dimensionality reduction techniques perform non-linear transformations. However, in many cases, `NL` dimensionality reduction techniques are related to linear methods, and they tend to belong to one of two groups:

*   `NL` techniques that provide high-to-low mapping (or vice versa)

*   `NL` techniques that provide visualization

`Mapping` methods are used to perform an initial feature extraction step, after which machine learning algorithms can perform pattern recognition. However, `NL` techniques that provide visualization perform calculations involving the distance between objects.

## Types of Distance Metrics

`Nonlinear` dimensionality reduction techniques can also have different distance metrics. For example, `linear` reduction techniques can use the `Euclidean` distance metric (based on the Pythagorean theorem). However, you need to use a different distance metric to measure the distance between two points on a sphere (or some other curved surface). In the case of `NLP`, the `cosine similarity` metric is used to measure the distance between word embeddings (which are vectors of floating point numbers that represent words or tokens).

`Distance` metrics are used for measuring physical distances, and some well-known `distance` metrics are listed here:

*   `Euclidean` distance

*   `Manhattan` distance

*   `Chebyshev` distance

The `Euclidean` algorithm also obeys the `triangle inequality`, which states that for any triangle in the Euclidean plane, the sum of the lengths of any pair of sides must be greater than the length of the third side.

In spherical geometry, you can define the distance between two points as the arc of a great circle that passes through the two points (always selecting the smaller of the two arcs when they are different).

In addition to physical metrics, there are algorithms that implement the concept of “edit distance” (the distance between strings), as listed here:

*   `Hamming` distance

*   `Jaro–Winkler` distance

*   `Lee` distance

*   `Levenshtein` distance

*   `Mahalanobis` distance metric

*   `Wasserstein` metric

The `Mahalanobis` metric is based on an interesting idea: given a point `P` and a probability distribution `D`, this metric measures the number of standard deviations that separate point `P` from distribution `D`. More information about `Mahalanobis` is here:

*[https://en.wikipedia.org/wiki/Mahalanobis\_distance](https://en.wikipedia.org/wiki/Mahalanobis_distance)*

In the branch of mathematics called topology, a `metric space` is a set for which distances between all members of the set are defined. Various metrics are available (such as the `Hausdorff` metric), depending on the type of topology.

The `Wasserstein` metric measures the distance between two probability distributions over a metric space `X`. This metric is also called the “earth mover’s metric” for the following reason: given two unit piles of dirt, it’s the measure of the minimum cost of moving one pile on top of the other pile.

`KL` divergence bears some superficial resemblance to the `Wasserstein` metric. However, there are some important differences between them. Specifically, the `Wasserstein` metric has the following properties:

*   It is a metric.

*   It is symmetric.

*   It satisfies the triangle inequality.

However, `KL` divergence has the following properties:

*   It is not a metric (it’s a divergence).

*   It is not symmetric: `KL(P,Q) != KL(Q,P)`.

*   It does not satisfy the triangle inequality.

Note that `JS` (Jenson-Shannon) divergence (which is based on `KL` divergence) is a true metric, which would enable a more meaningful comparison with other metrics (such as the `Wasserstein` metric).

## Other Well-Known Distance Metrics

Chapter [9](#ch09.xhtml) discusses recommendation systems, which involve finding similarities between users or items and then making recommendations. There are several similarity metrics available, such as item similarity metrics, Jaccard (user-based) similarity, and cosine similarity (which is used to compare vectors of numbers). The following subsections introduce you to these similarity metrics.

Another well-known distance metric is the so-called “taxicab” metric, which is also called the `Manhattan` distance metric. Given two points `A` and `B` in a rectangular grid, the taxicab metric calculates the distance between two points by counting the number of “blocks” that must be traversed in order to reach `B` from `A` (the other direction has the same taxicab metric value). For example, if you need to travel two blocks north and then three blocks east in a rectangular grid, then the Manhattan distance is 5.

In fact, there are various other metrics available, which you can learn about by searching Wikipedia. In the case of `NLP`, the most frequently used distance metric is calculated via the cosine similarity of two vectors, and it’s derived from the formula for the inner (“dot”) product of two vectors.

### Pearson Correlation Coefficient

*Pearson similarity* is the Pearson coefficient between two vectors. Given random variables `X` and `Y`, and the following terms:

`std(X)` = standard deviation of `X`  
`std(Y)` = standard deviation of `Y`  
`cov(X,Y)` = covariance of `X` and `Y`  

Then the Pearson correlation coefficient `rho(X,Y)` is defined as follows:

![image](images/588-01.jpg)

Keep in mind that the Pearson coefficient is limited to items of the same type. More information about the Pearson correlation coefficient is here:

*[https://en.wikipedia.org/wiki/Pearson\_correlation\_coefficient](https://en.wikipedia.org/wiki/Pearson_correlation_coefficient)*

### Jaccard Index (or Similarity)

The `Jaccard similarity` is based on the number of users which have rated item `A` and `B` divided by the number of users who have rated either `A` or `B`. `Jaccard` similarity is based on unique words in a sentence and is unaffected by duplicates, whereas `cosine` similarity is based on the length of all word vectors (which changes when duplicates are added). The choice between `cosine` similarity and `Jaccard` similarity depends on whether or not word duplicates are important.

The following Python method illustrates how to compute the Jaccard similarity of two sentences:
