\( A = I(u_0, v_0) \qquad B = I(u_0 + 1, v_0) \)
\( C = I(u_0, v_0 + 1) \qquad C = I(u_0 + 1, v_0 + 1) \)

To obtain the value \((x_0, y_0)\), two different linear interpolations are obtained that are established on the points \(E\) and \(F\) from the distance \(a = (x_0 - u_0)\) that is established between the point and the nearest neighbor. These values, when calculated from a linear interpolation, are defined as:

\( E = A + (x_0 - u_0) \cdot (B - A) = A + a \cdot (B - A) \)
\( F = C + (x_0 - u_0) \cdot (D - C) = C + a \cdot (D - C) \)

From the previous values, the interpolation for point \(G\) is obtained considering the vertical distance \(b = (y_0 - v_0)\), such that:

\(\hat{I}(x_0, y_0) = G = E + (y_0 - u_0) \cdot (F - E) = E + b \cdot (F - E) \)
\( = (a - 1)(b - 1)A + a(b - 1)B + (1 - a)bC + abD \)

Just as the linear convolution kernel was formulated, the two-dimensional bilinear interpolation kernel \(W_{bilinear}(x, y)\) can also be defined. This will be the product of two one-dimensional kernels \(w_{bilinear}(x)\) and \(w_{bilinear}(y)\). Performing this multiplication is obtained as follows:

\( W_{bilinear}(x, y) = \tau_{bilinear}(x) \cdot \tau_{bilinear}(y) \)
\( W_{bilinear}(x, y) = \begin{cases} 1 - x - y - xy & \text{si } 0 \le |x|, |y| < 1 \\ 0 & \text{if not} \end{cases} \)

# ## 3.3.3.3 Bicubic Interpolation

As in the previous section, the bicubic interpolation kernel \(W_{bicubic}(x, y)\) can be obtained from the multiplication of the one-dimensional kernels \(W_{bicubic}(x)\) and \(w_{bicubic}(y)\), that is:

\( W_{bicubic}(x, y) = w_{bicubic}(x) \cdot w_{bicubic}(y) \)

The one-dimensional cubic kernels used in multiplication (3.51) are defined in Equation 3.47. The bicubic kernel of Equation 3.54 is shown in Figure 3.19a, while Figure 3.19b shows the arithmetic difference between the bicubic kernel and that of the \(Sinc(x, y)\) function.