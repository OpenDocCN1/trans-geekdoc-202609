where

$$b_x = \frac{1}{4}[\sigma_{i,j,k} + \sigma_{i-1,j,k}] ,$$

$$b_y = \frac{1}{2}[\sigma_{i,j,k} + \sigma_{i,j-1,k}] ,$$

$$b_z = \frac{1}{2}[\sigma_{i,j,k} + \sigma_{i,j,k-1}] .$$

The operators $D_x$, $D_y$, and $D_z$ denote the first-order spatial derivative for $x$, $y$, and $z$, respectively. For example, the spatial-derivative operators along the $x$-axis, $D_x$, is evaluated as follows:

$$D_x g_{i,j,k} \approx \frac{1}{\Delta x} \sum_{m=1}^{M} c_m^{(M)} \left(g_{i+m-1/2,j,k} - g_{i-m+1/2,j,k}\right) .$$

Notice that the computation of $v_x$, for example, requires the specific volume at gridpoint $[i\Delta x, (j + \tfrac{1}{2})\Delta y, (k + \tfrac{1}{2})\Delta z]^T$. Unfortunately, the specific volume is not defined at this gridpoint. We took the arithmetic average of the specific volume at gridpoints $[(i - \tfrac{1}{2})\Delta x, (j + \tfrac{1}{2})\Delta y, (k + \tfrac{1}{2})\Delta z]^T$ and $[(i + \tfrac{1}{2})\Delta x, (j + \tfrac{1}{2})\Delta y, (k + \tfrac{1}{2})\Delta z]^T$ to obtain the specific volume at $[i\Delta x, (j + \tfrac{1}{2})\Delta y, (k + \tfrac{1}{2})\Delta z]^T$. We have denoted this specific-volume average as $b_x$. We use the same approach for the computations of $v_y$ and $v_z$ and end by introducing the arithmetic averages $b_y$ and $b_z$ for the specific volumes at $[(i + \tfrac{1}{2})\Delta x, j\Delta y, (k + \tfrac{1}{2})\Delta z]^T$ and $[(i + \tfrac{1}{2})\Delta x, (j + \tfrac{1}{2})\Delta y, k\Delta z]^T$, respectively. Notice also that the differential operators act only on the wavefield variables, not on the specific volume. Thus the differentiation of the medium parameters is not necessary in this scheme, and therefore the discontinuity of the specific volume is not modified by the differential operators.

Let us turn to the staggered-grid differentiation of the equations in (A.44). The idea that the results of the various differentiation operations in the staggered-grid technique are all naturally centered to coincide with the gridpoints and the quantities associated with the gridpoints does not work for some terms of equations (A.44). To add some concreteness to this point, let us consider the staggered-grid computation of $\tau_{xx}$; i.e.,

$$[\tau_{xx}]_{i+1/2,j+1/2,k+1/2}^{n+1} = [\tau_{xx}]_{i+1/2,j+1/2,k+1/2}^{n} = \Delta t \left[ C_{11} D_x v_x + C_{12} D_y v_y + c_{13} D_z v_z + C_{14} (D_z v_y + D_y v_z) + C_{15} (D_z v_x + D_x v_z) + C_{16} (D_y v_x + D_x v_y) + I_{xx} \right]_{i+1/2,j+1/2,k+1/2}^{n+1/2} . \quad (A.62)$$