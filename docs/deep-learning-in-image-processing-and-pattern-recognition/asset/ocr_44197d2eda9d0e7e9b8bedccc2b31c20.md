![](bbox=[0.22, 0.12, 0.88, 0.2])

Figure 5. The framework of VGG16.

# 3.1.1. SPP Module

In 2015, He et al. [23] proposed spatial pyramid pooling (SPP) to address the input size limitation of the standard CNN. As shown in Figure 6, the SPP layer is used after the last conv layer (conv5, with 256 filters) and before the FC layers (fc6, fc7). The SPP extracts the features from the output of conv5 through pooling bins (windows) with different sizes. Each bin obtains one output, so the size of the SPP output features is determined by the number of bins instead of the size of the input. Compared to the breaking fixed size limitation, the most important advantage of the SPP is found by researchers to be that different sizes of bins correspond to different regions of the original image, i.e., to objects of different scales. This greatly improves the robustness of the network to object scaling. The SPP is therefore an effective way to handle multi-scale networks.

![](bbox=[0.18, 0.44, 0.75, 0.73])

Figure 6. The network structure with a SPP layer.

Inspired by the different sizes of bins in the SPP, we proposed a SPP module with different pooling kernel sizes to replace the 2 × 2 max pooling layers in VGG16 and to further extract the features with scale invariance. Identical to the original 2 × 2 max-pooling, our SPP module reduces the width and height of the feature map by half, too. Therefore, it is denoted as “SPP-2” in Figure 4. As shown in Figure 7, the SPP module is a stack of three max-pooling layers. The size of the input feature maps is W × H, and the sizes of the three pooling kernels we used are 2 × 2, 2 × 2, and 3 × 3, and the strides are 2, 1, and 1, respectively. Finally, on every channel, the obtained three feature maps of size W/2 × H/2 are summed up. With three SPP modules fusing the spatial features, the front-end network can expand the receptive field and extract features in different scales without increasing the parameters.