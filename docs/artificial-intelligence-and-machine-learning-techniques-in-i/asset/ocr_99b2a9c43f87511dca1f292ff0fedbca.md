as shown in Figure 14.17. This upsampling image goes through an embedding stage to be converted into a set of feature maps. The output of the embedded network is used by one recursive layer, followed by the ReLU activation function (inference stage). Finally, the reconstruction network converts the output feature maps of the inference network into the original HR output image space.

![](bbox=[0.12, 0.285, 0.88, 0.405])

FIGURE 14.16 The basic architecture of ESPCNN for CNN-based image superresolution.

![](bbox=[0.12, 0.47, 0.88, 0.58])

FIGURE 14.17 The basic architecture of DRCN for CNN-based image superresolution.

# 14.2.3.9 DEEP LAPLACIAN PYRAMID SUPERRESOLUTION NETWORK

In contrast to one-step upsampling, the authors^9 used a progressively pyramidical approach to reconstruct the residuals of subbands of HR images at multiple levels up to an enlargement scale factor of 8x. The first, second, and last subnetworks are residues of 2x, 4x, and 8x. The cumulative sum of these residual images gives the final reconstructed HR output image. In this framework, the authors used three types of layers, convolution, leaky ReLU, and deconvolution layers, as shown in Figure 14.18. The leaky ReLU used the negative slope up to 0.2. LapSRN first used new loss functions, such as the Charbonier loss function, which can resolve outlier problems. The number of fitters and kernel size are 64, 3 x 3 in the