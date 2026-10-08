# Video Classification

The handcrafted features are Fisher vector and the features are from CNN. The following image demonstrates the extraction of the trajectories and features maps:

![](bbox=[0.109, 0.175, 0.891, 0.458])

Both the trajectories and features maps are combined temporally to form the final predictions over the temporal snippet.

# Multi-modal fusion

Yang et al. (http://research.nvidia.com/sites/default/files/pubs/2016-10_Multilayer-and-Multimodal_MMI6.pdf) proposed a multi-modal fusion, with 4 models, video classification. The four models are 3D convolution features, 2D optical flow, 3D optical flow, and 2D convolution features.