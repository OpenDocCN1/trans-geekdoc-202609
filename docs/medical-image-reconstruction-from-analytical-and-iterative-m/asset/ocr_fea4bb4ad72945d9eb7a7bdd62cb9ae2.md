![](bbox=[0.173, 0.103, 0.832, 0.236])

Fig. 6.13: An alternative approach to get the blob effect.

![](bbox=[0.173, 0.303, 0.735, 0.516])

Fig. 6.14: It is advantageous to use a detector bin size that is smaller than the image pixel size.

image size is 256 × 256 × 256 and there is no option on the scanner to acquire 512 × 512 projections, you can acquire data using the 256 × 256 mode and interpolate the data into 512 × 512 arrays during iterative image reconstruction.

# 6.6.4 Iterative methods: accurate modeling

Modeling the system’s point spread function (see Figure 6.15) and patient-induced attenuation and scattering in the matrix A will significantly reduce the deterministic errors between the projections P and the model AX. If you are not ready to model the imaging physics in matrix A, you still have a choice of line-length weighting or area weighting of the image path within the pixel to be used in calculating the elements in matrix A (see Figure 6.16). The freedom to model the imaging system with various geometries and physics effects is the main advantage of using an iterative reconstruction algorithm. We are able to control the errors between the projection data and the