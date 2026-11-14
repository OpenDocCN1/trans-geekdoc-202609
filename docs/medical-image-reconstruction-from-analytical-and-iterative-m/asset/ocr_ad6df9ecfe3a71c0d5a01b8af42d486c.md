![](bbox=[0.168, 0.098, 0.359, 0.246])

![](bbox=[0.414, 0.098, 0.631, 0.257])

![](bbox=[0.18, 0.287, 0.362, 0.429])

![](bbox=[0.404, 0.273, 0.627, 0.429])

Fig. 5.3: One measuring direction gives a measured plane in the Fourier space. A great circle trajectory provides full Fourier space measurements.

![](bbox=[0.18, 0.501, 0.604, 0.678])

Fig. 5.4: A great circle is a unit circle on the unit sphere.

# 5.1.1 Backprojection-then-filtering

If the data are sufficiently measured, the 3D image can be exactly reconstructed. Like 2D image reconstruction, one can reconstruct an image either by performing the backprojection first or by performing the backprojection last. If the backprojection is performed first, the algorithm is a backprojection-then-filtering algorithm, and it is described in the following steps: