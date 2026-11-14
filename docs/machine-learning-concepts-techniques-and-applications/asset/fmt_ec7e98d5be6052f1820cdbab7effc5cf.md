
The value of the gradients is controlled by the chain of derivatives starting from $\frac{\partial c_{t}}{\partial c_{t - 1}}$.

Expanding this value using the expression for `c[t]` (Equation 16.16),

(16.16)

$$\frac{\partial c_{t}}{\partial c_{t - 1}} = \frac{\partial c_{t}}{\partial f}\frac{\partial f}{\partial h_{t - 1}}\frac{\partial h_{t - 1}}{\partial c_{t - 1}} + \frac{\partial c_{t}}{\partial i}\frac{\partial i}{\partial h_{t - 1}}\frac{\partial h_{t - 1}}{\partial c_{t - 1}} + \frac{\partial c_{t}}{\partial g}\frac{\partial g}{\partial h_{t - 1}}\frac{\partial h_{t - 1}}{\partial c_{t - 1}} + \frac{\partial c_{t}}{\partial c_{t - 1}}$$

For a simple RNN, the term $\frac{\partial\mathbf{c}_{\mathbf{t}}}{\partial\mathbf{c}_{\mathbf{t} - 1}}$ begins to take values larger than 1 or less than 1 within the same range after a given duration. This is the underlying source of the problem with vanishing and exploding gradients. The term $\frac{\partial\mathbf{c}_{\mathbf{t}}}{\partial\mathbf{c}_{\mathbf{t} - 1}}$ in an LSTM can take any positive value at each time step, and hence convergence is not guaranteed. If the gradient begins to converge toward 0, the gate weights can be modified to bring the gradient closer to 1. During the training phase only these weights are adjusted, and hence the network can learn when the gradient can converge to zero and when to retain it.

## 16.4 Generative Adversarial Networks (GANs)

In June 2014, Ian Goodfellow and his colleagues came up with the concept for a class of machine learning frameworks called generative adversarial networks, or GANs for short. GAN deploys a learning technique that produces new data which is statistically similar to the input training data. For instance, a GAN that has been trained on images can produce new photographs that, at least to human observers, appear to be superficially legitimate and have many realistic properties. GANs were initially conceived of as a sort of generative model that could be used for unsupervised learning.

The general notion behind a GAN is predicated on the concept of “indirect” training through the discriminator, which is another neural network that can determine how “realistic” the input seems and is also being dynamically updated. That is, during the training, the generator does not minimise the distance with respect to an image; rather, it is trained to deceive the discriminator into thinking that the image is closer than it actually is. Because of this, the model is able to learn in a way that is not supervised. In evolutionary biology, mimicry is analogous to GANs, and both types of networks engage in an evolutionary arms race with one another.

### 16.4.1 Idea Behind GAN

The general idea behind a GAN is to have two different types of neural networks compete against one another. The first one uses noise as its input and produces samples (and so is called the generator). The second model, which is referred to as the discriminator, is provided with samples from both the generator and the training data, and it is expected to be able to differentiate between the two different data sets. These two networks engage in a never-ending game in which the generator learns to make samples that are more realistic with each iteration, and the discriminator learns to get better and better at separating generated data from actual data with each iteration. Both of these networks are trained at the same time with the expectation that the healthy competition between them will result in the generated samples being virtually indistinguishable from the actual data ([Figure 16.16](#ch16.xhtml#fig16_16)).

![Figure 16.16 GAN overview.](images/fig16_16_B.jpg)

[Figure 16.16 GAN overview.](#ch16.xhtml#R_fig16_16)

Until now, GANs have mostly been used to model natural images. They are presently achieving great results in image creation challenges, generating images that are substantially sharper than those taught with other top generative approaches whose training aims are focused on maximum probability.

**Example**: Let’s say we’re attempting to make hand-drawn images that resemble photographs of real people. The objective of the discriminator, when presented with a genuine photographic image of a real human, is to identify those that are genuine photographs of a real human. The generator generates new synthetic pictures, which are then sent to the discriminator. The purpose of the generator is to produce convincing hand-drawn representations of humans: to deceive without being discovered. The main task of the discriminator is to identify and recognize any images produced by the generator as fraudulent. The steps followed by GAN for the example scenario is summarized in [Figure 16.17](#ch16.xhtml#fig16_17).

![Figure 16.17 Working of GAN.](images/fig16_17_B.jpg)

[Figure 16.17 Working of GAN.](#ch16.xhtml#R_fig16_17)

The input to the generator network is a D-dimensional noise vector with random integers, and the output is a synthetic image. This synthetic image along with a set of photographs from the real-world data set acts as an input to the discriminator. The discriminator upon receiving both authentic and counterfeit photographs outputs a number between 0 and 1. This value is a probability value, where 1 indicates authentic and 0 represents counterfeit.

### 16.4.2 Generative Versus Discriminative Models

While the discriminative network assesses the candidates, the generative network comes up with new potential candidates. The competition will be run according to the distribution of data. Often the discriminative network filters the candidates produced from the original data distribution by the generative network. However, the generative network is responsible for mapping between the latent space and the preferred data distribution. The generative network’s training aims to increase the discriminator network’s error rate by supplying distinct candidates from the genuine data distribution.

The discriminator uses known training data. During training, it’s exposed to instances from the data set until it’s accurate enough. The generator learns whether it can fool the discriminator. Most generators are “seeded” using random input from a latent space. The discriminator will next make judgments based on the candidates that were generated by the generator. Both networks undergo their own unique backpropagation techniques so that the generator can produce higher quality samples and the discriminator may become more adept at identifying synthetic samples. When a neural network is being used to generate images, the discriminator is often a convolutional neural network, but the generator is typically a deconvolutional neural network.

Both types of models have their uses, but generative models have one interesting advantage over discriminative models: they have the potential to understand and explain the underlying structure of the input data even when there are no labels to describe it. Discriminative models, on the other hand, do not have this capability. Both types of models are useful. When working on data modelling problems in the real world, this is quite desired, as obtaining labelled data can be expensive, at best, and unfeasible, at worst. On the other hand, there is an abundance of unlabeled data, thus this is not a problem.

| **A mathematical representation of GAN appears as the following game** |
| --- |
