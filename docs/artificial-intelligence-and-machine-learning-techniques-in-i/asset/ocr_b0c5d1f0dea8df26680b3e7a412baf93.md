of upsampling to the later end layer, which means that all of an image’s features are retrieved in the convolutional layers before the final upsampling layer, as shown in Figure 14.6. This method has become more popular due to its lower computational cost and improved performance as compared to previous methods. This approach includes recent deep CNN methods, such as FSRCNN10 and ESPCN.11

![](bbox=[0.125, 0.285, 0.88, 0.415])

FIGURE 14.5 Early upsampling in image SR method.

![](bbox=[0.125, 0.485, 0.88, 0.635])

FIGURE 14.6 Late upsampling in image SR method.

# 14.2.2.3 PROGRESSIVE UPSAMPLING POSITION

Naturally, the 2x enlargement factor is the most common upsampling factor used by everyone to reconstruct the HR image. For example, image size 32 × 32 is to enlarge the scale factor 2x, which is equal to 64 × 64 pixels. In case we want to upscale this image up to scale 4x or 8x, then the network has a challenging task to alter directly in one step to enlargement factor 8x, but we can solve this issue by multiple upscaling steps to reconstruct the higher scale factor HR image, as shown in Figure 14.7. In this