If $m = n$, the matrix is said to be **square**.

We use the notation $A_{ij}$ or $A_{i,j}$ to denote the entry of $\mathbf{A}$ in the $i$th row and $j$th column. We use the notation $\mathbf{A}_{i,:}$ to denote the $i$'th row and $\mathbf{A}_{:,j}$ to denote the $j$'th column. We treat all vectors as column vectors by default (so $\mathbf{A}_{i,:}$ is viewed as a column vector with $n$ entries). We use bold upper case letters to denote matrices, bold lower case letters to denote vectors, and non-bold letters to denote scalars.

We can view a matrix as a set of columns stacked along the horizontal axis:

$\mathbf{A} = \left[ \begin{array}{cccc} | & | & \cdots & | \\ \mathbf{A}_{:,1} & \mathbf{A}_{:,2} & \cdots & \mathbf{A}_{:,n} \\ | & | & & | \end{array} \right].$  (C.4)

For brevity, we will denote this by

$\mathbf{A} = [\mathbf{A}_{:,1}, \mathbf{A}_{:,2}, \dots, \mathbf{A}_{:,n}]$  (C.5)

We can also view a matrix as a set of rows stacked along the vertical axis:

$\mathbf{A} = \left[ \begin{array}{c} - \mathbf{A}_{1,:}^\top - \\ - \mathbf{A}_{2,:}^\top - \\ \vdots \\ - \mathbf{A}_{m,:}^\top - \end{array} \right].$  (C.6)

For brevity, we will denote this by

$\mathbf{A} = [\mathbf{A}_{1,:}; \mathbf{A}_{2,:}; \dots; \mathbf{A}_{m,:}]$  (C.7)

(Note the use of a semicolon.)

The **transpose** of a matrix results from “flipping” the rows and columns. Given a matrix $\mathbf{A} \in \mathbb{R}^{m \times n}$, its transpose, written $\mathbf{A}^\top \in \mathbb{R}^{n \times m}$, is defined as

$(\mathbf{A}^\top)_{ij} = A_{ji}$  (C.8)

The following properties of transposes are easily verified:

$(\mathbf{A}^\top)^\top = \mathbf{A}$  (C.9)

$(\mathbf{A B})^\top = \mathbf{B}^\top \mathbf{A}^\top$  (C.10)

$(\mathbf{A} + \mathbf{B})^\top = \mathbf{A}^\top + \mathbf{B}^\top$  (C.11)

If a square matrix satisfies $\mathbf{A} = \mathbf{A}^\top$, it is called **symmetric**. We denote the set of all symmetric matrices of size $n$ as $\mathbb{S}^n$.

# C.1.1.3  Tensors

A **tensor** (in machine learning terminology) is just a generalization of a 2d array to more than 2 dimensions, as illustrated in Fig. C.1. For example, the entries of a 3d tensor are denoted by $A_{ijk}$.