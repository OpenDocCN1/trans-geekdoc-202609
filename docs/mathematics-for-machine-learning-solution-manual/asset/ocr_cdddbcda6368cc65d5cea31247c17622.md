which yields the expected result.

b. Let us now choose both vectors differently to obtain the expected result. Let $x = \left[\frac{1}{\sqrt{x_1}}, \dots, \frac{1}{\sqrt{x_n}}\right]^\top$ and $y = \left[\sqrt{x_1}, \dots, \sqrt{n}\right]^\top$. Note that our choice is legal since all $x_i$ and $y_i$ are strictly positive. The Cauchy-Schwarz inequality now becomes

$$\left(\sum_{i=1}^n \frac{1}{\sqrt{x_i}} \cdot \sqrt{x_i}\right)^2 \leqslant \left(\sum_{i=1}^n \left(\frac{1}{\sqrt{x_i}}\right)^2\right) \cdot \left(\sum_{i=1}^n \sqrt{x_i}^2\right)$$

so that

$$n^2 \leqslant \left(\sum_{i=1}^n \frac{1}{x_i}\right) \cdot \left(\sum_{i=1}^n x_i\right).$$

This yields $n^2 \leqslant \sum_{i=1}^n \frac{1}{x_i} \cdot 1$, which gives the expected result.

# 3.10 Rotate the vectors

$$x_1 := \begin{bmatrix}2\\3\end{bmatrix}, \quad x_2 := \begin{bmatrix}0\\-1\end{bmatrix}$$

by $30^\circ$.

Since $30^\circ = \pi/6\ \text{rad}$ we obtain the rotation matrix

$$A = \begin{bmatrix}\cos\left(\frac{\pi}{6}\right) & -\sin\left(\frac{\pi}{6}\right)\\ \sin\left(\frac{\pi}{6}\right) & \cos\left(\frac{\pi}{6}\right)\end{bmatrix}$$

and the rotated vectors are
$$A x_1 = \begin{bmatrix}2\cos\left(\frac{\pi}{6}\right) - 3\sin\left(\frac{\pi}{6}\right)\\ 2\sin\left(\frac{\pi}{6}\right) + 3\cos\left(\frac{\pi}{6}\right)\end{bmatrix} \approx \begin{bmatrix}0.23\\3.60\end{bmatrix}$$
$$A x_2 = \begin{bmatrix}\sin\left(\frac{\pi}{6}\right)\\ -\cos\left(\frac{\pi}{6}\right)\end{bmatrix} \approx \begin{bmatrix}0.5\\0.87\end{bmatrix}.$$