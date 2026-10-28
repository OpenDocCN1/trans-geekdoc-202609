
with

$$\Delta \hat{\mathbf{W}}^t = \eta \sum_{x \in \mathcal{B}_t} \frac{\partial L_x}{\partial \mathbf{W}^t} \tag{2.5}$$

being the gradient over the current batch $\mathcal{B}_t$. The gradient is weighted by the learning rate $\eta$ that specifies the step size in the gradient descent. To achieve faster convergence, a fraction $\omega$ of the previous weight update $\Delta \hat{\mathbf{W}}^{t-1}$ is typically added to the current weight update:

$$\mathbf{W}^{t+1} = \mathbf{W}^t + \Delta \hat{\mathbf{W}}^t + \omega \Delta \hat{\mathbf{W}}^{t-1}. \tag{2.6}$$

Thus, this method called *momentum* allows to overcome plateaus in the loss function [Dud12]. Besides SGD with momentum, several alternative optimization methods that dynamically adapt the learning rate have been proposed, including AdaDelta [Zei12], AdaGrad [Duc11], RMSprop [Tie12], and Adam [Kin14]. Particularly, the latter optimization method, which is a combination of SGD with momentum and RMSprop, often leads to good results in practice with only little tuning of hyper-parameters. Thus, time-consuming training of several networks with vanilla SGD and various learning rate schedules is avoided.

Overfitting – an over-adaptation to the employed training samples – is a general problem when training CNNs due to their large number of parameters. A common regularization method to address this problem is *weight decay*, which reduces the weights in each iteration by a small fraction $\delta$:

$$\mathbf{W}^{new} = (1 - \delta) \mathbf{W}^{old}. \tag{2.7}$$

This prevents the weights from growing too large, which otherwise dominate the output of the network. Another popular regularization method to avoid overfitting is *dropout* [Sri14]. During training, dropout deactivates neurons of particular layers with a given probability, forcing the network to learn redundant representations. Thus, formation of critical paths through the network specialized to the training samples is avoided.

To avoid unstable training caused by vanishing or exploding gradients, a proper initialization of the network weights is important. Random initialization, e.g., Xavier initialization [Glor10] or Kaiming initialization [He15], are often applied to address this issue. While random initialization allows more flexibility in the design of the network architecture, it often leads to less optimal results, especially in case of deep networks with many parameters and only a limited amount of available training data. Therefore, the weights of models pre-trained on very large datasets, e.g., the ImageNet classification challenge dataset comprising millions of images [Deng09], are commonly used in practice for initialization.

As the gradient signal can become less stable with increasing depth of the network, *batch normalization* has been proposed to make the gradient propagation in the network more stable [Iof15]. In general, batch normalization is applied immediately before the activation function by normalizing the network activations $\tilde{h}_i = W_i h_{i-1} + b_i$ to zero mean and unit variance:

$$\hat{\tilde{h}}_i = \frac{\tilde{h}_i - \mu_{\mathcal{B}}\mathbf{e}}{\sqrt{\sigma_{\mathcal{B}}^2 + \epsilon}}$$  \tag{2.8}

where $\mu_{\mathcal{B}}$ and $\sigma_{\mathcal{B}}^2$ are the mean and variance calculated for the current batch $\mathcal{B}$, while $\mathbf{e}$ is an all-ones vector with the same length as $\tilde{h}_i$. Furthermore, a small value $\epsilon$ is added to prevent a division by zero. To restore the representation power of the network, a set of learnable parameters $\gamma_i$ and $\beta_i$ that scale and shift the normalized input are introduced:

$$\tilde{h}_i^{BN} = \gamma_i\hat{\tilde{h}}_i + \beta_i\mathbf{e}$$  \tag{2.9}

As batch normalization prevents activations to become very high or very low, it allows the usage of higher learning rates and thus, accelerates the training process.

## 2.1.4 CNN Architectures

Since the development of early CNN architectures like LeNet[LeC98] and AlexNet[Kri12], several novel CNN architectures have been proposed to increase the performance and allow for more efficient learning by rearranging the combinations of convolutional layers, pooling layers and fully connected layers. The most notable architectures that have been adapted for a broad range of computer vision tasks can be distinguished into *VGG*, *residual* and *inception* networks.

Similar to prior state-of-the-art networks, e.g., AlexNet, VGG networks (named after the Visual Geometry Group from the University of Oxford) comprise convolutional layers and pooling layers followed by a sequence of fully connected layers arranged in a single path network [Sim14]. While prior state-of-the-art networks made use of computationally expensive 9 × 9 or 11 × 11 filters to achieve large receptive fields, VGG networks rely on sequences of 3 × 3 convolutional layers that emulate the effect of larger receptive fields. The use of sequences of small convolutional layers allowed to increase the network depth up to 19 layers and thus, the extraction of more complex image features. Its variant with 16 layers termed *VGG16* has become a popular choice as feature extractor in many computer vision tasks.

Inception networks rely on a basic unit referred to as *inception module* (see Figure 2.7) [Sze15]. An inception module – first applied in GoogLeNet [Sze15] – consists of parallel branches with different sets of convolutional layers, which are aggregated through concatenation. As each branch possesses a different receptive field, the inception module allows the model to recover both local features via smaller convolutions and more global features through larger convolutions. Bottleneck layers, i.e., 1 × 1 convolutional layers, are often carried out to restrict the number of channels before larger convolutions. To reduce the computational complexity, recent variants do not use convolutions larger than 3 × 3. Therefore, large *k* × *k* convolutions are either replaced by sequences of 3 × 3 convolutions or factorized to a combination of 1 × *k* and *k* × 1 convolutions [Sze16, Sze17].

![](img/99de1214c29cbc525a14b293385af5cf_38_0.png)

**Figure 2.7:** Inception module – the basic unit of inception networks consisting of parallel branches with different sets of convolutional layers, which are aggregated through concatenation.

![](img/99de1214c29cbc525a14b293385af5cf_38_1.png)

**Figure 2.8:** Residual block (a), residual block with bottleneck layers (b), and basic unit of ResNeXt networks (c).

Residual neural networks [He16a], shortened *ResNets*, overcome the problem of vanishing gradients by adding identity shortcuts to the network, which help to smoothly back-propagate the gradient signal (see Figure 2.8a). These shortcuts further facilitate the learning task, as the intermediate layers only

characterized by the *dilation coefficient* *d*, which defines the spacing between the elements of a filter. In practice, the filter elements are matched to distant elements of the input as illustrated in Figure 2.9 yielding a larger receptive field. Note that a dilated convolution with *d* = 1 is equivalent to the standard convolution.

*Group convolutions*, first mentioned in [Kri12], have been proposed to reduce the computational costs of standard convolutions. Rather than applying filters with the full channel depth of the input image, i.e., *D* kernels per filter, the input is split channel-wise into groups and the filters are applied independently for each group (see Figure 2.10b). Letting *g* denote the number of groups, group convolution filters only consider *D/g* channels instead of the full channel depth *D*. Thus, the computational costs are reduced by a factor of *g* compared to standard convolutions.

![](img/99de1214c29cbc525a14b293385af5cf_40_0.png)

Figure 2.10: Standard convolution (a) compared to group convolution with three groups (b).

A *depthwise separable convolution* (DSC) performs convolutions independently in spatial and channel domains to reduce the number of parameters and the computational costs [Sif14]. It factorizes the standard convolution into a *depthwise convolution* and a *pointwise convolution* as visualized in Figure 2.11. The depthwise convolution is in essence a special case of group convolution with the same number of groups *g* and input channels *D*. Thus,
