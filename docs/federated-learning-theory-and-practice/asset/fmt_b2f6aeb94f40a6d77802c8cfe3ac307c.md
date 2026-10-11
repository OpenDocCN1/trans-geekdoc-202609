
$h(\sigma) = \sqrt{2(e^{\sigma^{- 2}}\Phi(\frac{3\sigma^{- 1}}{2}) + 3\Phi( - \frac{\sigma^{- 1}}{2}) - 2)} = \sigma^{- 1} \cdot \sqrt{1 + \frac{15}{8}\frac{\sigma^{- 1}}{\sqrt{2\pi}} + O(\sigma^{- 2})}.$

![Image](OEBPS/images/B9780443190377000090/si237_u1.png)

This shows that for ‘large *N* and *E*’ DP-SGD is approximately *G*[$\mu$]![Image](OEBPS/images/B9780443190377000090/si56_u9.png)\-DP with $\mu = \sqrt{mE/(N\sigma^{2})}$![Image](OEBPS/images/B9780443190377000090/si238_u1.png). Notice that *σ* cannot be too small otherwise *h*(*σ*)![Image](OEBPS/images/B9780443190377000090/si62_u9.png) behaves like $\sqrt{2} \cdot e^{1/(2\sigma^{2})}$![Image](OEBPS/images/B9780443190377000090/si239.png) which yields a very weak DP guarantee.

Clearly, a weaker (than $\mathcal{A}_{adv}$![Image](OEBPS/images/B9780443190377000090/si214_u1.png)) adversary with less capability (less knowledge of the used randomness by Sample[$m$]![Image](OEBPS/images/B9780443190377000090/si216_u1.png) and $\mathcal{M}$![Image](OEBPS/images/B9780443190377000090/si72_u7.png)) achieves a trade-off function $\ge C_{m/N}(G[\sigma^{-1}])^{\otimes T}$![Image](OEBPS/images/B9780443190377000090/si240.png) closer to the ideal $1-\alpha$![Image](OEBPS/images/B9780443190377000090/si141_u1.png). It remains an open problem to characterize realistic weaker adversaries that lead to larger (lower bounds of) trade-off functions.

### 2.4.6 Group privacy

