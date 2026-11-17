Additionally, a flattening data method or a regulatory strategy should be implemented to reduce the dataset’s susceptibility to noise, contrast, and size (Fig. 6). Smoothing techniques are also applied to reduce the risk of data loss [31]. Finally, the time required for prediction can be reduced using efficient pre-processing techniques.

![](bbox=[0.203, 0.246, 0.788, 0.493])

Fig. (6). Schematic workflow showing the process happening in the Image Enhancement procedure.

# Active Contour Method

The active contour technique removes impediments such as labels, patient identities, scans, and taping artefacts using a thresholding-based automatic algorithm. It also creates the shape for the muscle part’s boundary. Finally, it combines the muscular part binary picture with the original image to get the required upper chest muscle.

# Seeded Region Growing Method

It is a colour image approach that focuses on the CLAHE procedure [32]. It uses a unique seeded region growing (SRG) strategy to establish a compact rectangle that distinguishes the musculature section of the ROI and then hides the tissue. The technique of region expansion as shown in Fig. (7) combines pixels into bigger patches based on established parameters [33]. The underlying plan is to replace it with a seed point and then develop it into sections. For example, the proposal of halting rules is a challenge in the seeded region-growing algorithm.