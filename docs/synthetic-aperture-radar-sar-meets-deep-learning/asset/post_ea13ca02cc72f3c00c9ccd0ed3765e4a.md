
## Synthetic Aperture Radar (SAR) Meets Deep Learning

Edited by
Tianwen Zhang, Tianjiao Zeng and Xiaoling Zhang
Printed Edition of the Special Issue Published in *Remote Sensing*

## Synthetic Aperture Radar (SAR) Meets Deep Learning

Editors

Tianwen Zhang
Tianjiao Zeng
Xiaoling Zhang

## Editors

Tianwen Zhang
University of Electronic Science
and Technology of China
China

Tianjiao Zeng
University of Hong Kong
Hong Kong

Xiaoling Zhang
University of Electronic Science
and Technology of China
China

## Editorial Office

MDPI
St. Alban-Anlage 66
4052 Basel, Switzerland

This is a reprint of articles from the Special Issue published online in the open access journal *Remote Sensing* (ISSN 2072-4292) (available at: https://www.mdpi.com/journal/remotesensing/special_issues/synthetic_aperture_radar_meets_deep_learning).

For citation purposes, cite each article independently as indicated on the article page online and as indicated below:

> LastName, A.A.; LastName, B.B.; LastName, C.C. Article Title. *Journal Name* Year, Volume Number, Page Range.

- ISBN 978-3-0365-6382-4 (Hbk)
- ISBN 978-3-0365-6383-1 (PDF)

© 2023 by the authors. Articles in this book are Open Access and distributed under the Creative Commons Attribution (CC BY) license, which allows users to download, copy and build upon published articles, as long as the author and publisher are properly credited, which ensures maximum dissemination and a wider impact of our publications.

The book as a whole is distributed by MDPI under the terms and conditions of the Creative Commons license CC BY-NC-ND.

## Contents

Preface to “Synthetic Aperture Radar (SAR) Meets Deep Learning” . . . . . . . . . . . . . vii

Tianwen Zhang, Tianjiao Zeng and Xiaoling Zhang
Synthetic Aperture Radar (SAR) Meets Deep Learning
Reprinted from: Remote Sens. 2023, 15, 303, doi:10.3390/rs15020303 . . . . . . . . . . . . . 1

Sandhi Wangiyana, Piotr Samczyński and Artur Gromek
Data Augmentation for Building Footprint Segmentation in SAR Images: An Empirical Study
Reprinted from: Remote Sens. 2022, 14, 2012, doi:10.3390/rs14092012 . . . . . . . . . . . . . 5

Jianwei Li, Congan Xu, Hang Su, Long Gao and Taoyang Wang
Deep Learning for SAR Ship Detection: Past, Present and Future
Reprinted from: Remote Sens. 2022, 14, 2712, doi:10.3390/rs14112712 . . . . . . . . . . . . . 27

Daning Tan, Yu Liu, Gang Li, Libo Yao, Shun Sun and You He
Serial GANs: A Feature-Preserving Heterogeneous Remote Sensing Image Transformation Model
Reprinted from: Remote Sens. 2021, 13, 3968, doi:10.3390/rs13193668 . . . . . . . . . . . . . 69

Gang Zhang, Zhi Li, Xuewei Li and Sitong Liu
Self-Supervised Despeckling Algorithm with an Enhanced U-Net for Synthetic Aperture Radar Images
Reprinted from: Remote Sens. 2021, 13, 4383, doi:10.3390/rs13214383 . . . . . . . . . . . . . 87

Jinyu Bao, Xiaoling Zhang, Tianwen Zhang, Jun Shi and Shunjun Wei
A Novel Guided Anchor Siamese Network for Arbitrary Target-of-Interest Tracking in Video-SAR
Reprinted from: Remote Sens. 2021, 13, 4504, doi:10.3390/rs13224504 . . . . . . . . . . . . . 109

Liming Pu, Xiaoling Zhang, Zenan Zhou, Liang Li, Liming Zhou, Jun Shi and Shunjun Wei
A Robust InSAR Phase Unwrapping Method via Phase Gradient Estimation Network
Reprinted from: Remote Sens. 2021, 13, 4564, doi:10.3390/rs13224564 . . . . . . . . . . . . . 135

Rezvan Habibollahi, Seyd Teymoor Seydi, Mahdi Hasanlou and Masoud Mahdianpari
TCD-Net: A Novel Deep Learning Framework for Fully Polarimetric Change Detection Using Transfer Learning
Reprinted from: Remote Sens. 2022, 14, 438, doi:10.3390/rs14030438 . . . . . . . . . . . . . 159

Yibo Fan, Feng Wang and Haipeng Wang
A Transformer-Based Coarse-to-Fine Wide-Swath SAR Image Registration Method under Weak Texture Conditions
Reprinted from: Remote Sens. 2022, 14, 1175, doi:10.3390/rs14051175 . . . . . . . . . . . . . 185

Runfan Xia, Jie Chen, Zhixiang Huang, Huiyao Wan, Bocai Wu, Long Sun, et al.
CRTransSar: A Visual Transformer Based on Contextual Joint Representation Learning for SAR Ship Detection
Reprinted from: Remote Sens. 2022, 14, 1488, doi:10.3390/rs14061488 . . . . . . . . . . . . . 211

Yun Feng, Jie Chen, Zhixiang Huang, Huiyao Wan, Runfan Xia, Bocai Wu, et al.
A Lightweight Position-Enhanced Anchor-Free Algorithm for SAR Ship Detection
Reprinted from: Remote Sens. 2022, 14, 1908, doi:10.3390/rs14081908 . . . . . . . . . . . . . 239

## Preface to “Synthetic Aperture Radar (SAR) Meets Deep Learning”

A synthetic aperture radar (SAR) is an important active microwave imaging sensor, whose all-day and all-weather working capacity give it an important place in the remote sensing community. Since the United States launched the first SAR satellite, SAR has received much attention in the remote sensing community, e.g., in geological exploration, topographic mapping, disaster forecast, and traffic monitoring. It is valuable and meaningful, therefore, to study SAR-based remote sensing applications.

In recent years, deep learning represented by convolutional neural networks has promoted significant progress in the computer vision community, e.g., in face recognition, the driverless field and Internet of things (IoT). Deep learning can enable computational models with multiple processing layers to learn data representations with multiple-level abstractions. This can greatly improve the performance of various applications. Today, scholars are realizing the potential value of deep learning in remote sensing. Many remote sensing application techniques incorporate deep learning, e.g., in target and oil spill detection, traffic surveillance, topographic mapping, AI-based SAR imaging algorithm updating, coastline surveillance, and marine fisheries management.

Interestingly, when SAR meets deep learning, how to use this advanced technology correctly needs to be considered carefully, and how to achieve the best performance of this “black-box” model also needs careful consideration. Notably, deep learning uncritically abandons traditional hand-crafted features and relies excessively on the abstract features of deep networks. Is this reasonable? Can the abstract features of deep networks fully represent a real SAR? Should the traditional hand-crafted features provided with mature theories and elaborate techniques be abandoned completely? These questions are worth pondering when one applies various deep learning techniques to the SAR remote sensing community. In general, deep learning is always proposed for natural optical images whose imaging mechanisms are greatly different from those of SARs.

When SAR meets deep learning, should an SAR adapt itself to deep learning, or should deep learning adapt itself to an SAR? The relationship between the two needs further exploration and research. Furthermore, is deep learning really suitable for SARs? The number of SAR samples is far smaller than that of natural optical images. In this case, could we ensure that deep networks are able to thoroughly learn SAR mechanisms?

This Special Issue provides a platform for researchers to handle the above significant challenges and present their innovative and cutting-edge research results when applying deep learning to SARs in various manuscript types, e.g., articles, letters, reviews and technical reports.

Tianwen Zhang, Tianjiao Zeng, and Xiaoling Zhang
Editors

(TDIoU loss), an attention-weighted feature pyramid network (AW-FPN), and a Rotated-SARShip dataset (RSSD) for arbitrary-oriented SAR ship detection. Their method showed superior performance on both SAR and optical image datasets, significantly outperforming the SOTA methods. Xiao et al. [17] proposed a simple, yet effective, self-supervised representation learning (Lite-SRL) algorithm for the scene classification task. Note that they successfully evaluate the on-board operational capability of Lite-SRL by transplanting Lite-SRL to the low-power computing platform NVIDIA Jetson TX2. Kačan et al. [18] explored object classification on a raw and a reconstructed Ground-based SAR (GBSAR) data. They revealed how processing raw data provides overall better classification accuracy than processing reconstructed data, and revealed the value of this method in industrial GBSAR applications where processing speed is critical. Bao et al. [19] proposed a guided anchor Siamese network (GASN) for arbitrary targets of interest (TOI) tracking in Video-SAR. GASN used a matching function for returning the most similar area, followed by a guided anchor subnetwork to suppress false alarms. GASN realized the TOI tracking with high diversity and arbitrariness, outperforming SOTA methods.

On the topic of SAR image intelligent processing, Tan et al. [20] proposed a feature-preserving heterogeneous remote sensing image transformation model. Through decoupling network design, the method enabled enhancing the detailed information of the generated optical images and reducing its spectral distortion. The results in SEN-2 satellite images revealed that the proposed model has obvious advantages in feature reconstruction and the economical volume of the parameters. Zhang et al. [21] proposed a self-supervised despeckling algorithm with an enhanced U-Net called SSEUNet. Unlike previous self-supervised despeckling works, the noisy-noisy image pairs in SSEUNet were generated from real-world SAR images through a novel generation training pairs module, making it possible to train deep convolutional neural networks using real-world SAR images. Finally, experiments on simulated and real-world SAR images show that SSEUNet notably exceeds SOTA despeckling methods. Habibollahi et al. [22] proposed a DL-based change detection algorithm for bi-temporal polarimetric SAR (PolSAR) imagery called TCD-Net. In particular, this method applied three steps as follows: (1) pre-processing, (2) parallel pseudo-label training sample generation based on a pre-trained model and the fuzzy C-means (FCM) clustering algorithm, and (3) classification. TCD-Net could learn more strong and abstract representations for the spatial information of a certain pixel, and was superior to other well-known methods. Fan et al. [23] proposed a high-precision, rapid, large-size SAR image dense-matching method. The method mainly included four steps: down-sampling image pre-registration, sub-image acquisition, dense matching, and the transformation solution. The experimental results demonstrated that the proposed method is efficient and accurate, which provides a new idea for SAR image registration. Zhang et al. [24] proposed A low-grade road extraction network Based on the fusion of optical and SAR images at the decision level called SDG-DenseNet. Furthermore, they verified that the decision-level fusion of road binary maps from SAR and optical images can significantly improve the accuracy of low-grade road extraction from remote sensing images.

On the topic of data analytics in the SAR remote sensing community, Wangiyana et al. [25] explored the impact of several data augmentation (DA) methods on the performance of building detection on a limited dataset of SAR images. Their results showed that geometric transformations are more effective than pixel transformations and DA methods should be used in moderation to prevent unwanted transformations outside the possible object variations. The study could provide potential guidelines for future research in selecting DA methods for segmentation tasks in radar imagery.

On the topic of interferometric SAR technology, Pu et al. [26] proposed a robust least squares phase unwrapping method called PGENet that works via a phase gradient estimation network based on the encoder-decoder architecture for InSAR. Experiments on simulated and real InSAR data demonstrated that PGENet outperformed the other five well-established phase unwrapping methods and was robust to noise.
