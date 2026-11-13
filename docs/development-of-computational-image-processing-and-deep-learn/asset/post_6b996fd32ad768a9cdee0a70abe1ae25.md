
![](img/332d06e0447dbfd85ea7d2fb553468f3_129_0.png)

On that account, Maas et al. introduced the Leaky ReLU as improvement of the standard ReLU function, which is defined by

```
\( h^{(l)} = \max(w^{(l)\top} x, 0) = \begin{cases} w^{(l)\top} x & \text{if } w^{(l)\top} x \ge 0, \\ \lambda w^{(l)\top} x & \text{if } w^{(l)\top} x < 0 \quad [204]. \end{cases} \quad (2.117) \)
```

The slope in the Leaky ReLU function depicted on the right in Figure 2.23 is chosen to \(\lambda = 0.01\) as suggested in the original paper [204]. When the unit is saturated and not active, the leaky rectifier allows for a small, non-zero gradient unlike the standard ReLU activation [204]. Sacrificing the so-called hard-zero sparsity of ReLU allows for a gradient which is potentially more robust during optimization [204].

### 2.4.1.6 Types of layers

The effect of increasing the number of layers to improve a network is limited, which is why alternatives to the previously introduced fully connected layers (also known as linear layers) have been developed. Some of the most important ones used in the networks in this work are briefly explained below. In some cases, the use of a certain type of layer also determines the name of the network, for example, an ANN that has one or more convolutional layers becomes a CNN.

**Dropout layers** Introduced by Hinton et al. in 2012, dropout layers can be used in ANNs to prevent overfitting and achieve improved robustness against choices of network architecture [210]. Dropout layers refer to a defined percentage of randomly selected neurons being ignored in an epoch, removing all connections from and to other units temporarily. The approach was partly motivated or at least linked to the fact that more advanced organisms have evolved due to the breaking up of sets of co-adapted genes during sexual reproduction compared to asexual reproduction increasing the robustness of the remaining units over time [211]. An example is given in Figure 2.24.

![](img/332d06e0447dbfd85ea7d2fb553468f3_130_0.png)

Figure 2.24: Model of a thinned dropout neural network, where crossed out single units are dropped. Based on [212].

One drawback of dropout is the two to three times increased training time due to its stochasticity. It mainly stems from training a different random architecture each time as the dropped out units change every iteration. As for every network, ANNs with dropout layers require extensive hyperparameter tuning with increased demands for network size, hence layers, higher learning rate, etc. [212]

**Batch normalization** Batch normalization, as proposed by Ioffe and Szegedy in 2015 [213], refers to the normalization of the input of every layer (and repeating so for every mini-batch) in a network as opposed to only the input layer. It can be included in backpropagation [213]. Batch normalization allows the use of higher learning rates, accelerating the training process up to 14 times [213], as one gets rid of the changing distribution of each layer’s inputs. It also decreases the importance of careful choice of initial hyperparameters. While being comparable to the impact of dropout layers, for which they can serve as substitute, its additional regularization effect may eliminate the need of dropout layers altogether in some cases. [213, 214]

**Convolutional layers** Convolution is continuously defined as follows:

```
$(f * g)(t) := \int_{-\infty}^{\infty} f(x)g(t-x)dx \quad \text{[215].} \quad (2.118)$
```

The convolution of two functions $f$ and $g$ can be understood as mirroring of function $g$ along the y-axis, subsequently adding a time offset $x$ and lastly sliding function $g$ from $-\infty$ to $\infty$. It passes function $f$ on the way. Wherever the two functions intersect, the integral of their product, so the area under function $f$ weighted by function $g$, is evaluated. Convolution is commutative.

In the context of neural networks, convolutional layers, as fundamental component of any CNN, introduced by LeCun et al. [216], are used to perform so-called feature extractions. They often consist of a combination of linear convolution and nonlinear activation functions. In this regard, a discrete definition of convolution is applied (changing the integral to a sum and working on finite sequences). It can be understood as a small array of numbers, called kernel or filter, sliding across the input tensor. By multiplying every entry of the kernel and the input element-wise and subsequently summing up these products, one obtains the so-called feature map (cf. Figure 2.25).

