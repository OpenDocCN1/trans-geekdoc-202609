# Classifying videos over long periods

The fusion method works for short video snippets. Classifying longer videos is difficult as a lot of frames have to be computed and remembered. Ng et al. (https://www.cv-foundation.org/openaccess/content_cvpr_2015/papers/Ng_Beyond_Short_Snippets_2015_CVPR_paper.pdf) proposed two methods for classifying longer videos:

+   - The first approach is to pool the convolutional features temporally. Max-pooling is used as a feature aggregation method.
- The second approach has an LSTM connecting the convolutional features that handle the variable length of the video.

Both approaches are shown in the following image:

![](bbox=[0.199, 0.396, 0.8, 0.723])