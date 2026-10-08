
![](img/020125e0e698f9771fbbd32f2ace1e80_24_0.png)

### FIGURE 1.6
A typical recurrent network with the gate structure.

In a standard RNN, there is a hidden state vector $h$, which is defined as

```
$h = \begin{bmatrix} h_1 \ h_2 \ \vdots \ h_T \end{bmatrix} \quad (1.36)
```

Here, the hidden state $h$ and the input vector $x$ satisfy the following formula:

```
$h_{t+1} = \sigma(W_x x_t + W_h h_t + b_h) \quad (1.37)
```

where $W_x$ and $W_h$ represent the weight matrix of the input state and the hidden state, while the symbols $b_h$ and $\sigma$ represent the bias of the hidden state and the activation function. After that, the ultimate output $\mathcal{Y}$ is able to be calculated on the basis of $h$:

```
$y_t = W_y h_t + b_y \quad (1.38)
```

Similarly, the $W_y$ and $b_y$ are the weight matrix and bias in the output layer. RNNs often face the problem of gradient disappearance and gradient explosion in the training process. In order to overcome this disadvantage, short-term memory (LSTM) networks [32] have been proposed, which can perform better in longer sequences. Compared with RNN with only one transmission state, LSTM (shown in Figure 1.6) has two transmission states, which can selectively forget the information passed in the previous node, thus focusing on more important information. Another special RNN structure is GRU [33], which is also proposed to solve the problems of long-term memory and gradient in backpropagation. The GRU is able to obtain a comparable result with the LSTM while it requires fewer computational

# Deep Learning Framework and Paradigm in Computational Physics

![](img/020125e0e698f9771fbbd32f2ace1e80_25_0.png)

**FIGURE 1.7** a typical Generative Adversarial Network, which is composed of the generator and the discriminator.

Besides, the BRNN is employed to enable the data to propagate forwards and backwards while the GRNN introduces the Resnet structure to decrease the number of parameters.

## 1.2.4 Generative Adversarial Network

Generative Adversarial Networks are a mighty category of DL frameworks utilized for unsupervised learning, which was invented by Ian Goodfellow in 2014 [3]. The GANs (shown in Figure 1.7) are generally composed of two networks competing with each other: the generator and the discriminator. The Generator is employed to generate a series of fake specimens and attempts to deceive the Discriminator. The Discriminator, on the other hand, endeavors to distinguish the real and fake specimens. Both the Generator and the Discriminator are DL networks that compete with each other during the training process.

The Discriminator in the GAN is targeting the reward $V(D,G)$, while the generator is at maximizing the loss $V(D,G)$ which can be mathematically depicted

```
$$\max_{G} \min_{D} V(D, G) = E_{p_{data}(x)}[\log D(x)] + E_{p_z(z)}[\log (1 - D(G(z)))]$$
(1.39)
```

The original loss of the GAN is equivalent to the JS divergence (JSD):

```
$$\max_{G} \min_{D} V(D, G) = -2\log 2 + \min [2JSD(p_{data}||p_G)]$$
(1.40)
```

There is a serious problem with JS divergence: when the two distributions do not overlap, JS divergence is zero. Therefore, at the beginning of training, JS divergence is likely to be zero. So if the discriminator is trained too strongly, the loss will fail to converge to $-2\log 2$ without gradient. For this problem, a new loss, the Wasserstein loss is proposed in the WGAN.

```
$W(P_r, P_g) = \inf_{\gamma \in \Pi(P_r, P_g)} E_{(x,y)\sim\gamma} |x - y| \quad (1.41)$
```

The intuitive meaning of this term is that it is the distance required to move distribution $r$ to distribution $g$. Therefore, if the two distributions do not overlap, this loss has a value. This loss function overcomes the disadvantage of the gradient disappearance of the traditional GAN loss and ensures the stability of the training process.

GANs are fairly active subjects and various novel frameworks are developed. Here, a series of emerging GAN-based frameworks are described below:

