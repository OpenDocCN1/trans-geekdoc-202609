One reason for this is the coarser feature map resolutions applied throughout the different methods, i.e., 1/8 or 1/16 of the input image, which may result in poorly located as well as duplicate detections (see Section 5.2.1). However, it is to mention that some of these approaches are designed for object detection in aerial imagery that comprise larger object instances such as NWPU.

# Table 8.10: Average precision and inference time for EMT-MFD Faster R-CNN + SAR with VGG16 and ZynNet, respectively, compared to representative existing work on the DLR 3K dataset.

| Method | Base Network | AP (in %) | Time (in FPS) |
|---|---|---|---|
| Shallow YOLOv2 [Car17]¹ | Darknet-19 | 73.4 | 6.4 |
| Adapted YOLOv2 [Aca18]¹ | Darknet-19 | 94.5 | 11.5 |
| DYOLO [Aca18]¹ | Darknet-19 | 94.9 | 5.8 |
| AVPN Faster R-CNN [Den17]² | ZF | 69.2 | 12.4 |
| Multi-Scale CNN [Guo18]² | VGG16 | 93.7 | 4.4 |
| Modified Faster R-CNN [Din18]² | VGG16 | 93.6 | 10.8 |
| DFL-CNN [Yan18]² | ResNet50 | 85.1 | 6.6 |
| Adapted RetinaNet [Tay18]³ | ResNet50 | 95.0 | 14.8 |
| Faster R-CNN + OHEM [Shr16b]² | VGG16 | 95.2 | 3.5 |
| FPN [Lin17a]³ | ResNet50 | 95.4 | 13.4 |
| FPN - DCNv1 [Dai17]³ | ResNet50 | 95.3 | 12.2 |
| FPN - DCNv2 [Zhu19]³ | ResNet50 | 95.4 | 12.2 |
| Cascade R-CNN [Cai18]³ | ResNet50 | 95.7 | 10.5 |
| Libra R-CNN [Pan19]³ | ResNet50 | 95.6 | 12.7 |
| YOLOv3 [Red18]¹ | Darknet-53 | 96.1 | 14.2 |
| DSSD [Fu17]² | ResNet101 | 94.7 | 2.9 |
| RefineDet [Zha18a]² | VGG16 | 96.1 | 6.7 |
| EMT-MFD Faster R-CNN + SAR | VGG16 | 96.3 | 4.0 |
| EMT-MFD Faster R-CNN + SAR | ZynqNet | 96.1 | 7.3 |

¹ Using the Darknet framework (https://github.com/pjreddie/darknet)

² Using the Caffe framework

³ Using the MMDetection [Che19b] toolbox based on PyTorch (https://github.com/open-mmlab/mmdetection)