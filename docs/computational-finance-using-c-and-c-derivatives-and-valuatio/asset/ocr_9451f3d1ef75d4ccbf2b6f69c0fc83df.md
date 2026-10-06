# 138 CHAPTER | 5 Single Asset American Options

where

```
$R_{i+1,n_{s-2}} = \tilde{a}_{n_{s-2}}f_{i,n_{s-3}} + b_{n_{s-2}}f_{i+1,n_{s-2}} + (\tilde{c}_{n_{s-2}} - c_{n_{s-2}})fBU \quad (5.4.25)$
```

Case 3
In this case, the boundary values do not enter into the expressions and we simply equate equation (5.4.144) as

```
$a_j f_{i,j-1} + b_j f_{i,j} + c_j f_{i+1,j+1} = R_{i+1,j}, \quad j = 3, \dots, n_{s-3}, \quad (5.4.26)$
```

where as the right-hand side, $R_{i+1,j}$, is

```
$R_{i+1,j} = \tilde{a}_j f_{i,j-1} + b_j f_{i,j} + \tilde{c}_j f_{i+1,j+1}. \quad (5.4.27)$
```

We can now draw all the information in equation (5.4.23) (5.4.27) and represent it by the following tridiagonal system:

```
$$\begin{pmatrix} b_1 & c_1 & 0 & 0 & 0 & f_{i,1} \ a_2 & b_2 & c_2 & 0 & 0 & f_{i,2} \ 0 & 0 & \cdot & 0 & 0 & \cdot \ 0 & 0 & 0 & \cdot & 0 & \cdot \ 0 & 0 & a_{n_{s-3}} & b_{n_{s-3}} & c_{n_{s-3}} & f_{i,n_{s-3}} & R_{i+1,n_{s-3}} \ 0 & 0 & 0 & a_{n_{s-2}} & b_{n_{s-2}} & f_{i,n_{s-2}} & R_{i+1,n_{s-2}} \end{pmatrix} = \dots \quad (5.4.28)$
```

In matrix notation, equation (5.4.28) can be written as

```
$AX = R, \quad \(5.4.29)$
```

where $A$ is an $n_{s-2} \times n_{s-2}$ tridiagonal matrix containing the known coefficients $a_j, j = 2, \dots, n_{s-2}, b_{j,j} = 1, \dots, n_{s-2},$ and $c_{j,j} = 1, \dots, n_{s-3}$. The vector $R$ denotes the known right-hand side, $R_{i+1,j} = 1, \dots, n_{s-2},$ and the vector $x$ contains the option values we wish to compute, $f_{i,j} = 1, \dots, n_{s-2}$.

It is well-known that, if matrix A is “non-singular”, equation (5.4.29) can be solved using LU decomposition, de, we factorize the $n \times n$ matrix $A$ as

```
$A = LU,$
```

where $L$ is an $n \times n$ lower triangular matrix with 1s on the diagonal and $U$ is an $n \times p$ upper triangular matrix. The LU decomposition for a $4 \times 4$ matrix below

```
$$\begin{pmatrix} a_{1,1} & a_{1,2} & a_{1,3} & a_{1,4} \ a_{2,1} & a_{2,2} & a_{2,3} & a_{2,4} \ a_{3,1} & a_{3,2} & a_{3,3} & a_{3,4} \ a_{4,1} & a_{4,2} & a_{4,3} & a_{4,4} \end{pmatrix} = \begin{pmatrix} 1 & 0 & 0 & 0 \ l_{2,1} & 1 & 0 & 0 \ l_{3,1} & l_{3,2} & 1 & 0 \ l_{4,1} & l_{4,2} & l_{4,3} & 1 \end{pmatrix} \begin{pmatrix} u_{1,1} & u_{1,2} & u_{1,3} & u_{1,4} \ 0 & u_{2,2} & u_{2,3} & u_{2,4} \ 0 & 0 & u_{3,3} & u_{3,4} \ 0 & 0 & 0 & u_{4,4} \end{pmatrix} \quad \(5.4.30)$
```