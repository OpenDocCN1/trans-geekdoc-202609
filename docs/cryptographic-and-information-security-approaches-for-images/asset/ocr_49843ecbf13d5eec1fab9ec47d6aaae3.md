![](bbox=[0.07, 0.15, 0.88, 0.48])

# Figure 26.7 Scale space SIFT.

First, in order to increase the number of stable features of the image, image dimensions are doubled using linear interpolation, and considered as the first level image in the first octave. Then, the first level image is convolved in an iterative manner with a Gaussian kernel to create Gaussian scale space images in each octave (the left column images in Figure 26.7). Therefore, the Gaussian scale space images are created using Equation 26.1

$$L(x,y,\sigma)=G(x,y,\sigma)\otimes I(x,y)\tag{26.1}$$

In this equation, $I(x,y)$ is the image function, $G(x,y,\sigma)$ is the Gaussian kernel and represents the convolution operator. $G$ represents the Gaussian function calculated according to Equation 26.2.

$$G(x,y,\sigma)=\frac{1}{2\pi\sigma^2}e^{-(x^2-y^2)/2\sigma^2}\tag{26.2}$$

The parameter $\sigma$ indicates the scale of each image and its initial value is equal to $\sigma_0=1/6$ and by using a fixed parameter. Then, DOG images are calculated using the differential between two adjacent Gaussian images according to Equation 26.3 (the images of the right column in Figure 26.7).

$$D(x,y,\sigma)=L(x,y,k\sigma)-L(x,y,\sigma)\tag{26.3}$$

In this equation, $L(x,y,\sigma)$ is the Gaussian image with the $\sigma$ scale, and $L(x,y,k\sigma)$ is the Gaussian image with the $k\sigma$ scale in each octave. As can be seen in Equation 26.3,