![](bbox=[0.36, 0.11, 0.64, 0.38])

Layer $m$ has five nodes and the filter has three units [$w_1, w_2, w_3$]. We compute the dot product between the filter and the first three nodes in layer $m$ and obtain the first node in the feature map; then, we compute the dot product between the filter and the middle three nodes and generate the second node; finally, we obtain the third node resulting from the last three nodes in layer $m$.

Another example that helps us better understand how the convolutional layer works on images is as follows:

![](bbox=[0.26, 0.56, 0.74, 0.74])

A 3*3 filter is sliding around a 5*5 image from the top left sub-region to the bottom right. For every sub-region, the dot product is computed with the filter. A 3*3 feature map is generated as a result.