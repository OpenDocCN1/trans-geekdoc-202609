![](bbox=[0.26, 0.1, 0.74, 0.21])

Figure 8.2 Comparison of estimated memory costs for two filtering sequences.

Thus two memory blocks are required to buffer the original image and the temporal high-pass filtered image (i.e., the **P** and **H** images in Eq. (8.1)) for subsequent usage and other two banks for textural and dynamic integral images. The DoG filter does not require an image buffer in a pixel stream processing architecture, as will be illustrated in Section 8.3. Indeed, a large amount of memory requirements can be optimized out if we carefully arrange the filtering sequence by fully leveraging the linearity of all the filters involved. In light of this, we have finally found the optimal I-HD sequence: computing the integral image of the input and then performing the temporal high-pass filtering with the spatial DoG filter embedded in it as

```
IH[t] = aIH[t - 1] + (1 + c)DoG((IP[t] - IP[t - 1])/2), (8.6)
```

where **IP** denotes the integral of the original input image (i.e., the textural integral image), and **IH** is the dynamic integral image. This way, **IP** can be reused for both textural and dynamic feature extractions, and we only need two memory banks to buffer the **IP** and **IH** images. We have estimated the memory consumption on the two filtering sequences for typical 640 × 480 × 8-bit images in Fig. 8.2. The I-HD sequence saves ~39% memory resources.

# 8.3 Hardware implementation and optimization

# 8.3.1 VLSI architecture

Fig. 8.3 shows the proposed object tracking VLSI system architecture. The feature extracting block includes an image integrator and a configurable spatiotemporal filter, which is a pixelwise temporal high-pass filter tightly embedding a spatial DoG filter. The feature matching block consists of a matching engine and an updating engine for the feature templates. These computational blocks are optimized and minimized to build a