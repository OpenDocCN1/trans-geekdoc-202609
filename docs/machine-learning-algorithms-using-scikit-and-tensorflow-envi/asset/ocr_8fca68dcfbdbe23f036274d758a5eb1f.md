# Figure 1. SCRNN deep model

![](bbox=[0.22, 0.16, 0.745, 0.545])

# Stage-1: Feature Extraction From Histological Images

ShuffleNetV2 is chosen as feature extraction component for SCRNN. ShuffleNetV2 is a deep learning architecture designed exclusively for image feature extraction. It is a lightweight model. It is distinguished by two distinct operations: channel shuffling and group convolutions. These techniques enable it to extract important visual characteristics, patterns, and structures from histological images. They also minimise the deep model's computational complexity and size. As a result, it is ideal for resource-constrained settings and applications. The architecture of ShuffleNetV2 is aimed to strike a balance between accuracy and computing efficiency. Because of this, it is an excellent candidate for the feature extraction phase of the SCRNN model.

The basic ShuffleNetV2 architecture is presented in Figure 2. It starts with a series of convolutional layers to capture low-level features from histological images. It introduces “shuffle units”, which include group convolution operations. These units enable information exchange between channels and reduce computational load. They consist of several key components –

+   a) Pointwise Group Convolution operation applies 1x1 convolutions to the input channels, partitioned into groups. It helps mix information between different channel groups.

+   b) Channel Shuffle: This step reorders the feature maps, promoting cross-group information flow.