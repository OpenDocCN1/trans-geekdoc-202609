sim(\mathbf{x}_i, \mathbf{x}_j) = e^{-\frac{d(\mathbf{x}_i, \mathbf{x}_j)^2}{2\sigma^2}}

serves the purpose, where \(\sigma\) is a parameter controlling the width of the neighborhoods, playing a role similar to the parameter \(\epsilon\) in the \(\epsilon\)-neighborhood graph approach.

Denote by \(W\) the similarity graph. For vertices \(\mathbf{x}_i\) and \(\mathbf{x}_j\), set \(w_{ij} > 0\) if they are connected in the similarity graph; 0 otherwise. Moreover, \(d_i = \sum_{j=1}^n w_{ij}\) is the degree of vertex \(\mathbf{x}_i\). The degree matrix \(D\) is the diagonal matrix with the degrees \(d_1, \dots, d_n\) on the diagonal.

The Ng-Jordan-Weiss algorithm uses the distance measure and constructs a fully connected graph. Particularly, it calculates a similarity matrix \(\mathbf{W}\) such that

\(w_{ij} = e^{-\frac{dist(o_i, o_j)^2}{2\sigma^2}},\)

where \(\sigma\) is a scaling parameter. In the Ng-Jordan-Weiss algorithm, \(W_{ii}\) is set to 0.

# Finding a new space

After we transform a set of objects into a similarity graph, where objects are connected by neighbor relationship, intuitively, we can explore how flow may be propagated among vertices in the similarity graph. The sources are the centers of the clusters. Following this intuition, the gradient describes the direction of flow, and the divergence of the gradient provides a quantity of the vector field's source at each point. Mathematically, the Laplace operator\(^3\) is what we need, which is a differential operator computing the divergence of the gradient of a function on Euclidean space.

There are two common ways to apply the Laplace operator on the similarity graph. The most commonly used approach is the unnormalized graph Laplacian, which is defined by \(L = D - W\). Alternatively, some methods use the normalized graph Laplacian, which is defined by \(L = D^{-\frac{1}{2}} W D^{-\frac{1}{2}}\).

In order to embed the nodes in the similarity graph in a space where the clusters stand out, we can extract the first \(k\) eigenvectors of the Laplacian matrix, that is, the \(k\) eigenvectors of the smallest eigenvalues for unnormalized graph Laplacian or the \(k\) eigenvectors of the largest eigenvalues for normalized graph Laplacian. The nodes collapse into clusters in the space represented using those \(k\) eigenvectors as the base.

The Ng-Jordan-Weiss algorithm employs the normalized graph Laplacian, and uses the first \(k\) eigenvectors \(\mathbf{u}_1, \dots, \mathbf{u}_k\) in columns to form a matrix \(\mathbf{U} \in \mathbb{R}^{n \times k}\) and normalizes the rows of \(\mathbf{U}\) to norm 1 and form matrix \(\mathbf{T}\), that is, \(t_{ij} = \frac{u_{ij}}{\sqrt{\sum_{l=1}^k u_{il}^2}}\). Let \(\mathbf{y}_i\) be the \(i\)th row of \(\mathbf{T}\), which is the embedding of object \(\mathbf{x}_i\) in the new space.

# Extracting clusters

We can employ a classical clustering algorithm, such as k-means, to extract the clusters in the new space formed by the first \(k\) eigenvectors in the previous step.

The Ng-Jordan-Weiss algorithm applies k-means on \(\mathbf{y}_1, \dots, \mathbf{y}_n\), the row vectors in matrix \(\mathbf{Y}\), to form the clusters \(C_1, \dots, C_k\). Then, it assigns the original data points to clusters according to how the

\(^3\) If \(f\) is a twice-differentiable real-valued function, then the Laplacian of \(f\) is \(\Delta f = \nabla^2 f = \nabla \cdot \nabla f\), where \(\nabla f = (\frac{\partial}{\partial x_1}, \dots, \frac{\partial}{\partial x_n})\). Equivalently, \(\Delta f = \sum_{l=1}^n \frac{\partial^2 f}{\partial x_l^2}\).