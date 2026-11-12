# # TABLE 1.2 (Continued)
Different Operations That Can Be Implemented Using the MATLAB® Function bwmorph

| Operation | Description |
|---|---|
| thin | Reduce objects without holes to lines and with holes to rings |
| tophat | Performs the bottom-hat operation using a reference structure of size 3 × 3. This function uses imbothat to perform the operation |

![](bbox=[0.136, 0.635, 0.863, 0.745])

**FIGURE 1.27**
Neighborhood criteria between pixels. (a) 4-Connected neighborhood, (b) 8-connected neighborhood, and (c) diagonally connected.

the 4-connected neighborhood), these diagonal elements include (P1), (P3),
(P6), and (P8). Figure 1.27c shows the diagonal connectivity.

The neighborhood criterion has a great implication for the result of the
detected objects in the image. Figure 1.28 illustrates the difference in object
labeling depending on the neighborhood criterion. Figure 1.28a shows the