![](bbox=[0.08, 0.11, 0.92, 0.37])

**Figure 1.** Improved YOLOv4 network for dangerous-goods detection.

# 3.1. *The Deformable Convolution*

The neck of YOLOv4 uses the PANet module to fuse the high- and low-level features and combines the semantic information and location information. However, the direct splicing between the upper sampling and local features may cause the feature map to contain misaligned context information, which can be converted into errors in prediction, especially on the object boundary, resulting in poor accuracy when detecting dangerous goods. Deformable convolution [27] introduces offset in the receptive field, which is different from the square receptive field of traditional convolution. This feature can be used to achieve more accurate feature alignment and improve the accuracy of detection.

The standard convolution layer usually uses sliding-window and scale-invariant feature transformation to deal with the geometric changes of the object. It can effectively expand the receptive field by stacking more convolution layers, but the corresponding calculation cost increases exponentially with the increase of the receptive field. With the increase in depth, the receptive field goes far beyond the area of interest, resulting in the extracted features being affected by redundant context information. The deformable convolution can adaptively determine the size of the receptive field and flexibly adjust the receptive field by learning the additional offset of the convolution network.

Traditional convolution uses a regular grid as the convolution kernel, slides on the input-characteristic graph step by step, and calculates the point product sum of the matrix of the input characteristic graph one by one, and finally adds the variation. The size of the convolution kernel determines the size of the receptive field. The corresponding value of each position in the output-characteristic diagram is calculated as shown in Formula (1):

```
$y(\mathbf{p}_0) = \sum_{\mathbf{p}_n \in \mathcal{R}} w(\mathbf{p}_n) \cdot x(\mathbf{p}_0 + \mathbf{p}_n)$ (1)
```

where $y$ represents the output-feature map, $x$ represents the input-feature map, $w$ represents the weight coefficient, $b$ represents the deviation, $\mathbf{p}_0$ is the 0th point in the grid, and $\mathbf{p}_n$ is the nth point in the grid.

The deformable convolution adds a learnable offset parameter on the basis of ordinary convolution, which can be used to adjust the receptive field to better extract the features of complex-shaped objects. In the deformable convolution, $\{\Delta p_n | n = 1, \dots, N\}$ is considered