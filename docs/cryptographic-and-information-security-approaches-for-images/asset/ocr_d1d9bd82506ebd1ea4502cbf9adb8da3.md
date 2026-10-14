# Table 17.3 Common Transform Domain Watermarking Technique

**Table 17.3 Common Transform Domain Watermarking Technique**

| S. No. | Transform Domain Technique | Description | Major Advantages |
|---|---|---|---|
| 1. | Discrete cosine transform (DCT) | It divides an image into low, high and middle frequency coefficients. Further, researchers can embed the secret watermark information into selected coefficients of the DCT image. | - The time and space (volume) required by DCT is less.
- It has excellent energy compaction property. |
| 2. | Discrete wavelet transform (DWT) | It divides an image into a set of four non-overlapping multi-resolution sub-bands. | - Most popular method as it provides the space frequency localization, multi-resolution and multi-scale analysis etc. |
| 3. | Singular value decomposition (SVD) | Divides an image into ortho-normal and diagonal parts. Singular values appear in the diagonal order in descending order in the diagonal parts of an image. | Singular values are unique, stable and exhibit excellent energy compaction properties. |
| 4. | Karhunen-Loeve transform (KLT) | The KL transform is a reversible linear transform that takes the advantage of statistical properties of a vector representation and optimally de-correlates the input data. | The de-correlation property of KL transform eradicates the requirement for cross channel smoothing. |
| 5. | Discrete Fourier transform (DFT) | It decomposes an image into a set of orthogonal functions and converts the spatial intensity of the image into its frequency domain. | DFT employs phase modulation in place of magnitude components for data hiding which yields better robustness against noise attacks. However, it shows poor energy compaction property. |