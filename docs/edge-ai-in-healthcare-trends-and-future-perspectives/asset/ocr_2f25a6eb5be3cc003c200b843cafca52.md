# ## 12.3.2 FEATURE EXTRACTION

After pre-processing, the texture features are extracted from each image. In this chapter, the gray-level co-occurrence matrix (GLCM) is used to extract the texture features. The GLCM gives a joint distribution of gray-level pairs of neighboring pixels within an image (Rajakumar & George 2013). For the computation of GLCM, first, a spatial relationship is established between two pixels, one being the reference pixel, and other a neighbor pixel.

Let _M(u, v)_ be the element of GLCM of a given image _A_ of size \(a \times b\), containing the number of gray levels _G<sup>L</sup>_ ranging from 0 to _G<sup>L</sup>_-1. Then, _M_ cab is defined as the matrix element and given by:

```
\( M(u, v) = \sum_{i=1}^u \sum_{j=1}^v \begin{cases} 1 & \text{if } A(a,b)=u \text{ and } I^{in} \left( a + \Delta a, b + \Delta b \right) = v \\ 0 & \text{otherwise} \end{cases} \text{ (12.2) }\)
```

where, (_a_, _b_) and (_a_+Δ _a_, _b_+Δ _b_) are the locations of the reference pixel and its neighboring pixel, respectively. Each element of GLCM, _M_\(\big(\)_u_, _v_\(\big|\) Δ_a_, Δ_b_\(\big)\), represent the relative frequency of two pixels in a given neighborhood separated by a distance (Δ _a_, Δ _b_) and having gray-level values _x_ and _y_, respectively (Esteva et al. 2019). It can be represented as _q_\(\big(\)_u_, _v_\(\big|\)_D<sup>p</sup>_, θ\(\big)\), where the parameter _D<sup>p</sup>_ is the distance of separation between two neighborhood resolution cells, with two pixels having intensities _u_ and _v_ in the image. The other parameter θ represents the direction of the neighboring pixel with respect to the reference pixel. The parameter _D<sup>p</sup>_ is also called the set distance as it specifies the distance of all neighboring resolution pairs contained in a set. For the texture calculation, the GLCM must be symmetrical and each entry of the GLCM should be a probability value. In this paper, twenty two GLCM features are extracted from each image, namely angular second moment, contrast, inverse difference moment, entropy, correlation, variance, sum average, sum variance, sum entropy, difference entropy, inertia, cluster shade, cluster prominence, dissimilarity, homogeneity, energy, autocorrelation, maximum probability, inverse difference normalised, inverse difference moment normalised, information measure of correlation I, and information measure of correlation II.

# ## 12.3.3 FEATURE SELECTION USING THE LPSO ALGORITHM

After the feature extraction process, the important features are selected using the LPSO algorithm. The feature selection process is to limit the number of input features to achieve optimum accuracy and also reduce computation complexity. For feature selection, in this chapter, the LPSO algorithm is used. The LPSO is a combination of the lion optimization and PSO algorithms.

_Step 1: Initialisation._ Initialization is an important process for all optimization algorithms. For feature selection, initially the solutions are randomly selected. In