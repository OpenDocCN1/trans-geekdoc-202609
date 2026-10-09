As shown in Figure 17.2, the samples in (a) are distributed on the Swiss roll, and the Euclidean distance (shown by the dashed line) between the two points does not represent the actual distance between the two points. The samples in (b) are distributed on the manifold. The curve is the distance between two points. The isomap dimension after the projection results of the two points and two paths (geodesic and short stitching) is shown in (c).

The Isomap algorithm is described below:

+   **Algorithm 17.2: Isomap algorithm**

Input: Sample input $X = \{x_1, x_2, \dots, x_n \in \mathbb{R}^p\}$, sample true dimension $d$, neighbourhood parameter $k$
Output: low-dimensional embedding $Y = \{y_1, y_2, \dots, y_n \in \mathbb{R}^d\}$

(1) Calculate the nearest neighbour point of each point (using $K$ nearest neighbour or $\varepsilon$ sphere neighbourhood).

(2) Define a weighted undirected graph on the sample set. If $x_i$ and $x_j$ are close neighbours, the weight of the edge is $d_X(i, j)$.

(3) Calculate the shortest distance between two points in the graph. Let the distance matrix $D_G = \{d_G(i, j)\}$

(4) Use MDS to find the low-dimensional embedded manifold. Let

$\mathcal{S} = (S_{ij}) = (D_{ij}^2)$, $\mathcal{H} = (H_{ij}) = (\delta_{ij} - 1/N)$, $\tau(\mathcal{D}) = -H \mathcal{S} H / 2$,

The low-dimensional embedding is the eigenvector corresponding to the second smallest $d + 1$ eigenvalue.

Isomap is characterised by the fact that the algorithm is non-linear and suitable for learning the internal low-dimensional manifolds, but it is not suitable for learning manifolds with larger inner curvatures. The isomap algorithm has two parameters $d$ and $k$. Like the LLE algorithm, the isomap algorithm also has some obvious defects. It needs to calculate the shortest distance between the two points on the map, and its implementation is relatively slow. It is unstable when used for visualisation, and it requires a larger neighbourhood to produce a short-line phenomenon. The low-dimensional projection results produce a large number of "holes", or the graphs reconstructed by the shortest path algorithm are not connected, although the overall structure can be guaranteed to be stable after the point projection of the smaller neighbourhood part.

# 17.3.3 Horizontal linear embedding (HLE)

The HLE algorithm can recover the generated coordinates of the manifolds that are locally equidistant from the low-dimensional Euclidean spaces. The algorithm is described as follows: