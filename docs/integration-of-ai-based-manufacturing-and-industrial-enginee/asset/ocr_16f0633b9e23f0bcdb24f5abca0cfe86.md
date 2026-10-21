![](bbox=[0.15, 0.1, 0.82, 0.23])

FIGURE 9.4 Pre-processing stages (a) compressed image, (b) transformed image.

# 9.4.2 SECONDARY PHASE

In the Secondary Phase of the process, all the compressed images are considered for further processing of categorization (Minnen et al., 2018). Here, in Stage-2, the images are pre-processed and then filtered based on their clarity and visibility. Based on the complexity of the image, this is then converted into ether grayscale or black & white (Figure 9.4).

To identify the properties of the image (Contrast, Blur, Noise, Artefact and Distortion, etc.), various pre-processing techniques are available, namely,

+   - regionprops() method in matlab.
+   - img.shape, img.size, img.dtype and many more properties in python.
+   - glFrustum(), glLoadIdentity() and many more methods in openGL.

The parameters to be considered to define the simplicity and discernibility of the imageries are the combination of Contrast, Blur, Noise, Artefact and Distortion.

For image filtration purposes, various commonly used techniques are available. These are stated below (Minnen et al., 2018; Owotogbe et al., 2019).

# 9.4.2.1 Strength Alterations and Spatial Filtering

+   - Histogram equalization
+   - Linear spatial filters, correlation, convolution
+   - Smoothing (linear) spatial filters
+   - Sharpening linear spatial filters using the Laplacian

# 9.4.2.2 Sifting in the Regularity Domain

+   - 1D and 2D continuous and discrete Fourier transforms
+   - Convolution theorem
+   - Properties of the Fourier transform
+   - Sieving in the incidence field (flattening and improving, low-pass and high-pass filtering)
+   - The Laplacian in the frequency domain, enhancement
+   - Homomorphic filtering
+   - Band Reject and Band Pass Filters