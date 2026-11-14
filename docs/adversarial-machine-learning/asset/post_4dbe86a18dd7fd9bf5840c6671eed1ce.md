
## Matrices

Usually denoted with an uppercase bold character such as **A**, a *matrix* is a multi-dimensional object with two indices, which represent a row and column. The $(i, j)^\text{th}$ element of **A** is denoted by $A_{i,j} \in \mathbb{X}$ where $i \in \{1, 2, \dots, M\}$ and $j \in \{1, 2, \dots, N\}$. The full matrix can then be expressed element-wise using the bracket notation:

\(\mathbf{A} = \begin{bmatrix} A_{1,1} & A_{1,2} & \cdots & A_{1,N} \\ A_{2,1} & A_{2,2} & \cdots & A_{2,N} \\ \vdots & \vdots & \ddots & \vdots \\ A_{M,1} & A_{M,2} & \cdots & A_{M,N} \end{bmatrix}\)

As suggested by this notation, a matrix's first index specifies its *row* and the second specifies its *column*. Each row and column are themselves vectors and are denoted by $\mathbf{A}_{i,\cdot}$ and $\mathbf{A}_{\cdot,j}$ respectively. We also use the bracket notation $[\cdot]_{i,j}$ to refer to the $(i, j)^\text{th}$ element of a matrix-valued expression; e.g., $[\mathbf{A} + \mathbf{B}]_{i,j}$ is the $(i, j)^\text{th}$ element of the matrix $\mathbf{A} + \mathbf{B}$. Special matrices include the identity matrix **I**, with 1's along its diagonal and 0's elsewhere, and the zero matrix $\mathbf{0}$ with zero in every element. The transpose of an \(M \times N\)-dimensional matrix is an \(N \times M\)-dimensional matrix denoted as $\mathbf{A}^\top$ and defined as $[\mathbf{A}^\top]_{i,j} = A_{j,i}$.

## Matrix Multiplication

Here we consider vectors and matrices whose elements belong to a scalar field $\mathcal{X}$ endowed with multiplication and addition (e.g., $\mathfrak{R}$, $\Re$). For the purpose of matrix multiplication, we represent an \(N\)-dimensional vector as the equivalent \(N \times 1\) matrix for notational convenience. The *inner product* between two vectors $\mathbf{v}$ and $\mathbf{w}$, with \(dim(\mathbf{v}) = dim(\mathbf{w}) = N\), is the scalar denoted by $\mathbf{v}^\top \mathbf{w} = \sum_{i=1}^N v_i \cdot w_i$. The *outer product* between \(M\)-dimensional vector $\mathbf{v}$ and \(N\)-dimensional vector $\mathbf{w}$ is an \(M \times N\)-dimensional matrix denoted by $\mathbf{v}\mathbf{w}^\top$ with elements $[\mathbf{v}\mathbf{w}^\top]_{i,j} = v_i \cdot w_j$. The product between an \(M \times N\)-dimensional matrix **A** and an \(N\)-dimensional vector $\mathbf{w}$ is denoted $\mathbf{A}\mathbf{w}$ and defined as the \(M\)-dimensional vector of inner products between the \(i^\text{th}\) row $\mathbf{A}_{i,\cdot}$ and the vector $\mathbf{w}$; i.e., $[\mathbf{A}\mathbf{w}]_i = \mathbf{A}_{i,\cdot}\mathbf{w}$. It follows that $\mathbf{v}^\top \mathbf{A}\mathbf{w}$ is a scalar defined as $\mathbf{v}^\top \mathbf{A}\mathbf{w} = \sum_{i,j} v_i \cdot A_{i,j} \cdot w_j$. The *matrix product* between an \(M \times N\)-dimensional matrix **A** and an \(N \times K\)-dimensional matrix **B** is an \(M \times K\)-dimensional matrix denoted by $\mathbf{A}\mathbf{B}$ whose \((i, j)^\text{th}\) element is the inner product between the \(i^\text{th}\) row of **A** and the \(j^\text{th}\) column of **B**; i.e., $[\mathbf{A}\mathbf{B}]_{i,j} = \mathbf{A}_{i,\cdot}^\top \mathbf{B}_{\cdot,j}$.

