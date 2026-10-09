of the head with YOLO-Pose, many weights can be transferred, which significantly saves training time.

During the training phase, both the regression model and the flow model are optimized simultaneously. The initial density distribution of the flow model is set to a Laplace distribution. During inference, there is no need to run the flow model, allowing the loss function to be flexibly applied to various regression algorithms without increasing the testing time. Since the flow model is lightweight, it has a minimal impact on the training speed. Due to the generality of this loss function, it can also be applied to other versions of YOLO.

# 4.2. Results on COCO Test Set

Table 1 compares the proposed model with other methods based on Higher, HR- Net, and EfficientHRNet. The proposed model demonstrates competitive performance in terms of AP values compared to existing methods. The achievements in AP values are particularly significant.

Table 1. Comparison with bottom-up methods on the COCO dataset.

| Method | Backbone | Size | AP | AP50 | AP75 | APL | AR |
|:---|:---|:---:|:---:|:---:|:---:|:---:|:---:|
| Onepose [10] | — | — | 61.8 | 84.9 | 67.5 | 68.2 | 66.5 |
| Hourglass [8] | Hourglass | 512 | 56.6 | 81.8 | 61.8 | — | 67.0 |
| PersonLab [36] | ResNet-152 | 1401 | 66.5 | 88.0 | 72.6 | 72.3 | 71.0 |
| PiPaf [37] | — | — | 66.7 | — | — | 72.9 | — |
| HRNet [24] | HRNet-W32 | 512 | 64.1 | 86.3 | 70.4 | 73.9 | — |
| EfficientHRNet-H0 [38] | EfficientNetB0 | 512 | 64.0 | — | — | — | — |
| EfficientHRNet-H0 T [38] | EfficientNetB0 [39] | 512 | 67.1 | — | — | — | — |
| HigherHRNet [11] | HRNet-W32 | 512 | 66.4 | 87.5 | 72.8 | 74.2 | — |
| HigherHRNet [11] | HRNet-W48 | 640 | 68.4 | 88.2 | 75.1 | 74.2 | — |
| HigherHRNet T [11] | HRNet-W48 | 640 | 70.5 | 89.3 | 77.2 | 75.8 | — |
| DEKR [40] | HRNet-W32 | 512 | 67.3 | 87.9 | 74.1 | 76.1 | 72.4 |
| DEKR [40] | HRNet-W48 | 640 | 70.0 | 89.4 | 77.3 | 76.9 | 75.4 |
| YOLOv5m6-Pose [16] | Darknet-csp-d53-s | 960 | 62.9 | 87.7 | 69.4 | 71.8 | 69.8 |
| YOLOv5m6-Pose [16] | Darknet-csp-d53-m | 960 | 66.6 | 89.8 | 73.8 | 75.2 | 73.4 |
| YOLOv5m6-Pose [16] | Darknet-csp-d53-l | 960 | 68.5 | 90.3 | 74.8 | 76.5 | 75.0 |
| YOLOv5m6-Release | Darknet-csp-d53-s | 960 | 65.0 | 87.8 | 71.2 | 71.7 | 71.5 |
| YOLOv5m6-Release | Darknet-csp-d53-m | 960 | 67.6 | 89.2 | 74.5 | 73.8 | 74.0 |

† Indicates multi-scale testing.

One of the reasons why the proposed model performs well in terms of AP values is the adoption of a novel loss function and network module, which enables the network to better understand the spatial relationships between keypoints. Through this approach, the model gains a better understanding of the structure and relationships of human poses.

Furthermore, the proposed model exhibits superiority in predicting keypoints that are partially occluded. As shown in Figure 5, the model accurately predicts partially occluded keypoints, which is crucial for practical applications where occlusions may occur.

Experiments indicate that the proposed model is competitive in keypoint detection tasks and achieves notable results in terms of AP values and predicting keypoints in occluded body parts. The authors believe that the proposed model can play an important role in various practical applications, such as human action analysis and human–computer interaction.