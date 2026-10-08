# Similarity Learning

# Chapter 6

Here is a sample of the images present in MTFL:

![](bbox=[0.109, 0.165, 0.89, 0.269])

![](bbox=[0.109, 0.27, 0.89, 0.374])

![](bbox=[0.109, 0.375, 0.89, 0.479])

+   - Pose estimation (0°, ±30°, ±60°)
- S/NS = smiling / not smiling
- G/NG = with / without glasses
- M/F = male / female

> Proposed by Zhang et al. and reproduced from mnlab.cuhk.edu.hk/projects/TCDCN/img/1.jpg

There are a lot of variations in the faces with respect to age, illumination, emotions and so on. Head pose is the angle of face direction, denoted in degrees. Glasses, smiling, gender attributes, and so are annotated with binary labels.

# The Kaggle keypoint dataset

The Kaggle keypoint dataset is annotated with 15 facial landmarks. There are 8,832 images present in the dataset. It can be downloaded from the link https://www.kaggle.com/c/facial-keypoints-detection/data. The images are 96 pixels by 96 pixels in size.