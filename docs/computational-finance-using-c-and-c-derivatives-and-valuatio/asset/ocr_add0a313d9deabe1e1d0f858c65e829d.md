# CHAPTER | 3 Generation of Random Variates

$B_{i,1}^T = \cos(\theta_{i,1}),\nB_{i,j}^T = \cos(\theta_{i,j}) \sin^{j-1}(\theta_{i,k}) \quad j=2,\dots,n-1,\nB_{i,n}^T = \sin^{n-1}(\theta_{i,k}), \quad n>1,$

```
$B^T = \begin{pmatrix} \cos(\theta_{1,1}) & \sin(\theta_{1,1}) & \cos(\theta_{1,2}) & \sin(\theta_{1,1}) & \sin(\theta_{1,2}) & \cos(\theta_{1,3}) \ \cos(\theta_{2,1}) & \sin(\theta_{2,1}) & \cos(\theta_{2,2}) & \sin(\theta_{2,2}) & \sin(\theta_{2,2}) & \cos(\theta_{2,3}) \ \cos(\theta_{3,1}) & \sin(\theta_{3,1}) & \cos(\theta_{3,2}) & \sin(\theta_{3,1}) & \sin(\theta_{3,2}) & \cos(\theta_{3,3}) \ \vdots & \vdots & \vdots & \vdots & \vdots & \vdots \end{pmatrix}$
```

It can be seen that the diagonal elements of $B^T$ are

```
$(B^T B)_{i,i} = \sum_{k=1}^n (x_{i,k})^2 = 1.$
```

The Cholesky decomposition can be formed by setting the angles of the upper triangular elements of $B^T$ to zero, and this results in

```
$L^T = \begin{pmatrix} 1 & 0 & 0 & \dots & \dots & \dots \ \cos(\theta_{2,1}) & \sin(\theta_{2,1}) & 0 & \dots & \dots & \dots \ \cos(\theta_{3,1}) & \sin(\theta_{3,1}) & \cos(\theta_{3,2}) & \sin(\theta_{3,1}) & \sin(\theta_{3,2}) & \dots \ \vdots & \vdots & \vdots & \vdots & \vdots & \vdots \ \vdots & \vdots & \vdots & \vdots & \vdots & \vdots \end{pmatrix}$
```

$L_{1,1}^T = 1,\nL_{i,1}^T = \cos(\theta_{i,1}),\nL_{i,j}^T = \cos(\theta_{i,j}) \sin^{j-1}(\theta_{i,k}), \quad j=2,\dots,i-1,\nL_{i,j}^T = \sin^{i-1}(\theta_{i,k}), \quad i>1,\nL_{i,j}^T = 0, \quad j=i+1,\dots,n.$

We want to find the positive definite matrix $C_r^*$ which minimizes $||C_r - C_r^*||$.
This can be found by writing

```
$C_r^* = L^T L$.
```