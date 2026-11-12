![](bbox=[0.17, 0.1, 0.82, 0.63])

# Figure 5.53: Bounding box regression

So, we understand object detection using RCNN now, but there are certain limitations of RCNN as well. Let us discuss some of them as follows:

+   - As RCNN extracts up to 2,000 regions from an input image using a selective search algorithm.
+   - After that, RCNN has to extract the feature from all the 2,000 regions of the input image.
+   - Now, let us say we have n number of input images, so in this case, the number of feature extraction will be for n*2,000 cases.
+   - And the whole RCNN process follows the following steps for object detection:
+     i. It uses a selective search algorithm to determine the region of interest.
+     ii. Furthermore, it uses CNN for feature extraction.