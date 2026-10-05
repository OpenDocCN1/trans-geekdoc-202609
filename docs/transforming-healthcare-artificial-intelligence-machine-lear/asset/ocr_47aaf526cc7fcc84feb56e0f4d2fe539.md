# 232 Transforming Healthcare

![](bbox=[0.125, 0.093, 0.843, 0.423])

Figure 11.2 Work done in the proposed model.

![](bbox=[0.125, 0.483, 0.843, 0.753])

Figure 11.3 Compact convolution transformer.

the valid attributes for classification, followed by the convolution and pooling layers, ensures not to miss out any of the desired attributes, as each layer is connected to one another to resolve the issue of disappearing gradients. The dense block is followed by the global average pooling layer before the reshaping of attributes as required by the transformer encoder blocks.