# ResNet

After the invention of VGG (Zisserman, 2015) and Google Net (al, 2015), it was thought that the more layers architecture stacks, the accuracy will be better. However, deeper neural networks with more than 20 layers generally are more difficult to form where very deep network formation requires slow training time and present several problems such as the disappearance of gradients in the backward propagation. In (He X. Zhang, 2015) He et al, presented a residual learning bloc (figure 7) to facilitate the formation of considerably deeper networks than (Zisserman, 2015) and other networks by including a link around each two convolutional layer, summing both the original diverted and its function. This solution is called the “residual block”. Each “residual block” integrates two layers of convolution (3x3). ResNet (He X. Zhang, 2015) was proposed by He et al and offers a result that ranked ILSVRC 2015 as the leading candidate for residual networks with maximum depth (152 layers) nearly 8 times deeper than (Zisserman, 2015). The error is equivalent to 3.57%. It is noted that even with a deeper architecture, ResNet (He X. Zhang, 2015) has a computing complexity lower than that (Zisserman, 2015). This architecture is similar to GoogLeNet (al, 2015) in terms of the use of a global sub-sampling followed by the classification layer, so this architecture does not use the “Dropout” layer. This model is formed for approximately 600K iteration using a stochastic gradient descent (SGD) with:

+   * Momentum of 0.9.
+   * Decreased weight 0.0001.
+   * Batch size 256.

Figure 7. Residual Block

![](bbox=[0.345, 0.59, 0.605, 0.905])