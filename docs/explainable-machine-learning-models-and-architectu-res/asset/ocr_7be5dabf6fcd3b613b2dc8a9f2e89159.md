# ## 2.2 Traditional Image Recognition Algorithms

Traditional image recognition algorithms consist of a detector and descriptor vector. Before assigning an invariant descriptor or feature to each region, they first identify places of interest in the compared pictures and choose a region surrounding each one. Thus, by matching the descriptors, correspondences can be found. It is best if detectors and descriptors are as invariant as feasible [3].

# ### 2.2.1 Harris Corner Detector (1988)

It is a mathematical approach to extracting corners in an image and deducing features in an image. This was first introduced in 1988 and since then it has been used in many algorithms. Determining corners is done by calculating the change in intensity of an image. It is calculated using the eq below which is derived using the Taylor function for the 2D equation.

```
E(u,v) = \sum_{x,y} w(x,y) \left[ I(x+u, y+v) - I(x,y) \right]^2 \qquad (2.1)
```

Where the term I x + u, y + v represents the shifted/new intensity and the shift is u and v and I u, v represents the original intensity. The above equation can be rewritten in the matrix form as follows,

```
E(u,v) \approx \begin{bmatrix} u & v \end{bmatrix} M \begin{bmatrix} u \\ v \end{bmatrix} \qquad (2.2)
```

Where the M in the above equation is

```
M = \sum_{x,y} w(x,y) \begin{bmatrix} I_x I_x & I_x I_y \\ I_x I_y & I_y I_y \end{bmatrix} \qquad (2.3)
```