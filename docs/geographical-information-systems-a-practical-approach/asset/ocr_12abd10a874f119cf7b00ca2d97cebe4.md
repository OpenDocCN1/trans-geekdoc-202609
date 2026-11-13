![](bbox=[0.08, 0.08, 0.86, 0.41])

Figure 7.15 High-pass filters.

median of DN values that can be displayed on the output device (for example, 127 for an 8-bit display). The resultant image enhances the edges normal to the direction of differencing and de-emphasises those parallel to the direction of differencing.

Edge enhancement can also be performed by convolving the image with a weighted kernel to produce different effects. Figure 7.16 lists some **embossing filters**, which emboss edges on a certain side. Embossing filters take a pixel on one side of the centre pixel and subtract one of the other sides from it. To use the negative pixels as shadow and positive ones as light, an offset of 127 is added to the resultant image. Embossing is achieved by setting pixels black, except where there is a change in DN values. The filtered image will represent the rate of change of DN values at each pixel of

the original image in a specific direction. Filter H in Figure 7.16 embosses edges in the east direction, Filter I embosses edges in the north direction and Filters J and K detect changes in the north-east and north-west directions, respectively.

Further edge detection filters can be implemented to detect and delineate edges using the kernels in Figure 7.17. Filters L, M, N and O in Figure 7.17 are horizontal, left-diagonal, right-diagonal and vertical directional filters, respectively. These filters should be applied before the image is smoothed in order to get better results.

**Laplacian filters** are non-directional edge detection filters, which emphasise all edges in an image. In other words, any feature with a sharp discontinuity (even noise, unfortunately) will be enhanced by a Laplacian filter. Laplacian filters are a second-derivative method of edge