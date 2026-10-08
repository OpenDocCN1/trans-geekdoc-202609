# Single asset American options

```
$$\begin{pmatrix} a_{1,1} & a_{1,2} & a_{1,3} & a_{1,4} \ a_{2,1} & a_{2,2} & a_{2,3} & a_{2,4} \ a_{3,1} & a_{3,2} & a_{3,3} & a_{3,4} \ a_{4,1} & a_{4,2} & a_{4,3} & a_{4,4} \end{pmatrix} = \begin{pmatrix} 1 & 0 & 0 & 0 \ l_{2,1} & 1 & 0 & 0 \ l_{3,1} & l_{3,2} & 1 & 0 \ l_{4,1} & l_{4,2} & l_{4,3} & 1 \end{pmatrix} = \begin{pmatrix} u_{1,1} & u_{1,2} & u_{1,3} & 0 \ 0 & u_{2,2} & u_{2,3} & u_{2,4} \ 0 & 0 & u_{3,3} & u_{3,4} \ 0 & 0 & 0 & u_{4,4} \end{pmatrix} \quad (5.4.30)$
```

If A is a tridiagonal matrix then the LU decomposition takes the simpler form:

```
$$\begin{pmatrix} a_{1,1} & a_{1,2} & 0 \ a_{2,1} & a_{2,2} & a_{2,3} \ 0 & a_{3,2} & a_{3,3} \end{pmatrix} = \begin{pmatrix} 1 & 0 & 0 \ l_{2,1} & 1 & 0 \ 0 & l_{3,2} & 1 \end{pmatrix} = \begin{pmatrix} u_{1,1} & u_{1,2} & 0 \ 0 & u_{2,2} & u_{2,3} \ 0 & 0 & u_{3,3} \end{pmatrix} \quad (5.4.31)$
```

where it can be seen that both L and U are bidiagonal.

Once the LU decomposition of A has been found, it is possible to solve for x in Eq. (5.4.29) using a two stage method (for example elimination is used to solve for $Ly = \mathcal{R}$, and back-substitution is applied to $Ux = y$). We can then write the procedure as:

```
$Ax = (LU)x = L(Ux) = Ly = \mathcal{R}$
```

We now provide code excerpts which show how to solve the $(n_s - 2) \times (n_s - 2)$ tridiagonal system represented by Eq. (5.4.29). These excerpts are in fact contained within the larger Code excerpt 518, which displays the complete C code for the option pricing function. If the reader requires more detail then this code should be consulted. (It should be noted that in Code 518, time is indexed using $j$ and asset price using index $i$. We have modified the indices for the smaller code given below so, as might expected, time is indexed using $i$, and asset price using $j$. The author apologizes for any inconvenience this may cause.) For brevity, we will assume that all the arrays have already been allocated and loaded with the relevant information.

We first need to compute the LU decomposition of the tridiagonal matrix A. The code to achieve this is given in Code 514. Here we use the following three arrays to store the elements of the tridiagonal matrix A: array $b$ contains the diagonal elements, array $c$ contains the upper diagonal elements, and array $a$ holds the lower diagonal elements.

It should be noted that all the diagonal elements of the matrix L. are known to be 1, and the sub-diagonal elements of L are computed from the diagonal elements of U using $l[j] = a[j]/u[j-1]$. Also we do not need to compute the upper diagonal elements of U since they are known to be the same as the upper diagonal