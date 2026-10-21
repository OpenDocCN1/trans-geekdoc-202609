algebraic errors, it outperforms existing methods in terms of speed, simplicity and combined 2-D, 3-D and parallax accuracy.

Fathy et al. (2011) clarified the overall situation as follows: the 8-point algorithm is a one-step method which is normally applied after outlier removal to obtain an initial estimate of the fundamental matrix: this is then iteratively refined to produce a more accurate solution.

# 1.4.19 The achievements and limitations of multiple view vision

The last few sections have discussed the transformations required for camera calibration and have outlined how calibration can be achieved. The camera parameters have been classified as ‘internal’ and ‘external’, thereby simplifying the conceptual problem and throwing light on the origins of errors in the system. It has been shown that a minimum of 6 points is required to perform calibration in the general case where 11 transformation parameters are involved. Nevertheless, it is normally important to increase the number of points used for calibration as far as possible, since substantial gains in accuracy can be obtained via the resulting averaging process.

Section 1.4.12 introduced multiple view vision. This important topic was seen to rest on generalized epipolar geometry, and led to the essential and fundamental matrix formulations, which relate the observed positions of any point in two camera frames of reference. The importance of the 8-point algorithm for estimating either of these matrices—and particularly the fundamental matrix, which is relevant when the cameras are uncalibrated—was stressed. In addition, the need for accuracy and robustness in estimating the fundamental matrix is still a research issue, though great strides have been made in recent years (see Section 1.4.18) regarding the outlier removal phase of fundamental matrix estimation.

# 1.5 Part D – Tracking moving objects

# 1.5.1 Tracking – the basic concept

In recent years, many algorithms have been devised for interpreting single images and identifying a high proportion of the objects within them: following this success, attention turned to the analysis of image sequences and videos. In fact, if the images in any sequence were simply regarded as sets of separate images or ‘frames’, this new task could already be regarded as solved; it therefore became just as relevant to interpret image sequences as entities in their own right. Thus, algorithms were needed for identifying and tracking moving objects through any sequence.

We could tackle this task by identifying objects in all the frames, and then computing tracks showing how the objects have moved between frames. This could be implemented by the following algorithm:

+   for all frames in sequence
+   find and identify all the objects
+   link the objects between frames
+   list all the objects and their tracks.