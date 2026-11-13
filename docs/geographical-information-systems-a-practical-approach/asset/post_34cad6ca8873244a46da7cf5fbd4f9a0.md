
![](img/8aad3fa01ca9db86bd50bb2edb9a3134_387_0.png)

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_387_1.png)

(a) Original image (no stretch)

(b) Contrast-stretched image

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_387_2.png)

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_387_3.png)

(c) Histogram for (a)

(d) Histogram for (b)

### Figure 7.13 Images before and after contrast stretching and their histograms.

contains two or more dominant classes with distinctly different ranges of reflectance.

There are basically two types of methods for contrast stretching: linear and non-linear. Linear contrast stretching expands the range of DN values uniformly to fill the entire range of the output device. It transforms the original image using the formula:

DN' = \left( \frac{DN - DN_{min}}{DN_{max} - DN_{min}} \right) \times R \quad (7.9)

where DN' is the stretched value assigned to a pixel in the output image, DN is the original value of the pixel in the input image, DN_{min} and DN_{max} are the minimum and maximum pixel values, respectively, in the input image and R is the range of DN values that can be displayed on the output device (for example, 255). In the example shown in Figure 7.13, R is 255, DN_{min} = 18 and DN_{max} = 191. Any pixel with a DN value of 18 in Figure 7.13a would have a DN value of 0 after applying equation (7.9), while any pixel with a DN value of 191 in Figure 7.13a would now have a DN value of 255. All pixel values between 18 and 191 in the original image would be proportionately stretched between 0 and 255. This method is usually called a min–max contrast stretch.

$DN_{min}$ and $DN_{max}$ in equation (7.9) could be defined as the minimum and maximum plus/minus one or more standard deviations of the DN values, and then a linear stretch could be applied between the two values. Any value that is smaller than $DN_{min}$ becomes 0, and any value that is greater than $DN_{max}$ is changed to R (for example, 255). This approach is commonly referred to as a **standard-deviation contrast stretch**. Figure 7.13b is a result of this kind of contrast stretching with 2.5 standard deviations. Usually, the DN values falling outside one or two standard deviations may be discarded without serious loss of most important data.

Another alternative is to define a certain percentage of pixels from the low and high end of the histogram to trim off the extreme values and use the new lowest DN value as $DN_{min}$ (called per cent clip minimum) and the new highest DN value as $DN_{max}$ (called per cent clip maximum) to stretch the image linearly. This method is often termed as a **per cent-clip contrast stretch**. The clipping percentages can be different at each tail of the histogram. For example, if we set 1 per cent as the clipping percentage at the low end of the histogram in Figure 7.13c and 10 per cent at the high end, $DN_{min}$ would become 42.5, while $DN_{max}$ would be 107.5.

The original DN values between 42.5 and 107.5 will spread evenly between 0 and 255, with all values 18–42.5 becoming 0 and 107.5–191 becoming 255. These linear methods may be effective in visualisation of a particular aspect of the information content of an image.

However, linear contrast stretching does not consider the shape of the image histogram. Original DN values between the defined lower and upper limits spread evenly within the full brightness range of the display device, no matter whether they are rarely occurring values or frequently occurring values. Nonlinear methods can overcome this limitation. The most popular nonlinear contrast stretching method is **histogram equalisation**, which assigns DN values to the output greyscale levels according to their frequency of occurrence. It effectively spreads out the most frequent DN values, thus enhancing the contrast in the most populated range of DN values in the image. Jensen (1996) provides a good explanation of this method with examples. The method is particularly useful for images with backgrounds and foregrounds that are both bright or both dark. A disadvantage of the method is that it is indiscriminate. It may increase the contrast of background noise while decreasing the usable information content.

### Practical 7.6 See the Support Material

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_388_0.png)

In this practical, you are going to learn how to enhance images using various contrast stretching methods in ArcGIS Pro or QGIS.

### 7.3.4 Spatial Filtering

