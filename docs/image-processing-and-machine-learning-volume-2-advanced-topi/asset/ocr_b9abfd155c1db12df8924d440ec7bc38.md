$h_j = 3.5 \cdot \sigma_j \cdot s^{-(\frac{1}{3})}, \quad \delta_j = \sqrt{0.5} \cdot \sigma_j, \quad (5.14)$
where $j \in [1,...,3]$.

# 5.4.3.2 Analysis of the Results

The MS achieves its operation through two sub-processes. First, the feature map is generated considering only the information contained in dataset O. Afterward, with the density map, their local optimals are identified. Therefore, it is determined a group of c attractor elements \(\{x^*_1,...,x^*_c\}\) and also a list of data X_i = (o_p,...,o_q) for each attractor x^*_i. The list includes all the data points (o_p, o_q \in C_i) attracted to each attractor point.

Assume Figure 5.5a as the image to be processed. The dimensions of the image are 214x320. Considering such an image, it is estimated that the group of characteristics F, which includes the grayscale I(x,y), variance V(x,y), and non-local mean NL(x,y) magnitudes for every pixel element. Then, a set of 3,424 pixels (o = int(0.05·214·320)) are sampled randomly from F to generate the operative dataset O. By considering the elements O = {o_1,...,o_s}, the MS method is applied. The MS generates as a result for each feature F(x,y) a density value \(\hat{f}(F(x,y))\). Therefore, we have four-dimensional data: three elements to describe the feature space and one for referring its density value. In order to visualize these results, we have used a polar technique [58,59] to represent high-dimensional data (d_1,...,d_4) into a two-dimensional space (u, v). Under this technique, the data are first normalized so that they vary

![](bbox=[0.145, 0.642, 0.845, 0.81])

FIGURE 5.5
Visual representation of the MS results. (a) Image to be processed and (b) visualization of the MS results.