\(\begin{bmatrix} Y(x, y) \\ U(x, y) \\ V(x, y) \end{bmatrix} = \begin{bmatrix} 0.299 & 0.587 & 0.114 \\ -0.147 & -0.289 & 0.436 \\ 0.615 & -0.515 & -0.100 \end{bmatrix} \begin{bmatrix} R(x, y) \\ G(x, y) \\ B(x, y) \end{bmatrix}\) (2.30)

The transformation from YUV to RGB can be obtained through the inversion of the matrix defined in Equation 2.30, producing the following model:

\(\begin{bmatrix} R(x, y) \\ G(x, y) \\ B(x, y) \end{bmatrix} = \begin{bmatrix} 1.000 & 0.000 & 1.140 \\ 1.000 & -0.395 & -0.581 \\ 1.000 & 2.032 & 0.000 \end{bmatrix} \begin{bmatrix} Y(x, y) \\ U(x, y) \\ V(x, y) \end{bmatrix}\) (2.31)

# 2.4.2 The YIQ Model

A variant of the YUV system is the YIQ system, where \(I\) implies the phase and \(Q\) the quadrature. The values of \(I\) and \(Q\) are derived from the values of \(U\) and \(V\), applying a geometric transformation, where the \(U\) and \(V\) planes are rotated 33° and mirror-inverted. This is defined as follows:

\(\begin{bmatrix} I(x, y) \\ Q(x, y) \end{bmatrix} = \begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix} \begin{bmatrix} \cos \beta & \sin \beta \\ -\sin \beta & \cos \beta \end{bmatrix} \begin{bmatrix} U(x, y) \\ V(x, y) \end{bmatrix}\) (2.32)

where \(\beta = 0.576\) (33). The component represents the same value as the one defined in the YUV model. This YIQ model is better compared to the bandwidth needed for YUV color rendering. However, its use was practically eliminated by the YUV model.

# 2.4.3 The YCbCr Model

The YCbCr color space is a variant of the YUV model used as a standard for color coding in digital television. The chromatic components are similar to their \(U\) and \(V\) counterparts. That is, they are conceived as differences between the luminance value and the \(R\) and \(B\) color planes. However, unlike the \(U\) and \(V\) planes, different factors are used that affect the existing difference. The equations used to calculate this color model are the following:

\(Y(x, y) = w_R R(x,y) + (1 - w_B - w_R) G(x,y) + w_B B(x,y)\)

\(C_b = \frac{0.5}{1 - w_B}(B(x,y) - Y(x,y))\) (2.33)

\(C_r = \frac{0.5}{1 - w_R}(R(x,y) - Y(x,y))\)