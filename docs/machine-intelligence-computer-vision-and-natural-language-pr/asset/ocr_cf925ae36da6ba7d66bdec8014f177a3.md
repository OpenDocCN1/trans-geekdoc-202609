# ML-Based Driving Assistance System 199

![](bbox=[0.119, 0.113, 0.859, 0.383])

Figure 10.6 Neural network model training.

intensity [5]. When edges are detected in an image, data is significantly reduced and useless information is culled, while the image’s significant structural properties are preserved. One example is an optimal edge detector, also called nanny. Ideally, the first criterion should have a low error rate and make sure that useful information is preserved while unwanted data is filtered out. As variation as possible should be kept between the original image and the processed image as the second criterion [5]. The third criterion involves removing multiple responses to edges. The edge detector uses these criteria to smooth out the image first. Next, it highlights regions with high spatial derivatives by calculating the image gradient.

Based on these regions, the algorithm then suppresses pixels that are not at the maximum using non-maximum suppression. To remove streaking along the edges and then the gradient array, hysteresis is now applied. Figure 10.7 shows the original image edge detection techniques applied. Figures 10.8 and 10.9 show the Sobel enhanced technique.

# 10.4.2 Feature Extraction Frontal Face

In this function, the classifier can recognize facial characteristics based on the Cascade Classifier’s function. This is followed by the function detect multiscale with grayscale image which detects faces on multiple scales [6]. Detection arrays are returned with coordinates, as well as height, which indicates the width of a box that defines the boundary of an object. This makes it easier to iterate over each face and draw boundary boxes. In the first step, both eyes are assigned to a