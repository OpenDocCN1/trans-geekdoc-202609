
![](img/332d06e0447dbfd85ea7d2fb553468f3_201_0.png)

Figure 3.27: Visualization of the image augmentation through (a) rotation and (b) mirroring. The arrows indicate the orientation of the images.

## 3.8.3 Network architecture 12

The code provided in the official PyTorch tutorial [310] served as a starting point for the DCGAN structure and was gradually adjusted to work with the given training data set. For larger image resolutions, the DCGAN structure by Milad Hasani [311] was found to work well. Inspired by this, a network structure for even larger resolutions was developed (cf. Figure 3.28). The generator takes a Gaussian sampled noise vector with 100 entries and uses a combination of transposed convolutional layers, batch normalization and ReLU activation to output images with a resolution of 256 px × 256 px. Tanh was used as final activation. In the discriminator, convolutional layers, batch normalization and Leaky ReLU activations were used. The latter was replaced by a Sigmoid activation in the final layer. The entire code can be found in the according GitHub repository linked in Chapter 9.

12 This section is extracted from the author's publication [275] with only slight linguistic changes.

![](img/332d06e0447dbfd85ea7d2fb553468f3_202_0.png)

Figure 3.28: Graphic of the final DCGAN network architecture. Designed with the help of the latex code in the GitHub repository of Haris Iqbal [291]. Extracted from Blarr et al. [275].

In a first step, all images from the input data set are loaded as PyTorch tensors (one 3D array per image of x value, y value and gray value) and normalized to values in the range [-1,1] to avoid coefficients equal to 0. The image tensors are then shuffled and divided into individual batches. The last non-full batch is dropped, i.e. the images are not used for training. Unlike in the original DCGAN paper [250], no initial weights were defined as this was found to increase the likelihood of a stable training process for this particular configuration. The training loss is calculated with the ADAM optimizer based on the commonly used BCE. Setting the ADAM optimizer parameters to \((\beta_1, \beta_2)\) = (0.5, 0.999) was found to improve the stability of training just as described by Radford et al. [250]. For multi-GPU parallelization and therefore a faster training, NVIDIA CUDA with the "DataParallel" method of PyTorch is used [310].

The actual training process follows this scheme: First, one batch of generated images is created based on random noise vectors and associated with the corresponding labels (0 for generated). These images are then fed to the discriminator together with one batch containing only real images from the training data set (labeled 1 for real). Based on the average of the calculated losses (following Equation (2.123)) on both batches, the discriminator biases are updated. As a next step, again Gaussian sampled random noise vectors are passed to the generator which outputs one batch of generated images. Based on the discriminator feedback on these images, the generator is then updated. Every epoch consists of multiple iterations and ends if the whole input data set was processed this way. It shall be mentioned that the losses were saved after every single iteration, whereas the Fréchet inception distance (FID) was only calculated after every epoch in order to avoid slowing down the training too much. Additionally, after every epoch a number of generated images based on fixed noise vectors was saved in order to visually analyze the training progress later on. Due to the computational effort needed, the image quality assessment was performed in a subsequent step.

## 3.8.4 Quantitative quality metrics 13

Apart from the visual and hence qualitative evaluation of the generated images, multiple quantitative measures have been developed in recent years in order to assess the performance of a generative network [312]. Of those, the FID and nearest neighbor evaluations based on two different metrics were conducted that are outlined in the following.

13 This section is extracted from the author’s publication [275] with only slight linguistic changes.

## 3.8.4.1 Fréchet inception distance (FID) 14

The Fréchet inception distance [313], as an advancement of the inception score [314], is a metric to determine the difference between feature vectors of generated samples and real training images. It is based on the Inception v3 Network [315] that is pre-trained on the ImageNet [316]. The FID compares the activations from the penultimate layer of the inception network of real \( p_r(x) \) and generated \( p_g(x) \) images [317]. The distributions of these real and generated images are thereby modeled as multi-dimensional Gaussians that are defined by their mean \( \mu \) and covariance \( cov(x, y) \). The distance is hence defined by

