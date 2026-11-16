+   2. **Configuration of TotalSegmentator:** TotalSegmentator is configured to recognize the typical features of breast tumors in MRI scans. Parameters such as segmentation depth, sensitivity, and specificity are adjusted based on preliminary tests to optimize the balance between true positive and false positive rates.

+   3. **Segmentation Execution:** The tool applies deep learning algorithms, specifically trained on extensive sets of labeled medical images, to automatically detect and segment the regions of interest (ROIs). This includes identifying and outlining tumor tissues within the breast, differentiating them from healthy tissue based on texture, intensity, and morphological criteria.

# 5.3.2.1.1 Mathematical Model of Segmentation

The segmentation process can be understood as a function that maps the intensity values of pixels to a label indicating whether the pixel belongs to a tumor or normal tissue. Mathematically, this can be represented as presented in Equation 5.3.

```
S(x, y) = \left\{\begin{array}{ll} 1 & \text{if pixel } (x, y) \text{ belongs to tumor} \\ 0 & \text{otherwise} \end{array}\right. \quad (5.3)
```

Where S is the segmentation function, and (x y) are the coordinates of a pixel in the image.

![](bbox=[0.13, 0.485, 0.87, 0.65])

**FIGURE 5.2** Illustration of a sample automated MRI image segmentation part 1.

![](bbox=[0.13, 0.72, 0.865, 0.885])

**FIGURE 5.3** Illustration of a sample automated MRI image segmentation part 2.