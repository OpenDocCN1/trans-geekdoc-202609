+   1. High probability and low probability marking of real edge point and non-edge points.
+   2. The points marked should be as close as to the centre of true edge.
+   3. It should be only one response to a single edge.

# # 11.2.3.1.1 Working Mechanism

The Canny edge detection algorithm's process can be divided into five steps shown in Figure 11.9:

+   - Smooth the image with a Gaussian filter to remove the noise.
+   - Find the image's intensity gradients.
+   - To eliminate spurious response to edge detection, use gradient magnitude thresholding or lower bound cut-off suppression.
+   - To identify potential edges, use a double threshold.
+   - Hysteresis track edge: Finish edge detection by suppressing all other weak edges that are not connected to strong edges.

# ## 11.2.3.1.1.1 GAUSSIAN FILTER

It is necessary to remove noise in the image done by gaussian filter. Gaussian filter kernel is used to smoothen the image. The equation (2k+1)x(2k+1) is computed by,

```
$$H_{ij} = \frac{1}{2\pi\sigma^2} \exp \left( - \frac{(i-(k+1))^2 + (j-(k+1))^2}{2\sigma^2} \right); 1 \le i, j \le (2k+1)$$
```

5 x 5 Gaussian filter is used to generate adjacent images with \(\infty=1\).

```
$$\mathbf{B} = \frac{1}{159} \begin{bmatrix} 2 & 4 & 5 & 4 & 2 \\ 4 & 9 & 12 & 9 & 4 \\ 5 & 12 & 15 & 12 & 5 \\ 4 & 9 & 12 & 9 & 4 \\ 2 & 4 & 5 & 4 & 2 \end{bmatrix} * \mathbf{A}.$$
```

![](bbox=[0.178, 0.763, 0.882, 0.896])

Figure 11.9 Steps in canny algorithm.