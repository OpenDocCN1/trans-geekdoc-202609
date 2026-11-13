images in the training data set that have the smallest distance to the generated image based on a suitable distance measure. In the following, we briefly introduce the Euclidean distance and the computationally more expensive structural similarity index measure (SSIM), as these serve as the basis of the k-nearest neighbor search in the results of this paper.

+   • Euclidean distance (ED)
+   The Euclidean distance being one of the simplest ways to determine the similarity between two arrays and the most common distance measure for nearest neighbor search [319] can be calculated for two gray scale images \(\boldsymbol{x} = (x_1, x_2, ..., x_{MN})\) and \(\boldsymbol{y} = (y_1, y_2, ..., y_{MN})\) of size \(M\) px \(\times\) \(N\) px as:

```
\(d^2_{\text{E}}(\boldsymbol{x}, \boldsymbol{y}) = \sum_{k=1}^{MN} (x_k - y_k)^2 \quad (3.19)\)
```

with the gray levels at the location \((k, l)\) given as \(x_{kN+l}\) and \(y_{kN+l}\). The smaller the calculated value, the higher the similarity. As there are major limitations like the non-consideration of spatial relationships, the nearest neighbors found through the calculation of the ED sometimes do not match human perception. Therefore, a second distance metric is considered. The ED is still calculated due to its computational simplicity.

+   • Structural similarity index measure (SSIM)
+   Another option for the evaluation of nearest neighbors of GANs is the SSIM [312] introduced by Wang et al. in 2005 [319]. It focuses especially on factors that are also relevant to human perception through evaluating luminance L, contrast C and structure S. Those three aspects are separately mathematically defined through means \(\mu_x\) and \(\mu_y\), standard deviations \(\sigma_x\) and \(\sigma_y\) and cross-correlation coefficient \(\sigma_{xy}\) of the two images \(\boldsymbol{x}\) and \(\boldsymbol{y}\). The detailed formulas can be found in the paper by Wang et al. [319]. In order to avoid instabilities for small values, constants \(C_i\) are added.