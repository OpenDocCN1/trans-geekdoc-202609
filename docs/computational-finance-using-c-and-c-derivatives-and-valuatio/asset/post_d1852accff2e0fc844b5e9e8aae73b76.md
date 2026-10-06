
# 138 CHAPTER | 5 Single Asset American Options

```
$R_{i+1,n_{s-2}} = \tilde{a}_{n_{s-2}}f_{i,n_{s-3}} + b_{n_{s-2}}f_{i+1,n_{s-2}} + (\tilde{c}_{n_{s-2}} - c_{n_{s-2}})fBU \quad (5.4.25)$
```

### Case 3
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
$$\begin{pmatrix} b_1 & c_1 & 0 & 0 & 0 & f_{i,1} \\ a_2 & b_2 & c_2 & 0 & 0 & f_{i,2} \\ 0 & 0 & \cdot & 0 & 0 & \cdot \\ 0 & 0 & 0 & \cdot & 0 & \cdot \\ 0 & 0 & a_{n_{s-3}} & b_{n_{s-3}} & c_{n_{s-3}} & f_{i,n_{s-3}} & R_{i+1,n_{s-3}} \\ 0 & 0 & 0 & a_{n_{s-2}} & b_{n_{s-2}} & f_{i,n_{s-2}} & R_{i+1,n_{s-2}} \end{pmatrix} = \dots \quad (5.4.28)$
```

In matrix notation, equation (5.4.28) can be written as

```
$AX = R, \quad (5.4.29)$
```

where $A$ is an $n_{s-2} \times n_{s-2}$ tridiagonal matrix containing the known coefficients $a_j, j = 2, \dots, n_{s-2}, b_{j,j} = 1, \dots, n_{s-2},$ and $c_{j,j} = 1, \dots, n_{s-3}$. The vector $R$ denotes the known right-hand side, $R_{i+1,j} = 1, \dots, n_{s-2},$ and the vector $x$ contains the option values we wish to compute, $f_{i,j} = 1, \dots, n_{s-2}$.

It is well-known that, if matrix A is “non-singular”, equation (5.4.29) can be solved using LU decomposition, de, we factorize the $n \times n$ matrix $A$ as

```
$A = LU,$
```

where $L$ is an $n \times n$ lower triangular matrix with 1s on the diagonal and $U$ is an $n \times p$ upper triangular matrix. The LU decomposition for a $4 \times 4$ matrix below

```
$$\begin{pmatrix} a_{1,1} & a_{1,2} & a_{1,3} & a_{1,4} \\ a_{2,1} & a_{2,2} & a_{2,3} & a_{2,4} \\ a_{3,1} & a_{3,2} & a_{3,3} & a_{3,4} \\ a_{4,1} & a_{4,2} & a_{4,3} & a_{4,4} \end{pmatrix} = \begin{pmatrix} 1 & 0 & 0 & 0 \\ l_{2,1} & 1 & 0 & 0 \\ l_{3,1} & l_{3,2} & 1 & 0 \\ l_{4,1} & l_{4,2} & l_{4,3} & 1 \end{pmatrix} \begin{pmatrix} u_{1,1} & u_{1,2} & u_{1,3} & u_{1,4} \\ 0 & u_{2,2} & u_{2,3} & u_{2,4} \\ 0 & 0 & u_{3,3} & u_{3,4} \\ 0 & 0 & 0 & u_{4,4} \end{pmatrix} \quad (5.4.30)$
```

## Grid Methods for Vanilla Options Section | 5.4

If A is a tridiagonal matrix, then the LU decomposition takes the simpler form

```
\begin{pmatrix} a_{1,1} & a_{1,2} & 0 & 1 & 0 & 0 & u_{1,1} & 2 & 0 \\ a_{2,1} & a_{2,2} & a_{2,3} & 0 & l_{2,1} & 1 & 0 & 0 & u_{2,2} & u_{2,3} & 0 \\ 0 & a_{3,2} & a_{3,3} & a_{3,4} & 0 & l_{3,2} & 1 & 0 & 0 & u_{3,3} & u_{3,4} \\ 0 & 0 & a_{4,3} & a_{4,4} & 0 & 0 & l_{4,3} & 1 & u_{4,4} \end{pmatrix} = (5.4.31)
```

where it can be seen that L and U are bipolar. Once the decomposition of A has been found, it is possible to solve for x in equation (5.4.29) using a two-stage method (for example, Golub and Van Loan (1989)). Here, forward elimination is used to solve $Ly = R$, and back-substitution is applied to $Ux = y$. We can then write the procedure as

```
Ax = (LU)x = L(Ux) = Ly.
```

We now provide code excerpts showing how to solve the $n_{s-2} \times n_{s-2}$ tridiagonal system represented by equation (5.4.29). These excerpts are contained within the larger Code excerpt 18, which details the complete code for option pricing. If reader requires more details concerning the code used for option pricing, then this code should be consulted (It should be noted that in Code excerpt 18, time is indexed using $j$ and price using $i$). We have modified the indices for the smaller code excerpts below so, as might be expected, time is indexed using $i$ and price using $j$. The author apologizes for any inconvenience this may cause. Here, by brevity, we assume that all the required arrays have been allocated and loaded with relevant information.

First compute the LU decomposition of the tridiagonal matrix. Here, we use the following arrays to store the elements of Code excerpt 14 below, the tridiagonal matrix $A$: array $b$ contains diagonal elements, array $c$ contains the upper diagonals, and array $a$ holds the lower diagonals.

```
u[0] = b[0];
if (u[0] != 0) printf("ERROR in array u");
for(j=1; j<n; j++) {
  u[j] = b[j]-a[j]*u[j-1];
  if (u[j] != 0) printf("ERROR in array u");
}
```

Code excerpt 14 calculates the diagonal elements of matrix $U$, in an LU decomposition of tridiagonal matrix $A$. The elements of matrix $A$ are stored in the following arrays: array $b$ contains diagonal elements, array $c$ contains upper diagonals, and array $a$ holds lower diagonals. The elements of $U$ are stored in the array $u$ for later use. We do not explicitly compute the elements of matrix $L$ because all the diagonal elements of $L$ are known to be 1, and the sub-diagonal elements can be computed from the diagonal elements of $U$ using $a[j]/u[j-1]$. We do not need to compute the upper diagonal elements of $U$ since they are known to be the same as the upper elements of the original matrix $A$ and are contained in array $c$, see for example, Hager (1988).

Having the LU decomposition, we can now solve the triangular system $Ly = R$ using forward elimination; this is shown in Code excerpt 15.

```
work[1] = rhs[1];
for(j=2; j<=ns-2; j++) {
  work[j] = rhs[j] - a[j]*work[j-1];
}
```

Code excerpt 15 uses forward elimination to solve the lower triangular system $Ly = R$, where $y$ is stored in the array work. As previously mentioned, the sub-diagonal elements of $L$ are given by $a[j]/u[j-1]$. The line

```
work[j] = rhs[j] - a[j]*work[j-1]/u[j-1];
```

is in fact equivalent to

```
[j] = rhs[j] - u[j]*work[j-1];
```

where $u[j], j=2,...,ns-2$ contains the sub-diagonal elements of $L$, if we had decided to allocate space for an extra array. We are now in position to solve the triangular system $Ux = y$ by back-substitution. The code to achieve this is given in Code excerpt 16. Here, the array work contains the computed values of $y$, the diagonal elements of $U$ are contained in the array $u$, and the upper diagonal elements of $U$ are contained in array $a$.

```
opt_vals[1] = work[ns-2]/u[ns-2];
for(j=ns-3; j>=1; j--)
  opt_vals[j] = work[j] - c[j]*opt_vals[j+1]/u[j];
