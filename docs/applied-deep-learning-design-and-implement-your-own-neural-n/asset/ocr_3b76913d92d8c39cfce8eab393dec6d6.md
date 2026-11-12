Example 4.9: The following example shows max pooling, as shown in figure 4.88 (a). It consists of an input image of size 224 × 224 × 3. It is first convolved with 64 filters of size 3 × 3 with stride one and padding of one. After convolving 224 × 224 × 3 with a 3 × 3 × 3 filter, we get the output feature size as 224 × 224 × 64; that is, 64 activation or feature maps of 224 × 224 are retrieved. After applying convolution, the max pool layer of size 2 × 2 is applied on feature maps with the stride of two. So, after applying Max pooling, the feature maps get reduced to 112 × 112 × 64. If we want to aggregate within the layer, then we do Max Pooling. Furthermore, when we do max pooling then the depth remains the same, and it does not get affected; that is, it remains as 64. Moreover, the 4*4 image gets reduced to 2*2 image with maximum feature values by using a Max pool of 2*2 filter with a stride of two, as shown in figure 4.88 (b):

![](bbox=[0.135, 0.345, 0.86, 0.585])

Figure 4.88: [a-b] (a) Convolution with 64 filters of size 3*3*3 with padding and stride of one and max pooling with 2*2 filter (112*112*64) (b) Max pool on 4*4 image with the stride of two

Furthermore, the same kind of max pooling is shown in figure 4.89 with a different set of values:

Conv. Layers (3 x 3 filter with stride 1 and pad 1)
Pool. Layers (2 x 2 Max. Pooling with stride 2 and pad 0)

| 0 | 0 | 0 | 0 | 0 | 0 |
|---|---|---|---|---|---|
| 0 | 1 | 5 | 3 | 9 | 0 |
| 0 | 4 | 4 | 7 | 5 | 0 |
| 0 | 6 | 7 | 5 | 6 | 0 |
| 0 | 6 | 5 | 3 | 1 | 0 |
| 0 | 0 | 0 | 0 | 0 | 0 |

![](bbox=[0.45, 0.76, 0.82, 0.92])

Figure 4.89: 2*2 Max pooling with a stride of two and padding of one