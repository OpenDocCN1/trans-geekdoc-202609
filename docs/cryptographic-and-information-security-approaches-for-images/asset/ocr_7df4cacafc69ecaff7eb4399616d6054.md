are expressed using partial derivatives. A change of the image function can be described by a gradient that points in the direction of the largest growth of the image function.

An edge is a property attached to an individual pixel and is calculated from the image function behavior in the neighborhood of that pixel. As such, an edge is a vector variable with two components, magnitude and direction, where the edge magnitude is the length of the gradient, while the edge direction gives the direction of maximum growth of the function, e.g., from black to white. Edge detection techniques can be used to divide into smooth and edge areas in data hiding to decide the embedding bits.

The gradient magnitude |G| and gradient direction ∂ are continuous image functions calculated as Equations 21.1 and 21.2.

$$|G| = \sqrt{(G_x)^2 + (G_y)^2} \tag{21.1}$$ $$\partial = \tan^{-1} \frac{G_y}{G_x} \tag{21.2}$$

The Sobel is the baseline historical “standard” and still frequently used in published research. Meanwhile, the Canny is a modern “standard,” in the sense that papers describing new edge detectors often compare the results to those of the Canny.

A variety of approaches for edge detection have been proposed for different purposes in different applications. Among the earliest works on edge detection are the Sobel, Prewitt, Roberts, and Laplacian edge detectors, all of which use convolution masks to approximate the first or second derivative of an image. Plus, an optimal filter for edge detection, referred to as the Canny edge detector, has also been proposed. The three performance criteria defined for optimal edge detection are good detection, good localization, and a unique answer for a true edge.

Let a 3 × 3 convolution window be defined as shown in Figure 21.7, where w_i is the intensity levels of each pixel, where i = 1, 2, …, 9.

# 21.3.1 Sobel Edge Detector

With the Sobel edge detector, the task of edge detection is fulfilled by performing a 2D spatial gradient convolution operation on an image using the following two convolution masks (kernels) K_x and K_y, as shown in Figure 21.8, to estimate the gradients G_x and G_y in the horizontal and vertical directions respectively.