Table 7.15: Comparison of the overall inference time and the time spent for the RPN in case of adapted prediction layers for the RPN.

| Base Network | Component | AP (in %) | Time (in ms) Server | Time (in ms) Desktop |
|---|---|---|---|---|
| ZynqNet_α=1.00 | RPN | 94.1 | 117.8 | 109.2 |
|  | Total |  | 162.1 | 216.4 |
| ZynqNet_α=0.75 | RPN | 94.0 | 116.5 | 106.1 |
|  | Total |  | 149.7 | 186.9 |
| ZynqNet_α=0.50 | RPN | 93.5 | 114.7 | 103.5 |
|  | Total |  | 140.9 | 160.7 |

The performed adaptations to the base network and prediction layers yield significantly decreased inference times, whereby in particular the time spent for the feature extraction and for the classification stage are clearly reduced on both setups. The bottleneck in terms of inference time is the RPN. While the inference time of its prediction layers is relatively small, the most time-consuming parts of the RPN are the mapping of the predictions to the image coordinates and the subsequent filtering of the candidate regions by means of their confidence score via NMS. In the next section, a procedure is proposed aiming at reducing the inference time of the RPN, amongst others.

# 7.2 Search Area Reduction

Restricting the search area to areas of interest, e.g., roads for vehicle detection, is an often applied preprocessing step in conventional object detection pipelines. In particular for vehicle detection in aerial imagery, both the computational costs for extracting feature descriptors as well as the subsequent classification and the number of false positive detections are reduced. While benchmark detection datasets typically comprise objects that are almost image filling, only a small fraction of aerial imagery datasets is occupied by objects, i.e., vehicles, due to their small dimensions in the range of only a few pixels. For instance, images of PASCAL VOC 2007 are occupied by more than