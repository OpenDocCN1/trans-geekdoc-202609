![](bbox=[0.26, 0.09, 0.79, 0.34])

Figure 7.8 A geometrically correct image superimposed on an original geometrically distorted image.

the corrected image must be recalculated based on the pixel values surrounding the transformed position in the original image. This process is called **image resampling**. There are basically three methods of resampling; nearest neighbour, bilinear interpolation and cubic convolution.

The nearest neighbour method determines the value of each pixel in the rectified output image as the value of its nearest pixel (centre to centre) in the original distorted image. For example, the bold blue outline in Figure 7.8 indicates a target pixel in the output image. It is assigned the value of the pixel labelled a on the input image. The nearest neighbour method does not change the values of the pixels; thus, it is quick and maintains the integrity of data. But it may create a blocky appearance in the corrected image because features on the output image may be offset spatially by up to half a pixel (Figure 7.9b).

The **bilinear interpolation** method calculates the value of a rectified output pixel as the average or distance-weighted average

of the four nearest input pixels. For example, the target output pixel in Figure 7.8 is determined as the average of the values of the pixels labelled a and b. It produces a smoother image than the nearest neighbour method but changes the range of brightness values of the original image (Figure 7.9c).

The **cubic convolution** method computes the value of a rectified pixel as the average or distance-weighted value of the 16 nearest input pixels. For instance, the target output pixel in Figure 7.8 is determined as the average of the values of the pixels labelled a, b and c. It is similar to bilinear interpolation, but it is more computationally intensive. The method sharpens an image and may smooth out noise (Figure 7.9d). Both bilinear interpolation and cubic convolution involve changing the original pixel values, which may cause some problems in subsequent spectral pattern analyses of the image. To avoid those problems, the two methods are often performed after spectral pattern analyses.