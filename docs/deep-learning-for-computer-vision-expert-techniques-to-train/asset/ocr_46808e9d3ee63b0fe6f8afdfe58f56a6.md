# 9 Video Classification

In this chapter, we will see how to train deep learning models for video data. We will start classifying videos on a frame basis. Then, we will use the temporal information for better accuracy. Later, we will extend the applications of images to videos, including pose estimation, captioning, and generating videos.

We will cover the following topics in this chapter:

+   - The datasets and the algorithms of video classification
- Splitting a video into frames and classifying videos
- Training a model for visual features on an individual frame level 0
- Understanding 3D convolution and its use in videos
- Incorporating motion vectors on video
- Object tracking utilizing the temporal information
- Applications such as human pose estimation and video captioning

# Understanding and classifying videos

A video is nothing but a series of images. Video brings a new dimension to the image along the temporal direction. The spatial features of the images and temporal features of the video can be put together, providing a better outcome than just the image. The extra dimension also results in a lot of space and hence increases the complexity of training and inference. The computational demands are extremely high for processing a video. Video also changes the architecture of deep learning models as we have to consider the temporal features.