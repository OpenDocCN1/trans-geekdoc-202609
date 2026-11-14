![](bbox=[0.105, 0.095, 0.645, 0.275])

Fig. 1.6: A sinogram is a representation of the projections on the s–\(\theta\) plane.

![](bbox=[0.105, 0.345, 0.595, 0.595])

Fig. 1.7: The projections are weighted by the line length within each pixel.

represents a uniform pixel, and \(x_i (i = 1, 2, 3, 4)\) is the linear density in the \(i\)th pixel. Here we would like to find the line-integral \(p(s, \theta)\) of the matrix at a view angle \(\theta\). The quantity \(a_{ij} (i = 1, 2, 3, 4 \text{ and } j = 1, 2, 3, 4)\) is the segment length of the path toward the detector bin \(i\) within the pixel \(j\), and \(a_{ij} = 0\) if the \(j\)th pixel is not on the path to the \(i\)th detector bin. The projection \(p(i, \theta)\) is calculated as

\(p(i, \theta) = a_{i1}x_1 + a_{i2}x_2 + a_{i3}x_3 + a_{i4}x_4 \quad \text{for } i=1, 2, 3, 4. \quad (1.5)\)