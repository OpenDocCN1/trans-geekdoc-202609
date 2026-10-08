# Semantic Segmentation

# Chapter 5

The architecture looks similar to the R-CNN with an addition of segmentation. It is a multi-stage network with end-to-end training. The region proposals are learned. The network is split into two, one for detection and the other for a classification score. The results are excellent, as shown here:

![](bbox=[0.106, 0.217, 0.894, 0.715])

Figure illustrating the segmenting instances process, Note that the objects are detected accurately and are segmented accordingly Reproduced with permission from He et al.

The same network can also predict the poses of people. The two tasks of segmentation and detection are processed in parallel.