![](bbox=[0.088, 0.131, 0.915, 0.246])

**Figure 4.** Loss-metric inconsistency. All ground truths (GT) and predicted boxes (PB) are represented as $(c_x, c_y, w, h, \theta)$ under the long-edge definition. (a) Regression loss variations versus angle differences (AD); (b) rotational IoU variations versus angle differences under different aspect ratios (AR); (c) regression loss variations versus aspect ratios.

# 3.1.2. Angular Boundary Discontinuity

The angular boundary discontinuity refers to the surge in loss at the boundary of the angle definition range due to the periodicity of the angle (PoA) and the exchangeability of edges (EoE) [23]. Figure 5a shows the boundary problem under the OpenCV definition. Suppose there is a blue anchor/proposal and a green ground truth. The angle of the anchor/proposal is exactly around the maximum or minimum of the defined range. The ideal regression form is to rotate the anchor/proposal counterclockwise by a small angle to the position of the red box. However, due to the angle periodicity, the angle of the predicted box exceeds the defined range $[-90^\circ, 0)$, and the width and height are interchanged relative to the ground truth, leading to a large smooth L1 loss. At this point, the anchor/proposal has to be regressed in a more complex way. For example, it should be rotated clockwise by a larger angle, and its width and height should be scaled at the same time. A similar phenomenon also occurs under the long-edge definition, as shown in Figure 5b.

![](bbox=[0.114, 0.56, 0.711, 0.662])

**Figure 5.** Angular boundary discontinuity under (a) the OpenCV definition and (b) the long-edge definition.

In essence, angular boundary discontinuity is a kind of manifestation of loss-metric inconsistency. In the boundary case, even if the IoU between the predicted box and the ground truth is very high, a considerable loss will be incurred. Based on the above analysis, we can conclude that the $l_n$-norms are inapplicable to rotated bounding box regression.

# 3.2. Limitations of Conventional IoU-Based Losses

It has been demonstrated in horizontal detection methods that the IoU-based losses [36–40] can ensure that the training target remains consistent with the evaluation metric. In theory, they should also work in the rotation case, as the only difference is that the IoU computation for oriented bounding boxes is more complex than that for horizontal ones.

Compared to $l_n$-norms, the IoU loss has several merits. Firstly, the IoU computation involves all of the geometric properties of bounding boxes, including location, orientation, shape, etc. Secondly, instead of treating the parameters as independent variables as in