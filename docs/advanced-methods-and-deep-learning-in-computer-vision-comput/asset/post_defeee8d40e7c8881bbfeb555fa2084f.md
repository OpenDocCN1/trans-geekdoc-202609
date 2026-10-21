
## References

- Yang, Y., Soatto, S., 2020. FDA: Fourier domain adaptation for semantic segmentation. arXiv preprint. arXiv:2004.05498.
- Zhang, Y., Qiu, Z., Yao, T., Liu, D., Mei, T., 2018. Fully convolutional adaptation networks for semantic segmentation. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR), pp. 6810–6818.
- Zhou, P., Mai, L., Zhang, J., Xu, N., Wu, Z., Davis, L.S., 2019. M2kd: multi-model and multi-level knowledge distillation for incremental learning. arXiv preprint. arXiv:1904.01769.
- Zhou, Q., Feng, Z., Cheng, G., Tan, X., Shi, J., Ma, L., 2020. Uncertainty-aware consistency regularization for cross-domain semantic segmentation. arXiv preprint. arXiv:2004.08878.
- Zhu, J., Park, T., Isola, P., Efros, A.A., 2017. Unpaired image-to-image translation using cycle-consistent adversarial networks. In: Proceedings of the International Conference on Computer Vision (ICCV).
- Zhu, X., Zhou, H., Yang, C., Shi, J., Lin, D., 2018. Penalizing top performers: conservative loss for semantic segmentation adaptation. In: Proceedings of the European Conference on Computer Vision (ECCV), pp. 568–583.
- Zhuo, J., Wang, S., Cui, S., Huang, Q., 2019. Unsupervised open domain recognition by semantic discrepancy minimization. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR), pp. 750–759.
- Zou, Y., Yu, Z., Liu, X., Kumar, B.V., Wang, J., 2019. Confidence regularized self-training. In: Proceedings of the International Conference on Computer Vision (ICCV), pp. 5982–5991.
- Zou, Y., Yu, Z., Vijaya Kumar, B., Wang, J., 2018. Unsupervised domain adaptation for semantic segmentation via class-balanced self-training. In: Proceedings of the European Conference on Computer Vision (ECCV), pp. 289–305.

## Biographies

Umberto Michieli received the M.Sc. degree in Telecommunication Engineering from the University of Padova in 2018. He is currently a final-year Ph.D. student at the same University. In 2018, he spent 6 months as a Visiting Researcher with the Technische Universität Dresden. In 2020 he interned as Research Engineer for 8 months at Samsung Research UK. His research focuses on transfer learning techniques for semantic segmentation, in particular on domain adaptation and on incremental learning.

Marco Toldo received the M.Sc. degree in ICT for Internet and Multimedia in 2019 at the University of Padova. At present, he is doing his Ph.D. at the Department of Information Engineering of the same university. In 2021 he interned as Research Engineer for 7 months at Samsung Research UK. His research interests involve domain adaptation and continual learning applied to computer vision.

Pietro Zanuttigh received the M.Sc. degree in Computer Engineering and the Ph.D. degree from the University of Padova, in 2003 and 2007, respectively. He is currently an Associate Professor with the Department of Information Engineering of the same university. His research interests include semantic understanding of images and 3D data, domain adaptation and incremental learning for visual data, 3D data processing with a special focus on ToF sensors, multiple sensors fusion and hand gesture recognition.

This page intentionally left blank

## CHAPTER 9 Visual tracking

Tracking in scenes containing multiple moving objects

Michael Felsberg<sup>a,b</sup>

<sup>a</sup>Computer Vision Laboratory, Department of Electrical Engineering, Linköping University, Linköping, Sweden <sup>b</sup>School of Engineering, University of KwaZulu-Natal, Durban, South Africa

### CHAPTER POINTS

- Visual object tracking.
- Discriminative tracking approaches.
- Correlation filters.
- Deep features.
- Deep learning of tracking.
- Video object segmentation.
- Discriminative segmentation.

### 9.1 Introduction

Tracking is a highly ambiguous term, and even for visual tracking, many different interpretations exist. Therefore, this chapter starts with a thorough definition of the problem addressed to delineate this chapter from other interpretations and to make all assumptions explicit.

#### 9.1.1 Problem definition