We also use the *Hadamard (element-wise)* product of vectors and matrices that we denote with the $\odot$ operator. The Hadamard product of vectors $\mathbf{v}$ and $\mathbf{w}$, with \(dim(\mathbf{v}) = dim(\mathbf{w})\), is a vector defined as $[\mathbf{v} \odot \mathbf{w}]_i \triangleq v_i \cdot w_i$. Similarly, the Hadamard product of matrices **A** and **B**, with \(dim(\mathbf{A}) = dim(\mathbf{B})\), is the matrix $[\mathbf{A} \odot \mathbf{B}]_{i,j} \triangleq A_{i,j} \cdot B_{i,j}$.

## Functions

We denote a function using regular italic font; e.g., the function \(g\). However, for common named functions (such as logarithm and sine) we use the non-italicized Roman typeface (e.g., log and sin). A function is a mapping from its *domain* \(\mathbb{X}\) to its *co-domain* or *range* \(\mathbb{Y}; g: \mathbb{X} \rightarrow \mathbb{Y}\). To apply \(g\) to \(x\), we use the usual notation \(g(x)\); \(x \in \mathbb{X}\) is the argument and \(g(x) \in \mathbb{Y}\) is the value of \(g\) at \(x\). We also use this notation to refer to parameterized objects, but in this case, we will name the object according to its type. For instance, \(\mathbb{B}^C (g) \triangleq \{x \mid g(x) < C\}\) is a set parameterized by the function \(g\) called the \(C\)-ball of \(g\), and so we call attention to the fact that this object is a set by using the set notation \(\mathbb{B}\) in naming it.

A convex function is any real-valued function \(g: \mathbb{X} \rightarrow \Re\) whose domain \(\mathbb{X}\) is a convex set in a vector space such that, for any \(x^{(1)}, x^{(2)} \in \mathbb{X}\) and any \(\alpha \in [0, 1]\), the function satisfies the inequality

\[ f \left(\alpha x^{(1)} + (1 - \alpha) x^{(2)}\right) \le \alpha f \left(x^{(1)}\right) + (1 - \alpha) f \left(x^{(2)}\right) . \]

## *Families of Functions*

A family of functions is a set of functions, for which we extend the previous concept of multidimensional sets. Functions can be defined as tuples of (possibly) infinite length—instead of indexing the tuple with natural numbers, it is indexed by the domain of the function; e.g., the reals. To represent the set of all such functions, we use the generalized Cartesian product over an index set \(\mathbb{I} \triangleq \times_{i \in \mathbb{I}} \mathbb{X}\) where \(\mathbb{X}\) is the co-domain of the family of functions. For instance, the set of all real-valued functions is \(\mathcal{G} = \times_{x \in \Re} \Re\); i.e., every function \(g \in \mathcal{G}\) is a mapping from the reals to the reals: \(g: \Re \rightarrow \Re\). We also consider special subsets such as the set of all continuous real-valued functions \(\mathcal{G}^{(\text{continuous})} = \{g \in \mathcal{G} \mid \text{continuous} (g) \}\) or the set of all convex functions \(\mathcal{G}^{(\text{convex})} = \{g \in \mathcal{G} \mid \forall t \in [0, 1] \quad g(tx + (1 - t)y) \le tg(x) + (1 - t)g(y) \}\). Particularly, we use the family of all classifiers (as defined in Section 2.2.2) in a \(D\)-dimensional space in Chapter 8. This family is the set of functions mapping \(\Re^D\) to the set \(\{ -, + \}\) and is denoted by \(\mathcal{F} \triangleq \times_{x \in \Re^D} \{ -, + \}\).

