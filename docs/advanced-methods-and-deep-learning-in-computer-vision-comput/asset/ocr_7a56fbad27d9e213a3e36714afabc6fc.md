where M is the number of detection branches, l^m the multitask loss combining classification and bounding box regression of (2.5), α_m the weight of loss l^m, and S = {S^1, S^2, …, S^M}, where S^m contains the examples of scale m. Note that only a subset S^m of the training samples, selected by scale, contributes to the loss of detection layer m.

# 2.8.2 FPN

Although the feature pyramid of Fig. 2.11(c) improves the representation of different object scales, it introduces a large semantic gap between these representations. While high-resolution maps contain information about features of low-level semantics, such as edges, corners, etc., low-resolution maps convey semantically rich information, such as object category. Hence, high-resolution (low-resolution) maps are mostly informative of object location (identity). By asking all feature representations to contribute to the localization and classification tasks, the architecture of Fig. 2.11(c) can have suboptimal detection performance.

To reduce these semantic gaps, the feature pyramid network (FPN) adds a top-down connection from the high-level (semantically richer) feature maps to the low-level (semantically poorest) feature maps, as shown in Fig. 2.11(d). This ensures that the feature pyramid has strong semantics at all pyramid levels. Like Fig. 2.11(c), the FPN is an in-network pyramid and thus efficient, but the top-down connections increase its representation power.

# 2.8.2.1 Architecture

The major difference between the FPN and standard bottom-up classification networks, like the ResNet (He et al., 2016), is the addition of a top-down pathway, to enable semantically rich feature pyramids. This is implemented with a simple set of building blocks, shown in Fig. 2.14.

# Bottom-up pathway

A standard feed-forward network is naturally a bottom-up pyramid, due to the use of downsampling operations like pooling, convolution with stride of 2, etc. In general, the resolution of feature maps is reduced by 2 times at every network stage, where a stage is defined as a sequence of layers with the same resolution. The FPN builds on the ResNet, extracting the bottom-up pyramid from the activations of the last layer of each ResNet stage. Specifically, the outputs of layers conv2, conv3, conv4, and conv5 of the ResNet, denoted as {C2, C3, C4, C5}, are used to create a pyramid of stride {4, 8, 16, 32} pixels with respect to the input image.

# Top-down pathway and lateral connections

The goal of the FPN is to enrich the semantics of the low-level feature maps. A simple way to do this is to add the high-level feature maps, of strong semantics, to the low-level ones. Since higher level feature maps have lower resolution, they are first upsampled spatially by a factor of two, using nearest neighbor sampling. Before the summation, the lower layer feature maps are fed to a 1 × 1 lateral convolutional layer, in order to ensure that both feature maps have the same channel dimensions. The feature maps are then summed element-wise and a 3 × 3 convolution is applied to generate the final feature map, so as to avoid potential aliasing due to the upsampling operation. There are no nonlinearities in these