Spatial filtering is to use spatial filters to detect, sharpen or smooth specific features in an image based on their spatial frequency. The spatial frequency refers to the frequency of change in DN values per unit distance along a particular direction in the image. The areas in an image where changes occur in very close proximity are said to have high spatial frequencies, while those areas with changes which occur over large distances have low spatial frequencies. Therefore, a scene with small details and sharp edges contains more high spatial frequency information than one composed of large coarse features. As the ability of the human eyes to discern spatial frequency is limited, it is often desirable to selectively remove certain spatial frequency ranges within an image to make it more interpretable with less noise. Spatial filtering involves examining the spatial variations in DN values of an image and using spatial filters to modify the image by selectively suppressing or separating certain spatial frequency ranges.

A spatial filter is an image operation where each pixel is changed by a function of the intensities or DN values of pixels in its neighborhood. It essentially calculates the focal sum statistic for each pixel of the input image using a weighted kernel (Section 5.4). A kernel is an array of coefficients or weights of a few pixels in dimension (for example, 3 × 3 and 5 × 5) (Figure 5.19). It is used as a moving window (Figure 5.20). A spatial filtering operation moves the kernel along in both the row and column dimensions pixel by pixel, multiplies the pixel values within the neighbourhood by the corresponding coefficients or weights in the kernel, sums all the resulting products and replaces the central pixel by the sum. The calculation is repeated until the entire image is filtered and a new image is generated. This process is also called image convolution, or simply convolution.

With different types of calculation, spatial filters can be designed to enhance or suppress different types of features. There are basically three types of spatial filters: low-pass, high-pass and edge detection filters. Low-pass filters are used to highlight low spatial frequency features, reduce the local variation in an image and generally serve to smooth the image. Figure 7.14 shows three low-pass filters and example outputs. The original image shown in Figure 7.14a is used for all filtering operations depicted in the subsequent figures. Filter A in Figure 7.14 uses a kernel whose coefficients are all set to 0.1111 (1/9). This filter calculates the mean value within each neighbourhood, commonly called a moving average filter. The outcome is that the high and low values within each neighbourhood will be averaged out. However, this low-pass filter blurs the image, particularly at the edges of features. To reduce blurring, Filters B and C in Figure 7.14 could be used, whose kernels have unequal coefficients.

High-pass filters enhance high spatial frequency features, increase smaller detail in an image and generally serve to sharpen the image. As an image is considered to consist of low- and high-frequency components as well as noise, a high-pass-filtered image can be derived by subtracting the low-pass-filtered image from twice the original image (Jensen 1996), for example:

```
I_{high} = 2 × I - I_{low} (7.10)
```

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_390_0.png)

where \( I_{high} \) is the high-pass-filtered image, \( I_{low} \) is the low-pass-filtered image and \( I \) is the original image. High-pass filters that sharpen edges can also be created using the kernels listed in Figure 7.15. These filters do not keep the low-frequency component of the image and can be used to enhance boundaries between land and water and urban structures such as roads and buildings.

**Edge detection filters** enhance and delineate linear features such as roads, linear geological structures and boundaries of area features. Different from high-pass filters, edge detection filters preserve both low- and high-frequency components of an image. Several edge enhancement techniques have been developed. One straightforward method is directional first differencing. This method calculates the difference between each pixel and one of its immediate neighbouring pixels and uses the difference as the output pixel value. It approximates

the first derivative between two adjacent pixels with regard to a certain direction, which can be horizontal, vertical and diagonal. Suppose \( DN_{ij} \) is the brightness value of the pixel at the \( i \) th row and \( j \) th column in the original image, and \( DN'_{ij} \) is the filtered value of the pixel. The horizontal, vertical and diagonal first differences at the pixel would be, respectively:

Vertical:
\( DN'_{i,j} = DN_{i,j} - DN_{i,j+1} + K \) (7.11)

Horizontal:
\( DN'_{i,j} = DN_{i,j} - DN_{i-1,j} + K \) (7.12)

North-east diagonal:
\( DN'_{i,j} = DN_{i,j} - DN_{i+1,j+1} + K \) (7.13)

South-east diagonal:
\( DN'_{i,j} = DN_{i,j} - DN_{i-1,j+1} + K \) (7.14)

where \( K \) is a constant added to make the differences positive. \( K \) is usually set as the
