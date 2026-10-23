details than just resizing the whole image (Figure 7). However, because it introduces randomness, these methods cannot be used as a reduction method for the validation dataset:

+   - **Random Crop**: a random region with the size of 320 × 320 pixels is cropped out of the rectangle image. This preserves pixel scale since no downsampling is performed.
+   - **Random Crop and Resize**: crops a random location with a random scaling, then downsample it to the target resolution.

![](bbox=[0.22, 0.31, 0.32, 0.34])

![](bbox=[0.62, 0.31, 0.77, 0.34])

![](bbox=[0.06, 0.34, 0.9, 0.54])

![](bbox=[0.22, 0.55, 0.32, 0.58])

![](bbox=[0.62, 0.55, 0.78, 0.58])

![](bbox=[0.06, 0.59, 0.9, 0.77])

Figure 7. Reduce Transformations comparison.

# 3.1.2. Geometric Transformations

In computer vision tasks, geometric transformations are cheap and easy to implement. However, it is important to be aware of choosing the transformations’ magnitude that preserves the label in the image. For example, in optical character recognition, rotating a number by 180° can result in a different label interpretation in the case of the numbers six and nine.

Flipping an image along the horizontal or vertical centerline is a common data augmentation method. Referring to Figure 2a, the range direction r_g for this dataset is on the vertical or y-axis, while the flight direction a_z is on the horizontal or x-axis. The Horizontal Flip does not alter the properties of a radar image. It would be as if the vehicle carrying the sensor was moving in the opposite direction. In contrast, the Vertical Flip makes the shadows and layovers appear on the opposite side, creating inconsistency.