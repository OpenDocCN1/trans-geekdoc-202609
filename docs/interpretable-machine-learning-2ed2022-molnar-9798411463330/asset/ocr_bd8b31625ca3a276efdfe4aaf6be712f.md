# 9.2 PIXEL ATTRIBUTION (SALIENCY MAPS)

| Greyhound (vanilla) | Soup Bowl (vanilla) | Eel (vanilla) |
| --- | --- | --- |
| ![image] | ![image] | ![image] |

Figure 9.9: Images of a dog classified as greyhound, a ramen soup classified as soup bowl, and an octopus classified as eel.

50%. The third image shows an octopus on the ocean floor, which is incorrectly classified as “Eel” with a high probability of 70%.

And these are the pixel attributions that aim to explain the classification:

| Greyhound (vanilla) | Soup Bowl (vanilla) | Eel (vanilla) |
| --- | --- | --- |
| Greyhound (Smoothgrad) | Soup Bowl (Smoothgrad) | Eel (Smoothgrad) |
| Greyhound (Grad-Cam) | Soup Bowl (Grad-CAM) | Eel (Grad-CAM) |
| ![image] | ![image] | ![image] |
| ![image] | ![image] | ![image] |
| ![image] | ![image] | ![image] |

Figure 9.10: Pixel attributions or saliency maps for the Vanilla Gradient method, Smooth-Grad and Grad-CAM.