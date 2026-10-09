![](bbox=[0.15, 0.105, 0.505, 0.315])

Figure 2. Pixel matrix in the 3 × 3 neighborhood.

The luminance of any pixel is assumed to be weighted by the luminance of other pixels in the 3 × 3 neighborhood, and different pixel points correspond to the same weights as their neighborhoods. For all the different pixels, a function $f_k(\omega_1, \omega_2, \ldots, \omega_9)$ is constructed concerning the 9-pixel weights, as shown in Equation (1).

$f(\omega_1,\omega_2,\dots,\omega_9) = \sum_{i=1}^H\sum_{j=1}^W(\omega_1I_{i-1,j-1}+\omega_2I_{ij-1}+\omega_3I_{i+1,j-1}+\dots+\omega_9I_{i+1,j+1}-I_{ij})^2$ (1)

where $\omega_1,\omega_2,\dots,\omega_9$ is the weight of a pixel point with other pixels in its $3 \times 3$ neighborhood, $I_{i,j}$ denotes the brightness of a pixel with horizontal coordinate $i$ and vertical coordinate $j$ in the image pixel matrix, $H$ is the image pixel matrix height value, and $W$ is the width value of the image pixel matrix. According to the least squares criterion, the derivative function of any pixel weight $\omega_k$ of $f$ is 0, i.e., Equation (2) holds.

$\frac{\partial f(\omega_1,\omega_2,\dots,\omega_9)}{\partial\omega_k}=0$ (2)

Bringing all the weights into Equation (2) according to Equation (1), a linear system of equations on the pixel weights is obtained, as shown in Equation (3).

$\begin{cases}\begin{array}{c}\sum_{i=1}^H\sum_{j=1}^W(\omega_1I_{i-1,j-1}+\omega_2I_{ij-1}+\dots+\omega_9I_{i+1,j+1}-I_{i-1,j-1})\times I_{i-1,j-1}=0\\ \sum_{i=1}^H\sum_{j=1}^W(\omega_1I_{i-1,j-1}+\omega_2I_{ij-1}+\dots+\omega_9I_{i+1,j+1}-I_{ij-1})\times I_{ij-1}=0\\ \dots\\ \sum_{i=1}^H\sum_{j=1}^W(\omega_1I_{i-1,j-1}+\omega_2I_{ij-1}+\dots+\omega_9I_{i+1,j+1}-I_{i+1,j+1})\times I_{i+1,j+1}=0\\ \end{array}\end{cases}$ (3)

By solving Equation (3) through the Jacobi iteration method, the optimal solution of any pixel weight can be obtained, as shown in Equation (4):

$\omega_k^{(t)}=\frac{\sum_{i=1}^H\sum_{j=1}^W(I_{ij}\times(\omega_1^{(t-1)}I_{i-1,j-1}+\omega_2^{(t-1)}I_{ij-1}+\dots+\omega_9^{(t-1)}I_{i+1,j+1}))\times I_{ij}}{\sum_{i=1}^H\sum_{j=1}^W I_{ij}^2}-\omega_k^{(t-1)}$ (4)

where $k \in [1,9]$, and the superscript t denotes the number of iterations. Let Equation (5) hold constant for all pixels. We set an error value to determine the termination of the iteration. When the error value is less than 0.001, the image effect difference does not change much. To take into account the efficiency and the image quality, we set the error value to 0.001.

$|\omega_k^{(t)}-\omega_k^{(t-1)}|\le 0.001$ (5)