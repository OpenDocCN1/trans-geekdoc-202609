![](bbox=[0.15, 0.13, 0.85, 0.7])

Figure 16.16 Schematic diagram of proposed watermark extraction process.

# 16.4.1.2.1 Image Fusion

Image fusion carries with DWT [4, 9], DCT [5, 12]. Here MRI provides soft tissue information and PET image provides blood cells information. An individual image does not provide maximum information. After fusion process to obtain fused image it contains soft tissue information and also blood information.

+   1. Read the MRI (ip1) and PET (RGB) (ip2) color image with same size. The PET (RGB) color image converted to HSI (hue, saturation and intensity) model. We can process only the intensity component while hue and saturation components remain unchanged.