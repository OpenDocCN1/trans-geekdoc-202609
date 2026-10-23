foreground and background probabilities of the corresponding anchors. The anchor is the foreground if the probability of the foreground is higher; otherwise, it is the background. Similarly, A^{reg}_{w×h×4k} is divided into k groups, and each group contains four feature maps (x, y, w, and h), which indicate the similarity metric between the corresponding anchor and the template. According to the highest similarity, the optimal location and the shape of the shadow are obtained.

![](bbox=[0.24, 0.27, 0.6, 0.32])

Figure 3. The feature composition of A^{cls}_{w×h×2k} and A^{reg}_{w×h×4k}.

# 2.2. Preprocessing

For all images of Video-SAR to have the same feature dimensions, preprocessing is required before entering GAS N. As shown in Figure 4, the input of GAS N is a pair of adjacent images in the SAR image sequence. The shadow template is a 127 × 127 area centered on the center (x, y) of the shadow in frame t-1. Similar to the image preprocessing in [17], we cropped an ((w + h) × 0.5 + w, (w + h) × 0.5 + h) area in frame t-1 centered on (x, y) and then resized it to 127 × 127, where (w, h) is the boundary of the shadow. Here, (x, y, w, and h) are known in the training stage, while in the testing stage, the parameters represent the prediction results of the previous frame. Because the template size of all existing methods is 127 × 127 [17,18], to ensure the rationality of the comparison, we chose 127 × 127 as the template size. The search area is centered on the center of the shadow in frame t, and we cropped an (((w + h) × 0.5 + w) × 255/127, ((w + h) × 0.5 + h) × 255/127) area and then resized it to 255 × 255. This area is larger than the shadow’s template to ensure that the shadow is always included in the search area.

![](bbox=[0.24, 0.6, 0.88, 0.85])

Figure 4. The input preprocessing of GAS N.

# 2.3. Tracking Process

The whole process of TOI tracking based on GAS N is shown in Figure 5. The details are as follows.