\( d^2((\mu_r, cov_r)(\mu_g, cov_g)) = |\mu_r - \mu_g|^2 + \text{tr}(cov_r + cov_g - 2(cov_r cov_g)^{1/2}). \) (3.18)

Thus, a lower FID value corresponds to a smaller distance between the two distributions of real and generated data. The FID values are dependent on the corresponding resize or compression operations and can even improve for higher compressed images (i.e. poorer resolution) [318]. The FID values must therefore be regarded as a benchmark for the quality of images created using the same network in different epochs and are of limited suitability for comparing different networks. The FID was calculated of 128 generated images per epoch.

## 3.8.4.2 Nearest neighbor procedures 15

A question that arises quite naturally is whether a network reproduces only the training data, which involves overfitting. To address this, a k-nearest neighbor search is performed, which calculates the k nearest neighbors from the entire training data set to a given generated image. This is equivalent to finding the images in the training data set that have the smallest distance to the generated image based on a suitable distance measure. In the following, we briefly introduce the Euclidean distance and the computationally more expensive structural similarity index measure (SSIM), as these serve as the basis of the k-nearest neighbor search in the results of this paper.

- Euclidean distance (ED)

The Euclidean distance being one of the simplest ways to determine the similarity between two arrays and the most common distance measure for nearest neighbor search [319] can be calculated for two gray scale images \(\boldsymbol{x} = (x_1, x_2, ..., x_{MN})\) and \(\boldsymbol{y} = (y_1, y_2, ..., y_{MN})\) of size \(M\) px \(\times\) \(N\) px as:

\(d^2_{\text{E}}(\boldsymbol{x}, \boldsymbol{y}) = \sum_{k=1}^{MN} (x_k - y_k)^2 \quad (3.19)\)

with the gray levels at the location \((k, l)\) given as \(x_{kN+l}\) and \(y_{kN+l}\). The smaller the calculated value, the higher the similarity. As there are major limitations like the non-consideration of spatial relationships, the nearest neighbors found through the calculation of the ED sometimes do not match human perception. Therefore, a second distance metric is considered. The ED is still calculated due to its computational simplicity.

- Structural similarity index measure (SSIM)

Another option for the evaluation of nearest neighbors of GANs is the SSIM [312] introduced by Wang et al. in 2005 [319]. It focuses especially on factors that are also relevant to human perception through evaluating luminance L, contrast C and structure S. Those three aspects are separately mathematically defined through means \(\mu_x\) and \(\mu_y\), standard deviations \(\sigma_x\) and \(\sigma_y\) and cross-correlation coefficient \(\sigma_{xy}\) of the two images \(\boldsymbol{x}\) and \(\boldsymbol{y}\). The detailed formulas can be found in the paper by Wang et al. [319]. In order to avoid instabilities for small values, constants \(C_i\) are added.

The product of these three quantities relatively weighted through three power parameters \(\alpha > 0\), \(\beta > 0\) and \(\gamma > 0\) results in the \(SSIM(x, y)\). Choosing \(\alpha = \beta = \gamma = 1\) and \(C_3 = C_2/2\) leads to the following SSIM formula:

\(SSIM(x, y) = \frac{(2\mu_x\mu_y + C_1)(2\sigma_{xy} + C_2)}{(\mu_x^2 + \mu_y^2 + C_1)(\sigma_x^2 + \sigma_y^2 + C_2)}.\) (3.20)

The values range between (-1, 1] with a value of one corresponding to optimal similarity, hence equality of the images. It shall be mentioned that the SSIM is usually not calculated globally but instead inside of a Gaussian window covering a local square patch which slides pixel by pixel across the entire image. In the so-called mean-SSIM or MSSIM all local values are summed up and divided by the total number of windows \(m\) in order to obtain one single quality measure. Conventionally, the MSSIM is often referred to as just the SSIM, which will be handled similarly in this work.

## 3.8.5 Overview of all chosen parameters 16

All values of important parameters are summarized in the following list.

- Image resolution 256 px x 256 px
- Learning rate \(r_1\) 0.0001
- ADAM optimizer \((\beta_1, \beta_2) = (0.5, 0.999)\)
