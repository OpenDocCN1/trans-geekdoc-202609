
Now, let’s obtain discrete approximation of Gaussian function that can be used as kernel in convolution operation on images. To make things simple, let us consider zero mean `μ=0` and standard deviation as `σ=1`. With these values, function becomes the following:

`G(x, y) = (1 / (2πσ²)) * exp(-(x² + y²) / (2σ²))`

Consider only the variable part of the function as `exp(-(x² + y²) / 2)` for writing the code. The following code shows the implementation. It accepts `(x, y)` coordinate values from 2D and outputs variable part of Gaussian function value: Following code shows implementation of Gaussian function.

```
1. import numpy as np
2. def gaussian_fn_2d(x, y):
3.     # Exponent part of gaussian function mean=0, sd=1
4.     exp_part = np.exp(-(np.power(x, 2.) + np.power(y, 2.)) / 2.)
5.     return exp_part
```

**Code 9.4:** Gaussian function in two dimensions

As discussed, considering `3σ` matrix is sufficient. We need odd matrix, so for `σ=1`, we should consider 7×7 matrix. Function parameter values consider for discretization should be with in 3σ distance from origin. We can consider `(x, y)` values, as shown in *[Figure 9.9](#c09.xhtml#fig9_9)(a)*, for the kernel matrix. These coordinate values are used to kernel matrix, as shown in the following code:

```
1. # 3 sigma distance from origin
2. X_START = Y_START = -3
3. X_STOP = Y_STOP = 3
4. def get_gaussian_kernel():
5.     kernel_shape = (X_STOP - X_START + 1, Y_STOP - Y_START + 1)
6.     gaussian_sample = np.zeros(shape=kernel_shape, dtype=float)
7.     ker_x = ker_y = 0
8.     for y_idx in range(Y_START, Y_STOP + 1):
9.         for x_idx in range(X_START, X_STOP + 1):
10.            gaussian_sample[ker_x][ker_y] = gaussian_fn_2d(x_idx, y_idx)
11.            ker_y = ker_y + 1  # updating index
12.        ker_x = ker_x + 1  # Updating index
13.        ker_y = 0
14.    return gaussian_sample
15. # Obtain gaussian kernel and normalize
16. gaussain_ker = get_gaussian_kernel()
17. div_part = 2. * np.pi
18. norm_gauss_kernel = (1. / div_part) * gaussain_ker
```

**Code 9.5:** Obtain Gaussian function value for few coordinates equidistant from origin

Obtained kernel matrix using the code is captured in *[Figure 9.9](#c09.xhtml#fig9_9)(b)*. Note that it is not normalized. Refer to the following figure:

![](images/9.9.jpg)

**Figure 9.9:** **(a)** *(x,y) coordinates considered for creating 2D kernel* **(b)** *Gaussian kernel with μ=0, σ=1 without normalization*

Normalization of the preceding Gaussian kernel can be performed in two ways. One approach is to divide all values of the kernel by the constant part of Gaussian function, that is, `1 / (2πσ²)` (case: **μ=0, σ=1**). All values of the kernel may not add to `1 / (2πσ²)` (**μ=0, σ=1**) due limited kernel size. We can follow another approach, in which we can divide all values of the kernel by the sum of all elements of the kernel. The second approach is better.

We have to use normalized Gaussian kernel for convolving with images. Normalized Gaussian kernel is captured in *[Figure 9.10](#c09.xhtml#fig9_10)*. Note that the sum of all elements of normalized kernel must equal 1. Refer to the following figure:

![](images/Image45924.jpg)

**Figure 9.10:** *Normalized Gaussian Kernel with μ=0, σ=1*

## Application of Gaussian filter

We have obtained normalized Gaussian kernel of size 7×7 that Gaussian function of zero mean as `μ=0` and standard deviation as `σ=1`. Now, let’s apply the kernel on gray image. Gray image can be obtained with *Code 9.1*. Apply normalized Gaussian kernel on gray image, shown in *[Figure 9.11](#c09.xhtml#fig9_11)*, to obtain smoothed image:

![](images/Image45933.jpg)

**Figure 9.11:** *Snapshot of a Wikipedia page in gray scale*

The following code shows the application of the kernel using OpenCV library:

```
1. image_gray = read_image(IMAGE_PATH)
2. gauss_filtered_img = cv.filter2D(
3.                          image_gray, ddepth=-1, kernel=norm_gauss_kernel)
4. cv.imshow("Gaussian Smoothed Image", gauss_filtered_img)
```

**Code 9.6:** Convolve normalized Gaussian kernel with every possible pixel of the image using `filter2D()`

Output of the *Code 9.6* is captured in *[Figure 9.12](#c09.xhtml#fig9_12)*. Figure is smoothed using Gaussian kernel. Refer to the following figure:

![](images/Image45943.jpg)

**Figure 9.12:** *Smoothing of gray Wikipedia image with Gaussian 7×7 kernel of μ=0, σ=1*

We can apply Gaussian kernel repeatedly too. Image is blurred further with each application of Gaussian kernel.

> **Note:** Working with gray scale images is simple as it can be represented in 2D and values represent intensity. Gaussian filter is applied to intensity of these pixels. How to apply the filter on color images, which are usually represented in 3D using Red, Green & Blue? Gaussian filter cannot be applied to the color components. Instead, image is converted to YUV format where Y is luma/intensity, U & V represents blue and red channels. Gaussian kernel will be applied on Y component only.

We saw that image blurring/smoothing is accomplished in spatial domain with the use of neighborhood pixel averaging technique (Gaussian function). There are other blurring techniques, which will be discussed later in the *Non-Linear Filters* section. Next, we will create edge detection filters using differentiation. Differentiation at a point is proportional to magnitude of intensity discontinuity. Thus, image differentiation enhances edges and other discontinuities with respect to slowly varying intensities.

## Image derivative-based kernels

Let us first understand the behavior of derivatives on constant intensity, onset and end of step and ramp intensity discontinuity/ramps. *[Figure 10.13](#c10.xhtml#fig10_13)* has plot of pixels intensity and depicts intensity ramp and step.

In image, along one dimension, pixels neighboring to pixel `x` are `x + 1` & `x - 1`. Using this information, basic definition of first order derivative for one-dimensional function is stated as follows:

`f'(x) = f(x + 1) - f(x)`

Properties of first order derivative are as follows:

*   Zero in area of constant intensity
*   Non-zero at onset and end of intensity ramp/step
*   Non-zero along intensity ramps

Similarly, definition of second order derivative can be stated as follows:

`f''(x) = f(x + 1) + f(x - 1) - 2f(x)`

Properties of second order derivative are as listed here:

*   Zero in on areas of constant intensity
*   Non-zero at onset and end of intensity ramp/step
*   Zero along intensity ramps

*[Figure 9.13](#c09.xhtml#fig9_13)* shows first and second order derivates of intensity values. We can verify the properties these derivates. Derivatives provide information about constant intensity, ramp up/down, and step intensity. Edges in digital images behave like ramp intensity. Identifying these ramps will help us in finding edges that will aid in sharpening the image. Next, we will use second order derivative for image sharpening. Refer to the following figure:

![](images/Image45988.jpg)

**Figure 9.13:** *Graph captures pixel intensity along 1D, table captures derivatives for each pixel*

> **Note:** Due to the property "zero in area of constant intensity", derivative kernels must sum up to zero.

## Laplacian kernel – Second order derivative

The simplest derivative operator that is also isotropic (applies equally in all direction) is *Laplacian*, and it is defined for function with two variables as follows:

`∇²f = ∂²f/∂x² + ∂²f/∂y²`

As derivatives of any order are linear, Laplacian is linear operator. We need to express the operator in discrete format for 2D images, as follows:

`∇²f(x, y) = f(x+1, y) + f(x-1, y) + f(x, y+1) + f(x, y-1) - 4f(x, y)`

Discretized Laplacian can be written as follows:

```
0  1  0
1 -4  1
0  1  0
```
