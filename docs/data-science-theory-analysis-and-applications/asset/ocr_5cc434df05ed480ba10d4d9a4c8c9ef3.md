![](bbox=[0.182, 0.098, 0.878, 0.359])

**FIGURE 11.10** Variation of MAP according to the number of cells used to calculate pixel density. (The best score appears in light gray.)

MAP scores obtained for original ICDAR-2011. It is clear that there is no similarity measure that gives the best performance for all features. We note that Manhattan distance is the most suitable for HOG, pixel density, and RLF. On the other hand, Canberra distance fits with LBP<sup>riu</sup> and GLBP features, while the Chi-square distance gives the best performance for LBP. Moreover, one can see that dissimilarity measures outperform similarities, which seem less effective for Writer Retrieval. So, in the retrieval experiments, each feature is associated with the most suitable dissimilarity.

Overall, the best configuration for LBP descriptors is (16×2) associated with the Chi-square distance for LBP and Canberra distance for LBP<sup>riu</sup>. HOG and pixel density features reach their best performance using uniform grids with (3×6) and (8×6) cells, respectively. On the other hand, Manhattan distance gives the best performance for pixel density, HOG, and RLF. Finally, GLBP is more efficient

**TABLE 11.2**

**MAP (%) Obtained Using different Similarity and Dissimilarity Measures**

| Descriptor | Manhattan | Euclidean | Canberra | Chi-square | Cosine | Jaccard |
|---|---:|---:|---:|---:|---:|---:|
| LBP<sub>16×2</sub> | 54.74 | 27.97 | 63.10 | **78.34** | 60.96 | 6.34 |
| LBP<sup>riu</sup><sub>16×2</sub> | 27.17 | 22.51 | **50.43** | 42.91 | 33.63 | 6.34 |
| HOG | **62.67** | 53.45 | 54.33 | 49.11 | 53.29 | 50.99 |
| GLBP | 49.25 | 46.77 | **79.01** | 58.55 | 61.55 | 9.62 |
| Pixel density | **41.87** | 41.38 | 41.63 | 41.33 | 31.89 | 7.92 |
| RLF | **92.22** | 85.15 | 87.84 | 90.88 | 84.87 | 50.48 |