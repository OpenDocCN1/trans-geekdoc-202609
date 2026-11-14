![](bbox=[0.17, 0.09, 0.7, 0.32])

Fig. 5.7: The central slice theorem for the 3D Radon transform.

![](bbox=[0.17, 0.38, 0.7, 0.53])

(i) Backproject points into lines. (ii) Backproject lines into planes.

Fig. 5.8: Three-dimensional Radon backprojection is implemented as two steps: a point to a line and then a line to a plane.

# 5.3 Cone-beam data

Cone-beam image reconstruction is considerably more complex than that of parallel line-integral and parallel plane-integral data. There is no equivalent central slice theorem known to us. Cone-beam imaging geometry (see the two lower figures in Figure 4.13) is extremely popular, for example, in X-ray computed tomography (CT) and in pinhole SPECT (single-photon emission computed tomography); we will spend some effort to talk about its reconstruction methods.

First, we have a cone-beam data sufficiency condition (known as Tuy's condition): every plane that intersects the object of interest must contain a cone-beam focal point.

This condition is very similar to the fan-beam data sufficiency condition: Every line that intersects the object of interest must contain a fan-beam focal point.