
This `CCR` identity can be used in showing that either `P` or `M` is an unbounded operator. Standard induction techniques are employed in showing unboundedness. Begin with `[M^(n), P]=M^(n) P−P M^(n)=ih n M^(n−1)`. This is true for `n=1`, `[M, P]=ihI` holds, and if it is assumed true for `n`, then by induction it must be shown true for `n+1`. That is, it must be shown that the following expression holds: `M^(n+1)P−P M^(n+1)=ih(n+1)M^(n)`. The left hand side can be written as follows: `M^(n) (M P−P M)+(M^(n) P−P M^(n)) M=M^(n) ih+ih n M^(n−1) M=the right hand side, ih(n+1) M^(n)`. Now bounding the right hand side: for `[M^(n), P]` gives the bound: `n ‖(M^(n−1)) ‖` is less than or equal to `‖M^(n) ‖‖P‖+‖P ‖‖M^(n)‖`, and so factoring out `‖M^(n−1)‖` gives `n` is less than or equal to `2 ‖M ‖‖P‖`. Therefore at least one `M` or `P` is not bounded.

An interesting example of a real Banach algebra is given next involving an important subset of continuous real-valued functions. They are the almost periodic functions, a generalization of periodic functions. Among the most famous is the Bohr-type uniformly almost periodic continuous function `f`. This means that for every `a` greater than zero, there exists a relatively dense subset `Da` of `R`, such that `sup|f(x+t)−f(x)|<a`, for all `t` in `Da`. The value `t` is called an `a` translation number. Intuitively, this means that even though there may not exist a value `t` such that `f(x+t)=f(x)` for all real values `x`, there may be numbers that make this relation an approximate equality. The concept is best illustrated by the following example ([Gelbaum and Olmsted, 2003](#Ch008_145-164_B9780443136979000059.xhtml#bib5)).

### Example 8.8
For `f: R→R`, consider `f (x)=sin (2πx)+sin (2^(1/2) 2π x)`; this function is not periodic. However, for any `ε>0`, it can be shown that there are an infinite number of integer values `t`, such that `2^(1/2)·t`, differs from another integer by less than or equal to `ε/(2π)`. Moreover, the difference between two consecutive such integers is bounded, by `δ`. Using one such integer value, `t`, then `f (x+t)=sin (2πx+2π t)+sin (2^(1/2) (2π x+2π t))=sin (2πx)+sin (2^(1/2) 2π x+δ ε)=f (x)+δ′ ε`, where `δ′` is a bounded quantity. The basic idea is that `f` comes close to being periodic, but it is not periodic.

Almost periodic functions are well behaved. They are uniformly bounded and uniformly continuous. Additionally, if `f[n]` is a sequence of almost periodic functions that converges uniformly to `f`, then `f` is also almost periodic. The space of all almost periodic functions is a closed subspace of all bounded and continuous functions. Under the sup norm, it is a Banach space. Using point-wise multiplication of functions shows that it is a Banach algebra. An instance of a space of almost periodic functions is all the trigonometric polynomials. These are finite sums over `k` an integer, involving linear combinations of sinusoids, (`b[k] cos(d[k] x)+c[k] sin(d[k] x)`), with `b[k]`, `c[k]`, and `d[k]` in `R`.

The space of almost periodic functions forms a pre-Hilbert space using the inner product: `<f, g>=limit as T goes to infinity of [1/2 T ∫[−T]^(T) f(x)*g(x) dx]`.

This space is completed to the class `B²` often called the class of Besicovitch almost periodic functions ([Besicovitch, 1954](#Ch008_145-164_B9780443136979000059.xhtml#bib2)).

## 8.3 Subgroup in a Banach algebra
An important subset of a Banach algebra `A` is the group `G` of invertible elements from `A`. Here, from the MSA perspective, there is a single sort, `SUBG`. Concentrating on the algebraic properties of `A`, there are three signature sets each containing a single operational name. The arity sequence therefore is `(1, 1, 1)`. The operational names in each signature set agree with those from the superset, namely the Banach algebra. Additionally, however, there is the new operator name `INV`. It is given in a suggestive fashion. There are no partial operators in this case. The arities with corresponding operational names are the following:

`Arity`2:`BINE`:`SUBG x SUBG → SUBG`

![Equation](Images/F000059si10.png)

`Arity`1:`INV`:`SUBG → SUBG`

![Equation](Images/F000059si11.png)

`Arity`0 : `V-ONE`

![Equation](Images/F000059si12.png)

Three equational identities must hold because this is a similar algebra to the additive group structure within a vector space. Before these identities are given again, several symbols are assigned representing the specified sort. Additionally, suggestive symbols are provided for the operational names. These are given for

* `SUBG` by `u`, `v`, `w`
* `BINE` by `·`
* `INV` by `/`
* `V-ONE` by `I`

The equational identities are as follows:

1. 1) Associative for multiplication: `(u·(v·w))=((u·v)·w)`.
2. 2) One law: `I·v=v·I=v`, `I` is `V-ONE`.
3. 3) Inverse law: using `1/v`, then `v·1/v=1/v·v=I`.

In the [Fig. 8.1](#Ch008_145-164_B9780443136979000059.xhtml#f0010), the names of operations in a subgroup of a Banach algebra are illustrated. An important topological property of the group `G` of invertible elements from the Banach algebra `A` is that `G` is an open set within `A`. This means that for every point within `G`, this point is an interior point. There exists a sphere or ball of radius `ε` about that point such that the sphere lies wholly within `G`.

![Figure 8.1 Polyadic graph for subgroup in Banach algebra.](Images/F000059f08-01-9780443136979.jpg)

[Figure 8.1](#Ch008_145-164_B9780443136979000059.xhtml#Bf0010) Polyadic graph for subgroup in Banach algebra.

The next few examples illustrate the interplay between the (sub) group `G`, within the Banach Algebra `A`, and `A` itself. The next example is particularly important in spectral analysis. It involves the identity function `I`, as well as many of the inherited properties that the group `G` obtains from the Banach algebra `A`. For instance, the norm and convergence properties from `A` carry throughout the subgroup `G`.

### Example 8.9
Let `v` be in the Banach algebra and `A` be such that `‖v ‖` is less than one, and set `r=I – v`. Then `r` has an inverse. This result follows from a power series argument. The series involved is often called the Neumann series. Let `w[n]=v+v²+…+v^(n)`; then, the sequence of partial sums is a Cauchy sequence, and therefore, it converges to some vector in `A`. Note that `(I −v) w[n]=w[n] (I – v)=(I – v^(n+1))`, and this quantity converges to `I` as `n` goes to infinity. Likewise, as `n` goes to infinity, the sequence of partial sums converges to say `w`. Additionally, `(I – v) w=w (I – v)=I`, that is, `r w=w r=I`, by continuity of multiplication. Also, `$w = I/r = 1/\\left( {1 - v} \\right)\\sum\_{n = 0}^{\\infty}v^{n}$`![Equation](Images/F000059si13.png) will be the standard notation for the inverse when it exists.

An instance of criteria for vectors within `A` to have an inverse is illustrated in the following example.

### Example 8.10
Let `v` be in `G` and `w` be in the Banach algebra `A`. Assume that `‖v – w‖` is less than `1/‖v ^(−1)‖`; then `w` is also in `G`, that is, it is invertible. To see this, consider the vector `z` in `A`, where `z=I – v^(−1) w`. Then, `‖z‖=‖I – v^(−1) w‖=‖v^(−1) (v−w)‖` is less than or equal to `‖v^(−1)‖‖(v−w)‖`, which is less than `‖v^(−1)‖/‖v^(−1)‖=1`. Because, `‖z^(n) ‖` is less than or equal to `‖z ‖^(n)` for nonnegative integers, it will be shown that the summation `∑_{n = 0}^{∞}z^{n}` converges to say `y` in `A`. That is, the sequence of partial sums `∑_{n = 0}^{N}{z^{n} = (I - z^{N + 1})/(I - z) = (I - (I - v^{- 1}w)^{N + 1})/(v^{- 1}w)}` converges to `y=1/(1−z)`. Accordingly, `y=1/(v^(−1) w)`.
