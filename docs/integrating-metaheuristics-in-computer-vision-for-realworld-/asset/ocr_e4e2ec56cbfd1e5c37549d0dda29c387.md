![](bbox=[0.22, 0.09, 0.83, 0.26])

Figure 11.2 Block diagram-sobel edge detector block diagram.

| -1 | 0 | +1 |
|---|---|---|
| -2 | 0 | +2 |
| -1 | 0 | +1 |

| +1 | +2 | +1 |
|---|---|---|
| 0 | 0 | 0 |
| -1 | -2 | -1 |

Figure 11.3 Sobel convolution kernels.

+   * Thresholding
+   * Finally, Edge detection

# 11.2.2.1.2 Working Mechanism

The operator consists of 3 x 3 convolution kernels shown in Figure 11.3. These kernels are optimized to respond to edges that run both vertically and horizontally relevant to the pixel grid. Each perpendicular orientation requires one kernel. The kernels can be applied to the input image separately to produce measurements of the gradient component in each orientation (call these Gx and Gy) [5]. These can then be combined to determine the absolute magnitude and orientation of the gradient at each point.

The magnitude of the gradient is given by

```
|G| = \sqrt{Gx^2 + Gy^2}
```

Approximately, magnitude is calculated by

```
|G| = |Gx| + |Gy|, Which is fast to compute.
```

The orientation of the edge with respect to angle relative to pixel grid of the spatial gradient is computed by,

```
\theta = \arctan (Gy/Gx)
```

Here, the direction of maximum contrast from black to white on the image is taken to be the mean of orientation \theta, and other angles are measured anticlockwise from this. Using