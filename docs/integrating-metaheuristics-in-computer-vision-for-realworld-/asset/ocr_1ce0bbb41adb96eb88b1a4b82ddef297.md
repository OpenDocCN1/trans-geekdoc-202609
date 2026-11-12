$F(\boldsymbol{\phi})=d^2(\boldsymbol{\phi})=\sum_{p=0}^{p_{\max }} \sum_{q=-p}^{p} \frac{\pi}{p+1}\left|Z_{p q}-Z^{\prime}_{pq} e^{jq \boldsymbol{\phi}}\right|^2$ (7.7)

If two images are similar, that is one image is rotated version of the other, then \(d^2(\phi) = 0\). If the two images are different, then \(d^2(\phi)\) is expected to assume a high value. After simplification, Eq. (7.7) becomes [35].

\(F(\boldsymbol{\phi})=\sum_{p=0}^{p_{\max }} \sum_{q=-p}^{p} \frac{\pi}{p+1}\left[\left|Z_{p q}\right|^2+\left|Z^{\prime}_{pq}\right|^2-2\left|Z_{p q} Z_{p q}^r\right| . \cos (q \boldsymbol{\phi}+\boldsymbol{\phi}_{pq}^r-\boldsymbol{\phi}_{p q})\right].\) (7.8)

The minimum of \(F(\phi)\) lies in one of the intervals, \([\phi_n, \phi_{n+1}]\), where \(\phi_{_n}=n \pi / 2 p_{max}, 0 \le n < 4p_{max}\). The method is simplified by finding the zeros of the following function:

\(F'(\boldsymbol{\phi})=0=\sum_{p=0}^{p_{\max }} \sum_{q=-p}^{p} \frac{2 \pi q}{p+1}\left|Z_{p q} Z_{p q}^r\right| \sin (q \boldsymbol{\phi}+\boldsymbol{\phi}_{p q}^r-\boldsymbol{\phi}_{p q})\) (7.9)

Therefore, after computing rotation angle \(\phi\) and making phase correction using Eq. (7.4) the phase coefficients are made rotation invariant and they are used as features along with magnitudes in the proposed approach. However, ZMs are computation intensive. The time complexity of ZMs is of the order \(O(N^2 p_{max}^3)\), if moments are computed up to order \(p_{max}\) (where \(p_{max}\) is the maximum order) over an image of size \(N \times N\) pixels. The order \(O(N^2 p_{max}^3)\) is very large when both \(N\) and \(p_{max}\) are large. For speeding up the computation of ZMs, we employ \(q - recursive\) method proposed by Chong et al. [38] and extended by Singh et al. [37].

# 7.3.1.1 Recurrence Relation for Radial Polynomials \(R_{pq}(r)\) [38, 39]

The following recursive steps reduce the time complexity of Zernike polynomials

+   I. \(R_{pp}(r) = r^p\)  
+   II. \(R_{p,p-2}(r) = p r^p - (p-1)r^{p-2}\)  
+   III. \(R_{pq}(r) = K_1 R_{p,q+4}(r) + \left(K_2 + \frac{K_3}{r^2}\right) R_{p,q+2}(r), q = p - 4, p - 6, ..., 1 (\text{or } 0),\)  
+   (7.10)