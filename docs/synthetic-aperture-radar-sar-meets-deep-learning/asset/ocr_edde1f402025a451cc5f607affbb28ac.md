Our proposed RSSD acquires data from three SAR satellites with different resolutions, polarizations, and imaging modes. The imaging areas are selected in ports and canals with busy trade. All images have been meticulously pre-processed and split into 8013 ship slices of 800 × 800 pixels. With the help of professional tools, 21,479 ships are precisely annotated by OBBs. All these treatments contribute to the complexity and diversity of our dataset.

# 3. Analysis of Angle Regression Problems and Conventional IoU-Based Losses

In this section, we first discuss two major problems in the existing rotation detectors mainly caused by angle regression. Then, we review the conventional IoU-based losses and analyze the limitations they may encounter in rotated bounding box regression. Finally, we summarize several requirements that should be met for the rotational IoU loss.

# 3.1. Problems of Rotation Detectors Based on Angle Regression

Figure 3 demonstrates two generic parametric definitions of oriented bounding boxes (i.e., OpenCV definition and long-edge definition). According to the above two definitions, any two-dimensional bounding box can be represented as a group of five parameters (cx, cy, w, h, and θ), where (cx, cy) represents the centroid coordinate of the oriented bounding box, w and h indicate the width and height, respectively, and θ denotes the rotation angle. To predict the angle θ of the bounding box, most rotation detectors directly introduce an additional output channel into the regression subnet and use L_n-norms as the regression loss during the training phase. However, in the testing stage, the performance is evaluated by IoU. Obviously, such a mismatch may present some problems, which we will now summarize.

![](bbox=[0.2, 0.6, 0.92, 0.78])

Figure 3. Two generic parametric definitions of oriented bounding boxes. (a) OpenCV definition, where θ indicates the acute or right angle between the width w and the x-axis; (b) Long-edge definition, where w and h signify the long side and short side of a bounding box, respectively. Here, θ denotes the angle from the x-axis to the direction of the width w.

# 3.1.1. Loss-Metric Inconsistency

In Figure 4a, we compare the relationships between different regression losses and angle differences. Despite the fact that they are all monotonic, only the IoU loss (the light blue curve) and our TDLou loss (the navy blue curve) are concave, indicating that the gradient directions of L_n-norms are inconsistent with that of IoU. Figure 4b displays the relationship between the rotational IoU and angle differences under different aspect ratios. For a target with a large aspect ratio, a slight angle difference will also lead to a rapid drop in the IoU value. Figure 4c displays the relationships between different regression losses and aspect ratios. All L_n-norm losses remain constant regardless of aspect ratio variations, while the IoU-based losses vary dramatically. The loss-metric inconsistency leads to the conclusion that even a small training loss cannot guarantee high detection performance.