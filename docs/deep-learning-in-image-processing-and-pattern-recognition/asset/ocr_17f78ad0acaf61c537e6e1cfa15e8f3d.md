# # YOLO-Rlepose: Improved YOLO Based on Swin Transformer and Rle-Oks Loss for Multi-Person Pose Estimation

**Yi Jiang** $^{1,\dagger}$, **Kexin Yang** $^{1,* ,\dagger}$, **Jinlin Zhu** $^{1}$ and **Li Qin** $^{2}$

+   1.  Department of Communications Engineering, Harbin University of Science and Technology, Harbin 150080, China; jason@hrbust.edu.cn (Y.J.); 2220600035@stu.hrbust.edu.cn (J.Z.)  
2.  Department of Engineering Mechanics, Harbin University of Science and Technology, Harbin 150080, China  
* Correspondence: 2220610148@stu.hrbust.edu.cn  
$^{\dagger}$ These authors contributed equally to this work.

**Abstract:** In recent years, there has been significant progress in human pose estimation, fueled by the widespread adoption of deep convolutional neural networks. However, despite these advancements, multi-person 2D pose estimation still remains highly challenging due to factors such as occlusion, noise, and non-rigid body movements. Currently, most multi-person pose estimation approaches handle joint localization and association separately. This study proposes a direct regression-based method to estimate the 2D human pose from a single image. The authors name this method YOLO-Rlepose. Compared to traditional methods, YOLO-Rlepose leverages transformer models to better capture global dependencies between image feature blocks and preserves sufficient spatial information for keypoint detection through a multi-head self-attention mechanism. To further improve the accuracy of the YOLO-Rlepose model, this paper proposes the following enhancements. Firstly, this study introduces the C3 Module with Swin Transformer (C3STR). This module builds upon the C3 module in You Only Look Once (YOLO) by incorporating a Swin Transformer branch, enhancing the YOLO-Rlepose model’s ability to capture global information and rich contextual information. Next, a novel loss function named Rle-Oks loss is proposed. The loss function facilitates the training process by learning the distributional changes through Residual Log-likelihood Estimation. To assign different weights based on the importance of different key points in the human body, this study introduces a weight coefficient into the loss function. The experiments proved the efficiency of the proposed YOLO-Rlepose model. On the COCO dataset, the model outperforms the previous SOTA method by 2.11% in AP.

**Keywords:** human pose estimation; deep learning; convolutional neural network; transformer

# ## 1. Introduction

The task of multi-person 2D keypoint detection aims to enable computers to understand all instances in an image and simultaneously identify the motion joints of each individual. Human pose estimation is one of the fundamental tasks in the field of computer vision, with extensive applications in numerous areas, including activity recognition [1], human–robot interaction [2], pedestrian tracking [3], and the re-identification of individuals [4].

Due to the various bending, stretching, or twisting movements of joints during human activities, as shown in Figure 1c,d,f, human joints may also be occluded by other objects, body parts, or themselves, as shown in Figure 1a,b,e. These factors make it challenging for pose estimation algorithms to accurately detect the positions and angles of joints. Therefore, pose estimation algorithms need to accurately capture these non-rigid variations to provide accurate pose estimation results. As a result, multi-person 2D human pose estimation is a challenging task.

Human pose estimation algorithms can be classified based on two criteria. The first criterion is the algorithm’s workflow, which categorizes human pose estimation approaches