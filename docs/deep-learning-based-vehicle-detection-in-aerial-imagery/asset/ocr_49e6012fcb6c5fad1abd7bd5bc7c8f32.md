![](bbox=[0.335, 0.123, 0.726, 0.33])

**Figure 2.7:** Inception module – the basic unit of inception networks consisting of parallel branches with different sets of convolutional layers, which are aggregated through concatenation.

![](bbox=[0.173, 0.432, 0.894, 0.681])

**Figure 2.8:** Residual block (a), residual block with bottleneck layers (b), and basic unit of ResNeXt networks (c).

Residual neural networks [He16a], shortened *ResNets*, overcome the problem of vanishing gradients by adding identity shortcuts to the network, which help to smoothly back-propagate the gradient signal (see Figure 2.8a). These shortcuts further facilitate the learning task, as the intermediate layers only