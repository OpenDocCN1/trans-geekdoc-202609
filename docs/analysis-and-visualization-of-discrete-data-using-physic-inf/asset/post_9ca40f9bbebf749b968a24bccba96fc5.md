
VR/AR: VR/AR technology [13] can also be used to visualize data in three-dimensional space.

## 2.1.3.4. Particle-based volume rendering

For 3-D plots, this section describes one of the typical visualization methods, volume rendering [14]. This visualization method successfully represents the overall characteristics of the data, including its internal structure, by representing the target volume data as a semitransparent cloud. This section focuses on physical data visualization techniques based on volume rendering.

We will discuss PVBR (Particle-Based Volume Rendering) [15], in which the given physical data comprise opaque emitting particles to perform volume rendering. PBVR is a simple method that basically consists of two processing steps: particle generation and particle projection. Particle generation first requires an estimate of the particle density. PBVR was originally a visualization technique for continuously distributed physical data. Therefore, it was necessary to determine how to sample for that defined area. This time, however, the physical data are defined at discrete points. Thus, the particle density is determined by the originally given points. Next, the particle radius is determined by the user-specified transfer function for the opacity according to Equation (2.4).

The particle density $\rho$ means the number of particles per unit volume. Consider a sphere of a certain radius and align each particle's position with the center of the sphere. The particles inside the sphere are counted and divided by the volume of the sphere to obtain the number density, which is the particle density $\rho$.

In ray casting, if the radius of the ray is $r$, consider a cylindrical interval of a certain length $l$ along a ray and assume that the particles are Poisson distributed in this interval. The Poisson distribution is one of the probability distributions in probability theory and is used for random variables that take non-negative integer values, not continuous values. In particular, the Poisson distribution with mean $\lambda$ is expressed by the following probability density function:

$$p(k; \lambda) = (\lambda^k e^{-\lambda})/k! \tag{2.1}$$

In this function, $k$ represents a non-negative integer value (0, 1, 2, 3 ...), $\lambda$ represents the positive mean, $e$ represents the base of the natural logarithm, and $k!$ represents the factorial of $k$.

The Poisson distribution is often used to represent the number of times independent events occur. For example, it is used to represent the number of times in which a certain event occurs in a given time frame, such as an accident or breakdown. The Poisson distribution is also used as an approximation for many events because the mean and variance are equal. In terms of physical data analysis and visualization, it is a means of expressing, for example, the probability of the number of particles generated in a particular spatial region.

Ray casting is a method of determining the pixels of an image along the line of sight from within a three-dimensional scene. This allows a three-dimensional scene to be projected onto a two-dimensional screen. Ray casting is often used to create realistic images because it allows physically accurate visualization of shadows, reflections, and other physical phenomena.

Light can travel along a ray without any obstruction in a space with a defined group of particles when the number of particles present in that space is zero. This probability is called transparency. The transparency $t$ can be calculated as

$$t = e^{-\rho \pi r^2 l}, \tag{2.2}$$

assuming that particles are generated according to the Poisson distribution described before since the volume is now $\pi r^2 l$ and the particle density is $\rho$. The sum of opacity and transparency is 1. Thus, the opacity can be calculated as follows:

$$\alpha = 1 - t = 1 - e^{-\rho \pi r^2 l} \tag{2.3}$$

The particle radius $r$ can be calculated using the particle density $\rho$, the opacity value $\alpha$, and the ray segment length $\Delta t$ used in volume ray casting:

$$r = \sqrt{\frac{\log(1-\alpha)}{\pi \rho \Delta t}} \tag{2.4}$$

The opacity value $\alpha$ is calculated by a user-specified transfer function. The transfer function shows the relationship between physical data values and opacity. A high opacity is set for data values that are to be emphasized, and a low opacity is set for physical data values that are not.

The first step in PBVR is to generate particles in the coordinates where the physical data are defined according to the particle radius given in the above equation. The second step is to project the generated particles onto the image plane. The particles are projected onto the image surface, and pixel values are calculated for each pixel. This basic processing step is repeated several times. The pixel values are added to the frame buffer and then divided by the number of iterations to obtain the final pixel values by averaging.

In PBVR, the projected images from the generated particles are added to the image plane to calculate the luminance values at the corresponding pixels. PBVR makes particles completely opaque so that when viewed by the eye, light, $c_i (i = 1, \ldots, n)$, from the particles at the back is blocked by the particles in the front. This effect can be achieved using the $Z$-buffer algorithm. The pre-projection sorting and alpha compositing processes typically required in volume rendering are unnecessary. The translucency effect is achieved in this averaging process.

In the projection process of the generated particles, the $Z$-buffer algorithm is used to keep the projected images of the particles closest to the eye position, and pixel values are calculated using these images. As particles are opaque, they do not require alpha compositing or reordering according to their distance from the eye position. For the last remaining particles, color mapping and shading calculations are performed. Color mapping uses a color transfer function to convert scalar data calculated by interpolation at the particle position into color data. The shading is determined by calculating the brightness based on the interpolated gradient vector and the light source vector, both of which are computed at the particle's position, and then multiplying this value by the color data. To calculate the final pixel values, we discuss ensemble averaging (Figure 2.4).

An ensemble is a set of results from multiple iterations of conceptually equivalent trial experiments. Each set of ensembles has the same attribute values for particle radius and particle density. In the ensemble averaging method, a trial experiment is assumed to be a single image creation process consisting of particle generation and projection with the same attribute values. The seed for random number generation is changed for each trial experiment. In ensemble averaging, the final pixel value is the average of the pixel values over all iterations. Therefore, if the $i$ luminance value is $B_i$, the final pixel value is calculated as follows:

![](img/fa57e7010b16a211d5cf69ebb17e416e_42_0.png)

In this equation, $L_R$ represents the number of iterations and $B^{total} (L_R)^i$ represents the final luminance value from $L_R$ iterations. Also, $\langle B^i \rangle$ represents the ensemble mean of $B^i$.

![](img/fa57e7010b16a211d5cf69ebb17e416e_43_0.png)

The variance of the final luminance value, with the luminance value $B_{i}$ as the random variable, is expanded as follows:

$$\begin{align} B_{\text{Var}}^{\text{total}}(L_R)&=\text{Var}\left(\sum_{i=1}^{L_R}\frac{B^i}{L_R}\right)\\ &=\frac{1}{L_R^2}\left\{\sum_{i=1}^{L_R}\text{Var}\left(B^i\right)+2\sum_{i,j,i<j}\text{Cov}\left(B^i,B^j\right)\right\}\tag{2.6} \end{align}$$

The luminance values $B_{i}$ are independent of each other. Thus, the value of the covariance $\operatorname{Cov}(B_{i},B_{j})$ is 0. The variance of $B_{i}$ can be determined as $B_{\text{var}}$ regardless of the number of iterations. Thus, the standard deviation of the final luminance value is as follows:

$$B_{\mathrm{Var}}^{\text {total }}\left(L_{R}\right)=\frac{B_{\mathrm{Var}}}{L_{R}} \quad (2.7)$$

Note that the more the number of iterations used, the better the image quality becomes. This method is often used to improve the image quality of noisy images such as satellite images. The ensemble averaging method can be used to control the level of detail in the display of volume rendering results. Creating an average image with a small number of iterations is
