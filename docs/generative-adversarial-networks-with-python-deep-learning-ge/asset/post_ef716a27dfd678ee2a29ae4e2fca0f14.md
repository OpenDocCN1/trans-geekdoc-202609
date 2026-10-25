
Without auxiliary stabilization techniques, this training procedure is notoriously brittle, requiring finely-tuned hyperparameters and architectural choices to work at all.

> — Large Scale GAN Training for High Fidelity Natural Image Synthesis, 2018.

Most of the improvements to the training process have focused on changes to the objective function or constraining the discriminator model during the training process.

Much recent research has accordingly focused on modifications to the vanilla GAN procedure to impart stability, drawing on a growing body of empirical and theoretical insights. One line of work is focused on changing the objective function [...] to encourage convergence. Another line is focused on constraining D through gradient penalties [...] or normalization [...] both to counteract the use of unbounded loss functions and ensure D provides gradients everywhere to G.

> — Large Scale GAN Training for High Fidelity Natural Image Synthesis, 2018.

More recently, work has focused on the effective application of the GAN for generating both high-quality and larger images. One approach is to try scaling up GAN models that already work well.

## 27.3 Develop Better GANs by Scaling Up

The BigGAN is an implementation of the GAN architecture designed to leverage the best from what has been reported to work more generally. It was described by Andrew Brock, et al. in their 2018 paper titled Large Scale GAN Training for High Fidelity Natural Image Synthesis and presented at the ICLR 2019 conference. Specifically, the BigGAN is designed for class-conditional image generation. That is, the generation of images using both a point from latent space and image class information as input. Example datasets used to train class-conditional GANs include the CIFAR or ImageNet image classification datasets that have tens, hundreds, or thousands of image classes. As its name suggests, the BigGAN is focused on scaling up the GAN models. This includes GAN models with:

- More model parameters (e.g. more feature maps).
- Larger Batch Sizes
- Architectural changes

We demonstrate that GANs benefit dramatically from scaling, and train models with two to four times as many parameters and eight times the batch size compared to prior art. We introduce two simple, general architectural changes that improve scalability, and modify a regularization scheme to improve conditioning, demonstrably boosting performance.

> — Large Scale GAN Training for High Fidelity Natural Image Synthesis, 2018.

The BigGAN architecture also introduces a truncation trick used during image generation that results in an improvement in image quality, and a corresponding regularizing technique to better support this trick. The result is an approach capable of generating larger and higher-quality images, such as 256 × 256 and 512 × 512 images.

When trained on ImageNet at 128 × 128 resolution, our models (BigGANs) improve the state-of-the-art [...] We also successfully train BigGANs on ImageNet at 256×256 and 512 × 512 resolution ...

> — Large Scale GAN Training for High Fidelity Natural Image Synthesis, 2018.

## 27.4 How to Scale-Up GANs With BigGAN

The contribution of the BigGAN model is the design decisions for both the models and the training process. These design decisions are important for both re-implementing the BigGAN, but also in providing insight on configuration options that may prove beneficial with GANs more generally. The focus of the BigGAN model is to increase the number of model parameters and batch size, then configure the model and training process to achieve the best results. In this section, we will review the specific design decisions in the BigGAN.

### 27.4.1 Self-Attention Module and Hinge Loss

The base for the model is the Self-Attention GAN, or SAGAN for short, described by Han Zhang, et al. in the 2018 paper titled Self-Attention Generative Adversarial Networks. This involves introducing an attention map that is applied to feature maps, allowing the generator and discriminator models to focus on different parts of the image. This involves adding an attention module to the deep convolutional model architecture.

![](img/443014fed0f53a293f6ece3b211c1603_600_0.png)

Figure 27.1: Summary of the Self-Attention Module Used in the Self-Attention GAN. Taken from: Self-Attention Generative Adversarial Networks.

Additionally, the model is trained via hinge loss, commonly used for training support vector machines.

In SAGAN, the proposed attention module has been applied to both generator and discriminator, which are trained in an alternating fashion by minimizing the hinge version of the adversarial loss

> — Self-Attention Generative Adversarial Networks, 2018.

The BigGAN uses the model architecture with attention modules from SAGAN and is trained via hinge loss. Appendix B of the paper titled Architectural Details provides a summary of the modules and their configurations used in the generator and discriminator models. There are two versions of the model described: BigGAN and BigGAN-deep, the latter involving deeper resnet modules and, in turn, achieving better results.

