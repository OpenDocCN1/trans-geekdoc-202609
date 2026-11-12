In the case of a gray-scale image (8-bit) (or a black and white image), the image is usually a matrix of two-dimension with pixel values ranging from 0 to 255, where 255 denotes complete white and 0 denotes complete black and the range from 0 to 255 represents grey-scale image as shown in figure 1.7.

# # Spatio temporal features

Space-time features capture the distinctive shapes in a video. It provides a self-determined representation of events that occurred with time during different types of motion in a scene. Spatiotemporal features are generally extracted from the video directly and avoid the possible failures of pre-processing techniques such as tracking and motion segmentation.

So, the motion and space features are combined over a finite time interval to form the spatiotemporal features. These types of features are commonly used for human action recognition systems, as shown in figure 1.8:

![](bbox=[0.253, 0.432, 0.792, 0.835])

Figure 1.8: Use of spatio-temporal features