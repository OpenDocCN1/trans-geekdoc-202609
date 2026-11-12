![](bbox=[0.11, 0.11, 0.89, 0.4])

**FIGURE 3.8** Projective transformation between any two polygons of four points. This type of transformation is performed using a two-step method; the first involves an inverse transformation \(A_1^{-1}\) from polygon \(P_1\) to unit square \(C_1\), while the second involves a direct transformation \(A_2\) from unit square \(C_1\) to polygon \(P_2\), in such a way that the complete transformation is characterized by \(A = A_2 \cdot A_1^{-1}\).

As already mentioned in this section, through the inversion of matrix \(A\), the inverse transformation \(T^{-1}\) can be calculated, which in this case would mean obtaining the unit square from any polygon of four points.

As Figure 3.8 shows, the transformation from any four-point polygon \(P_1\) to any other four-point polygon \(P_2\) can be performed using a two-step transformation performed on the unit frame. This can be expressed as follows:

```
\(P_1 \xrightarrow{T_1^{-1}} C_1 \xrightarrow{T_2} P_2\) (3.25)
```

The operations \(T_1\) and \(T_2\) for the transformation from the unit square to each of the four-point polygons are obtained from the points that define them \(x_i\) and \(x'_i\) using the expressions defined in Equation 3.24, while the inverse transformation \(T_1^{-1}\) is obtained by calculating the matrix \(A_1\). The complete transformation \(T\) is finally produced through the coupling of the transformations \(T_1^{-1}\) and \(T_2\), in such a way that:

```
\(x' = T(x) = T_2 \left( T_1^{-1}(x) \right)\) (3.26)
```

Or in matrix form:

```
\(x' = A \cdot x = A_1 \cdot A_2 \cdot x\) (3.27)
```