In this chapter, we will consider the problem of generic visual tracking, in the sense as defined in the visual object tracking (VOT) challenges 2013–2020 (Kristan et al., 2013, 2015a,b, 2016, 2017, 2019,b, 2020), which also coincides with the online tracking benchmark (OTB) definition (Wu et al., 2013). The tracking is performed in the image domain and no prior knowledge about object classes is available: generic means class agnostic.

The problem is formulated in the 2D image plane, in contrast to 3D tracking approaches (Garon and Lalonde, 2017). Also, only a single object (target) is considered in contrast to the multiple object tracking case (Dendorfer et al., 2020) that requires association of targets through the sequence. However, focusing on tracking a single object does not imply that no other moving objects, so-called distractors, exist in the sequences. The tracking task thus requires not to mix up the target with any of the distractors even if they partly occlude the target. It is assumed that the target is at least partly visible throughout the sequence such that no redetection is required. The sequence might originate from a moving camera, which excludes simple background modeling (Stauffer and Grimson, 2000) for detecting the target.

The tracking target is provided by a single annotation in the first frame of an image sequence in the form of a bounding-box (or a segmentation mask – see Section 9.5). The task is then to predict the bounding-box (or segmentation mask) that contains the same object in all subsequent frames. Bounding-boxes can be defined in many different coordinates; the exact format does not matter as long as it is consistently used. In the VOT challenge, the upper left corner (x, y) and the width w and height h are used (origin in the upper left). Thus, we get the formal task definition:

- input: a video (image sequence) and one annotated bounding-box (x0, y0, w0, h0) for the initial frame in the sequence
- output: prediction of bounding-boxes (xk, yk, wk, hk) for all frames k > 0
- requirement: the prediction of the bounding-box for frame K may only use data from frames k ≤ K.

This task definition formulates a one-shot learning problem, as one annotated training sample for the present sequence is provided. The goal of this learning problem is to train a detector that predicts the best fitting bounding-box in the subsequent frame, also called tracking-by-detection. Typically, the best fitting bounding-box is classified as the target, all others as background. However, it is also possible to use regression methods to determine the bounding-box parameters.

#### 9.1.2 Challenges in tracking

The main difficulty in tracking by detection is that the object of interest might change appearance in the course of the sequence: It might

- rotate in the image plane
- change scale by moving in depth
- change aspect by out-of-plane rotations / changes in viewpoint
- be articulated
- suffer from motion blur
- undergo changes of illumination
- be partly occluded.

These changes might make the detector fail and lose the target, particularly in the presence of cluttered background and distractors. Therefore, modern tracking approaches usually adapt the detector model using its own predictions from previous frames; see Fig. 9.1.

![](img/fe161b7f6e96e35e7e853eece52c6dce_327_0.png)

FIGURE 9.1 Adaptive tracking model. Block diagram of an adaptive tracking model. After initial training (left), the model adapts using its own predictions as training samples (right).

This adaptive process establishes a bootstrapping procedure, i.e., a recursive self-improvement that proceeds without external input other than the single initial annotation. One key problem of this process is to balance the previous model against the update information. If the model is too rigid, it will lose the target under appearance changes, if the model is too flexible, it will drift away from the target (Matthews et al., 2004; Wang et al., 2016).

#### 9.1.3 Motivation of the setting

The drift problem is largely reduced if the class of the object of interest is known. However, as pointed out in Section 9.1.1, we aim at generic, i.e. class agnostic, models. The main motivation for this choice is the open-world assumption, which, in contrast to the closed-world assumption, does not infer the incorrectness of a statement from its absence (Reiter, 1978), or, translated to detection, does not infer the nonexistence of an object from the absence of a corresponding detector response. There are two issues with the closed-world assumption in context of visual detectors:

- The visual appearance of objects is characterized by a high intra-class variability, e.g., cars and bicycles in traffic scenarios.
- The set of objects is continuously growing, e.g., e-bikes and hover-boards appear in traffic scenarios.

If an object is not detected due to the former reason, it means that the detector failed to model the variety of appearance of the object. This might be caused by limitations in the training set or by infinite possible variations of appearance. If an object is not detected due to the latter reason, it means that the object class is not represented in the training set at all. However, just because the data set fails to cover a certain class, does not mean that this class is irrelevant to the detector. Designing a system based on the premise that classes not present at training time are neglected is ethically problematic, e.g. in traffic safety applications.

Traffic safety systems are often based on other sensors than vision: Lidar, radar, ultrasound, etc. However, visual sensors will always be of central interest as they establish an approach.
