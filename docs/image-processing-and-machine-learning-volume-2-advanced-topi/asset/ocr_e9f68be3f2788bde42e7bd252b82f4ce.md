![](bbox=[0.2, 0.1, 0.78, 0.56])

**FIGURE 3.19** (a) Kernel of cubic interpolation and (b) difference between cubic kernel and $Sinc(x, y)$ in the form of $Sinc(x, y) - W_{cubic}(x, y)$.

# ## 3.4 Aliases

As discussed throughout this chapter, a geometric transformation is essentially performed in three steps:

+   1. For each one of the coordinates of the transformed image $(x', y')$, its corresponding coordinates in the original image $(x, y)$ are obtained by means of the inverse of the transformed $T^{-1}(x, y)$.
+   
+   2. From the transformed image, the values are interpolated by using one of the previously seen kernels, with the aim of reconstructing the image.