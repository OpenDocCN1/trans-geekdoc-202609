![](bbox=[0.196, 0.074, 0.646, 0.273])

Figure 11.7 Noise artifact.

line-based scanning approach of the WSI scanner. If the scanner assigns a focus point to each patch, the focus of the image will be more accurate, and the resultant image will be high in quality. But a higher number of focus points will increase the scanning time significantly which is not practically feasible. Therefore, it is necessary to select an optimal number of points for which the quality is satisfactory and scanning time is minimal. Selecting the optimal focus points for sufficient quality in a minimal scanning time is the main challenge while scanning a specimen. As a result, sometimes parts of the image become out of focus. After assigning the focus points, the scanner adjusts the focal planes for the selected patches either by adjusting the objective lens position and the slide stage. Now, if the scanner selects focus points from some regions that are not properly aligned with the height, then those areas will be blurry in the WSI. The difference in distance between the erroneously selected focus point and the ideal focus points is directly proportional to the amount of blurriness. Appropriate stage and optics alignment are necessary to avoid focus problems. Figure 11.9 shows how autofocusing works in the WSI scanner.

![](bbox=[0.113, 0.642, 0.888, 0.808])

Figure 11.8 Tile-based (a) and line-based (b) scanning methods of a WSI scanner. Solid circles indicate focus points.

Noise is the other common scanning artifact found in WSI. The noise of a digital image can be classified broadly into two types. Firstly, the noise which is independent