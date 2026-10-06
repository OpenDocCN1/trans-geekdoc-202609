# CHAPTER 11

# Convolutional neural networks

We have seen in Chap. 10 that neural networks are very versatile and flexible machine learning models. However, a downside of fully connected networks is that their linear layers have large numbers of parameters. Let's take an example of typical image, with 300 x 200 pixels and 3 channels (red, green and blue). This image has 300 x 200 x 3 = 180,000 features. If we want to implement a neural network with second layer of size 150 x 100 x 6, which has 90,000 features, our linear layer have 180,000 x 90,000 = 16.2 billion parameters. A network with such a number of parameters would be computationally expensive to store and optimize and would certainly result in overfitting. Medical images tend to be even larger and 3D, for example, a modern MRI of the brain can have dimensions of 300 x 200 x 200 voxels.

A solution to this problem arrived in computer vision in the form of convolutional layers [28]. In a convolutional layer, the weights are shared between different features, which significantly reduces the number of parameters. At the same time, the convolutional neural networks are inspired by the mammalian visual system works and, therefore, are well adapted for visual tasks, such as object recognition. In this chapter we will explain these concepts and how to implement a single convolutional neural network to classify brain MR images of term and preterm babies. We will conclude the chapter by implementing a convolutional neural network for segmentation of brain structures in neonatal MRI.

# 11.1. Why convolution?

# 11.1.1 Convolution operation

Convolutions are used for filtering of images, e.g., to smooth or denoise images or detect the edges. The desired effect is achieved by hand-engineering a filter, also called a convolution kernel, that is repeatedly applied to all locations of the image to produce a new filtered image. Fig. 11.1 shows examples of the resulting filtered images and the corresponding filters. Vertical and horizontal edges are obtained using a Sobel filter and the blurred image by a Gaussian filter.

So, how does the convolution or filtering work? Let's denote the image pixels $x_{ij}$ and elements of a filter $w_{kl}$. In our case, the values of $k$ and $l$ are $-1$ and $0$, and we have $3 	imes 3$ convolution kernels (Fig. 11.1, bottom row). The convolution can be