![](img/332d06e0447dbfd85ea7d2fb553468f3_132_0.png)

Figure 2.25: Schematic description of a convolutional layer in a neural network. A filter of a specific kernel size, in this case 3 x 3 is applied on the original image to obtain a so-called feature map. The feature map carries its name due to the fact that the most important features of an image are kept or even enhanced with this method, while the dimensions decrease compared to the original image.

Especially if this is repeated for different filter kernels, the characteristics or features of the input image are enhanced and captured. The output of the convolutional layer typically has decreased dimensions. In the case that this is unwanted, so-called padding, typically zero padding, which signifies the addition of rows and columns of zeros on each side of the input tensor, is applied in order to keep the same in-plane dimension throughout the convolution operation. If in contrast, the size reduction is desired, another parameter influencing the final output size, the stride parameter, comes in play, which defines the distance between two consecutive kernel positions. [217] While setting a stride larger than one can reduce overlap, it can also lead to checkerboard artifacts, especially if the size of the output window and kernel are not a multiple of the stride [218]. The alternative of applying pooling layers for the further reduction of output size will be discussed in the next paragraph.

The final output size can be calculated by

```
O = 1 + \frac{N + 2P - F}{S}, \quad (2.119)
```

with the image dimension $N \times N$, the filter dimension $F \times F$, stride $S$ and thickness of padding $P$ [219]. As an example, in the case in Figure 2.25, with $N = 6, P = 0, F = 3$ and $S = 1$, the output size of 4 results.

The output vector $\boldsymbol{h}^{(l)}$ of a hidden convolutional layer can be calculated analogously to the equations for MLPs and using the discrete definition of convolution (cf. Equation (2.103)) by

```
$$h_i^{(l)} = \sigma \left( \sum_{i \in M_j} h_i^{(l-1)} * W_{ij}^{(l)} + b_j^{(l)} \right), \quad (2.120)$$
```

with a selection of input maps $M_j$ [220, 221]. The weights $W_{ij}$ are updated through backpropagation and stochastic gradient descent just like the previously introduced fully connected layers [221] and the kernel values are the only parameters to be learned (while their size, padding, stride, etc. are hyperparameters that are set in advance) [217]. The inverse operation is used in some CNNs and also in deep convolutional generative adversarial networks (DCGANs); the layers are then called deconvolutional layer.

**Pooling layers** Pooling layers are used to decrease the in-plane dimensionality. They further introduce a higher translation invariance concerning small shifts and distortions in images, and decrease the number of subsequent learnable parameters. It shall be stressed that in contrast to a convolutional layer there are no learnable parameters in any of the pooling layers. [217] Some common, self-explanatory pooling operations that were used in the CNN in this work are depicted in Figure 2.26, Figure 2.27 and Figure 2.28.

![](img/332d06e0447dbfd85ea7d2fb553468f3_133_0.png)

Figure 2.26: Depiction of a MaxPooling layer.

![](img/332d06e0447dbfd85ea7d2fb553468f3_134_0.png)

![](img/332d06e0447dbfd85ea7d2fb553468f3_134_1.png)

## 2.4.2 Generative adversarial networks

Generative adversarial networks, or GANs for short, were introduced by Goodfellow et al. [143] in 2014, and have since been considered one of the biggest findings in AI science [222], which is underlined by the over 78,000 citations of the original paper to date [223]. In 2020 alone, about 28,500 papers related to GANs were published, corresponding to approximately 78 papers every day, which are more than three per hour [222]. The main function of GANs is the generation of realistically looking images after being trained on a given training image data set [143]. Possible areas of application range from 3D object generation via medicine, pandemics (mostly during COVID-19), image processing, face detection and text transferring to traffic control and many more [224]. In these application fields, the function of a GAN is not limited to the generation of images per se, but includes noise reduction, classification, detection of human motion, the generation of 3D images from 2D images, face recognition or super-resolution of images [224]. After a slow start, GANs have also established themselves in materials science. They have been used among others
