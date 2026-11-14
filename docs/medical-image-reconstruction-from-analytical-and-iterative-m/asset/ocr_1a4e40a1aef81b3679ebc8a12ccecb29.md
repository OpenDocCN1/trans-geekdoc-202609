![](bbox=[0.095, 0.095, 0.85, 0.455])

Fig. 1.12: Coordinate systems for 2D parallel-beam imaging.

\[ B = A^T P = \begin{bmatrix} 1 & 0 & 1 & 0 \\ 0 & 1 & 0 & 1 \\ 1 & 1 & 0 & 0 \\ 0 & 0 & 1 & 1 \end{bmatrix}^T \begin{bmatrix} 7 \\ 2 \\ 5 \\ 4 \end{bmatrix} = \begin{bmatrix} 1 & 0 & 1 & 0 \\ 0 & 1 & 1 & 1 \\ 1 & 0 & 0 & 1 \\ 0 & 1 & 0 & 1 \end{bmatrix} \begin{bmatrix} 7 \\ 2 \\ 5 \\ 4 \end{bmatrix} = \begin{bmatrix} 12 \\ 7 \\ 11 \\ 6 \end{bmatrix} \, , \]
(1.14)

which is the same as the result obtained “graphically” in Figure 1.11.

For the continuous case, the backprojection image \( b(x, y) \) can be expressed in the following equivalent ways:

\( b(x, y) = \int_0^\pi p(s, \theta)|_{s = x \cos \theta + y \sin \theta} \, d \theta, \) \qquad (1.15)
\( b(x, y) = \int_0^\pi p(s, \theta)|_{s = \overline{x}, \overline{\theta}} \, d \theta, \) \qquad (1.16)
\( b(x, y) = \int_0^\pi p\left( \overline{x}, \overline{\theta}, \theta \right) \, d \theta, \) \qquad (1.17)