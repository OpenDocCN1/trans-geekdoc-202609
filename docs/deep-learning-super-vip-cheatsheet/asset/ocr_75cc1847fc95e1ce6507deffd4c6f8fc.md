| Bounding box detection | Landmark detection |
|---|---|
| Detects the part of the image where the object is located | - Detects a shape or characteristics of an object (e.g. eyes)
- More granular |
| ![Bounding box with b_h, b_w and (b_x,b_y)](image) | ![Landmark points (l1x,l1y)...(lnx,lny)](image) |
| Box of center $(b_x,b_y)$, height $b_h$ and width $b_w$ | Reference points $(l_{1x},l_{1y}),...,(l_{nx},l_{ny})$ |

Intersection over Union – Intersection over Union, also known as IoU, is a function that quantifies how correctly positioned a predicted bounding box $B_p$ is over the actual bounding box $B_a$. It is defined as: $\text{IoU}(B_p,B_a)=\frac{B_p\cap B_a}{B_p\cup B_a}$

![](bbox=[0.1, 0.52, 0.46, 0.7])

> > Remark: we always have $IoU\in[0,1]$. By convention, a predicted bounding box $B_p$ is considered as being reasonably good if $IoU(B_p,B_a)\ge0.5$.

Anchor boxes – Anchor boxing is a technique used to predict overlapping bounding boxes. In practice, the network is allowed to predict more than one box simultaneously, where each box prediction is constrained to have a given set of geometrical properties. For instance, the first prediction can potentially be a rectangular box of a given form, while the second will be another rectangular box of a different geometrical form.

Non-max suppression – The non-max suppression technique aims at removing duplicate overlapping bounding boxes of a same object by selecting the most representative ones. After having removed all boxes having a probability prediction lower than 0.6, the following steps are repeated while there are boxes remaining:

+   - Step 1: Pick the box with the largest prediction probability.
- Step 2: Discard any box having an IoU ≥ 0.5 with the previous box.

![](bbox=[0.55, 0.08, 0.92, 0.22])

YOLO – You Only Look Once (YOLO) is an object detection algorithm that performs the following steps:

+   - Step 1: Divide the input image into a $G\times G$ grid.
- Step 2: For each grid cell, run a CNN that predicts $y$ of the following form: $y=[p_c,b_x,b_y,b_h,b_w,c_1,c_2,...,c_p,...]^T\in\mathbb{R}^{G\times G\times k\times(5+p)}$ repeated $k$ times where $p_c$ is the probability of detecting an object, $b_x,b_y,b_h,b_w$ are the properties of the detected bounding box, $c_1...c_p$ is a one-hot representation of which of the $p$ classes were detected, and $k$ is the number of anchor boxes.
- Step 3: Run the non-max suppression algorithm to remove any potential duplicate overlapping bounding boxes.

![](bbox=[0.55, 0.5, 0.92, 0.65])

> > Remark: when $p_c=0$, then the network does not detect any object. In that case, the corresponding predictions $b_x,...,c_p$ have to be ignored.

R-CNN – Region with Convolutional Neural Networks (R-CNN) is an object detection algorithm that first segments the image to find potential relevant bounding boxes and then run the detection algorithm to find most probable objects in those bounding boxes.

![](bbox=[0.55, 0.78, 0.92, 0.9])

> > Remark: although the original algorithm is computationally expensive and slow, newer architectures enabled the algorithm to run faster, such as Fast R-CNN and Faster R-CNN.