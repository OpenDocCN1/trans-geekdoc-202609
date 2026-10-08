![](bbox=[0.358, 0.103, 0.642, 0.303])

Figure 2. Facial ROIs. $R^1$, right forehead side; $R^2$, left forehead side; $R^3$, right periorbital side; $R^4$, left periorbital side; $R^5$, tip of nose; $R^6$, right cheek; $R^7$, left cheek; $R^8$, right perinasal side; $R^9$, left perinasal side; $R^{10}$, right chin side; $R^{11}$, left chin side.

# 3.2.5. ROI Detection

Infrared images are more blurred than color images [23]; therefore the ROI detection over thermal images of low-cost cameras is a challenge. For this reason, the well-known Viola-Jones algorithm [32] was used on color images for head detection and other facial regions, such as nose and eyes [17,21,32]. Then, initial detected regions were used as references to automatically locate ROIs within the face (see Table 1), the nose, both sides of forehead, cheeks, periorbital area (close to the eyes) and perinasal area (bottom of the nose).

Table 1. ROIs used to locate facial landmarks over a frame $k_i$.

| Reference ROIs | Located ROIs |
| --- | --- |
| Head | $R^1, R^2, R^{11}$ |
| Eyes | $R^3, R^4, R^7, R^9$ |
| Nose | $R^5, R^6, R^8, R^{10}$ |

$R^1$, right forehead side; $R^2$, left forehead side; $R^3$, right periorbital side; $R^4$, left periorbital side; $R^5$, tip of nose; $R^6$, right cheek; $R^7$, left cheek; $R^8$, right perinasal side; $R^9$, left perinasal side; $R^{10}$, right chin side; $R^{11}$, left chin side.

In our study, the ROI sizes were also computed using the width of the head, and the aforementioned proportions [17,18,21]. Additionally, the facial ROIs were spatially spaced, taking them as the expert annotation. Afterwards, the corresponding facial ROIs were projected onto the thermal image through the aforementioned transformation using a homology matrix (Section 3.2.2), as shown in Figure 4. Here, the ROI set of a thermal frame $b$ is defined by $R_b = \{R_1^b, R_2^b, \dots, R_{11}^b\}$, being the head ROI and $R_k^b$ for $k=1$ to the 11 facial ROIs. That $R^i$ is described by several pixels $R_k^b$ for a range from 0 to 255 (gray scale of 8 bits).

Figure 2.c show our proposal to accurately locate facial ROIs, formed by the following two-stages:(1) automatic ROI detection and (2) ROI placement correction.

# 3.2.6. ROI Location Correction

A new method is proposed here to correct with accuracy the detected ROIs by the Viola-Jones algorithm, taking into account all pre-defined ROI positions, which were also manually annotated on a first frame by a trained expert.