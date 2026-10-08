# 144 Computational Finance Using C and C#

or equivalently:

```
$$a_{n_s-2}f_{i,n_s-3} + b_{n_s-2}f_{i,n_s-2} = R_{i+1,n_s-2}$ $\$(5.4.24)$
```

where

```
$$R_{i+1,n_s-2} = \tilde{a}_{n_s-2}f_{i+1,n_s-3} + \tilde{b}_{n_s-2}f_{i+1,n_s-2} + (\tilde{c}_{n_s-2} - c_{n_s-2})f_{BU}$ $\$(5.4.25)$
```

Case 3

In this case the boundary values do not enter into the entries, and we simply extract Eq. (5.4.14):

```
$$a_j f_{i,j-1} + b_j f_{i,j} + c_j f_{i,j+1} = R_{i+1,j}, \quad j=3, \dots, n_s-3,$ $\$(5.4.26)$
```

where as before the right-hand side, $R_{i+1,j}$, is:

```
$$R_{i+1,j} = \tilde{a}_j f_{i,j+1} + \tilde{b}_j f_{i+1,j} + \tilde{c}_j f_{i+1,j+1}$ $\$(5.4.27)$
```

We now gather all the information in Eqs. (5.4.23)-(5.4.27) and represent by the following triangular system:

```
$$\begin{array}{rccccc} & b_1 & c_1 & 0 & 0 & 0 & f_{i,1} \ a_2 & b_2 & c_2 & 0 & 0 & f_{i,2} \ & 0 & 0 & 0 & 0 & & \ & 0 & 0 & 0 & 0 & & \ 0 & 0 & 0 & a_{n_s-3} & b_{n_s-3} & c_{n_s-3} & f_{i,n_s-3} \ & & & 0 & 0 & a_{n_s-2} & b_{n_s-2} & f_{i,n_s-2} \end{array}$$
```

```
$= \begin{pmatrix} & R_{i+1,1} \ & R_{i+1,2} \ & & R_{i+1,n_s-3} \ & & & R_{i+1,n_s-2} \end{pmatrix}$ $\$(5.4.28)$
```

In matrix notation Eq. (5.4.28) can be written as:

```
$$Ax = \mathcal{R}$ $\$(5.4.29)$
```

where $A$ is the $(n_s-2) 	imes (n_s-2)$ tridiagonal matrix containing the coefficients $a_j, j=2, \dots, n_s-2, b_j, j=1, \dots, n_s-2$, and $c_j, j=1, \dots, n_s-3$. The vector $\mathcal{R}$ represents the known right-hand side, $R_{i+1,j}$, and the vector $x$ contains the unknown values that we wish to compute, $f_{i,j}, j=1, \dots, n_s-2$.

It is well known that, if matrix $A$ is nonsingular, (5.4.29) can be solved using LU decomposition. We factorize the $n \times n$ matrix $A$ as:

```
$$A = LU$
```

where $L$ is an $n \times n$ lower triangular matrix with 1s on the diagonal and $U$ is an $n \times n$ upper triangular matrix. We illustrate the LU decomposition for a full $4 \times 4$ matrix below: