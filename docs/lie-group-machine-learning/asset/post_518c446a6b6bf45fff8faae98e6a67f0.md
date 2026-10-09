
## Bibliography

- [1] Nir SC, Ron K, Ravi kanth M. A General Framework for Low Level Vision. IEEE Transaction on Image Processing, 1998, 7(3), 310–318.
- [2] Chen S, Sochen NA, Kimmel R. Stereographic Combing a Porcupine or Studies on Direction Diffusion in Image Processing. Siam Journal of Applied Mathematics, 2004, 64(5), 1477–1508.
- [3] Pearson DW. Approximating vertical vector fields for feedforward neural networks. Applied Mathematics Letters, 1996, 9(2), 61–64.
- [4] Chao J, Kim J. A Fibre Bundle Model of Surfaces and its Generalization. International Conference on Pattern Recognition. IEEE Computer Society, 2004, 560–563.
- [5] Brockett RW. Control Theory and Analytical Mechanics, Geometrical Control Theory. Ed, by C, Martin and R, Hermann, Math. Sci. Press, 1977.
- [6] Brockett RW. Nonlinear control theory and differential geometry, Warszawa. Proceedings of the International Congress of Mathematicians, August 16–24, 1983.
- [7] Mu XW. The Geometrical Framework of General Nonlinear Control System on Fiber Plexus and its Minimum Realization Theory. Applied Mathematics and Mechanics, 1996, 17(10), 939–950.
- [8] Zhang J. Research of the fiber bundle learning algorithm based on popular learning. Soochow: Thesis. Soochow University, 2008.
- [9] Zhang J, Li FZ. Study on the fiber cluster learning model based on manifold learning. Journal of Nanjing University, 2008, 44(5), 477–485.
- [10] Min WL, Lu L, He XF. Locality pursuit embedding. Pattern Recognition, 2004, 37(4), 781–788.
- [11] Hastie T, Stuetzle W. Principle Curves. Journal of the American Statistical Association, 1989, 84; 502–615.
- [12] Tarpey T, Flury B. Self–Consistency: A Fundamental Concept in Statistics. Statistical Science, 1996, 11(3), 229–243.
- [13] Tibshirani R. Principal Curves Revisited. Statistics and Computation, 1992, 2, 183–190.
- [14] Delicado P. Another Look at Principal Curves and Surfaces. Journal of Multivariate Analysis, 2001, 77, 84–116.
- [15] Chang KY, Ghosh J. A unified Model for Probabilistic Principal Surfaces. IEEE Trans. On Pattern Analysis and Machine Intelligence, 2001, 23(1), 22–41.
- [16] Duchamp T, Stuetzle W. Geometric Properties of Principal Curves in the Plane. Robust Statistics, Data Analysis and Computer Intensive Methods. New York: Springer Press, 1996, 109, 135–152.
- [17] Duchamp T, Stuetzle W. Extremal Properties of Principal Curves in the Plane. Annals of Statistics, 1996, 24(4), 1511–1520.
- [18] Martínez-Morales JL. Extremal Properties of Principal Embeddings. Journal De Mathématiques Pures et Appliquées, 1999, 78(9), 913–923.
- [19] Krzyzak A, Zeger K. Learning and Design of Principal Curves. IEEE Transactions on Pattern Analysis & Machine Intelligence, 2000, 22(3), 281–297.
- [20] Zhao LW, Luo SW, Liao LZ, Tian M. Research on Main Curve Construction Algorithm. Journal of Beijing Jiaotong University, 2005, 30(2), 80–83.

## 6 Lie group covering learning

This chapter deals with the related theory of the Lie group machine learning covering algorithm, the simply connected covering algorithm of Lie group machine learning, the multiply connected covering algorithm of Lie group machine learning, and an application of the covering algorithm in molecular docking.

### 6.1 Theory of Lie group machine learning covering algorithm

This section deals with the theory of linear representation of a group, the basic properties of the Lie group, and the covering group theory of the Lie group. This knowledge serves as the theoretical basis for studying the Lie group machine learning covering algorithm.

