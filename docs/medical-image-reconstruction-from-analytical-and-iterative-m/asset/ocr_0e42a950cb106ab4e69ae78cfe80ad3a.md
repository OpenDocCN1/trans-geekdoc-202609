![](bbox=[0.105, 0.095, 0.55, 0.215])

Fig. 9.21: A 4-input/3-output neural network can be constructed by combining three 4-input/1-output networks.

![](bbox=[0.105, 0.285, 0.485, 0.395])

Fig. 9.22: An autoencoder uses the same input and output to train this network. The dimension of x̄ is greater than the dimension of ȳ. Here ȳ is the extracted principal feature vector from the original vector x̄.

same data as both the input and the output as shown in Figure 9.22. Then the availability of the training data becomes relatively less challenging.

# 9.3 Image reconstruction as an n-tuple to m-tuple mapping

In Section 9.2, we learned that a (shallow or deep) neural network can accurately approximate an n-tuple to m-tuple mapping. If we treat measurements as the input n-tuple and a reconstructed image as the output m-tuple, there exist neural networks that can perform this mapping. Here, the input n-tuple is the measurements represented in the vector format, and the output m-tuple is the reconstructed image represented in the vector format. These neural networks can be obtained by training with many measurements/reconstruction pairs. A drawback of this naive approach is that a fully connected layer (i.e., a dense layer) is necessary to map the measurement-domain images into the reconstruction-domain images (see Figure 9.23). Due to the large sizes of the measurements and the images, the number of the parameters in the fully connected layer can be too large, especially in 3D imaging, for a regular computer. This approach currently may not be the most practical choice.

A more practical neural network image reconstruction approach is to use the FBP algorithm or the iterative ML-EM algorithm to perform the mapping between the sinogram domain and the image domain and to use the neural network to process the images in the sinogram domain or in the image domain. The image processing tasks include denoising, deblurring, and super-resolution. The image processing neural