## *Optimization*

Learning theory makes heavy use of mathematical optimization. Optimization typically is cast as finding a *best object* \(x\) from a space \(\mathcal{X}\) in terms of finding a minimizer of an objective function \(f: \mathcal{X} \rightarrow \Re\):

\[ x^* \in \underset{x \in \mathcal{X}}{\text{argmin}} [f(x)] \]

where \(\text{argmin} [\cdot]\) is a mapping from the space of all objects \(\mathcal{X}\) to a subset \(\mathbb{X}' \subseteq \mathcal{X}\), which is the set of all objects in \(\mathcal{X}\) that minimize \(f\) (or equivalently maximize \(-f\)). Optimizations can additionally be restricted to obey a set of *constraints*. When specifying an optimization with constraints, we use the following notation:

\[ \text{argmin}_{x \in \mathcal{X}} [f(x)] \]

\[ \text{s.t.} \quad C(x) \]

where \(f\) is the function being optimized and \(C\) represents the constraints that need to be satisfied. Often there will be several constraints \(C_i\) that must be satisfied in the optimization.

## *Probability and Statistics*

We denote a probability distribution over the space $\mathcal{X}$ by $P_{\mathcal{X}}$. It is a function that is defined on the subsets in a $\sigma$-field of $\mathcal{X}$ (i.e., a set of subsets $\mathbb{A}^{(i)} \subseteq \mathcal{X}$ that is closed under complements and countable unions) and satisfies (i) $P_{\mathcal{X}} (\mathbb{A}^{(i)}) \ge 0$ for all subsets $\mathbb{A}^{(i)}$, (ii) $P_{\mathcal{X}} (\mathcal{X}) = 1$, and (iii) for pairwise disjoint subsets $\mathbb{A}^{(1)}, \mathbb{A}^{(2)}, ...$, it yields $P_{\mathcal{X}} (\bigcup_i \mathbb{A}^{(i)}) = \sum_i P_{\mathcal{X}} (\mathbb{A}^{(i)})$ . For a more thorough treatment, we refer the interested reader to Billingsley (1995). A random variable drawn from distribution $P_{\mathcal{X}}$ is denoted by $X \sim P_{\mathcal{X}}$—notice that we do not use a special notation for the random variable, but we make it clear in the text that they are random. The expected value of a random variable is denoted by $\text{E}_{X \sim P_{\mathcal{X}}} [X] = \int x \, dP_{\mathcal{X}} (x)$ or simply by E [X] when the distribution of the random variables is known from the context. The family of all probability distributions on $\mathcal{X}$ is denoted by $\mathcal{P}_{\mathcal{X}}$; as above, this is the family of all functions that assign probability to elements of the $\sigma$-field of $\mathcal{X}$.

## **A.2 Covering Hyperspheres**

Here we summarize the properties of hyperspheres and spherical caps and a covering number result provided by Wyner (1965) and Shannon (1959). This covering result will be used to bound the number of queries required by any evasion algorithm for $\ell_2$ costs in Appendix D.2.

![](img/0637c4902205011abc4f185025bd5607_274_0.png)

![](img/0637c4902205011abc4f185025bd5607_274_1.png)

## **(a) A Spherical Cap on a Circle**

## **(b) An Angular Cap on a Circle**

**Figure A.1** This figure shows various depictions of spherical caps. **(a)** A depiction of a spherical cap of height h, which is created by a halfspace that passes through the sphere. The gray region represents the area of the cap. **(b)** The geometry of the spherical cap: The intersecting halfspace forms a right triangle with the centroid of the hypersphere. The length of the side of this triangle adjacent to the centroid is R - h, its hypotenuse has length R, and the side opposite the centroid has length $\sqrt{h(2R - h)}$. The half-angle $\phi$, given by $\sin (\phi) = \frac{\sqrt{h(2R - h)}}{R}$, of the right circular cone is used to parameterize the cap.
