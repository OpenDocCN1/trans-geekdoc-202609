
Figure 7. *Snap codes of the lenses*

![](img/4a898a1f1442f24bfffba36e7ac62ad8_107_0.png)

## REFERENCES

Abdel, H. (2019). Internet of Things (IOT): Research Challenges and Future Applications. *International Journal of Advanced Computer Science and Applications.*

Anand, P., Gupta, R., Tiwari, N. K., & Gupta, S. (2022). Glass Virtual Try-On. *International Journal for Research in Applied Science and Engineering Technology, 10*(5), 718–722. Advance online publication. doi:10.22214/ijraset.2022.42317

Antim, A., & Luigi, L. (2017). An extensive review on Interfaces between IoT and Cloud Computing. *International Journal of Engineering Research & Technology.*

Boardman R, Zhu A. (2020). Augmented Reality and Virtual Reality – New Drivers For Fashion Retail? *Technology-Driven Sustainability: Innovation in the Fashion Supply Chain.* doi:10.1007/978-3-030-15483-7_9

Borges, A., & Carlos, H. (2019). A Virtual Makeup Augmented Reality System. *21st Symposium on Virtual and Augmented Reality (SVR).* 10.1109/SVR.2019.00022

Dov & Kaufman. (2018). Augmenting Reality with Intelligent Interfaces. *IntechOpen.* doi:10.5772/intechopen.75751

Eugeni, R. (2022). Augmented Reality Filters and the Faces as Brands: Personal Identities and Marketing Strategies in the Age of Algorithmic Images. *24th HCI International Conference.* 10.1007/978-3-031-05064-0_17

## Chapter 5

### Insulator Fault Detection From UAV Images Using YOLOv5

S. Venkata Suryanarayana  
CVR College of Engineering, India

Katakam Koushik  
CVR College of Engineering, India

Prabu Sevugan  
Pondicherry University, India

### ABSTRACT

Identification of insulator defects is one of the most important goals of an intelligent examination of high-voltage transmission lines. Because they provide mechanical support for electric transmission lines as well as electrical insulation, insulators are essential to the secure and reliable operation of power networks. A fresh dataset is first built by collecting aerial pictures in various scenes that have one or more defects. A feature pyramid network and an enhanced loss function are used by the CSPD-YOLO model to increase the precision of insulator failure detection. The insulator defective data set, which has two classes (insulator, defect), is used by the suggested technique to train and test the model using the YOLOv5 object detection algorithm. The authors evaluate how well the YOLOv3, YOLOv5, and related families perform when trained on the insulator defective dataset. Practitioners can use this information to choose the appropriate technique based on the insulator defective dataset.

### INTRODUCTION

When inspecting high-voltage transmission lines, a number of sensors are employed, and one crucial technique is the status detection of electrical equipment. Vision sensor-based techniques have advanced significantly over the past few decades, and various topics, including insulator identification, power line detection, and power tower detection, have been studied. The insulator string, which may offer both mechanical support and electrical insulation, is one of the high-voltage transmission line’s most crucial pieces of equipment, according to early research. However, insulator flaws typically manifest themselves after some amount of running time as a result of factors including lightning strikes, material aging, and overloading. Therefore, a crucial job for high-voltage transmission line inspection is the accurate detection of insulator failures. In a standard manual inspection, workers must traverse paths close to high-voltage transmission lines to examine the status of each insulator using a variety of tools, including cameras, ultraviolet imagers, infrared imagers, and audition sensors. However, because high-voltage transmission lines are typically erected in complicated environments with woods and lakes, the traditional manual method is ineffective and impractical in real-world applications. The study of aerial photographs taken by unmanned aerial vehicles (UAVs) has recently become more popular for insulator status inspection due to advancements in UAV handling and image processing techniques.

Multiple features, such as color, form, edge, gradient, texture, key-points, and their fusions, have been investigated in the man-made feature-based approaches. Some mathematical models, such as the snake model, Hough transform, Active Contour Model, Fuzzy c-means, and Receptive field model, have also been used in the interim. AdaBoost, Sparse representation-based classifier, SVM, Cascade classifier, and KNN are used in machine learning-based approaches to identify insulator placements and identify insulator problems. The insulators in aerial photographs, however, are typically overlapped since the shooting angle and distance are constantly changing during UAV inspection, making it difficult to collect the spatial information of each insulator.

According to Liu et al. (2021), high-voltage transmission is essential because of the rising demand for electricity, particularly in relation to intelligent power grids. However, a defect will inevitably happen because the insulator spends a considerable amount of time outside. Unmanned aerial vehicle (UAV) patrols have gradually replaced typical manual patrol, which wastes resources and is ineffective. As a result, employees no longer need to use telescopes to find insulator defects along transmission lines. The automatic diagnosis of insulator failures has, however, been extremely difficult because of the complexity and diversity of application settings.

