# 5.5. Real-Time Detection Is the Key to Application

Real-time SAR ship detection needs to start from many aspects. For example, we can design a lightweight detection network, compress and accelerate the model to improve the speed, and transplant the detection algorithm to high-performance AI chips at the edge (NVIDIA Jetson TX2). At present, most of the work in this field is focused on the first two aspects, and there is less research on the third aspect, which needs to be focused on in the future. Only by realizing this technology can we realize the real-time detection and recognition of ships on satellite or aircraft platforms.

# 5.6. Transformer Is the Future Trend

In the past two years, transformer shows great advantage in object detection compared with CNN, for example, DETR (detection transformer) [257] and Swin Transformer. DINO [258] can achieve 63.6% AP on the COCO test-dev, which surpasses CNN-based detector by a large margin. Nowadays, the hot topic of computer vision is the transformer. CRTransSar [182] is the first to use a transformer for SAR image ship detection. It shows a great advantage in accuracy (97% AP on SSDD). Although there are still some problems when a transformer is used for SAR ship detection, there is no doubt that the transformer will be the research trend in the future due to its great advantages.

# 5.7. Bridging the Gap between SAR Ship Detection and Computer Vision

Compared with the field of computer vision, the field of ship detection in SAR images is relatively small and not active enough. Therefore, it is necessary to bring this field to computer vision, and systematically learn from the rich achievements in computer vision. We should also learn about its openness, standardized evaluation, and easily accessed codes. This work can promote this field to develop rapidly. What we should do is as follows: firstly, the existing public datasets (SSDD, SAR-Ship-Dataset, AIR-SARShip, HRSID, LS-SSDD-v1.0, SRSDD-v1.0, and RSDD-SAR) need to be combined into a large dataset, which can be called LargeSARDataset here. The modes trained on it can avoid over-fitting. Secondly, determine the training samples and testing samples. Thirdly, determine the evaluation indicators. Fourthly, release the benchmark. Fifthly, bring it into the field of computer vision. As shown in Figure 15. Through this work, we can bridge the gap between SAR ship detection and computer vision.

![](bbox=[0.13, 0.7, 0.82, 0.85])

Figure 15. Bridging the gap between SAR ship detection and computer vision.

In addition to detection, classification and segmentation of SAR images also enter into the deep learning era [259–265]. Classification and segmentation algorithms borrowed from computer vision are extensively used in SAR images. We will review them in the future. In the process of detection, only ship and non-ship targets are considered, and the specific content of non-ship targets is not analyzed [266–268]. Some icebergs have great similarities in shape and size with ships, and the algorithms are difficult to distinguish them. So, we will study how to solve this problem in the future.