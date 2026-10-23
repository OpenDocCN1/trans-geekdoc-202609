![](bbox=[0.25, 0.11, 0.82, 0.28])

Figure 14.9: Illustration of 1 × 1 × 3 × 2 convolution. Adapted from Figure 6.4.2 of [Zha+19a].

of features, as illustrated in Fig. 14.1. We can do this by making W into a 4d weight matrix. The filter to detect feature type d in input channel c is stored in W_{...,c,d}. We extend the definition of convolution to this case as follows:

z_{i,j,d} = b_d + \sum_{u=0}^{H-1} \sum_{v=0}^{W-1} \sum_{c=0}^{C-1} x_{s i+u, s j+v, c} w_{u,v,c,d} (14.14)

This is illustrated in Fig. 14.8. Each vertical cylindrical column denotes the set of output features at a given location, z_{i,j,1:D}; this is sometimes called a hypercolumn. Each element is a different weighted combination of the C features in the receptive field of each of the feature maps in the layer below.²

# 14.2.4.2 1 × 1 (pointwise) convolution

Sometimes we just want to take a weighted combination of the features at a given location, rather than across locations. This can be done using using 1x1 convolution, also called pointwise convolution, as illustrated in Fig. 14.9. This changes the number of channels from C to D, without changing the spatial dimensionality:

z_{i,j,d} = b_d + \sum_{c=0}^{C-1} x_{i,j,c} w_{0,0,c,d} (14.15)

This can be thought of as a single layer MLP applied to each feature column in parallel.

# 14.2.5 Pooling layers

Convolution will preserve information about the location of input features (modulo reduced resolution), a property known as equivariance. In some case we want to be invariant to the location. For example, when performing image classification, we may just want to know if an object of interest (e.g., a face) is present anywhere in the image.

2. In Tensorflow, a filter for 2d CNNs has shape (H,W,C,D), and a minibatch of feature maps has shape (batch-size, image-height, image-width, image-channels); this is called NHWC format. Other systems use different data layouts.