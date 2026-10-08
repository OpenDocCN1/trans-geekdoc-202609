This algorithm is utilized for an example of satellite imagery in a later section.

# ## Dilated convolutions

The pixel-wise classification and image classification are structurally different. Hence, pooling layers that decrease information will produce coarse segmentation. Hence, remember, pooling is essential for having a wider view and allows sampling. A new idea called **dilated convolution** was introduced to solve this problem for less-lossy sampling while having a wider view. The dilated convolution is essentially convolution by skipping every pixel in the window as shown here:

![](bbox=[0.296, 0.396, 0.703, 0.683])

The dilation distance varies from layer to layer. The output of such a segmentation result is upscaled for a finer resolution. A separate network is trained for multi-scale aggregation.