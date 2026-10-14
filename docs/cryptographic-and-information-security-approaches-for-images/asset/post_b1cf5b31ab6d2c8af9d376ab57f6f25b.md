
![](img/f4c3bcc9f5332d57a8ec85a75075f8da_626_0.png)

Figure 21.5 Flowchart of interpolation and edge detection based data hiding methods.

When edge detection techniques are used, how many bits can be embedded? It came from the basic idea that it is difficult to discriminate the distortion in edge areas even though the embedding bits are larger than in smooth areas.

The cover image is easily calculated from the original image and used as the source for the data hiding method. An edge detection algorithm is then applied to divide the cover image into edge and non-edge areas, as more secret data can be embedded in edge areas, plus a different data hiding method is used when embedding the secret data in edge and non-edge areas.

In this chapter, reversible data hiding methods using image interpolation techniques and edge detection techniques are described.

The rest of this chapter is organized as follows. In Sections 21.2 and 21.3, interpolation and edge detection techniques are explained. Important properties of data hiding and performance analysis measurements are treated in Section 21.4. The previous interpolation and edge detection based reversible data hiding methods are described in Section 21.5. The conclusions are presented in Section 21.6.

## 21.2 Interpolation Techniques

Interpolation techniques are the problem of approximating the value of a function for a non-given point in some space [70]. Image interpolation techniques have many applications which are as old as computer graphics and image processing field [71–82]. There is generally a trade-off between speed and degree to which the visual artifacts are reduced. The capability of digitally interpolating images to a higher resolution with a good image quality is important in many applications of electronic imaging. Plus, the sharpness of edges and freedom from artifacts are two critical factors in the perceived quality of an interpolated image, along with ease of computation. The nearest neighbor method finds the closest corresponding pixel in the source image for each pixel in the destination image. Yet, nearest neighbor interpolation suffers from normally unacceptable aliasing effects when enlarging and reducing images. Meanwhile, bilinear interpolation determines the grey level from the weighted average of the four closest pixels to the specified input coordinates and assigns that value to the output coordinates. Although this method generates an image with a smoother appearance than nearest neighbor interpolation, the grey level values are altered in the process, resulting in blurring or a loss of image resolution. Therefore, due to these changes in the grey level values, any image classification process must be performed before the interpolation. As such, bilinear interpolation requires 3 to 4 times the computation time of the nearest neighbor method. There is also a great variety of methods, like B-spline, cubic, bi-cubic, Lagrange, and Gaussian interpolation.

### 21.2.1 Nearest Neighbor Interpolation

Nearest neighbor interpolation, also known as proximal interpolation, is a simple method of multivariate interpolation in one or more dimensions [70]. Nearest neighbor is the basic algorithm and it requires the least processing time of all the interpolation algorithms which has the effect of simply making each pixel bigger.

While the nearest neighbor interpolation method is simple to implement, it often produces undesirable artifacts, such as the distortion of straight edges in images with a high resolution. Smoother results can be obtained by using more sophisticated techniques, such as cubic convolution interpolation. Yet, the price paid for smoother approximations is an additional computational burden.

The basis function associated to nearest neighbor interpolation is the simplest of all, since it is made of a square pulse. It satisfies the partition of unity, provided a slight asymmetry is introduced at the edges of the square pulse.

### 21.2.2 Bilinear Interpolation

For general purpose image processing, a bilinear interpolation approach that uses the gray levels of the four nearest neighbors is usually adequate. The bilinear interpolation technique considers the closest 2 × 2 neighborhood of known pixel values surrounding the unknown pixel. Then, it takes a weighted average of these 4 pixels to reach its final interpolated value. This results in much smoother looking images than nearest neighbor. Bilinear interpolation determines the grey level from the weighted average of the four closest pixels to the specified input coordinates and assigns that value to the output coordinates. Although this method generates an image with a smoother appearance than nearest neighbor interpolation, the grey level values are altered in the process, resulting in blurring or a loss of image resolution. Therefore, due to the changes in the grey level values, any image classification process must be performed before the interpolation. Thus, bilinear interpolation requires 3 to 4 times the computation time of the nearest neighbor interpolation method.

