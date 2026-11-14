![](bbox=[0.17, 0.09, 0.76, 0.33])

Fig. 8.2: The 1D ramp filter is a central slice of the 2D ramp filter.

# 8.4.2 Landweber algorithm: FBP with view-based noise weighting

One of the most important reasons to use an iterative algorithm is to incorporate the noise model during image reconstruction. This section considers a simplified case: the noise weighting is view-based. In other words, the weighting factors for all rays at a particular view are the same.

If the initial image is zero, the closed-form Landweber algorithm is

$$X^{(k)} = (A^T W A)^{-1}[I - (I - \alpha A^T W A)^k]A^T W P.$$ (8.15)

If the noise weighting is view-based, matrix W is block-diagonal. Each block corresponds to all the rays in a view. Within each block the diagonal elements are identical.

It is not easy to see what matrix W is doing in $A^T W A$. However, a central slice at a particular angle of $A^T W A$ is simply $|\omega|$ multiplied by a scalar $w_m$, where m is the view index. Thus, the windowed ramp filter at the mth view is given as

$$\frac{|\omega|}{w_m} \left[ 1 - \left( 1 - \frac{\alpha w_m}{|\omega|} \right)^k \right].$$ (8.16)

In eq. (8.15), $A^T W P$ is weighted backprojection of the projections P. At the mth view, all the projections are first multiplied by the scalar $w_m$ and then are backprojected to the image domain. In fact, at the mth view, the projection data multiplier $w_m$ cancels the $w_m$ in the first part $|\omega|/w_m$ of eq. (8.16). The net result is that for view-based noise weighting eq. (8.15) is equivalent to