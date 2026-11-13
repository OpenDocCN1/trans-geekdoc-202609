The low-resolution spectral bands used to simulate the panchromatic band must fall within the range of the high-resolution panchromatic band. The weights used in the process depend on the spectral response of these bands. It uses the spectral response function of a given sensor to estimate what the panchromatic data look like, so that the sharpness is maximised and, at the same time, the colour or spectral distortion of the pan-sharpened output image is minimised. For more details about the Gram-Schmidt method, see Laben and Brower (2000).

Simple mean transformation simply calculates the mean between a multispectral band and the panchromatic band as the output for the multispectral band:

$I_{out}^{\lambda} = \frac{1}{2} \times (I_{in}^{\lambda} + Pan)$ (7.8)

This method can only be applied to three bands: red, green and blue.

# 7.3.3 Contrast Stretching

**Contrast stretching** attempts to improve the contrast in an image by expanding the narrow range of brightness or DN values in the image over a wider range of values or over the entire brightness range of the

display medium (such as computer screens). For example, Figure 7.13a is an 8-bit grey-scale image with no stretch, which has DN values ranging from 18 to 191. It is rather dark and low in contrast. After contrast stretching by extending the DN values of the image to range from 0 to 255 (the full range of the brightness values for an 8-bit video cathode ray tube display), we obtain Figure 7.13b, which appears brighter and higher in contrast. In other words, in the contrast-stretched image, light-toned areas appear brighter and dark areas appear darker, making visual interpretation much easier. This helps accentuate the contrast between features of interest and their backgrounds.

Contrast stretching involves adjusting the distribution and range of DN values. The distribution of the DN values that comprise an image is usually represented graphically using a histogram, as shown in Figures 7.13c and 7.13d. In an image histogram, the DN values are displayed along the x-axis of the graph, while the number of pixels in the image at each different DN value is shown on the y-axis. The distribution of DN values in a histogram of remote sensing imagery is often unimodal (with one clear peak). Both Figures 7.13c and 7.13d have a unimodal distribution. Multimodal distributions (with two or more clear peaks) result if a scene

# Practical 7.5 See the Support Material

In this practical, you are going to learn how to pan-sharpen multispectral imagery in ArcGIS Pro or QGIS.