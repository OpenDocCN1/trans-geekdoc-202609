# Peak-Signal to Noise Ratio (PSNR)

This statistical metric is also used to measure the performance of the image enhancement methods. PSNR is the ratio between the maximum possible power of the signal and the power of the noise (Dhal, K.G., Quraishi, I. M., Das, S. (2017), Dhal, K. G., Das, S. (2015). It is actually distortion metric which is crucially depends on Mean-Squared Error (MSE). MSE defined as:

```
MSE(f, G) = \frac{\sum_{i=0}^{N-1} \sum_{j=0}^{M-1} [f(i, j) - G(i, j)]^2}{M \times N} (20)
```

Where, f and G are the input and output image respectively. M and N are the number of rows and columns of the image.

The PSNR is calculated as follows:

```
PSNR(f, G) = 10 \log_{10} \left\{ \frac{(L-1)^2}{MSE(f, G)} \right\} (21)
```

L is the number discrete grey level. For 8 bit image it is 256.

If the value of PSNR is increased then contrast of the image is also enhanced and Absolute Mean Brightness Error (AMBE) is also reduced to some extent.

Simple popular metrics for gray level image enhancement such as Absolute Mean Brightness Error (AMBE) cannot be used in color image domain as each color model has their own representation for the brightness component (Kong, N. S. P., Ibrahim, H. (2008)). Therefore, apart from the visual results one popular referenced image quality assessment metric, PSNR-HVS-M (Ponomarenko N. (2007)) and one well-known non-referenced quality assessment metric, Cube Root Mean Enhancement (CRME) (Gao, C., Panetta, K., Agaian, S. (2013), Panetta, K, Gao, C.,Agaian, S. (2013)) have been taken into consideration which are explained as follows:

# Cube Root Mean Enhancement (CRME)

CRME is a contrast measurement technique for color image which measures the contrast not only within each color plane but also across the color planes (Gao, C., Panetta, K., Agaian, S. (2013), Panetta, K, Gao, C.,Agaian, S. (2013)). CRME computes the contrast by measuring the relative difference of color cube center and