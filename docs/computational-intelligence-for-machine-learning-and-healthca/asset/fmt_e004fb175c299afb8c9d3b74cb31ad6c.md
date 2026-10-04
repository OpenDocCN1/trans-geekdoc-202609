
The thresholding method was discovered to be the most common method out of all the current methods used to segment different image kinds. There are two distinct types of thresholding: bilevel thresholding and multilevel thresholding. If the images are clearly separated by a single threshold value from the image background, a bilevel threshold is considered, while multilevel thresholds are used to divide a picture into several separate parts.

Multilevel thresholding methods have played a significant part in image analysis over the years and lot of scientists and academics have done a lot of work on it. Image thresholding extracts items from the background in a scene that helps analyze and interpret the picture. Selecting a preeminent gray-level threshold is a difficult task for scientists in image processing. Selection of thresholds is simple, because of the multi-modality of the histograms of many threshold image choices. It is an Non Polynomial (NP) hard problem, and researchers have therefore suggested many methods for the threshold of preeminent gray level (Sezgin and Sankur, 2004).

### 13.2.1 Bilevel thresholding

A gray picture has intensity values between 0 and *N* − 1, where *N* is the highest possible intensity value. Bilevel image thresholding detects an intensity value separating the image’s front and background object. There are several techniques implemented for bilevel threshold estimation, such as pixel value variance estimation and entropy values ([Arora et al., 2008](#bodymatter-013.xhtml#b_9783110648195-013_ref_003); Gao et al., 2010b):

(13.1)*E**Q**k*[0] = {*F* (*x*, *y*) ∈ *X*|0 ≤ *F*(*x*, *y*) ≤ *k*[1] − 1} (13.2)*k*\_1 = {*F* (*x*, *y*) ∈ *X*|*K*1 ≤ *F*(*x*, *y*) ≤ *N* − 1}

where `X` is the display object, and `F(x,y)` is the frequency pixel of the situations for `x` and `y` components.

### 13.2.2 Multilevel thresholding

Bilevel image thresholding is ineffective in images where we cannot differentiate between background and subjects of concern and we are, therefore, compelled to move toward a multilevel picture threshold scheme (Otsu, 1979a; Tsai, 1985b). Multilevel thresholds detect more than one gray level to differentiate the items of concern from the picture. It can be mathematically articulated as follows:

(13.3)$\\mspace{-2250mu} k\_{0} = \\{ F\\ \\left( {x,\\ y\\ } \\right) \\in X|0 \\leq F\\left( {x,\\ y\\ } \\right) \\leq k\_{1} - {1\\}}$ (13.4)$\\mspace{-230mu} k\_{1}\\mspace{220mu} = \\{ F\\ \\left( {x,\\ y\\ } \\right) \\in X|k\_{1} \\leq \\ F\\left( {x,\\ y\\ } \\right)\\, \\leq \\ k\_{2} - {1\\}}$ (13.5)$\\mspace{-630mu} k\_{p} = \\{ F\\left( {x,\\ y\\ } \\right) \\in X| \\leq \\ F\\left( {x,\\ y\\ } \\right) \\leq k\_{p} + 1 - {1\\}}$ (13.6)$\\mspace{-1800mu} k\_{q}\\mspace{-40mu} = \\{ F\\left( {x,\\ y\\ } \\right) \\in X|k\_{q} \\leq \\ F\\left( {x,\\ y\\ } \\right) \\leq N - 1\\}$

where `X` is the display object, and `F(x,y)` shows the pixel frequency corresponding to `x` and `y` and `K[P] = 1, 2, …, M`.

#### 13.2.2.1 Otsu’s method

Another technique known as interclass variance is a nonparametric segmentation technique aimed at optimizing interclass variance and increasing interclass pixel variance in each class (Tsai, 1985).

We might recognize `μ[1] … μ[m]` as mean cost of pixels in group 0, 1, …, `m` for the multilevel segmentation issue:

(13.7) *σ*[0]² = *ω*[0](*μ*[0]− *μ*[*T*])²,         *σ*[*j*]² = *ω*[0](*μ*[1]− *μ*[*T*])² (13.8) *σ*[*j*]² = *ω*[*j*](*μ*[*j*]− *μ*[*T*])²,         *σ*[*m*]² = *ω*[*m*](*μ*[*m*]− *μ*[*T*])² (13.9) $\\mu\_{0} = \\ \\sum\\limits\_{i = 0}^{t\_{1} - 1}ip\_{i}/\\omega\_{0},\\,\\,\\,\\,\\,\\,\\,\\,\\ \\mu\_{1} = \\ \\sum\\limits\_{i - t1}^{t\_{2} - 1}ip\_{i}/\\omega\_{1}$ (13.10) $\\mu\_{j} = \\ \\sum\\limits\_{i = t\_{j}}^{t\_{j + 1} - 1}ip\_{i}/\\omega\_{0},\\,\\,\\,\\,\\,\\,\\,\\,\\ \\mu\_{m} = \\ \\sum\\limits\_{i - t\_{m}}^{N - 1}ip\_{i}/\\omega\_{1}$

Therefore, the segmentation technique aims at optimizing `f(t)`, the amount of the difference characteristics between groups is to obtain the optimal values in [eq. (13.11)](#bodymatter-013.xhtml#b_9783110648195-013_eq_011):

(13.11) $\\overset{\\rightarrow}{t^{\\ast}} = \\arg\\max\\left( {f\\left( t \\right)} \\right)\\;\\,\\,{where}\\, f\\,(t) = \\;\\sum\\limits\_{i = 0}^{m}\\sigma\_{i}^{2}$

### 13.2.3 Kapur’s entropy method

The theory of maximizing the Kapur’s entropy method for segmentation of objects is based on the assumption that a picture consists of a foreground and a background region attributing values for distribution of object intensity (Agrawal et al., 2013a). Both regions are calculated individually, maximizing their amount. Then, an optimal limit value is calculated to maximize the entropy amount. The same idea can readily be used for multilevel image thresholds that can be formulated mathematically:

$\\mspace{-360mu} H\_{0} = - \\sum\\limits\_{i = 0}^{ti - 1}{(p\_{i}/\\omega\_{0})\\;\\log\_{2}(p\_{i}/\\omega\_{0})}$ (13.12) $\\mspace{-860mu} H\_{0} = - \\sum\\limits\_{i = t1}^{t2 - 1}(p\_{i}/\\omega\_{1})\\ \\log\_{2}(p\_{i}/\\omega\_{1})$ $\\mspace{500mu} H\_{1} = - \\sum\\limits\_{i = 0}^{t\_{j + 1} - 1}(p\_{i}/\\omega\_{j})\\ \\log\_{2}(p\_{i}/\\omega\_{1})$ (13.13) $\\mspace{-360mu} H\_{m} = - \\sum\\limits\_{i = 0}^{N - 1}(p\_{i}/\\omega\_{m})\\ \\log\_{2}(p\_{i}/\\omega\_{m})$ (13.14) $\\mspace{-4450mu}\\omega\_{0} = \\ \\sum\\limits\_{i = 0}^{t\_{i} - 1}p\_{i};\\ \\,\\,\\,\\omega\_{1} = \\ \\sum\\limits\_{i = t\_{1}}^{t\_{2} - 1}p\_{i}$ (13.15) $\\mspace{-2340mu}\\omega\_{1} = \\ \\sum\\limits\_{i = t\_{j}}^{t\_{j + 1}\\! - 1}p\_{i};\\ \\,\\,\\,\\omega\_{m} = \\ \\sum\\limits\_{i - t\_{m}}^{N - 1}p\_{i}$

where `H[0]`, `H[1]`, …, `H[m]` are entropy values of separate areas or divisions of `m + 1`, and `P[i]` is probability `i` where `i` is between 0 and 255 and `N` is the peak gray intensity concentration.

## 13.3 Optimum thresholding methods problem

Image thresholding is a method of transforming a gray image with peak thresholds to a black and white image. Thresholding can be regional or international, but in computational terms, these methods are costly, so optimization techniques are required to optimize the objective functional results of computational time constraints locally and globally. Through optimizing the objective function, the optimization techniques seek the optimum thresholds so that the segmented image distinguishes the background and foreground image clearly. Let us say a gray-level image of `G` and is {1,2,…,(`G`−1)}. Then, probability `P[i] = A[i]/P(0 < 1 < (G−1))`,

where `A[i]` denotes the pixel number for the corresponding gray rate `G` and `P` denotes the total pixel number in the image equal to the pixel number in the image equal to $\\sum\_{i = 0}^{G - 1}A\\left( i \\right)$, respectively.

### 13.3.1 Fuzzy entropy

Measuring uncertainty is taken as a test of data. Accordingly, fuzzy data measures are called fuzzy entropy ([Herencia and Lamata, 1997](#bodymatter-013.xhtml#b_9783110648195-013_ref_023); [Rudas and Kaynak, 1998](#bodymatter-013.xhtml#b_9783110648195-013_ref_022)). It is used to evaluate an amount of fuzzy data gathered from a fuzzy system or fuzzy set. Here, it should be noted that the idea of blurred entropy is quite different from Shannon’s classical entropy since representing it does not require a probabilistic notion ([McCulloch and Pitts, 1943](#bodymatter-013.xhtml#b_9783110648195-013_ref_037); [Garrett, 1994](#bodymatter-013.xhtml#b_9783110648195-013_ref_017); [Hasanipanah et al., 2016](#bodymatter-013.xhtml#b_9783110648195-013_ref_020)). This is because fuzzy entropy includes uncertainties of vagueness and ambiguity, while entropy from Shannon includes random (probabilistic) uncertainty.

### 13.3.2 Multilevel fuzzy entropy
