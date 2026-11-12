However, as in the one-dimensional case, the kernels required for this ideal interpolation mean that in practice they cannot be carried out, so other alternatives must be considered. These alternatives include some of the interpolation approaches discussed in the one-dimensional case and include the following methods: nearest neighbors, bilinear, and bicubic interpolation [8].

# ## 3.3.3.1 Nearest Neighbor Interpolation Method

For the interpolation of a certain point $(x_0, y_0)$, the coordinates of the pixel $(u_0, v_0)$ that is closest to it are assigned; in many cases, to carry out this method, it is enough to apply a rounding to the coordinates obtained by the geometric transformation.

This is:

```
$I(x_0, y_0) = I(u_0, v_0)$
```

where

```
$u_0 = round(x_0)$
$v_0 = round(y_0)$
(3.49)
```

# ## 3.3.3.2 Bilinear Interpolation

What linear interpolation represents for the one-dimensional case, bilinear interpolation represents for the two-dimensional or image case. To explain the operation of this type of interpolation, the illustration shown in Figure 3.18 will be used. Where each of the neighboring pixels to $(x_0, y_0)$ are defined as:

![](bbox=[0.345, 0.68, 0.655, 0.825])

**FIGURE 3.18** Bilinear interpolation. The interpolation of point G at position $(x_0, y_0)$ is produced in two steps considering the neighboring pixels defined at points A, B, C, and D. First through linear interpolation, points E and F are obtained considering the distance between the point to be interpolated and the adjoining pixel $a = (x_0 - u_0)$, then the vertical interpolation is performed, obtaining the intermediate points between E and F by means of the distance $b = (y_0 - v_0)$.