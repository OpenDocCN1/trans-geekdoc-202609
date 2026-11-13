\(\sigma_\mathrm{B}^2 = \omega_0(\mu_0 - \mu_\mathrm{T})^2 + \omega_1(\mu_1 - \mu_\mathrm{T})^2 = \omega_0\omega_1(\mu_1 - \mu_0)^2,\)

(2.81)

with the class mean levels

\(\mu_0(t) = \sum_{i=0}^{t-1} \frac{ip_i}{\omega_0(t)} \text{ and } \mu_1(t) = \sum_{i=t}^{L-1} \frac{ip_i}{\omega_1(t)} \text{ and } \mu_\mathrm{T} = \mu(L) = \sum_{i=0}^{L-1} ip_i.\)

(2.82)

Finally, the optimal threshold t is found by either maximizing the between-class variance or minimizing the within-class variance:

\(t = \arg \left\{ \max_{0 \le t \le L-1} \{ \sigma_\mathrm{B}^2(t) \} \right\} = \arg \left\{ \min_{0 \le t \le L-1} \{ \sigma_\mathrm{W}^2(t) \} \right\} [47, 165].\)

(2.83)

Another automatic thresholding procedure is the _moment-preserving threshold_ by Tsai [48]. Thereby, a threshold value is selected so that the first three moments of image _i_ in the resulting binarized image _o_ are preserved. The moments of _i_ are defined by

\(m_i = \frac{1}{n} \sum_j n_j(z_j)^i = \sum_j p_j(z_j)^i,\)

(2.84)

with _n_ being the entire amount of pixels of image _i_, _nj_ being the total number of pixels in _i_ with the gray value _zj_ and \(p_j = \frac{n_j}{n}\). After having applied the threshold and binarized the image, the first three moments of _o_ can be computed in the following way: