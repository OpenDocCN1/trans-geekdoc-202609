Article

# A Low-Grade Road Extraction Method Using SDG-DenseNet Based on the Fusion of Optical and SAR Images at Decision Level

Jinglin Zhang 1, Yuxia Li 1,*, Yu Si 1, Bo Peng 1, Fanghong Xiao 1, Shiyu Luo 1 and Lei He 2

1 School of Automation Engineering, University of Electronic Science and Technology of China, Chengdu 611731, China; 2018060507021@std.uestc.edu.cn (J.Z.); 2019210605248@std.uestc.edu.cn (Y.S.); 2018060507023@std.uestc.edu.cn (B.P.); xiao_fanghong@std.uestc.edu.cn (F.X.); shiyuluo@uestc.edu.cn (S.L.)
2 School of Software Engineering, Chengdu University of Information Technology, Chengdu 610225, China; hele1978@cuit.edu.cn
* Correspondence: liyuxia@uestc.edu.cn

Abstract: Low-grade roads have complex features such as geometry, reflection spectrum, and spatial topology in remotely sensing optical images due to the different materials of those roads and also because they are easily obscured by vegetation or buildings, which leads to the low accuracy of low-grade road extraction from remote sensing images. To address this problem, this paper proposes a novel deep learning network referred to as SDG-DenseNet as well as a fusion method of optical and Synthetic Aperture Radar (SAR) data on decision level to extract low-grade roads. On one hand, in order to enlarge the receptive field and ensemble multi-scale features in commonly used deep learning networks, we develop SDG-DenseNet in terms of three modules: stem block, D-Dense block, and GIRM module, in which the Stem block applies two consecutive small-sized convolution kernels instead of the large-sized convolution kernel, the D-Dense block applies three consecutive dilated convolutions after the initial Dense block, and Global Information Recovery Module (GIRM) combines the ideas of dilated convolution and attention mechanism. On the other hand, considering the penetrating capacity and oblique observation of SAR, which can obtain information from those low-grade roads obscured by vegetation or buildings in optical images, we integrate the extracted road result from SAR images into that from optical images at decision level to enhance the extraction accuracy. The experimental result shows that the proposed SDG-DenseNet attains higher IoU and F1 scores than other network models applied to low-grade road extraction from optical images. Furthermore, it verifies that the decision-level fusion of road binary maps from SAR and optical images can further significantly improve the F1, COR, and COM scores.

Keywords: low-grade road extraction; remote sensing; image segmentation; SAR image; deep learning

Citation: Zhang, J.; Li, Y.; Si, Y.; Peng, B.; Xiao, F.; Luo, S.; He, L. A Low-Grade Road Extraction Method Using SDG-DenseNet Based on the Fusion of Optical and SAR Images at Decision Level. Remote Sens. 2022, 14, 2870. https://doi.org/10.3390/rs14122870

Academic Editor: Giuseppe Scarpa
Received: 5 May 2022
Accepted: 14 June 2022
Published: 15 June 2022

Publisher's Note: MDPI stays neutral with regard to jurisdictional claims in published maps and institutional affiliations.

Copyright: © 2022 by the authors. Licensee MDPI, Basel, Switzerland. This article is an open access article distributed under the terms and conditions of the Creative Commons Attribution (CC BY) license (https://creativecommons.org/licenses/by/4.0/).

# 1. Introduction

Research on extracting road information from remote sensing images has been carried out for many years. However, due to the different width and shape characteristics of different grades of roads, such as national roads, provincial roads, village roads, and mountain roads; roads with different materials have different color and texture characteristics, such as cement, asphalt, earth road, etc.; at the same time, the road area is blocked by buildings, trees, the central green belt of the road and many other factors, so the accurate extraction of road information is still the research frontier and poses a technical difficulty in the field of remote sensing information extraction.

Road extraction can be described as a pixel-level binary classification problem that distinguishes whether each pixel belongs to a road or not [1]. Recently, deep convolution neural networks (DCNNs) have been demonstrated to have significant improvements to typical computer vision tasks such as semantic segmentation [2]. Road semantic segmentation has