$B_t = \eta \tilde{F}_t \circ F_t + (1 - \eta) B_{t-1}, \quad B_1 = \tilde{F}_1 \circ F_1. \tag{9.28}$

Note that similar to the updated NCC, the filter with time index $t$ is applied to frame $t + 1$. In addition to unbounded growth in the expressions, a denominator close to zero can cause numerical issues. This problem has been addressed by regularization of the filter coefficients with penalizing their L2-norm (Henriques et al., 2012). This leads to the following ridge-regression problem:

$\min_{M} \sum_{t} \|F_t \circ \tilde{M} - C_t\|^2 + \lambda \|M\|^2. \tag{9.29}$

The solution is a minor modification of (9.23):

$\tilde{m} = \mathcal{F}^{-1} \left\{ \frac{\sum_t \tilde{C}_t \circ F_t}{\lambda + \sum_t \tilde{F}_t \circ F_t} \right\} \tag{9.30}$

and for the incremental case we only change (9.26) to

$\tilde{m}_t = \mathcal{F}^{-1} \left\{ \frac{A_t}{\lambda + B_t} \right\} \tag{9.31}$

and keep (9.27) and (9.28) unchanged.

# 9.3.2 Discriminative correlation filters

The MOSSE filter defined in the previous section acts directly on the image data. The derivations also assume that the image data is scalar-valued (single-channel) and the generalization to color images (multichannel) is nontrivial. Furthermore, we might want to use multiple features extracted from the image instead of, or in addition to, the pure image data. Also in this case, multichannel input data needs to be processed, which leads to a generalization of the (regularized) MOSSE filter: the discriminative correlation filter (DCF).

Note that for the definition of the DCF, we change notation to symbols commonly used in machine learning. Compared to the signal processing inspired notation in the MOSSE filter, we apply the following mappings: $f \mapsto x$ for the input data, $m \mapsto f$ for the filter, and $c \mapsto y$ for the target outputs (Danelljan et al., 2015). For input data with $d$ channels, we reformulate (9.29) as the minimization of the objective

$\varepsilon_t(f) = \sum_{k=1}^{t} \alpha_k \| S_f(x_k) - y_k \|^2 + \lambda \sum_{l=1}^{d} \| f^l \|^2 \tag{9.32}$

where we define the score function

$S_f(x) = \sum_{l=1}^{d} x^l \star f^l \tag{9.33}$