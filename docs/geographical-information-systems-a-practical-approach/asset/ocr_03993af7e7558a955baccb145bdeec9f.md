![](bbox=[0.09, 0.08, 0.87, 0.25])

# Figure 7.12 IHS pan-sharpening process.

IHS is very fast and can quickly process large volumes of data and produce enhanced images. However, the fused images suffer from spectral distortion compared to the original multispectral image.

it should not be used if the original scene radiometry needs to be preserved.

Brovey transformation assumes that the spectral range spanned by the panchromatic image is the same as that covered by the multispectral bands. It first multiplies each resampled multispectral band by the panchromatic band minus the weighted near-IR band, then divides each product by the weighted sum of all the multispectral bands, as expressed in the following:

Gram–Schmidt transformation is based on an algorithm for vector orthogonalisation used in linear algebra and multivariate statistics (Farebrother 1974). Basically, this method is performed in the following steps:

```
I^{\lambda}_{out} = I^{\lambda}_{in} \times \frac{Pan - NearIR \times w_{nir}}{R \times w_{red} + G \times w_{green} + B \times w_{blue}}
(7.7)
```

+   1. Computing a simulated low-resolution panchromatic band as a weighted mean of the multispectral bands
+   2. Applying the Gram–Schmidt orthogonalisation algorithm on the simulated panchromatic band (used as the first vector that is not transformed) and the multispectral bands (each treated as a high-dimensional vector) to make all bands orthogonal, which de-correlates all the bands
+   3. Replacing the simulated panchromatic band by the gain- and bias-adjusted high-resolution panchromatic band and resampling all multispectral bands to the same resolution as the high-resolution panchromatic band
+   4. Applying the inverse Gram–Schmidt transform using the same transform coefficients, but on the high-resolution bands, to form the pan-sharpened spectral bands

where I^{\lambda}_{out} is the output intensity value for band \lambda, I^{\lambda}_{in} is the original intensity value for band \lambda, R is the red band, G is the green band, B is the blue band and w_{red}, w_{green} and w_{blue} are the weights assigned to the red, green and blue bands, respectively. \lambda could be red, green, blue or near-IR. This method can increase contrast in the low- and high-reflectance areas in the image. As a result,