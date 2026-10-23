Article

# A Lightweight Self-Supervised Representation Learning Algorithm for Scene Classification in Spaceborne SAR and Optical Images

Xiao Xiao, Changjian Li and Yinjie Lei *

College of Electronics and Information Engineering, Sichuan University, Chengdu 610064, China; xiaoxiao@stu.scu.edu.cn (X.X.); li_changjian@stu.scu.edu.cn (C.L.)
* Correspondence: yinjie@scu.edu.cn

**Abstract:** Despite the increasing amount of spaceborne synthetic aperture radar (SAR) images and optical images, only a few annotated data can be used directly for scene classification tasks based on convolution neural networks (CNNs). For this situation, self-supervised learning methods can improve scene classification accuracy through learning representations from extensive unlabeled data. However, existing self-supervised scene classification algorithms are hard to deploy on satellites, due to the high computation consumption. To address this challenge, we propose a simple, yet effective, self-supervised representation learning (Lite-SRL) algorithm for the scene classification task. First, we design a lightweight contrastive learning structure for Lite-SRL, we apply a stochastic augmentation strategy to obtain augmented views from unlabeled spaceborne images, and Lite-SRL maximizes the similarity of augmented views to learn valuable representations. Then, we adopt the stop-gradient operation to make Lite-SRL’s training process not rely on large queues or negative samples, which can reduce the computation consumption. Furthermore, in order to deploy Lite-SRL on low-power on-board computing platforms, we propose a distributed hybrid parallelism (DHP) framework and a computation workload balancing (CWB) module for Lite-SRL. Experiments on representative datasets including OpenSARUrban, WHU-SAR, NWPU-Resisc45, and AID dataset demonstrate that Lite-SRL can improve the scene classification accuracy under limited annotated data, and it is generalizable to both SAR and optical images. Meanwhile, compared with six state-of-the-art self-supervised algorithms, Lite-SRL has clear advantages in overall accuracy, number of parameters, memory consumption, and training latency. Eventually, to evaluate the proposed work’s on-board operational capability, we transplant Lite-SRL to the low-power computing platform NVIDIA Jetson TX2.

**Keywords:** synthetic aperture radar; optical images; scene classification; on-board; lightweight self-supervised algorithm

**Citation:** Xiao, X.; Li, C.; Lei, Y. A Lightweight Self-Supervised Representation Learning Algorithm for Scene Classification in Spaceborne SAR and Optical Images. *Remote Sens.* 2022, 14, 2956. https://doi.org/10.3390/rs14132956

**Academic Editors:** Tianwen Zhang, Tianjiao Zeng and Xiaoling Zhang

Received: 24 May 2022
Accepted: 15 June 2022
Published: 21 June 2022

**Publisher's Note:** MDPI stays neutral with regard to jurisdictional claims in published maps and institutional affiliations.

![](bbox=[0.05, 0.85, 0.18, 0.9])

**Copyright:** © 2022 by the authors. Licensee MDPI, Basel, Switzerland. This article is an open access article distributed under the terms and conditions of the Creative Commons Attribution (CC BY) license (https://creativecommons.org/licenses/by/4.0/).

# 1. Introduction

The remote sensing scene classification (RSSC) task aims to classify scene regions into different semantic categories [1–5], which plays an essential role in various Earth observation applications, i.e., land resource exploration, forest inventory, urban-area monitoring [6–8]. In recent years, Landsat, Sentinel, and other missions have provided an increasing number of spaceborne images for scene classification task, including synthetic aperture radar (SAR) images and optical images. With more available data, scene classification methods based on convolution neural networks (CNN) have undergone rapid growth [7,9].

However, the amount of annotated scene data available for supervised CNN training remains limited. Taking SAR data as an example, SAR images are affected by speckle noise due to the imaging mechanism, resulting in poor image quality [10,11]. In addition, the random fluctuation of pixels makes it difficult to distinguish between scene categories [12]. Therefore, the annotation of SAR images requires experienced experts and