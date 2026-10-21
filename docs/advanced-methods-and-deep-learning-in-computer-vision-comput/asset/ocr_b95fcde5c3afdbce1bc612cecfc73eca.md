![](bbox=[0.2, 0.08, 0.8, 0.36])

FIGURE 1.31 Basic form for a Laws' texture classifier. Here I is the incoming image, M represents the microfeature calculation, E the energy calculation, S the smoothing, and C the final classification.

rather greater than the basic filter mask size (e.g., Laws used a 15 × 15 smoothing window after applying his 3 × 3 masks): the effect of this is to smooth over the gaps between the texture edges and other micro-features. At this point the image has been transformed into a vector image, each component of which represents energy of a different type. While Laws (1980b) used both squared magnitudes and absolute magnitudes to estimate texture energy, the former corresponding to true energy and giving a better response, the latter are useful in requiring less computation:

$$E(l,m)=\sum_{i=l-p}^{l+p}\sum_{j=m-p}^{m+p}|F(i,j)|\tag{1.113}$$

F(i, j) being the local magnitude of a typical microfeature which is smoothed at a general scan position (l, m) in a (2p + 1) × (2p + 1) window.

A further stage is required to combine the various energies in a number of different ways, providing several outputs which can be fed into a classifier to decide upon the particular type of texture at each pixel location (Fig. 1.31): if necessary, principal component analysis is used to help select a suitable set of intermediate outputs.

Laws' method resulted in excellent classification accuracy quoted at (for example) 87% compared with 72% for the co-occurrence matrix method, when applied to a composite texture image of grass, raffia, sand, wool, pigskin, leather, water and wood (Laws, 1980b). He also found that the histogram equalization normally applied to images to eliminate first-order differences in texture field grey-scale distributions led to little improvement. In an independent research study, Pietikäinen et al. (1983) confirmed that Laws' texture energy measures are more powerful than measures based on pairs of pixels (notably, co-occurrence matrices).