Theorem 2.14 in [\[11\]](#Chp002_29-55_B9780443190377000090_split_001.xhtml#br0055) analyzes how privacy degrades if *d* and *d*′![Image](OEBPS/images/B9780443190377000090/si7_u6.png) do not differ in just one sample, but rather in *g* samples. If a mechanism is *f*\-DP, then it is

$$[1 - (1 - f)^{\circ g}]\text{-DP}$$

![Image](OEBPS/images/B9780443190377000090/si241.png)

for groups of size *g* (where $\circ g$ denotes the *g*\-fold iterative composition of function $1-f$![Image](OEBPS/images/B9780443190377000090/si242.png), where 1 denotes the constant integer value 1 and not the identity function, i.e., $(1-f)(\alpha) = 1-f(\alpha)$![Image](OEBPS/images/B9780443190377000090/si243.png)). This is a tight statement in that *there exist f* such that the trade-off function for groups of size *g* cannot be bounded better. In particular, for $f = G[\mu]$![Image](OEBPS/images/B9780443190377000090/si244.png) we have $G[g\mu]$![Image](OEBPS/images/B9780443190377000090/si245.png)\-DP for groups of size *g*.

The intuition behind the $[1 - (1 - f)^{\circ g}]$![Image](OEBPS/images/B9780443190377000090/si246.png)\-DP result is that the adversary can create a sequence of data sets $d_0 = d, d_1, \dots, d_{g-1}, d_g = d'$![Image](OEBPS/images/B9780443190377000090/si247.png) such that each two consecutive data sets $d_i$![Image](OEBPS/images/B9780443190377000090/si248.png) and $d_{i+1}$![Image](OEBPS/images/B9780443190377000090/si249.png) are neighboring. We know that $T(\mathcal{M}(d_i), \mathcal{M}(d_{i+1})) \ge f$![Image](OEBPS/images/B9780443190377000090/si250.png). For each rejection rule, we may plot a point (in *x* and *y* coordinates)

$(\mathbb{E}_{o \sim \mathcal{M}(d_i)}[\phi(o)], \mathbb{E}_{o \sim \mathcal{M}(d_{i+1})}[\phi(o)])$.

![Image](OEBPS/images/B9780443190377000090/si251.png)

Since $f(\alpha)$![Image](OEBPS/images/B9780443190377000090/si179.png) is a lower bound on the Type I vs. Type II error curve, the resulting collection of points is upper bounded by the curve $1-f(\alpha)$![Image](OEBPS/images/B9780443190377000090/si252.png). We have that $\alpha = \mathbb{E}_{o \sim \mathcal{M}(d_i)}[\phi(o)]$![Image](OEBPS/images/B9780443190377000090/si253.png) is mapped to

$\mathbb{E}_{o \sim \mathcal{M}(d_{i+1})}[\phi(o)] \le 1-f(\alpha) = (1-f)(\alpha)$.

![Image](OEBPS/images/B9780443190377000090/si254.png)

By transitivity, we have that $\alpha = \mathbb{E}_{o \sim \mathcal{M}(d=d_0)}[\phi(o)]$![Image](OEBPS/images/B9780443190377000090/si255.png) is mapped to

$\mathbb{E}_{o \sim \mathcal{M}(d'=d_g)}[\phi(o)] \le (1-f)^{\circ g}(\alpha)$.

![Image](OEBPS/images/B9780443190377000090/si256.png)

This yields the lower bound

$T(\mathcal{M}(d), \mathcal{M}(d')) \ge 1 - (1-f)^{\circ g}$

![Image](OEBPS/images/B9780443190377000090/si257.png)

on the Type I vs. Type II error curve.

Let $\phi[\alpha]$![Image](OEBPS/images/B9780443190377000090/si258.png) denote a rejection rule that realizes the mapping from

$\alpha = \mathbb{E}_{o \sim \mathcal{M}(d_i)}[\phi[\alpha](o)]$ to $(1-f)(\alpha) = \mathbb{E}_{o \sim \mathcal{M}(d_{i+1})}[\phi[\alpha](o)]$.

![Image](OEBPS/images/B9780443190377000090/si259.png)

Then the mapping from $(1-f)^{\circ i}(\alpha) = \mathbb{E}_{o \sim \mathcal{M}(d_i)}[\phi(o)]$![Image](OEBPS/images/B9780443190377000090/si260.png) to $(1-f)^{\circ (i+1)}(\alpha) = \mathbb{E}_{o \sim \mathcal{M}(d_{i+1})}[\phi(o)]$![Image](OEBPS/images/B9780443190377000090/si261.png) is realized by $\phi = \phi[(1-f)^{\circ i}(\alpha)]$![Image](OEBPS/images/B9780443190377000090/si262.png). This shows that the lower bound $1 - (1-f)^{\circ g}$![Image](OEBPS/images/B9780443190377000090/si263.png) is tight only if we can choose all $\phi[(1-f)^{\circ i}(\alpha)]$![Image](OEBPS/images/B9780443190377000090/si264.png) equal to one another. In general, this may not be the case for DP-SGD and future work may be able to produce an improved analysis for DP-SGD.

### 2.4.7 DP-SGD's trade-off function

We remind the reader that we can directly infer $(\epsilon, \delta)$![Image](OEBPS/images/B9780443190377000090/si88_u6.png)\-DP guarantees from [(2.7)](#Chp002_29-55_B9780443190377000090_split_001.xhtml#deq28); function $\delta(\epsilon)$![Image](OEBPS/images/B9780443190377000090/si265.png) turns out to only depend on $\mu \approx \sqrt{mE/(N\sigma^{2})}$![Image](OEBPS/images/B9780443190377000090/si266.png), see Section [2.4.5](#Chp002_29-55_B9780443190377000090_split_001.xhtml#s0100). This leads to a dependency on data set size *N*, which, see Section [2.3.2](#Chp002_29-55_B9780443190377000090_split_000.xhtml#s0065), by setting $\delta(\epsilon) = 1/N$![Image](OEBPS/images/B9780443190377000090/si267.png) favorably biases smaller data sets.

Appendix B in [\[11\]](#Chp002_29-55_B9780443190377000090_split_001.xhtml#br0055) shows how to infer divergence based DP guarantees. In particular, $G[\mu]$![Image](OEBPS/images/B9780443190377000090/si56_u9.png)\-DP implies $(\omega, \frac{1}{2\mu^{2}} \cdot \omega)$![Image](OEBPS/images/B9780443190377000090/si268.png)\-RDP (Renyi differential privacy) for any $\omega > 1$![Image](OEBPS/images/B9780443190377000090/si269.png), hence, we have

$$\frac{1}{2\mu^{2}}\text{-zCDP}.$$

![Image](OEBPS/images/B9780443190377000090/si270.png)

For group privacy with $g \ge 1$![Image](OEBPS/images/B9780443190377000090/si271.png), we have $G[\mu \cdot g]$![Image](OEBPS/images/B9780443190377000090/si272.png)\-DP and RDP and zCDP scale with another factor $g^2$![Image](OEBPS/images/B9780443190377000090/si273.png).

## 2.5 Future work

We are still in the midst of bringing DP-SGD to practice where we want to achieve good convergence to and accuracy of the final global model and where we have a strong DP guarantee (the trade-off function should be close to $1-\alpha$![Image](OEBPS/images/B9780443190377000090/si141_u1.png) which represents random guessing between the two hypotheses). Towards finding a good balance between utility and privacy, we discuss a couple future directions in next subsections.

### 2.5.1 Using synthetic data

One main problem is that local data is used for training models for various learning tasks. Each application of DP-SGD will leak privacy since the local data set is being reused. One way to control and be in charge of the amount of privacy leakage is to have data samples in local client data expire according to some expiration date (per sample). This is problematic because in our current data economy, data is a valuable asset which we do not want to give a limited lifetime.
