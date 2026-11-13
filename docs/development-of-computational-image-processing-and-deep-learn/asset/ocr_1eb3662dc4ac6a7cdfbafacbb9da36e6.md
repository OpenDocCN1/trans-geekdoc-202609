into 8 bit. Dark slices at the borders resulting from the specimens not being exactly even-surfaced and further image errors were cut. Each loaded scan was converted into a 3D array. In the following, every slice is handled separately; so it was iterated through the thickness of the samples and worked on 2D images. At first, a filter was applied to reduce the noise. The filters tested include the "normal" blur filter, the median blur filter, the Gaussian blur filter and the bilateral filter each with various kernel sizes. The kernel size defines the dimension of the window that is slided across the image and in which the filter-specific calculation is performed. The performance of the filters was judged afterwards by comparing the resulting calculated fiber volume contents with the experimental values. The results of the specimens of the Plate 2 can be seen in Table A.3, Table A.4 and Table A.5 and the results of the specimens of the Plate 3 in Table A.6 and Table A.7 in the Appendix (Section 9). The median filter with resolution-adapted kernel size performed the best. It works by creating a kernel of pixels around a central pixel. The values are sorted and the central pixel gets replaced by the median value. From the then noise-reduced image, a threshold value was determined by using the Otsu algorithm. The Otsu algorithm separates an image in two sections by maximizing the inter-class variance of the gray-level intensities between those sections:

```
$\sigma_\mathrm{B}^2(t) = \omega_1(t) \cdot \omega_2(t) (\mu_1(t) - \mu_2(t))^2 . \quad (3.3)$
```

$t$ is the gray value of the threshold being searched for and $i$ is the run variable with $i \in [0, L]$. $\omega_1$ and $\omega_2$ are the probabilities of the two sections with

```
$\omega_1(t) = \sum_{i=0}^{t-1} p(i) \text{ and } \omega_2(t) = \sum_{i=t}^{L-1} p(i), \quad (3.4)$
```

while $p(i)$ represents the probability for each gray level intensity.