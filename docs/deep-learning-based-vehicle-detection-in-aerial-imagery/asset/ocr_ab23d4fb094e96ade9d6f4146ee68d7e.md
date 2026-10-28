![](bbox=[0.14, 0.17, 0.86, 0.45])

Figure 4.7: Examples for semantic labeling masks (top row) resulting in split (1st column) and merged (2nd column) GT annotations that are manually adjusted (bottom row) and examples for semantic labeling masks with vehicles beneath a tree labeled as category tree (3rd and 4th column) whose annotations are manually added.

# 4.2 Evaluation Metrics and Protocol

In the following, common metrics to evaluate the performance of the proposed detection pipeline, the region proposal generation, i.e., RPN, and the semantic labeling approaches to integrate semantic context information are introduced.

# Object Detection

In this thesis, average precision (AP) [Sal83], which is a common metric to measure the detection performance, is applied following the evaluation protocol introduced in [Eve10]. To compute the AP, the detection results are compared against GT. The detection results and GT are provided as bounding boxes with an associated class label. The detection results further comprise for each bounding box the probability for the assigned class, which is denoted as confidence score.

The confidence score and the Intersection over Union (IoU), also referred to as Jaccard coefficient, are used as criteria to determine whether a detection is