### 27.4.2 Class Conditional Information

The class information is provided to the generator model via class-conditional batch normalization. This was described by Vincent Dumoulin, et al. in their 2016 paper titled A Learned Representation For Artistic Style. In the paper, the technique is referred to as conditional instance normalization that involves normalizing activations based on the statistics from images of a given style, or in the case of BigGAN, images of a given class.

We call this approach conditional instance normalization. The goal of the procedure is to transform a layer's activations x into a normalized activation z specific to painting style s.

> — A Learned Representation For Artistic Style, 2016.

Class information is provided to the discriminator via projection. This is described by Takeru Miyato, et al. in their 2018 paper titled Spectral Normalization for Generative Adversarial Networks. This involves using an integer embedding of the class value that is concatenated into an intermediate layer of the network.

Discriminator for conditional GANs. For computational ease, we embedded the integer label y in 0, ..., 1000 into 128 dimension before concatenating the vector to the output of the intermediate layer.

> — Spectral Normalization for Generative Adversarial Networks, 2018.

Instead of using one class embedding per class label, a shared embedding was used in order to reduce the number of weights.

Instead of having a separate layer for each embedding, we opt to use a shared embedding, which is linearly projected to each layer's gains and biases. This reduces computation and memory costs, and improves training speed (in number of iterations required to reach a given performance) by 37%.

> — Large Scale GAN Training for High Fidelity Natural Image Synthesis, 2018.

### 27.4.3 Spectral Normalization

The weights of the generator are normalized using spectral normalization. Spectral normalization for use in GANs was described by Takeru Miyato, et al. in their 2018 paper titled _Spectral Normalization for Generative Adversarial Networks_. Specifically, it involves normalizing the spectral norm of the weight matrix.

Our spectral normalization normalizes the spectral norm of the weight matrix W so that it satisfies the Lipschitz constraint σ(W) = 1:

> — _Spectral Normalization for Generative Adversarial Networks_, 2018.

The efficient implementation requires a change to the weight updates during minibatch stochastic gradient descent, described in _Appendix A_ of the spectral normalization paper.

**Algorithm 1 SGD with spectral normalization**

- Initialize \(\bar{\mathbf{u}}_l \in \mathcal{R}^{d_l}\) for \(l = 1, \dots, L\) with a random vector (sampled from isotropic distribution).
- For each update and each layer \(l\):
  1. Apply power iteration method to a unnormalized weight \(W^l\):
     \(\bar{\mathbf{v}}_l \leftarrow (W^l)^T \bar{\mathbf{u}}_l / \|(W^l)^T \bar{\mathbf{u}}_l\|_2\) (20)
     \(\bar{\mathbf{u}}_l \leftarrow W^l \bar{\mathbf{v}}_l / \|W^l \bar{\mathbf{v}}_l\|_2\) (21)
  2. Calculate \(\bar{W}_{SN}\) with the spectral norm:
     \(\bar{W}_{SN}^l(W^l) = W^l / \sigma(W^l)\), where \(\sigma(W^l) = \bar{\mathbf{u}}_l^T W^l \bar{\mathbf{v}}_l\) (22)
  3. Update \(W^l\) with SGD on mini-batch dataset \(\mathcal{D}_M\) with a learning rate \(\alpha\):
     \(W^l \leftarrow W^l - \alpha \nabla_{W^l} \ell(\bar{W}_{SN}^l(W^l), \mathcal{D}_M)\) (23)

Figure 27.2: Algorithm for SGD With Spectral Normalization. Taken from: Spectral Normalization for Generative Adversarial Networks.

### 27.4.4 Update Discriminator More Than Generator

In the GAN training algorithm, it is common to first update the discriminator model and then to update the generator model. The BigGAN slightly modifies this and updates the discriminator model twice before updating the generator model in each training iteration.

### 27.4.5 Moving Average of Model Weights

The generator model is evaluated based on the images that are generated. Before images are generated for evaluation, the model weights are averaged across prior training iterations using a moving average. This approach to model weight moving average for generator evaluation was described and used by Tero Karras, et al. in their 2017 paper titled _Progressive Growing of GANs for Improved Quality, Stability, and Variation_.

... for visualizing generator output at any given point during the training, we use an exponential running average for the weights of the generator with decay 0.999.

> — _Progressive Growing of GANs for Improved Quality, Stability, and Variation_, 2017.
