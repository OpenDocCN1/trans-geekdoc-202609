# 140 CHAPTER | 5 Single Asset American Options

upper diagonal elements of U since they are known to be the same as the upper diagonal elements of the original matrix A and are contained in the array c, see, for example, Hager (1988).

Having the LU decomposition, we can now solve the lower triangular system $L_y = \mathcal{R}$ using forward elimination; this is shown in Code excerpt 5.15.

```
work[1] = rhs[1];
for(j=2; j<=ns-2; j++) {
  work[j] = rhs[j] - a[j]*work[j-1]/u[j-1];
}
```

Code excerpt 5.15 Computer uses forward elimination to solve the lower triangular system $L_y = \mathcal{R}$, where y is stored in the array work.

In Code excerpt 5.15, we make use of the following two arrays: the array rhs is used to store the elements of the right-hand side R, and the array work is both used as workspace and to store the computed solution vector y. As previously mentioned, the sub-diagonal elements of L are given by 1[j] = a[j]/u[j-1]. The line

```
work[j] = rhs[j] - a[j]*work[j-1]/u[j-1];
```

is in fact equivalent to

```
work[j] = rhs[j] - 1[j]*work[j-1];
```

where 1[j],j=2,...,ns-2 contains the sub-diagonal elements of L, if we had (needlessly) decide to allocate space for an extra array 1.

We are now in a position to solve the triangular system $Ux = y$ by back-substitution. The code to achieve this is given in Code excerpt 5.16. Here, the array work contains the previously computed values of y, the diagonal elements of U are contained in the array u, and (previously mentioned) the upper diagonal elements of U are contained in the array a.

```
opt_vals[1] = work[ns-2]/u[ns-2];
for(j=ns-3; j>=1; j--)
opt_vals[j] = work[j] - c[j]*opt_vals[j+1]/u[j];
```

Code excerpt 5.16 uses back-substitution to solve the upper triangular system $Ux = y$. At instant time $t_i = i\Delta t$, the elements of x are the calculated option values $f_i,i=1,...,ns-2$.

In Code excerpt 5.16, the array opt_vals contains the solution vector x. As its name suggests the contents of the array opt_vals are in fact the computed option values, $f_{i,j}=1,...,n_{s-2}$, in equation (5.4.28) represents the solution of the Black-Scholes partial differential equation at at instant time $t_i = i\Delta t$, based on the previously computed option values $f_{i+1,j}=1,...,ns-2$.