#### 6.1.1 Linear representation of a group

From the group theory point of view, two isomorphic groups have the same properties. Because the matrix group is easier to study, if we can find a matrix group and a given group isomorphism, then we can study the nature of the matrix group and fully grasp the nature of a given group. If the matrix group is only homogeneous with a given group, it not only reflects the partial properties of the given group but also plays a role in studying the properties of the given group. A matrix group with a given group isomorphism or homomorphism is called a linear representation of a given group.

**Definition 6.1.** If a group $D(G)$ consists of a set of $m \times m$ matrices having a determinant that is not zero and $G$ is a given isomorphism or homomorphism, then $D(G)$ is called an $m$-dimensional linear representation of $G$. In $D(G)$, the matrix $D(R)$ corresponding to the element $R$ in $G$ is called the representation matrix of the element $R$ in the expression $D(G)$, and the matrix trace $\chi(R) = \text{Tr } D(R)$ of $D(R)$ is called the character $R$ in the representation $D(G)$.

The determinant of the matrix is not zero in order to exclude the mediator of the representation matrix and the zero matrix. Under this rule, the representation matrix of the constant element is the unit matrix, $D(E) = 1$, and the representation matrix of the reciprocal elements is an inverse matrix, $D(R^{-1}) = D(R)^{-1}$. If $D(G)$ is isomorphic to group $G$, then $D(G)$ is called the true representation of group $G$, and if it is homomorphic, it is not the true representation of group $G$. When all the elements in the group correspond to 1, $D(R) = 1$; this representation is called the identity representation, also known as medioctre representation.

Any group has a constant expression. The matrix group is a representation of itself. The representation matrix is the representation of the unitary matrix. Further, the representation matrix is the representation of the real orthogonal matrix, called the real orthogonal representation.

Before we can find all the linear representations of a group, we should simplify the problem.

**Definition 6.2.** If the two representations $D(G)$ of all the elements $R$ of the group $G$ and the representation matrix in the group $G$ have the same transformation relation $\overline{D}(R)=X^{-1}D(R)X$, then the two representations are called equivalent, i.e., $D(G)=\overline{D}(G)$.

The two equivalents represent equal dimensions, and the similarity transformation matrix $X$ also has the same dimension. The two equivalent representations have equivalent group elements. Equivalence means that there is no substantial difference in the search for all the problems expressed in the group $G$ to find all the unequal representations of the group $G$.

How do we judge whether the two are equivalent? The identity of any element in two equivalents is equal: $\chi(R)=\operatorname{Tr} D(R)=\operatorname{Tr}\overline{D}(R)=\chi(R)$.

For a finite group, the eigenvalues of each element in the two representations are equal and are two necessary equivalents. As the signature is a function of the class, in order to test the equivalence of the two representations, we only need to select an element in each class to check whether the signatures in the two representations are equal.

**Definition 6.3.** If the group $G$ indicates that each representation matrix $D(R)$ of $D(G)$ can be transformed into the same form of the step matrix by a similar transformation $X$:

$$X^{-1}D(R)X=\left(\begin{array}{cc}D^{(1)}(R) & M(R)\\ 0 & D^{(2)}(R)\end{array}\right)$$

then this representation is called an irreducible representation; otherwise, it is called reducible. The set of two sub-matrices $D^{(1)}(R)$ and $D^{(2)}(R)$ in the above equation constitutes a linear representation of group $G$. The signature of the element in the reducible representation is equal to the sum of the signatures in the child representation:

$$\chi(R)=\chi^{(1)}(R)+\chi^{(2)}(R)\ .$$

The nature of $D(G)$ is expressed by the properties of two sub-representations. On the other hand, the number of irreducibles represents straight and together; it constitutes a fully reducible expression. Such an exponential representation does not give any new properties; its representation space is a number of irreducible representations of the sum of spaces. The vectors in the space can be uniquely decomposed into the sum of the vectors belonging to each subspace and are transformed according to each irreducible representation. Thus, the problem of finding all unequal representations of the group is further reduced to the problem of finding all unequal irreducible representations of the group.
