![](bbox=[0.326, 0.096, 0.715, 0.306])

Figure 7.14 Comparison of P-R performance for robustness and scalability for extended database.

Table 7.2 Demonstration of average CPU elapsed.

| Feature extraction | TCS | QLS | Proposed |
|---|---|---|---|
| Offline (1400 images) | 87.39 | 96.29 | 89.75 |
| Offline (4200 images) | 336.39 | 358.29 | 340.15 |
| Online (1 image) | 0.062 | 0.069 | 0.064 |

with a difference of 8 pixels in each dimension, which are grabbed from the Scale database. However, in MPEG-7 database images are resized to a fixed scale of 96 × 96 pixels.

# 7.6 Conclusions

In this chapter, we suggested a synthesized approach to CBIR. We see that both contour and region based features of images are important for describing the outline as well as entire structure of the image. Therefore, we propose a local feature extractor based on Hough transform for linear edge detection, which gives the association among next to next edge points in the edge map of image. Being robust to noise and rotation, the linear edges derived using Hough transform are capable to effectively discriminating one class of images from the other, thus improving the retrieval accuracy significantly. We use ZMs’ magnitudes and phase coefficients for extracting the global features, as both are considerably proficient in representing the entire structure of an image. The use of Bray-Curtis similarity measure further enhances the results. The results of a large number of experiments over various databases representing a variety of geometric and photometric variations establish that the proposed synthesized solution outperforms and provide improved CBIR system.
For future study, medical images will be considered and classification algorithms incorporated to further improve the accuracy.