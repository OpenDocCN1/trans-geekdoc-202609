![](bbox=[0.16, 0.15, 0.84, 0.34])

Figure 5.1: Example of the Generator Model Architecture for the DCGAN. Taken from: Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Networks.

The findings in this paper were hard earned, developed after extensive empirical trial and error with different model architectures, configurations, and training schemes. Their approach remains highly recommended as a starting point when developing new GANs, at least for image-synthesis-based tasks.

... after extensive model exploration we identified a family of architectures that resulted in stable training across a range of datasets and allowed for training higher resolution and deeper generative models.

> — Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Networks, 2015.

Below provides a summary of the GAN architecture recommendations from the paper.

| Architecture guidelines for stable Deep Convolutional GANs |
| :--- |
| Replace any pooling layers with strided convolutions (discriminator) and fractional-strided convolutions (generator). |
| Use batchnorm in both the generator and the discriminator. |
| Remove fully connected hidden layers for deeper architectures. |
| Use ReLU activation in generator for all layers except for the output, which uses Tanh. |
| Use LeakyReLU activation in the discriminator for all layers. |

Figure 5.2: Summary of Architectural Guidelines for Training Stable Deep Convolutional Generative Adversarial Networks. Taken from: Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Networks.

We will look at how to implement seven best practices for the DCGAN model architecture in this section.