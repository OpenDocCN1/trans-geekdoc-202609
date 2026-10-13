
### 4. 6.22

生成一个 `150 × 90` 矩阵 `X`，其元素服从高斯分布 `𝒩(0, 1)`。生成向量 `θ[o] ∈ ℝ^(90)`。该向量的各分量也是独立同分布（i.i.d.）获得的，同样通过高斯分布 `𝒩(0, 1)` 获得。计算向量 `y = X θ[o]`。向 `y` 添加一个 `90 × 1` 的噪声向量 `η`，以生成 `ỹ = y + η`。`η` 的元素通过高斯分布 `𝒩(0, 0.01)` 生成。随后，添加一个 `150 × 90` 的噪声矩阵 `E`，以产生 `X̃ = X + E`；`E` 的元素根据高斯分布 `𝒩(0, 0.2)` 生成。通过使用公式 [(6.5)](#Chp006_249-291_B9780443292385000123.xhtml#deq12) 计算最小二乘（LS）估计：
(a) 使用真实输入矩阵 `X` 和带噪输出 `ỹ`；
(b) 使用带噪输入矩阵 `X̃` 和带噪输出 `ỹ`。

### 5.

随后，通过使用公式 [(6.69)](#Chp006_249-291_B9780443292385000123.xhtml#deq153) 计算总体最小二乘（TLS）估计，使用带噪输入矩阵 `X̃` 和带噪输出 `ỹ`。

### 6.

重复实验多次，计算前三种情况下获得的估计值与真实参数向量 `θ[o]` 之间的平均欧氏距离。

### 7.

尝试不同的噪声水平并对结果进行评论。

## 参考文献

*   [1] R.J. Adcock, Note on the method of least-squares, *Analyst* 1877;4(6):183–184.
*   [2] J.A. Apolinario Jr., ed. *QRD-RLS Adaptive Filtering*. New York: Springer; 2009.
*   [3] K. Berberidis, S. Theodoridis, Efficient symmetric algorithms for the modified covariance method for autoregressive spectral analysis, *IEEE Trans. Signal Process.* 1993;41:43.
*   [4] A. Bertrand, M. Moonen, Consensus-based distributed total least-squares estimation in ad hoc wireless sensor networks, *IEEE Trans. Signal Process.* 2011;59(5):2320–2330.
*   [5] J.L. Botto, G.V. Moustakides, Stabilizing the fast Kalman algorithms, *IEEE Trans. Acoust. Speech Signal Process.* 1989;37:1344–1348.
*   [6] S. Boyd, L. Vandenberghe, *Convex Optimization*. Cambridge University Press; 2004.
*   [7] G. Carayannis, D. Manolakis, N. Kalouptsidis, A fast sequential algorithm for least-squares filtering and prediction, *IEEE Trans. Acoust. Speech Signal Process.* 1983;31:1394–1402.
*   [8] F.S. Cattivelli, C.G. Lopes, A.H. Sayed, Diffusion recursive least-squares for distributed estimation over adaptive networks, *IEEE Trans. Signal Process.* 2008;56(5):1865–1877.
*   [9] J.M. Cioffi, T. Kailath, Fast recursive-least-squares transversal filters for adaptive filtering, *IEEE Trans. Acoust. Speech Signal Process.* 1984;32:304–337.
*   [10] J.M. Cioffi, The fast adaptive ROTOR's RLS algorithm, *IEEE Trans. Acoust. Speech Signal Process.* 1990;38:631–653.
*   [11] M.H. Costa, J.C.M. Bermudez, An improved model for the normalized LMS algorithm with Gaussian inputs and large number of coefficients, *Proceedings, IEEE Conference in Acoustics Speech and Signal Processing*. 2002:1385–1388.
*   [12] C.E. Davila, An efficient recursive total least-squares algorithm for FIR adaptive filtering, *IEEE Trans. Signal Process.* 1994;42:268–280.
*   [13] W.E. Deming, *Statistical Adjustment of Data*. J. Wiley and Sons; 1943.
*   [14] P.S.R. Diniz, M.L.R. De Campos, A. Antoniou, Analysis of LMS-Newton adaptive filtering algorithms with variable convergence factor, *IEEE Trans. Signal Process.* 1995;43:617–627.
*   [15] P.S.R. Diniz, *Adaptive Filtering: Algorithms and Practical Implementation*. third ed. Springer; 2008.
*   [16] Y.C. Eldar, Minimax MSE estimation of deterministic parameters with noise covariance uncertainties, *IEEE Trans. Signal Process.* 2006;54:138–145.
*   [17] B. Farhang-Boroujeny, *Adaptive Filters: Theory and Applications*. NY: J. Wiley; 1999.
