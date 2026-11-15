
In order to describe the technology of parallel shift in terms of set theory, we should consider the processes of clustering and classification (Duran and Odell, 1974, Islam and Ahmed, 2013). These processes are necessary for combining the elements of a set for selection of its subsets, which are similar by their certain characteristic features. The ability to distinguish one object from the other one gives you the opportunity for further analysis.

Clustering is characterised by several factors, which include the number of clusters that compose the original set. At a constant amount of clusters, this process is called ‘clear clustering’ and in an uncertain amount of clusters, it is called ‘fuzzy clustering’. In the case of clear clustering, each element of the original set belongs to only one subclass of elements. Subclasses of elements do not intersect. In fuzzy clustering, the subclasses of elements of the original set can intersect. Belonging of elements to a certain subclass is determined by some factor. This ratio is called degree of membership of object to the cluster. For elements with clear clustering, it takes the values 0 or 1, and for fuzzy clustering, it is in the range of 0 to 1.

Also the parameter of clustering is a measure of the distance. This parameter is selected to perform certain tasks randomly of some number-designed measures; for example, the most widespread methods for determining measures of distances are to use the Euclidean distance or Euclidean square distance. Using other measures of distances is determined by the need to allocate some feature of the set elements.

The third parameter is the clustering criterion. The choice of these criteria is based on the needs of the specific problem to be solved and on the developer’s experience. The most common ones are determination of the maximum and minimum values specified in the characteristic features of the set element.

The basis for implementation of the clustering process is formation of the vector of characteristic features. This vector is generated to describe the object. The characteristic features can be both qualitative and quantitative. The composition of the set depends on the specific problem to be solved. The description of the variety of elements of vectors leads to complication of clustering algorithms. The use of parallel shift technology allows formation of a homogeneous characteristic features to describe the object.

Assume there is a set of objects x, which are located in the examined area of features. Each of them has some predetermined amount of N of characteristics.

\[
\overline{x} = (CF_1, ..., CF_N) \quad (1.1)
\]

Parallel shift technology involves the selection of a total of one or more of the same type of quantitative features for each object x to form a transformed object xt.

\[
(CF_i, ..., CF_j) \in (CF_1, ..., CF_N) \quad (1.2)
\]

The list of CF is determined by the ability to describe the original object for solving a specific task; other features are discarded as not being essential in its decision.

\[
\overline{xt} = (CF_1, ..., CF_N) \quad (1.3)
\]

The scheme for the process of conversion of x set by reducing the number of characteristic features in the vectors that describe its elements is shown on Fig. 1.1.

Thus, each of the original objects x is converted into some transformed object xt. The x and xt sets are bijective. Further manipulation is necessary to carry out the objects of the xt set.

We describe the process of using parallel shift technology in the case of discretized initial set. For example, for 2D-objects such a set can be considered as the digitized image.

In this case xt object is a set of m elements xti, each of which is described by a vector of the n characteristic features.

\[
\overline{xt_i} = (cf_{1i}, ..., cf_{Ni}) \quad (1.4)
\]

These features form the CFs, which are chosen to describe the transformed xt object and their number is same.

\[
CF_j = \frac{\sum_{i=1}^m cf_{i,j}}{m} \quad (1.5)
\]

As a result of the interaction of the xt object and of xt' object, in which the value of all the characteristic features ($CF_j, ..., CF_j$) are changed in a certain shift direction in the space of selected characteristic features at a value SHIFT, a xpost set is obtained. The xt' object is obtained and it is a moved copy of the xt object.

![](img/d6ed6c69a61b1252a9084096bb4904c6_23_0.png)

Fig. 1.1: Scheme of the set transformation process by reducing the number of characteristic features in the vectors, which describe the elements

\[
CF'_j = CF_j + SHIFT_j = \frac{\sum_{i=1}^m (cf_{i,j} + shift_{i,j})}{m} \quad (1.6)
\]

The value SHIFT displacement will depend on the shift_j and displacement of each characteristic feature. If the shift is parallel, then SHIFT_j = shift_j; else, it is object deformation.

\[
SHIFT = \sqrt{\sum_{j=1}^n (SHIFT_j)^2} = \sqrt{\sum_{j=1}^n \left(\frac{\sum_{i=1}^m shift_{i,j}}{m}\right)^2} \quad (1.7)
\]

Variants of the organisation of interaction of the sets can be varied. In this book it is considered the simplest option-determination of intersection of two sets.

\[
xt \cap xt' = x_{pst} \quad (1.8)
\]

The scheme of the x_pst sets formation for some shifting distance SHIFT is shown in Fig. 1.2.

![](img/d6ed6c69a61b1252a9084096bb4904c6_24_0.png)

Fig. 1.2: Scheme for obtaining the set x_pst for some distance of displacement

The \(x_{pst}\) set is only a part of the \(xt\) set, so information about its elements is not enough to assign the initial x element to a certain cluster. A \(x_{pst}\) set can determine its cardinality (\(crd\)). For 2D-objects, this is the area of intersection of images; for 3D-objects, this is the volume of intersection, etc. These parameters are numerical values, so it is not enough to describe the \(x\) elements. It is necessary to make the dynamics of change of these static parameters. For each possible direction of the shift in space of the selected characteristic features (\(CF_i\), ..., \(CF_j\)), each possible SHIFT shift distance can be determined by the \(crd\) parameter. Using a set of all possible \(crd\) parameters, each \(x\) element can be described. For each direction of parallel shift, a sequence of \(crd\) parameters will be a function of the \(x_{pst}\) set cardinality that depends on the shift. The set of all such functions for each element \(x\) is used for further processing and analysis by a variety of methods based on parallel shift technology.

Assume the average value of cardinality of the elements of \(x_{pst}\) set, which belong to one cluster, for each shifting distance \(SHIFT=j\) will be equal to \(CRD_{SHIFT_j}\). The number of elements in the specified i-cluster will be \(cnt\_clast_i\). They are related by the following relation:

\[
CRD_{SHIFT_j} = \frac{\sum_{i=0}^{cnt\_clast_i} crd_{SHIFT_{i,j}}}{cnt\_clast_i} \quad (1.9)
\]

For comparison functions in the process of clustering, we introduce a threshold value \(thr\). The criterion for clustering of objects will be assumed and the deviation values of the function is \(crd_{SHIFT_{i,j}}\) and depend on the \(CRD_{SHIFT_j}\) for the i-th cluster as each shift distance \(SHIFT = j\) will not more than the threshold value.

\[
\left| CRD_{SHIFT_j} - crd_{SHIFT_{i,j}} \right| \le thr \quad (1.10)
\]

Schematic representation of the CRD function of the mean value cardinality of the \(x_{pst}\) set and the range of possible \(crd\) value features that belong to one cluster is selected in grey in Fig. 1.3.

In Fig. 1.3, the CRD graph is shown for one direction of displacement of the \(xt'\) set in the space of selected CF. For a description of the \(xt\) object it is essential to use the set of functions for all shift directions. It should be noted that this example gives fixed value of \(thr\) threshold for all possible displacement range. The deviation value of threshold can be changed, depending on the shift distance. Due to possible changes in \(thr\) parameter, the belonging of object to one or another cluster will also change. This fact confirms the principles of ‘fuzzy clustering’ of the set.

To describe objects of studies by using a set of functions, any methods of functional analysis can be used. Here dualism is manifested similar
