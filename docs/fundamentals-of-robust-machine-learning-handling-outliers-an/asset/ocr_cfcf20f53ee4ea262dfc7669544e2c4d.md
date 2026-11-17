# 10.3 Example: MNIST Dataset

In this section, we take on a more challenging problem in the domain of multi-class classification with neural networks to compare LCNN against CENN (refer to Chapter 9) using the MNIST dataset.¹ Note that we consider fully connected networks rather than the advanced convolutional neural network (CNN). A CNN is more appropriate for image recognition but our goal is to compare CENN and LCNN so a fully connected architecture is sufficient for our purposes. As such, we will use the same NN architecture for both methods and the same learning rate. The objective is to tackle a large multi-class problem to determine if LCNN is suitable for this purpose.

The MNIST dataset consists of 42,000 handwritten numbers from 0 to 9 (total of 10 digits) in the form of 28 × 28 grayscale images with the objective of correctly recognizing as many numbers as possible using neural networks. For a fully connected architecture, each 28 × 28 image must first be unrolled to 784 pixels, each of which represents an input variable. Associated with each image is a corresponding label of 0–9, i.e. the digit being represented by the image. The dataset has no known outliers but the robust approach has a habit of finding outliers even when none are expected.

A sampling of 10 such digits is provided in Figure 10.3. They are hand-drawn digits such as would be used in a US zip code or street address on letters to be mailed. Recognizing digits is challenging since every person writes each digit in a slightly different way. The NN is given a subset of these images for training purposes, while the rest are used for testing purposes.

The MNIST dataset falls into the category of multi-class classification. Rather than one output of the network, we need 10 outputs—one for each digit to be recognized. The standard training approach is to apply a given image at the input and then set the corresponding output to 1 while setting all other outputs to 0. For example, an image of the number 3 would be encoded at the output as 0001000000, the

![](bbox=[0.112, 0.565, 0.872, 0.81])

Figure 10.3 Ten representative images from the MNIST dataset.

1 This dataset is available on the website kaggle.com in the Competitions section.