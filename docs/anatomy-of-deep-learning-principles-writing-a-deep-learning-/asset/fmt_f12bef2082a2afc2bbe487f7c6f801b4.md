
### 6.1.1 One-dimensional convolution

```python
y[i] = np.sum(x_pad[i*s:i*s+K]*w)
return y
```

With different padding widths and strides, perform this convolution function `conv1d()`:

```python
y1 = conv1d(x,w,0,s=2)
y2 = conv1d(x,w,1,s=2)
print(y1)
print(y2)
```

```
[17.3 32.8 37.7 17.2]
[ 8.7 26.3 23.8 27.9 16.3 ]
```

### 6.1.2 Convolution of one-dimensional signal

Convolution is used to process data such as one-dimensional signals or two-dimensional images, which can remove noise in the data or obtain certain features contained in the data.

For example, two sets of numbers `x` and `y` are generated below. `x` is a set of numbers (100) uniformly distributed on `[0, 2*π]`, and `y` is a number near the corresponding sinusoidal curve `sin(x)` (i.e. `y` is a noisy sample of the sinusoid):

```python
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline

x = np.linspace(0, 2*np.pi, 100)
y = np.sin(x) + np.random.random(100) * 0.2
plt.plot(x, y)
plt.show()
```

![](EPUB/media/file123.png "fig:")
Figure 6-10 Random noise sampling of a sinusoid

The following code generates a set of weight vectors (convolution kernel) `w` according to the normal distribution:

```python
sigma = 1.6986436005760381
x_for_w = np.arange(-6, 6)
w = np.exp(-(x_for_w) ** 2 / (2 * sigma ** 2))
w /= sum(w)
print(x_for_w)
print(["%0.2f" % x for x in w])
plt.bar(x_for_w, w)
```

```
[-6 -5 -4 -3 -2 -1  0  1  2  3  4  5]
['0.00', '0.00', '0.01', '0.05', '0.12', '0.20', '0.23', '0.20', '0.12', '0.01', '0.00']
```

![](EPUB/media/file124.png "fig:")
Figure 6-11 A set of weight parameters sampled according to the normal distribution

The middle value of this weight vector `w` is large, the values on both sides are small, and the sum of all ownership values is 1. This weight vector `w` is used to convolve `y`:

```python
# w = np.array([0.1, 0.2, 0.5, 0.2, 0.1])
yhat = np.correlate(y, w, "same")
plt.plot(x, yhat, color='red')
```

![](EPUB/media/file125.png "fig:")
Figure 6-12 Use the weight vector of Gaussian distribution to weight the original sinusoidal sampling data, which plays a smooth (smooth) effect

This weight vector calculates the weighted average of the values in `y`. When the weight vector slides along `y`, the calculated value `yhat` is the average weight of the center point `y` of the sliding window and its surrounding `y`. The center point `y` corresponds to the largest weight value, and the weight value corresponding to `y` farther away from the center point is smaller. The resulting vector is equivalent to an average or smoothing process on the original data. It can be seen from Figure 6-12 that the curve corresponding to the convolved data point `(x, yhat)` becomes smoother, that is, the noise in the original data `y` is reduced to a certain extent.

### 6.1.3 Two-dimensional convolution

The reason why the display screens of various electronic devices can display colorful text and image content is that the display screen itself is composed of some pixels, and these pixels are arranged in rows and columns to form a rectangle. In a computer, any image is represented by a pixel matrix. The number of pixels in the image is called the resolution of the image. For example, the image resolution `1024 * 768` means that the number of pixels in the width and height directions of the image rectangle is 1024 and 768. This image represented by a matrix of pixels in a computer is called a **digital image**. As shown in Figure 6-13, it is an image with a resolution of `170 * 225`.

Figure 6-13 Mona Lisa image with 170 * 225 resolution