- 1. Conditional GAN (CGAN): CGAN [35] is a deep learning framework where some conditional parameters are introduced. Here, an additional parameter is introduced to the Generator for producing the required data. Besides, labels are also fed to the Discriminator for distinguishing ground truth and the generated false data.

- 2. Deepal GAN (DCGAN): DCGAN [36] is another prevalent application of GAN which is consisted of convolutional networks rather than fully connected layers. Besides, the convolutional networks substitute the max pooling with the convolutional stride to enhance the capability for characteristic extraction.

- 3. Super Resolution GAN (SRGAN): SRGAN [37] is employed to generate higher resolution images, which is especially applicable for low-resolution images to enhance the detailed characteristics.

- 4. Laplacian Pyramid GAN (LAPGAN): The Laplacian GAN [38] employs a couple of Generator and Discriminator frameworks for it is to produce high-quality images, which is firstly down-sampled and up-scaled in the back pass in which the Conditional GAN is implemented to generate some noise.

Finally, several advanced DL techniques such as the Graph Network, the Fourier Network, and the Transformer will be introduced at the last chapter. For the sake of conciseness, they will not be discussed as expendable in this chapter.

## 1.3 Paradigms in Deep Learning

The previous section discussed several basic architectures in depth. In fact, there are many paradigms to solve practical problems using machine learning.

![](img/020125e0e698f9771fbbd32f2ace1e80_27_0.png)

FIGURE 1.8 Examples of the data driven examples in computational physics. (a) Poisson's solver, (b) EM scattering solver, (c) steady-state heat conduction solver and (d) Schrödinger equation solver.

This part mainly discusses them of: data-driven, physical problems, physical constraints, operator learning and deep learning-traditional algorithm fusion. The following four paradigms will be elaborated:

### 1.3.1 Data Driven

Data-driven deep learning technology is the most straightforward application of deep learning in computational physics. This method is usually based on supervised learning, and its application requires a large number of pre-generated data, which are often constructed by utilizing numerical algorithms. The data-driven network model can be regarded as a black box, that is, researchers do not need to pay attention to the connection between the network structure and physical problems, but only focus on the input and output. In other words, this kind of learning style is basically end-to-end. The advantage of data-driven network is that it can realize online prediction after offline training, which can be applied to various high-speed scenes.

As displayed in Figure 1.8, the data-driven techniques have been extensively deployed in a plethora of computational physics. For instance, in electrostatics. Shan et al. [39] developed a purely data-driven model to solve the Poisson's equation based on convolutional network. With sufficient training data and a proper training platform, the framework is able to attain a reliable result with satisfied accuracy. It is noted that

In nano photonics, Li et al. [40, 41] proposed a fully trained network to resolve the near-field EM scattering of isolated structure. It can be found that a relatively small number of specimens are required to train the CNN to achieve high precision. Compared to the existing CPU-based numerical approaches such as the LBM, the CNN enables faster predictions thousands of times faster. In heat transfer, Tadeparti et al. [42] exploited a data-driven architecture to solve steady-state heat conduction problems in two-dimensional cases. The involved conductors have square geometries and various boundaries. In terms of the SSIM, the image-based algorithms performed better than the non-image ones. In quantum mechanics, Mills et al. [43] presented a Schrödinger solver to solve the ground-state energy. The raised DL architecture is based on a convolutional network, aiming at constructing a map between the constrained electrostatic potential and the unknown ground-state energy. The results have affirmed that the model can yield high accuracy with the absolute error of 3%. Additionally, other physical quantities like the kinetic energy and the first excited state can also be solved by the developed framework, serving as promising candidates for computational physics in quantum fields. In hydrodynamics, Liu et al. [44] raised a universal and flexible model to predict the non-uniform unsteady flow at real time. The DL network is based on the convolutional network, which accomplishes the anticipated velocity with high fidelity.
