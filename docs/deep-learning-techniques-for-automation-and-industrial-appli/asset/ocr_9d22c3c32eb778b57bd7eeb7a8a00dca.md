![](bbox=[0.161, 0.114, 0.874, 0.536])

**Figure 4.6** Accuracy and loss plots of Resnet101.

# #### 4.4.2.2  ResNet152

In comparison to the ResNet101, ResNet152’s performance is slightly more consistent. When comparing the graphs to ResNet101, they fluctuate less. The accuracy plot and loss plots are shown in Figure 4.7(a) and Figure 4.7(b) curves, respectively.

As can be seen in Figure 4.7(c), the ResNet152V2 accuracy curve varies. The validation and training of both curves show similar performance. Both the training and testing data showed that the loss of ResNet152V2 was stable after 5 epochs, as seen in Figure 4.7(d).

# #### 4.4.3  MobileNet Family

Depth-wise, separable convolutions are used by MobileNet to reduce the number of parameters. As a consequence, lightweight deep neural networks are created [17] with a few bumps in the graph. However, when using testing data, the MobileNet family is doing well. The model’s training