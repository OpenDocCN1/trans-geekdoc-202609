
# Introduction 289

problems. Similar singularities may also exist in other coordinate systems and are particularly relevant for “floppy” molecules. Several effective strategies have been proposed to avoid or alleviate problems associated with such singularities.${15,16}

## Direct Diagonalization

The matrix eigenequation in Eq. [6] can also be considered as the result of the Rayleigh-Ritz variation with the trial function in Eq. [2]. According to MacDonald’s theorem,$^{17}$ the approximate eigenvalues obtained by solving Eq. [6] provide the upper bounds for the exact counters. Hence, eigenvalues $\mu_n$ of the $N \times N$ Hamiltonian matrix can be determined by optimizing the variation parameters (B).$^{3,4}$ In principle, the eigenequation in Eq. [6] can be solved by finding the roots in the Nth-order characteristic polynomial $[H - \ell I]$, where $I$ is the identity matrix. However, root-searching becomes inefficient when the order of matrix $N$ increases, especially considering that there is no explicit formula for $N \ge 4$. A more effective way to find the eigenpairs of the Hamiltonian matrix is by diagonalization. Indeed, multiplying $B^{-1}$ on both sides of Eq. [6] on the left yields

```
$B^{-1}HB = E$
```

```
$B^{-1}B = BB^{-1} = I$. In other words, the diagonalization of $H$ by a similarity transformation gives its eigenvalues as the diagonal matrix elements, whereas the matrix that transforms the Hamiltonian to its diagonal form contains the eigenvectors. For a real-symmetric matrix, the transformation $B$ is orthogonal, whereas the $B$ matrix becomes unitary if $H$ is Hermitian.
```

When a non-orthogonal basis is used, a generalized eigenproblem will ensue. Its solution becomes more involved than a non-diagonal overlap matrix, but methods to handle such problems exist and are referred to other sources for details.$^{18}$ One popular approach is to remove the linear dependence by diagonalizing the overlap matrix. This-called singular value decomposition (SVD) reduces a generalized eigenproblem to a regular one. In some techniques discussed below, the solution of a small generalized eigenproblem might be required.

There are several ways to diagonal a real-symmetric matrix. The common strategy is to use orthogonal matrices to gradually reduce the magnitude of off-diagonal elements.${18,19}$ The most widely and well-known approach is the Jacobi rotation, which zeros one element at a time. The alternative rotation scheme devised by Givens can be used to make the process more efficient. Perhaps the most efficient and commonly used approach is that

## Recursive Solutions to Large Eigenproblems

From Householder, which reduces the full matrix H to a symmetric tridiagonal form (T) by using a finite number (N-2) of reflections:

```
$T = Q_{N-2}^{-1}Q_{N-3}^{-1} \cdots Q_1^{-1}HQ_1 \cdots Q_{N-3}Q_{N-2} \quad [17]$
```

where the inverse of the orthogonal matrix Q can be readily obtained: $Q^{-1} = Q^T$. The efficiency of the Householder method stems from the fact that multiple zeros can be produced at each step.
The subsequent diagonalization of the symmetric tridiagonal matrix T is relatively straightforward and numerically inexpensive. It can be carried out by root-searching methods such as bisection if a small number of eigenvalues is of interest.$^{18,19}$ When the entire spectrum is needed, on the other hand, one would use factorization methods such as QR (or the related QL), which are named after the matrices shown below.$^{18,19}$ In the QR approach, the tridiagonal matrix is factorized into the product of an orthogonal matrix Q and an upper triangular R:

```
$T = QR \quad [18]$
```

```
$T' = RQ = Q^{-1}TQ \quad [19]$
```

maintains the tridiagonal form and eventually converges to the diagonal form. We note in passing that the QR factorization itself can be used to diagonalize matrices, but the efficiency is usually not optimal. Other methods such as inverse iteration may also be used to find eigenpairs of a symmetric tridiagonal matrix.$^{18,20}$
As the modification of the original Hamiltonian matrix is involved in the diagonalization methods discussed above, we denote such approaches as *direct diagonalization* to distinguish them from the recursive ones below. The direct diagonalization process is illustrated in Figure 1.

![](img/fa9d34afc1bcb785fd3792baa6c5c679_321_0.png)

Figure 1 Schematic procedure for direct diagonalization.

## Introduction

