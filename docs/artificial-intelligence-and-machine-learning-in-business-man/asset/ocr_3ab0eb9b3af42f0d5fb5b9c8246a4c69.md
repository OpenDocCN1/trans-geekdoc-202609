# Semantic Data Extraction Using Video Analysis

![](bbox=[0.135, 0.093, 0.864, 0.296])

FIGURE 15.4 Before and after localization

![](bbox=[0.336, 0.347, 0.665, 0.466])

FIGURE 15.5 Segmented Licence plate.

goal of predicting the exact position of an object in the image (i.e., where precisely in the picture, the object is present). The distinction between object localization and object detection is found here. Whilst object localization searches for the primary or the most visible object in a picture, object detection aims to locate all the objects with their boundaries.

In the licence plate detection, after mapping all the features and using object localization to mark them, the image looks as shown in Figure 15.4.

Multiple regions in the image may exhibit the characteristics and get marked. From these marked regions, the licence plate is differentiated by performing vertical projection on all regions. In vertical projection, the pixel values of all pixels aligned in a vertical line are added. The concept here is, since the licence plate has characters printed on it, there will be variations in the pixel values which the rest of the regions will lack. This will ensure that only the licence plate is highlighted. After performing preprocessing, feature extraction, localization and vertical projection of pixels on our image, we segment the required portion of the image, and the result is shown in Figure 15.5.

Segment Licence plate is given in Figure 15.5.

# 15.4.6 CHARACTER SEGMENTATION

Now that we have the required image segment, i.e., licence plate, the next thing to do is to segment individual characters from the image. There are many techniques