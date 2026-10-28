
ABOs close to 0.5, in particular for a GSD of 26 cm. This confirms that larger distances to the IoU threshold used to generate positive and negative training samples lead to better detections, since the corresponding region proposals may be classified with higher confidence as vehicle or background.

Table 5.7: AP (in %) for different anchor box scales and consequently different anchor box areas with respect to the GSD.

| Anchor Box Area (in pixels) | GSD (in cm) |  |  |
|---|---|---|---|
|  | 13 | 19.5 | 26 |
| 256² | 88.1 | 73.2 | 52.9 |
| 112² | 92.8 | 85.4 | 71.4 |
| 56² | 93.8 | 88.3 | 81.1 |
| 42² | 94.1 | 89.0 | 82.9 |
| 28² | 94.3 | 89.5 | 83.1 |
| 14² | 94.2 | 89.4 | 83.2 |

![](img/99de1214c29cbc525a14b293385af5cf_106_0.png)

Figure 5.19: Relation between average precision and average best overlap for different anchor box scales and various GSDs. For all GSDs, candidate regions with higher ABO result in better AP.

## 5.2.4 Arising Challenges

Despite the considerably improved detection accuracy, in particular for high GSDs, the performed adaptations lead to several shortcomings that have to be addressed for real-world applications. These shortcomings are primarily the weaker semantic and spatial context information of the employed features and the inference time, which are discussed in the following.

### Semantic and Spatial Context

In general, each convolutional layer within a CNN learns filters of increasing complexity, since features from the previous layers are aggregated and recombined. The first layers learn basic feature representations, e.g., edges and corners, whereas the middle layers learn to respond to object parts and the last layers learn higher representations to recognize full objects with different shapes and positions or even entire scenes [Zho15]. Furthermore, the region of the input space that affects a particular unit of the network, also referred to as *receptive field*, and consequently the spatial context information generally increases with deeper layers [Luo16]. Hence, removing deep layers to increase the feature map resolution required for accurately locating tiny objects leads to less semantic and spatial context information.

![](img/99de1214c29cbc525a14b293385af5cf_107_0.png)

Figure 5.20: Error analysis of false positive detections for various GSDs.

Analyzing the erroneous detections indicates that the less semantic and contextual information cause a high number of false positive detections. Figure 5.20 shows the division of the false positive detections into localization and classification errors using the output of conv3_3 as feature map. For all GSDs, the false positive detections are mainly due to classification errors as background objects are classified as vehicles.

To highlight the effect of the comparatively poor semantic and contextual information on the detection accuracy, false positive detections for a GSD of 13 cm are qualitatively visualized in Figure 3.4. These false positive detections are mainly due to objects with vehicle-like shapes, e.g., rectangular structures on buildings such as solar cells or windows. Note that several of these false positive detections comprise small components that activate filters responding to particular vehicle parts such as windshields or front lights. Figure 5.21 exemplarily depicts activations of four filters that respond to vehicle parts but also to similar structures.

![](img/99de1214c29cbc525a14b293385af5cf_108_0.png)

Figure 5.21: Activations of four filters from conv3_3 that respond to particular vehicle parts but also to similar structures.

However, looking at the surrounding areas of the false positive detections exhibits that most false positive detections are located on regions that are unlikely to contain a vehicle such as buildings or vegetation. Though the training data comprises no such positive samples for classification, the learned representation is not sufficient to distinguish between relevant and non-relevant surrounding areas. Hence, increasing the spatial or semantic context information of the employed features to better learn the representations of relevant surrounding areas like road surfaces or parking lots can reduce the number of false positive detections. Approaches to enrich the spatial and semantic content of employed feature maps aiming at improving the detection accuracy are presented in Chapter 6.

### Inference Time

