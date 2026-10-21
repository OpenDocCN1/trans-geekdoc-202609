# Successful Localization

![](bbox=[0.13, 0.1, 0.88, 0.4])

FIGURE 12.18 Qualitative Examples: Error-based attention location and the final prediction. Green BB: Prediction, Blue BB: Ground truth.

# 12.6 Other event segmentation approaches in computer vision

Typically, there are three different classes of approaches for temporal event segmentation: fully supervised, weakly supervised, and fully unsupervised. While fully supervised approaches have more precise localization and better labeling accuracy, the required number of annotations is rather large. The labeled training data demands do not scale well with an increase in label classes. While not requiring frame-level annotations, weakly supervised approaches have the underlying assumption that there exists a large, annotated training set that allows for effective detection of all possible actors (both human and nonhuman) in the set of action classes. Unsupervised approaches, such as ours, do not make any such assumptions but can result in poorer localization performance. We alleviate this to an extent by leveraging advances in region proposal mechanisms and robust self-learning representations. One particular class of unsupervised approach, called self-supervision, uses the data itself, without annotations, for supervision.

# 12.6.1 Supervised approaches

Fully supervised methods have been the dominant approach to temporal event segmentation. They consider the problem to be fully supervised and use the groundtruth annotations to take a segment by classification approach i.e., they assign the labels to semantically coherent "chunks", with contiguous frames sharing the same label, to segment the video into its constituent segments. The common pipeline in these approaches has been to extract features