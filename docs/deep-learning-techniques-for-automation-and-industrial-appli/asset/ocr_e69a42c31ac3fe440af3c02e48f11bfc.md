![](bbox=[0.12, 0.15, 0.95, 0.55])

Figure 8.4 VGGNet architecture [40].

# 8.2.2.2.2 ResNet-50

ResNet-50 is a very deep network with skip connections. These skip connections help to diminish vanishing gradients and make it possible to train very deep networks. Inspired by SRNet and other pretrained networks [25, 32], this work has used ResNet-50 [35] for comparative analysis and found that it performs better than simple VGGNet-16. It uses a residual learning block which has skip connections that helps to propagate gradient back to the initial layers as shown in Figure 8.5 [41]. Furthermore, the use of 1*1

![](bbox=[0.15, 0.72, 0.92, 0.92])

Figure 8.5 ResNet-50 architecture [41].