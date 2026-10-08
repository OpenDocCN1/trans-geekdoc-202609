# Video Classification

# Chapter 9

The frames from the video are taken and passed through a convolutional network. The layers are fused, and the pose heatmaps are obtained. The pose heatmaps are combined with optical flow to get the warped heatmaps. The warped heatmaps across a timeframe are pooled to produce the pooled heatmap, getting the final pose.

# Tracking facial landmarks

Face analysis in videos requires face detection, landmark detection, pose estimation, verification, and so on. Computing landmarks are especially crucial for capturing facial animation, human-computer interaction, and human activity recognition. Instead of computing over frames, it can be computed over video. Gu et al. (http://research.nvidia.com/sites/default/files/publs/2017-07_dynamic-Facial-Analysis/rnnface.pdf) proposed a method to use a joint estimation of detection and tracking of facial landmarks in videos using RNN. The results outperform frame wise predictions and other previous models. The landmarks are computed by CNN, and the temporal aspect is encoded in an RNN. Synthetic data was used for training.

# Segmenting videos

Videos can be segmented in a better way when temporal information is used. Gadde et al. (https://ps.is.tuebingen.de/uploads_file/attachment/386/gadde2017videocnns.pdf) proposed a method to combine temporal information by warping. The following image demonstrates the solution, which segments two frames and combines with the warping:

![](bbox=[0.203, 0.631, 0.796, 0.813])

> Reproduced from Gadde et al.