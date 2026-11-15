approach, an upscale operation is performed in many steps to reconstruct the HR image.

![](bbox=[0.125, 0.205, 0.875, 0.315])

FIGURE 14.7 Progressive upsampling in image SR method.

# 14.2.2.4 ITERATIVE UP-AND-DOWN SAMPLING POSITION

Iterative up-and-down sampling is one of the most important techniques. Currently, most frameworks employ this technique to iteratively add upsampling and downsampling at various stages of the network, as shown in Figure 14.8. The recently published articles include RBPN,12 SRFBN,13 DBPN,14 and others.

![](bbox=[0.125, 0.545, 0.875, 0.675])

FIGURE 14.8 Iterative up-and-down upsampling in image SR method.

# 14.2.3 DEEP LEARNING-BASED UPSCALING APPROACH FOR IMAGE SUPERRESOLUTION

The deep learning-based approach has achieved remarkable performance and reduced the computational cost in terms of network parameters. In this subsection, we discuss the upscaling technique involved in deep CNN for converting the LR image into an HR image.