A pixel at each position in a digital image contains data representing color information. For a color image, it may contain multiple values such as red (R), green (G), blue (B), and transparency (A). For black and white images, it is a value representing brightness. These values are usually represented by byte (8-bit binary) integers, that is, the range of each value is `[0, 255]`. A black and white image is a matrix of such integers, while a color image can be seen as a superposition of matrices corresponding to each color, and each color matrix is called a **channel**. For example, an image consists of red (R), green (G), and blue (B) color images superimposed together.

Figure 6-14 The color image is superimposed by the color images of 3 channels

Of course, computer digital images can also use real numbers in the `[0, 1]` interval to represent pixel values. The following code uses the `io` module of the `skimage` package to read a color image into a numpy multidimensional array `img`, then uses the `rgb2gray` of the `skimage.color` module to convert the color image into a black and white (grayscale) image, and then displays the two images, and prints out the pixel value of a `5*5` window in the middle part.

```python
from skimage import io, transform
from skimage.color import rgb2gray
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline

img = io.imread('image.jpg')
gray_img = rgb2gray(img)  # io.imread('./imgs/image.jpg', as_grey=True)

fig, axes = plt.subplots(1, 2, figsize=(8, 4))
ax = axes.ravel()

plt.subplot(1, 2, 1)
plt.imshow(img)
plt.subplot(1, 2, 2)
plt.imshow(gray_img, cmap='gray')

# img = io.imread('./imgs/lenna.png', as_grey=True)  # load the image as grayscale
# plt.imshow(img, cmap='gray')

print('image matrix size: ', img.shape)      # print the size of image
print('image matrix size: ', gray_img.shape)      # print the size of image

print('\n First 5 columns and rows of the color image matrix: \n', img[150:155, 110:115])
print('\n First 5 columns and rows of the gray image matrix: \n', gray_img[150:155, 110:115])
```

```
image matrix size: (233, 328, 3)
image matrix size: (233, 328)

First 5 columns and rows of the color image matrix:
[[[143 106 88]
  [141 104 86]
  [150 108 94]
  [144 102 88]
  [137 95 81]]

 [[108 78 68]
  [106 76 66]
  [107 77 67]
  [101 71 61]
  [ 92 62 52]]

 [[159 138 133]
  [160 139 134]
  [167 149 145]
  [167 149 145]
  [167 149 145]]

 [[225 213 215]
  [227 215 217]
  [220 216 217]
  [220 216 217]
  [220 216 217]]

 [[206 203 210]
  [207 204 211]
  [204 209 215]
  [204 209 215]
  [204 209 215]]]

First 5 columns and rows of the gray image matrix:
[[0.4414302  0.43358706 0.45457098 0.43104157 0.40359059]
 [0.3280549  0.32021176 0.32413333 0.30060392 0.2653098 ]
 [0.55726275 0.56118431 0.59818275 0.59818275 0.59818275]
 [0.84585961 0.85370275 0.8506749  0.8506749  0.8506749 ]
 [0.80055765 0.80447922 0.81713765 0.81713765 0.81713765]]
```

![](EPUB/media/file126.png)
Figure 6-15 Converting a color image to a black and white (grayscale) image

It can be seen that the color image is read into a three-dimensional numpy array, and the third dimension of the numpy array represents the three color channels of the color image, namely the RGB channel. Each channel is a two-dimensional array (matrix). Therefore, a color image can be viewed as 3 matrices. The `rgb2gray()` function converts a 3-channel color image into a one-channel grayscale image, that is, a two-dimensional array (matrix). The value of each grayscale pixel is computed from the weighted sum of the red (R), green (G), and blue (B) three-color pixel values.

$$ Y = 0.2125 R + 0.7154 G + 0.0721 B $$

From the output results, the RGB color value will be converted from the integer value in the `[0, 255]` interval to the real value in the `[0, 1]` interval.

The color value can also be converted from a real value in the `[0, 1]` interval to an integer value in `[0, 255]`. The following code converts the pixel value of the grayscale image to an integer in the `[0, 255]` interval.

```python
gray_img2 = gray_img * 255
gray_imgs = gray_img2.astype(np.uint8)
print('The values of the first 5 rows and 5 columns of the grayscale matrix: \n', gray_imgs[150:155, 110:115])
```