The accuracy of conventional image processing algorithms is lowered because the correlation properties of insulators in aerial photos are unknown. These techniques have various advantages over more conventional image processing techniques. With the widespread use of CNN suggested by Xiao and Sun (2021), deep learning techniques are able to surpass the constraints of conventional image processing methods, displaying outstanding performance and significantly enhancing object detection accuracy. With the advancement of hardware technology and deep learning theory, object detection has made significant strides over the last five years. Numerous exemplary deep convolutional networks, including RCNN, Fast-RCNN, Faster-RCNN, YOLOv1, YOLOv2, YOLOv3, and various variants, are proposed and confirmed on open datasets. These techniques use high-dimensional semantic attributes to represent objects.

In general, the majority of machine learning- and feature-based algorithms created by humans are extremely sensitive to complicated background interference. Additionally, the filming distance and angle typically reduce their performances. The majority of these techniques take a long time to complete and are not suitable for real-time applications. Since there aren’t any insulator aerial picture datasets accessible from public sites, current deep learning techniques haven’t been greatly improved. Most notably, none of the currently used machine learning, deep learning, or feature-based algorithms offer a systematic analysis that addresses the issue of insulator multi-fault detection. Therefore, it makes sense to provide a strategy that can address the issues with the current approaches.

To solve the widespread issue of the poor real-time performance of two-stage detection algorithms, Redmon et al. (2016) introduced the first one-stage network, YOLOv1. Since the entire detection pipeline is a single network, it uses object detection as a regression issue, allowing for a direct end-to-end improvement of detection performance. YOLOv1 is prone to missed detections in situations with object overlaps and occlusions, however, and is inefficient at recognizing small objects. As a result, in 2017, Redmon and Farhadi proposed YOLOv2, an improved version of YOLOv1 that uses DarkNet-19 as the foundational network and adds enhancements like batch normalized pre-processing, a multiscale training mechanism, and a binary cross-entropy loss function, leading to a noticeably higher level of recall and precision. In 2018, Redmon and Farhadi (2018) introduced the YOLOv3 method to increase the network’s sensitivity to small object detection. It expands the number of network layers, implements the cross-layer summing function in ResNet, and employs Darknet-53 as the backbone network. In real-world applications, YOLOv3 is quick, and its rate of background false detection is low.

### RELATED WORK

Zhao et al. (2019) presented the setting of anchor in traditional Faster R-CNN models only satisfy the requirements for general object detection. After fine-tuning a Faster R-CNN, some cases of subpar insulator identification produce power transmission and transformation inspection images. There are two horizontal insulators with colours that resemble the background. One insulator can only be detected in small portions, and the output box’s dimensions are inadequate for the insulator. Infrared images were taken on-site, which is what actual application require. The selection of the photographs took into account a variety of settings. The country’s 110–500 kV indoor high-voltage laboratories of various grades, four substations, one converter station, and about 33 transmission lines were selected. In terms of materials, glass, porcelain, and composite insulators were all taken into consideration. The Faster R-CNN in the VGG-16 Net had an average precision (AP) value of 0.640. We concentrated on how to further increase the detection accuracy based on this. It can successfully accomplish the distinct detection of the insulators in the image, laying the groundwork for further insulator defect diagnostics and status detection.

Rahman et al. (2021) developed the electric supply businesses concentrate mostly on inspecting damaged and faulty insulators to guarantee consumers receive safe and dependable power transmission. In both classes, YOLOv4 has an average precision (AP) of 82.9%, with pin insulators having an AP of 78.2% and suspension disc insulators having an AP of 87.7%. YOLOv4 Tiny has a lower AP than the regular YOLOv4 model since it is a lightweight model with a fast rate of inference. The complicated dataset is made up of pictures of several complex electric poles that are located outside a 132 kV grid substation that was captured with a cell phone camera. To avoid overfitting and noisy estimations, cross iteration batch normalization (CmBN) is utilized.

Liao et al. (2015) developed that the identification of regional feature points or regional patches is referred to as “feature detection.” We want to find as many feature points of the insulator as we can in order to simplify the subsequent processing (to increase recall, we allow noise to exist but restrict the insulator point from being missed). There are numerous ways to find local feature points, including Lowe’s difference-of-Gaussians detector and the Harris affine area detector. By employing a z-score normalization, our improved Harris corner selection technique only looks for corners that are close to enhanced edges. The exact same quantity of training data is used by all methods.