### 21.2.3 Bi-cubic Interpolation

The bi-cubic interpolation technique goes one step beyond bilinear by considering the closest 4 × 4 neighborhood of known pixels that will total 16 pixels. Since these are at various distances from the unknown pixel, closer pixels are given a higher weighting in the calculation. Bi-cubic algorithm produces noticeably sharper images than the previous two methods, and is perhaps the ideal combination of processing time and output quality. For this reason, it is a standard in many image editing programs, printer drivers, and in-camera interpolation.

### 21.2.4 Higher Order Interpolation

There are many other interpolators which take more surrounding pixels into consideration and are thus also much more computationally intensive. These algorithms include spline and sinc functions, and retain the most image information after an interpolation. They are therefore extremely useful when the image requires multiple rotations or distortions in separate steps. However, for single-step enlargements or rotations, these higher-order algorithms provide diminishing visual improvement as processing time is increased [82].

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_629_0.png)

Figure 21.6 Result images of some interpolation techniques. (a) Baboon, (b) Nearest Neighbor, (c) Bilinear, (d) Cubic, (e) Lena, (f) Nearest Neighbor, (g) Bilinear, (h) Cubic.

For 256 × 256 gray images, results of interpolation techniques are shown in Figure 21.6.

## 21.3 Edge Detection Techniques

Edge detection techniques are an important topic in digital image processing. Edges are usually considered an important feature of images and widely applied to high level applications such as image compression, region segmentation, pattern recognition, image retrieval, data hiding and so on. Detecting edge boundaries is based on changes in the pixel intensity, and several basic schemes such as Sobel, Roberts, Prewitt, Laplacian, and Canny have been proposed [83–89].

Edge detectors are a collection of very important local image pre-processing methods used to locate changes in the intensity function; edges are pixels where this function changes abruptly. Calculus describes the changes of continuous functions using derivatives; an image function depends on two variables—coordinates in the image plane—and so operators describing edges are expressed using partial derivatives. A change of the image function can be described by a gradient that points in the direction of the largest growth of the image function.

An edge is a property attached to an individual pixel and is calculated from the image function behavior in the neighborhood of that pixel. As such, an edge is a vector variable with two components, magnitude and direction, where the edge magnitude is the length of the gradient, while the edge direction gives the direction of maximum growth of the function, e.g., from black to white. Edge detection techniques can be used to divide into smooth and edge areas in data hiding to decide the embedding bits.

The gradient magnitude |G| and gradient direction θ are continuous image functions calculated as Equations 21.1 and 21.2.

$$|G| = \sqrt{(G_x)^2 + (G_y)^2} \tag{21.1}$$

$$\theta = \tan^{-1} \frac{G_y}{G_x} \tag{21.2}$$

The Sobel is the baseline historical “standard” and still frequently used in published research. Meanwhile, the Canny is a modern “standard,” in the sense that papers describing new edge detectors often compare the results to those of the Canny.

A variety of approaches for edge detection have been proposed for different purposes in different applications. Among the earliest works on edge detection are the Sobel, Prewitt, Roberts, and Laplacian edge detectors, all of which use convolution masks to approximate the first or second derivative of an image. Plus, an optimal filter for edge detection, referred to as the Canny edge detector, has also been proposed. The three performance criteria defined for optimal edge detection are good detection, good localization, and a unique answer for a true edge.

Let a 3 × 3 convolution window be defined as shown in Figure 21.7, where w_i is the intensity level of each pixel, where i = 1, 2, …, 9.

### 21.3.1 Sobel Edge Detector

With the Sobel edge detector, the task of edge detection is fulfilled by performing a 2D spatial gradient convolution operation on an image using the following two convolution masks (kernels) K_x and K_y, as shown in Figure 21.8, to estimate the gradients G_x and G_y in the horizontal and vertical directions respectively.
