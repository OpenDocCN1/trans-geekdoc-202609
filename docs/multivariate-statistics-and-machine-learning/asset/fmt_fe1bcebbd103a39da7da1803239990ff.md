
Nonparametric methods in the machine learning literature sometimes go by the name of `instance-based learning` methods or `memory-based learning` as a result of their heavy reliance on the data in determining fit. At a computational level, memory-based methods store the entire or at least much of the data set when making predictions about future data. As a result of this storage requirement, such memory-based methods are generally fast to train but can be slower to make predictions ([Bishop, 2006](#ref.xhtml#re_CIT000032)).

## 1.18.3 Revisiting Classical Nonparametric Tests

If the reader has taken a classic statistics course, she may recall encountering nonparametric statistics, at least in a single chapter usually toward the end of the book. Nonparametric statistical tests included such things as the Kruskal-Wallis test and a host of others. Given our characterization of nonparametric tests above in the most general way, we can now revisit earlier teachings on nonparametric tests as traditionally and “classically” taught. What was it about those tests that made them nonparametric? In line with our definition above, it was the fact that they presumably did not make parametric assumptions that made them nonparametric. Or, at minimum, made `fewer` of them. For instance, the Kruskal-Wallis test does not assume observations come from normal populations as the competing parametric ANOVA test does. These nonparametric tests often operate on `ranks` and such, and thus often make minimal, if any, assumptions about the underlying population.52

The problem with this characterization of nonparametric tests is that the modern statistician versed in machine learning may not recognize those “simple” nonparametric tests as being examples of today’s nonparametric expanse largely due to increased computing power. Today’s nonparametric methods can seem much more vast, much more elaborate, much “bigger” than those simpler nonparametric tests of the classical age in statistics. When we say “nonparametric” today, we typically are not referring to those simpler tests, we are instead referring to things like the `bootstrap`, `splines` or other algorithms that make `fewer assumptions about the underlying population`, and for good pragmatic reason as well, such that in many cases of “Big Data” today we are closer to being able to approximate the entire population in our data recruitment anyhow. The key to today’s nonparametric methodologies isn’t so much about not making parametric assumptions, even though this still is their defining characteristic. The “spirit” of today’s nonparametric landscape is that of `letting the data speak for itself`. It’s about getting the parametric assumptions out of the way and replacing them with modern computing capabilities. [Efron and Hastie (2016)](#ref.xhtml#re_CIT000094) summarize the newfound rise of nonparametric methods:

> Two words \[parametric and nonparametric\] explain the classic preference for parametric models: mathematical tractability. In a world of `sliderules` \[sic\] and slow mechanical arithmetic, mathematical formulation, by necessity, becomes the computational tool of choice. Our new computation-rich environment has unplugged the mathematical bottleneck, giving us a more realistic, flexible, and far-reaching body of statistical techniques. But the classic parametric families still play an important role in computer-age statistics, often assembled as small parts of larger methodologies.

> 
> (p. 53)

As referenced earlier, a good resource on classic nonparametric tests is Siegel and Castellan Jr ([1988](#ref.xhtml#re_CIT000335)).

## 1.19 Dimension Reduction, Distance, and Error Functions: Commonalities in Modeling

Most processes or data do not have thousands of intrinsic parameters that underlie them. Instead, there are usually only a few that govern things at a lower dimension. The lower-dimensional structure is said to be `embedded` in the higher-dimensional space that we come across in our work. That is, we say there is a `manifold` or `subspace` that “lives” within this higher-dimensional space. Dimensionality reduction seeks to reveal or uncover that manifold or subspace.

The search for essential dimensions has dominated science in one way or another since its infancy. Instead of thousands of “things going on,” there may be just a few things underlying the surface. At first glance, dimensionality reduction is quite naturally associated with techniques such as `principal components analysis`, `factor analysis`, etc., but the truth is that dimensionality reduction is implicitly present in virtually almost every technique we deal with. Even the basic `t`-test and its transformations (e.g., linear contrasts, ANOVA) can be shown to contain essential primitive concepts of dimension reduction, though at an elementary level of presentation this is not immediately apparent nor would it make sense to teach `t`-tests as related to dimensionality-reduction techniques in an introductory course.

### 1.19.1 Dimension Reduction: What’s the Big Idea?

The idea of dimension reduction is to `project` data points onto lower dimensions. The general question posed by dimensionality reduction is the following:53

> `What would these data points look like if they existed in these lower dimensions?`

As we will see later in the book, this is basically what PCA is all about, assuming the underlying dimensions are linear functions. We may have 1000 variables, but when we reduce the dimensionality from 1000 to say, 3, we then want to know what the scores `would have been` on these 3 dimensions. This will be answered by projecting the data onto those three dimensions and then computing `component scores`, which are the scores yielded on those now three dimensions.

As an example of what we are talking about and to preview what lies ahead in the book, PCA can be defined most generally as

```
l[i] = a[1]y[1] + a[2]y[2] + ... + a[p]y[p]
```

(1.7)

where `l[i]` is a linear combination of weighted values of observed variables `y[1]` through `y[p]`. Even if the data are not truly on a linear manifold (we will define “manifold” later in the book; for now it may be regarded as simply a `shape` of sorts), PCA is often still useful and a very good `approximation` to the true underlying manifold. PCA, as we will see later, is essentially seeking to discover a new `basis` from which to project the data. A `basis`, as we will review in our survey of linear algebra, is `the maximum set of linearly independent vectors that spans the space`. When we collect data in its raw form, it is already on a basis but that basis is relatively `arbitrary`. For instance, the typical Cartesian plane, from this perspective, is an arbitrary basis but constrained at a 90-degree angle. Transforming the data to a new basis is what PCA and many other techniques accomplish. We then project the data from that basis to learn what the data look like from that `vantage point`, the vantage point being the new basis. The basis in the case of PCA is the set of orthogonal eigenvectors that result from the eigen decomposition (or singular value decomposition). The basis is orthonormal, which means orthogonal and each eigenvector having a length equal to unity.

What shall our dimensionality reduction look like? What is the form of these lower dimensions? We have two general possibilities: `linear` vs. `nonlinear` dimensionality reduction. While traditionally linear dimensionality reduction has been the norm, relatively recent techniques have allowed for sophisticated nonlinear reduction, or what is more generally called `nonlinear manifold learning`. While linear reduction may capture a process relatively well, in some cases a nonlinear manifold is required to capture more of the complexities and intricacies of the underlying manifold.

### 1.19.2 The Curse of Dimensionality
