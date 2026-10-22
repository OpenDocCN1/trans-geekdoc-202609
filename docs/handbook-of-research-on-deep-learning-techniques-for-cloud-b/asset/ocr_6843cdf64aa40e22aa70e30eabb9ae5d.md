# Bidirectional Feature Pyramid Network (BFPN)

The original YOLOv5 model uses PANet (Liu et al., 2018) in the neck part for multi-scale feature fusion, but PANet merges the features without distinction when fusing the different features. However, because the resolutions of these different input features differ, their contributions to the fused output features are often unequal. A BFPN, or Weighted Bi-directional Feature Pyramid Network (Chen et al., 2021), is a feature pyramid network that allows for simple and fast multi-scale feature fusion. Traditional approaches typically treat all features fed into the Feature Pyramid Network (FPN) equally, regardless of their varying resolutions. However, input features at different resolutions frequently contribute unequally to output features. As a result, the BFPN adds a weight to each input feature, allowing the network to learn the significance of each as shown in Figure 4.

When compared to PANet, PANet added an additional bottom-up path for information flow at the cost of increased computational cost. BFPN, on the other hand, optimises these cross-scale connections by removing nodes with a single input edge, adding an extra edge from the original input to output node if they are on the same level, and treating each bidirectional path as a single feature network layer.

In the proposed model, the PANet is substituted with the BFPN in order to fuse image features without incurring a significant computational cost.

# EXPERIMENTS AND RESULTS

The dataset used in the experiment consists of 2324 images of size 416 x 416 after applying the augmentation. The augmentation is applied to artificially increase the dataset for training. The proposed YOLOv5 model needs the input images be annotated both in class and in the ground truth bounding box, hence the images are annotated with the help of VGG image annotator. The training hyper parameters used in the proposed model are 100 epochs with a momentum of 0.9 and an initial learning rate of 0.01.

# Evaluation Metrics

The precision (P) metric was used in this study to assess the accuracy of tomato fruit detection as mentioned in (Anand et al., 2022). The detection of positive samples in all images is measured by using recall (R). The average precision (AP) of a detector measures its performance in each category. The average of all class average precisions(Aps) is known as the mean average precision (mAP), and the definitions of precision(P), recall(R), average precision(AP), and mean average precision(mAP) of the mode are defined using (1-4). A model's complexity is determined by the quantity of floating-point operations (FLOPs) and parameters (Params).

P = True_Positive / (True_Positive + False_Positive) ×100% (1)