Besides the detection accuracy, the inference time is another essential factor for most applications, e.g., search and rescue tasks. In Table 5.8, the impact of the performed adaptations, in particular the increased feature map resolution, which exhibits the largest gain in detection accuracy, is regarded with respect to the inference time. Following the protocol for time measurements introduced in Section 4.2, the inference time is reported for the Faster R-CNN detector as well as for each detector component in milliseconds (ms) averaged over the complete test set including 240 image tiles of size 936 × 936 pixels. For both the server and the desktop setup, the overall inference time gets worse with increasing feature map resolutions. While the inference time for the classification stage remains unchanged, as for all models the same number of region proposals are processed, the inference time considerably increases for the RPN because of the higher feature map resolution. As described in Section 5.1.1, the RPN comprised of a small network is applied on each feature map location, whereby anchor boxes centered at the respective feature map location are utilized for bounding box regression. Using conv3_3 instead of conv4_3 or conv5_3 results in 4 and 16 times more feature map locations that have to be processed and consequently, the number of region proposals to compute the bounding box coordinates for and that have to be sorted increases by factor 4 and 16, respectively. Hence, the computational effort clearly increases. However, the increase in inference time is not linear, as NMS is applied on the 10,000 region proposals exhibiting the highest confidence score for each model.

Comparing the different device setups indicates that clearly less inference time is spent on more powerful devices, i.e., server setup. Especially the inference times for the base network used for feature extraction and the classification stage are considerably worse. Though multiple convolutional layers are discarded in case of conv3_3, the inference time for conv5_3 only slightly increases for the server setup, whereas for the desktop setup, the inference time for feature extraction notably rises. Note that in case of conv3_3, the inference time for feature extraction includes the time spent for the auxiliary convolutional layer to account for the required number of inputs channels of the fully connected layers. In order to speed up the detector for different devices, optimization of the feature extraction as well as of the RPN and classification stage are required. Strategies to address these issues are introduced in Chapter 7.

Table 5.8: Comparison of the inference time of Faster R-CNN using different feature maps. The overall inference time gets worse with higher feature map resolutions due to the RPN.

| Feature Map | Component | Time (in ms) |  |
|---|---|---|---|
| | Server | Desktop | |
| *conv3_3* | Feature Extractor | 58.9 | 177.4 |
| | RPN | 139.8 | 212.8 |
| | Classification Stage | 87.5 | 273.3 |
| | Total | 286.2 | 663.5 |
| *conv4_3* | Feature Extractor | 59.1 | 230.2 |
| | RPN | 40.1 | 58.7 |
| | Classification Stage | 86.9 | 275.2 |
| | Total | 186.1 | 564.1 |
| *conv5_3* | Feature Extractor | 62.0 | 255.6 |
| | RPN | 20.3 | 23.6 |
| | Classification Stage | 86.8 | 273.7 |
| | Total | 169.1 | 552.9 |

## 6.1 Spatial Context

Exploiting shallower layers as feature map for Faster R-CNN is crucial for vehicle detection in aerial imagery, as the resolution of deeper layers is often not sufficient to accurately localize tiny objects. To overcome the lack of semantic and contextual content resulting in false alarms, an extension to the original Faster R-CNN architecture called Multi Feature Deconvolutional (MFD) Faster R-CNN is proposed in the context of this thesis. The schematic structure of the MFD Faster R-CNN is illustrated in Figure 6.1. Inspired by semantic labeling networks aiming at the prediction of fine and coarse structures, features from various layers (indicated by different blue tones) offering different semantic and contextual information are combined. For this purpose, a context enhancement module (CEM) highlighted in green is introduced to allow the combination of these features, while the feature map resolution is kept sufficiently high to localize tiny objects. In the following, the CEM and the implementation details are presented followed by experiments and discussion of the results to highlight the enhanced detection accuracy.

![](img/99de1214c29cbc525a14b293385af5cf_113_0.png)

Figure 6.1: Schematic structure of the proposed Multi Feature Deconvolutional Faster R-CNN, which extends the original Faster R-CNN by a CEM to combine features of shallow and deep layers, while the resolution of the feature map is kept sufficient to localize tiny objects.
