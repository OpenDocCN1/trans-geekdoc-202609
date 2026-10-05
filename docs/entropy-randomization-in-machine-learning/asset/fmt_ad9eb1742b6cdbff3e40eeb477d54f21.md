
| *r* || 12 || 11 || 10 || 9 || 8 || 7 |

| PCA || 0.2935 || 0.3317 || 0.3857 || 0.4399 || 0.4941 || 0.5671 |

| --- | --- | --- | --- | --- | --- | --- |

| RP || 0.1444 || 0.3708 || 0.5190 || 0.6051 || 0.6736 || 0.8167 |

| EDR || 0.3083 || 0.3013 || 0.3184 || 0.2772 || 0.2589 || 0.2792 |

|  |

[Figure 3.4](#chapter3.xhtml#f3_4) shows the graphs of the relative information losses for the data sets *simulation* and *heart*.

![Figure 3.4: Relative information losses for data sets simulation and heart.](images/fig3_4.jpg)

[Figure 3.4:](#chapter3.xhtml#f3_4b) Relative information losses for data sets *simulation* and *heart*.

The relative information losses caused by the EDR method for different values *δ* are combined in [Tables 3.10](#chapter3.xhtml#t3_10)–[3.11](#chapter3.xhtml#t3_11).

[Table 3.10:](#chapter3.xhtml#t3_10b) Dependence *I*(*δ*) for data set *simulation* (EDR method).

|  |

| --- |

| *δ / r* || 9 || 8 || 7 || 6 || 5 |

| 0.1 || 0.0959 || 0.0997 || 0.1594 || 0.2795 || 0.3996 |

| --- | --- | --- | --- | --- | --- |

| 0.2 || 0.2000 || 0.1932 || 0.1982 || 0.2656 || 0.3880 |

| 0.3 || 0.2896 || 0.2896 || 0.2952 || 0.2943 || 0.3805 |

| 0.4 || 0.3615 || 0.3887 || 0.3933 || 0.3981 || 0.3992 |

| 0.5 || 0.3971 || 0.4842 || 0.4707 || 0.5130 || 0.4954 |

|  |

![Figure 3.5: Dependence I(\\delta) for data sets simulation and heart (EDR method).](images/fig3_5.jpg)

Figure 3.5: Dependence *I*(*δ*) for data sets *simulation* and *heart* (EDR method).

[Table 3.11:](#chapter3.xhtml#t3_11b) Dependence *I*(*δ*) for data set *heart* (EDR method).

|  |

| --- |

| *δ / r* || 12 || 11 || 10 || 9 || 8 || 7 |

| 0.1 || 0.1071 || 0.0478 || 0.0821 || 0.1244 || 0.1065 || 0.1254 |

| --- | --- | --- | --- | --- | --- | --- |

| 0.2 || 0.5947 || 0.0898 || 0.0676 || 0.0568 || 0.1435 || 0.1428 |

| 0.3 || 0.3344 || 0.7126 || 0.6659 || 0.3530 || 0.2961 || 0.2992 |

| 0.4 || 0.2921 || 0.3878 || 0.3833 || 0.4066 || 0.2814 || 0.3974 |

| 0.5 || 0.2134 || 0.2683 || 0.3932 || 0.4452 || 0.4670 || 0.4310 |

|  |

The results of the computational experiment allow drawing the following conclusions:

*   The EDR method is operable for any amounts of data in the learning and testing data collections; PCA does not work when the amount of data is smaller than the dimension of the attribute space; the operability of the RP method requires additional research.

*   The level of information losses when applying the EDR method is retained up to the two-fold reduction of the attribute space; for PCA and the RP method, the level of information losses grows significantly with decreasing the dimension of the attribute space.

*   Thanks to the control parameter *δ* in the EDR method, the level of relative information losses can be regulated. At the same time, this possibility is absent in PCA and the RP method.

## 3.7Entropy Methods for Random Projection

### 3.7.1Statements of Entropy Randomized Projection Problems

**1. Point-set representation of data matrices: indicator of compactness**

Consider a data matrix describing some objects and their attributes:

$$
\begin{array}{r} {U\_{(m \times s)} = \left( \begin{array}{l} \mathbf{u}^{(1)} \\ \cdots \\ \mathbf{u}^{(m)} \\ \end{array} \right),\quad\quad\mathbf{u}^{(i)} = \left\{ u\_{1}^{(i)},\ldots,u\_{s}^{(i)} \right\} \in R^{s},\, \, i = \overline{1,m}.} \\ \end{array}
$$

(3.109)

Here *m* and *s* are the numbers of objects and their attributes, respectively; *R*^(*s*) denotes the attribute space. Assume that the elements of this data matrix are standardized, i.e., $u\_{ij} \in \lbrack 0,1\rbrack,\, i = \overline{1,m},\, j = \overline{1,s}.$

*The point-set representation of a matrix *U*[(*m* × *s*)] in the attribute space *R*[(*m*)]^(*s*) is the set 𝔘[*m*]^(*s*) of the points {**u**^((1)),…,**u**^((*m*))}*.

For example, the set 𝔘[100]² of 100 two-dimensional points represents a matrix *U*[(100 × 2)].

The spread of points in a set 𝔘[*m*]^(*s*) can be characterized by *the indicator of compactness* *ρ*[*U*], which will be defined as the arithmetic average of the distances between the points:

$$
\begin{array}{r} {\rho\_{U} = \frac{2}{m(m - 1)}{\sum\limits_{(\alpha,\beta) = 1,\mspace{2mu}\alpha \neq \beta}^{m}\varrho}(\mathbf{u}^{(\alpha)},\mathbf{u}^{(\beta)}),} \\ \end{array}
$$

(3.110)

where 𝜚(**u**^((*α*)), **u**^((*β*))) gives the distance between the points **u**^((*α*)) and **u**^((*β*)). If the elements of the data matrix are standardized, then

$$
\begin{array}{r} {0 \leq \varrho(\mathbf{u}^{(\alpha)},\mathbf{u}^{(\beta)}) \leq \sqrt{2}\quad\quad\text{for~all}\,(\alpha,\beta) = \overline{1,m},} \\ {0 \leq \rho\_{U} \leq 1.} \\ \end{array}
$$

(3.111)

Introduce the following classes of transformations for data matrices:

*   (*m**r*) *\-class*: *U*[(*m* × *s*)]→*Y*[(*m* × *r*)], the set 𝔜[*m*]^(*r*) is in the space *R*[(*m*)]^(*r*);

*   (*n**s*) *\-class*: *U*[(*m* × *s*)]→*B*[(*n* × *s*)], the set 𝔅[*n*]^(*s*) is in the space *R*[(*n*)]^(*s*);

*   (*n**r*) *\-class*: *U*[(*m* × *s*)]→*Z*[(*n* × *r*)], the set ℨ[*n*]^(*r*) is in the space *R*[(*n*)]^(*r*).

**2. Random projector matrices and their probabilistic characteristics**

*1. Projection onto the space *R*[(*m*)]^(*r*) (generation of the set 𝔜[*m*]^(*r*))* This operation will be performed using a projector matrix *Q*[(*s* × *r*)]:

$$
\begin{aligned} & {Y\_{(m \times r)} = \left( \begin{array}{l} \mathbf{y}^{(1)} \\ \cdots \\ \mathbf{y}^{(m)} \\ \end{array} \right) = U\_{(m \times s)}Q\_{(s \times r)};} \\ & {\quad y\_{j}^{(i)} = {\sum\limits\_{k = 1}^{s}u\_{ik}}q\_{kj},\, \, i = \overline{1,m};\, j = \overline{1,r}.} \\ \end{aligned}
$$

(3.112)

The projector matrix *Q*[(*s* × *r*)] is random and of the interval type, i.e.,

$$
\begin{array}{r} {Q\_{(s \times r)} \in \mathcal{Q} = \lbrack Q^{-},Q^{+}\rbrack.} \\ \end{array}
$$

(3.113)

The probabilistic properties of the projector matrix are characterized by a continuously differentiable probability density function (PDF) *P*(*Q*), defined on 𝒬.

The vectors **y**^((*i*)) form the set 𝒴[*m*]^(*r*) of *r*\-dimensional points, *m* in total. Define the distance 𝜚(**y**^((*α*)),**y**^((*β*)) | *Q*[(*s* × *r*)]) between them and the indicator of compactness

$$
\begin{array}{r} \left. \rho\_{Y}(Q) = \frac{2}{m(m - 1)}{\sum\limits_{(\alpha,\beta) = 1,\mspace{2mu}\alpha \neq \beta}^{m}\varrho}(\mathbf{y}^{(\alpha)},\mathbf{y}^{(\beta)}\, \middle| \, Q\_{(s \times r)}). \right. \\ \end{array}
$$

(3.114)

Since the elements of the projector matrix have random values, the average distance (3.114) is random as well.

Hence, define the mathematical expectation of the indicator of compactness:

$$
\begin{array}{r} {{\overline{\rho}}\_{Y} = {\int\_{\mathcal{Q}}P}(Q)\rho\_{Y}(Q)dQ.} \\ \end{array}
$$

(3.115)

*2. Projection onto the space *R*^((*n* × *s*)) (generation of the set 𝔅[*n*]^(*s*))* This operation will be performed using a projector matrix *T*[(*n* × *m*)] with random elements:

$$
\begin{aligned} B\_{(n \times s)} & {= \left( \begin{array}{l} \mathbf{b}^{(1)} \\ \cdots \\ \mathbf{b}^{(n)} \\ \end{array} \right) = T\_{(n \times m)}U\_{(m \times s)};\quad b\_{j}^{(i)} = {\sum\limits\_{k = 1}^{m}t\_{ik}}\, u\_{kj},} \\ & {\quad i = \overline{1,n};\, j = \overline{1,s}.} \\ \end{aligned}
$$

(3.116)

The projector matrix *T*[(*n* × *m*)] is random and of the interval type, i.e.,

$$
\begin{array}{r} {T\_{(n \times m)} \in \mathcal{T} = \lbrack T^{-},T^{+}\rbrack.} \\ \end{array}
$$

(3.117)

Its probabilistic properties are characterized by a PDF *W*(*T*) defined on 𝒯.

The vectors **b**^((*i*)) form the set 𝔅[*n*]^(*s*) of *s*\-dimensional points, *n* < *m* in total. Define the indicator of compactness
