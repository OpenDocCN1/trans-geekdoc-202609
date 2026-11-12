Then, Gx is calculated by the following equation:

\( G_x = \frac{\partial f}{\partial x}(x, y) = (a_7 + a_8 + a_9) - (a_1 + a_2 + a_3) \)

And Gy can be given as follows:

\( G_y = \frac{\partial f}{\partial y}(x, y) = (a_3 + a_6 + a_9) - (a_1 + a_4 + a_7) \)

# Example 4.4: Prewitt filter for vertical edge detection

The Prewitt filter (kernel) used to detect the vertical edges of the image is a 3*3 filter given as follows:

| 1 | 0 | -1 |
|---|---|---|
| 1 | 0 | -1 |
| 1 | 0 | -1 |

When we apply the preceding filter to an input image, it works as the first-order derivative and computes the difference in intensities of the pixel in a particular region.

Suppose we have a Grayscale image of size 6*6 represented as follows:

| 3 | 0 | 1 | 2 | 7 | 4 |
|---|---|---|---|---|---|
| 1 | 5 | 8 | 9 | 3 | 1 |
| 2 | 7 | 2 | 5 | 1 | 3 |
| 0 | 1 | 3 | 1 | 7 | 8 |
| 4 | 2 | 1 | 6 | 2 | 8 |
| 2 | 4 | 5 | 2 | 3 | 9 |

The filter (kernel) used to detect the vertical edges of the image is a 3*3 filter given as follows.

| 1 | 0 | -1 |
|---|---|---|
| 1 | 0 | -1 |
| 1 | 0 | -1 |

So, to obtain the vertical edges of the image, we have to convolve the image pixel matrix with the above 3*3 filter as follows:

![](bbox=[0.335, 0.8, 0.665, 0.915])