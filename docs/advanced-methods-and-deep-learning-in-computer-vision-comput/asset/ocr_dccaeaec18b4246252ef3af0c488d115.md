![](bbox=[0.1, 0.12, 0.95, 0.36])

FIGURE 2.13 The feature pyramid architecture of the MS-CNN. The cuboids are the output tensors of the network (except the input image). h × w is the filter size, c the number of classes, and b the number of bounding box coordinates.

can be addressed by simply adding output layers at multiple stages of the network, as shown in Fig. 2.11(c). In this way, the MS-CNN implements several detectors that specialize in different scale ranges. While detectors based on lower network layers, such as “conv-3,” have smaller receptive fields and are better matched to detect small objects, those based on higher layers, such as “conv-5,” are best suited for the detection of large objects. The complementary detectors at the outputs of different layers are combined into a strong multiscale detector.

# 2.8.1.1 Architecture

The detailed architecture of the MS-CNN proposal network is shown in Fig. 2.13. The network detects objects through several detection branches, which are merged into a final set of proposals. It has a standard CNN trunk, depicted in the center of the figure, and a set of output branches, which emanate from different layers of the trunk. These branches consist of a single detection layer. Note that a buffer convolutional layer is introduced on the branch that emanates after layer “conv4-3”. Since this branch is close to the lower layers of the trunk network, it affects their gradients more than the other detection branches. This can lead to some instability during learning. The buffer convolution prevents the gradients of the detection branch from being back-propagated directly to the trunk layers.

During training, the parameters W of the multiscale proposal network are learned from a set of training samples S = {(Xi, Yi)}i=1N, where Xi is a training image patch, and Yi = (yi, bi) the combination of its class label yi ∈ {0, 1, 2, …, K} and bounding box coordinates bi = (bi^x, bi^y, bi^w, bi^l). This is achieved with a multitask loss

L(W) = Σm=1M Σi∈Sm αm lm(Xi, Yi|W),  (2.12)