```

Code excerpt 16 uses back-substitution to solve the upper triangular system $Ux = y$. At instant time $t_i = i\Delta t$, the elements of $x$ are the calculated option values $f_{i,j}=1,...,n_{s-2}$. In Code excerpt 16, the array opt\_vals contains the solution vector $x$. As its name suggests, the contents of the array opt\_vals are in fact the computed option values, $f_{i,j}=1,...,n_{s-2}$, in equation (5.4.28) represents the solution of the Black-Scholes partial differential equation at instant time $t_i = i\Delta t$, based on the previously computed option values $f_{i+1,j}=1,...,n_{s-2}$.

![](img/9db5fe198f8966da8d21f3e2bc886a_148.png)

**FIGURE 5.5** An example grid could be used to estimate the value of a vanilla option which matures in two-year time. The grid parameters are $n_s = n_t = 10, \Delta t = 0.2, \Delta S = 2.5$, and $S_{max} = 50$. The option parameters are $E = 25, S_0 = 0$, and $\tau = 2.0$. As we denote the grid node values by $f_{i,j}$, where $i$ is the time index and $j$ is the asset index. The option values of the grid nodes are $f_{10,j}, j = 0, \dots, 10$, where $val$ is the value of the option at the node; these are shown on the right-grid boundary. Since $E = 25$, only nodes with $j < 5$ have nonzero option values.

## Backwards Iteration and Early Exercise

The Black-Scholes equation can be solved over the time interval $t$ to $t + \tau$ by iteratively solving equation (5.4.28). We iterate backwards in time by solving equation (5.4.28) at the $i$-th time step and then using the computed values to solve equation (5.4.28) for the $(i-1)$-th time step. The option values at current time $t$ are obtained when time index $i = 0$. It can be seen that the grid method yields $n_{s-2}$ option values, $f_{0,j}, j = 1, \dots, n_{s-2}$, which corresponds to the current asset price

```
$S_0 = j\Delta S, \quad j = 1, \dots, n_{s-2}$.
```

As previously mentioned, the asset price $S_0$ coincides with grid index $j = n_1$. Therefore, $S_0 = S_0'$, and the option value for the current asset price $S_0$ is given by $f_{0,n_1}$.