## Scaling Laws and Motivation for Recursive Diagonalization

Three major advantages of the direct diagonalization approach exist. First, it yields all eigenpairs at the same time. Second, it is very stable and robust. For instance, the orthonormality of the eigenvectors can be achieved with machine precision. Third, several well-developed and easy-to-use “canned” routines allow robust diagonalization of Hermitian and real-symmetric matrices. Similar routines can also be found for generalized eigenvalue problems. One can find such routines from numerical libraries such as Numerical Recipes,$^{19}$ LAPACK or freely EASPACK (www.netflix.org/lapack/), IMSL (www.vni.com/products/imsl/), and NAG (www.nag.co.uk/). Among these, LAPACK is free. As a result, direct diagonalization has been the method of choice for many years.

However, a potentially serious problem for direct diagonalization is its scaling. The number of arithmetic operations in the Householder method scales $N^3$. Moreover, all $N^2$ matrix elements must be stored in the core memory, even if it is a sparse matrix. The scaling laws for diagonalizing a tridiagonal matrix are much less than that of the tridiagonalization step. Hence, diagonalization becomes a computational bottleneck when $N > 10,000$, with rapidly increasing central processing unit (CPU) speed and core memory.

The adverse effect of the scaling laws for the direct diagonalization can be illustrated when a direct product basis is used and each degree of freedom is allocated ten basis functions, the dimensionality of the Hamiltonian matrix (N) becomes $10^3$ for a triatomic molecule, and it increases to $10^4$ for the polyatomic molecule. The storage of $10^{12}$ double-precision numbers is difficult, if not impossible, to accomplish with a state-of-the-art super-computer. Of course, various basis truncation and/or optimization schemes have been proposed to minimize the size of the Hamiltonian matrix,$5,22}$ but these schemes are system dependent, in general more difficult to program, and more importantly merely postpone the onset of the bottleneck. There is thus a strong desire to use diagonalization schemes that scale better than direct methods.

Apart from the scaling laws, one can also argue that the complete solution of the eigenequation mandated by direct diagonalization might not be necessary because only small regions of the spectrum are often of interest. It is thus desirable sometimes to extract only a few eigenvalues in a spectral range.

As discussed, an alternative to direct diagonalization is by recursion. The recursive diagonalization approach has several attractive features, including more favorable scaling laws, which make it ideally suited for large eigenproblems. For example, some applications of linear-scaling methods in

## Recursive Solutions to Large Eigenproblems

quantum chemistry have been discussed in this book series.^23 A related problem in quantum mechanics is the recursive interpolation of operator functions, such as the time propagator. Although diagonalization in those cases might be overkill, recursive methods are nonetheless extensively used. As a result, we will offer some discussions about this issue when appropriate.

## RECURSION AND THE KRYLOV SUBSYPACE

To understand the recursive diagonalization idea, it is instructive to examine the power method.^18,20 Assuming that the eigenvector of H corresponds to its largest eigenvalue (b1, ε1 = emax) is contained in an initial vector (q):

```
q = \sum_{n=1} a_n b_n  [20]
```

the repeated multiplication of the Hamiltonian matrix on the initial vector generates a series of vectors:

```
q, Hq, H²q, ..., H^k q  [21]
```

As K increases, the vector H^kq will eventually converge to b1 because overwhelms all terms in q with its large eigenvalue:

```
H^k q = \sum_{n=1} a_n ε_n^k b_n \xrightarrow{k\to\infty} a_1 ε_1^k b_1  [22]
```

Here, we have assumed that the dominant eigenvector b1 is nondegenerate.
The power method uses only the last vector in the recursive sequence in Eq. [21], discarding all information by preceding vectors. It is difficult to imagine that significantly more information may be extracted from the space spanned by these vectors, which is often called the Krylov subspace.^20,24

```
K^{(K)}(q, H) = span{q, Hq, H²q, ..., H^{K-1}q  [23]
```

Unless the initial vector is already an eigenvector, the Krylov vectors are linearly independent and they eventually span the eigenspace of H:

```
C^{(N)}(q, H) = span{q, Hq, H²q, ..., H^{N-1}q} = span{b1, b2, ..., bN}  [24]
```

provided that the initial vector has nonzero overlaps with all eigenvectors.
 conclusion suggests that one can in principle extract eigenpairs of H
