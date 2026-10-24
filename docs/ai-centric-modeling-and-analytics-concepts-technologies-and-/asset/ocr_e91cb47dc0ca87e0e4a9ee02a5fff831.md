The preceding matrix can be represented as a block matrix in Equation 7.27:

$$B = \begin{pmatrix} B_{11} & B_{12} \\ B_{21} & B_{22} \end{pmatrix}\tag{7.27}$$

where Equation 7.28

$$B_{11}=(-2d_1 - \beta I - \mu)$$

$$B_{12}=\begin{pmatrix} \frac{\beta S I}{E} & 0 & \frac{\beta S I}{E} & 0 & 0 \end{pmatrix}$$

$$B_{21}=\begin{pmatrix} \frac{E'\mu}{I} \\ 0 \\ 0 \\ 0 \\ 0 \end{pmatrix}$$

$$B_{22}=\begin{pmatrix} -2d_1 - d_2 - \alpha - \beta I + \frac{E'}{E} - \frac{I'}{I} & 0 & 0 \\ \alpha & \frac{E'}{E} - \frac{I'}{I} -2d_1 - d_2 - \delta - \beta I & 0 \\ \beta I & 0 & \frac{E'}{E} - \frac{I'}{I} -(2d_1 + d_2 + \mu + \alpha) \\ 0 & \beta I & \alpha \\ 0 & 0 & 0 \\ 0 & 0 & 0 \\ 0 & -\beta S & 0 \\ 0 & 0 & 0 \\ \frac{E'}{E} - \frac{I'}{I} -(2d_1 + \mu + d_2 + \delta) & \beta S & 0 \\ \mu & \frac{E'}{E} - \frac{I'}{I} -(2d_1 + 2d_2 + \alpha + \delta) \end{pmatrix}\tag{7.28}$$

The Lozinskii measure of the matrix can be calculated as $\mu(B) \le \sup\{g_1, g_2\}$, where

$$g_1 = \mu(B_{11}) + |B_{12}| = -2d_1 - \beta I - \mu + \frac{\beta S I}{E}$$

$$g_2 = |B_{21}| + \mu(B_{22}) = -2d_1 + \mu + \frac{E'}{E} - \frac{I'}{I}\tag{7.29}$$