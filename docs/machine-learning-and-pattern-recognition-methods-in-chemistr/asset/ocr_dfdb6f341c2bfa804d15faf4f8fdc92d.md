Regardless of the dimension of the hyperplane, Null operator in MATLAB can be implemented to calculate the coordinates of the hyperplane.

Hence, $t_{aug}$ contains coefficients of the total hyperplane of all components in the row space of the augmented data, and $Z_{aug}$ is the coordination of any arbitrary point on a hyperplane:

```
$t_{aug} Z_{aug} = 0 \quad (7.15)$
```

Based on the duality concept, this hyperplane sets a point, $t_{aug} S_{aug}$ in the column space of the augmented data matrix. As a consequence, linear combination of columns of $U_{aug}$ with coordination of the point ($t_{aug} S_{aug}$), can generate $C_{aug}$.

```
$C_{aug} = t_{aug} S_{aug} U_{aug} \quad (7.16)$
```

By converting this column vector with $k$ parts to a matrix with $k$ columns, $C_{aug}$ can be calculated:

```
$C_{aug} = [C_{aug,1}, C_{aug,2}, ..., C_{aug,K}] \quad (7.17)$
```

Due to the trilinear nature of $C_{aug}$, second eigenvalue of the metricized $C_{aug}$ should be zero. Non-zero value for the singular value shows the non-linearity of the $C_{aug}$. In summary, the calculated $c_1$ (based on $l_1$) is projected to the column space of all sub-matrices and complementary subspace is calculated based on these projections. Trilinear constraint, which works based on the proportionality property, can produce the unique solution. If $c_1$ belongs to the column space of all sub-matrices, the second eigenvalue of $C_{aug}$ should be close to zero; otherwise, $c_1$ does not belong to all sub-matrices.

# 4. Nonexistence information

Information on the absence of a chemical species in part of the presence region of components is introduced by several constraints in literature, and this information is used to reduce the range of feasible solutions. Dataset analysis, chemical information related to the presence/absence of each component in the matrices aligning together is considered as the correspondence of species (Abdullahi & Sajjadi, 2010). It can be said that applying this constraint is, in fact, equivalent to applying a zero concentration region for species not present in each data matrix (Tavakkoli et al., 2018).