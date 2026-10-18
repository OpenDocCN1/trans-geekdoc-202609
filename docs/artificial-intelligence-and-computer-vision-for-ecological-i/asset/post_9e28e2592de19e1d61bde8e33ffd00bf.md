
## Evaluation Parameters

Assessing our YOLOv8 model's performance in basil crop detection is integral to comprehending its effectiveness and reliability in precision agriculture. We utilize a comprehensive set of evaluation parameters that provide quantitative and qualitative insights into the model's capabilities.

Mean Average Precision (mAP) is a fundamental metric in object detection tasks, representing the model's ability to locate objects with different degrees of precision accurately. We compute mAP at two primary thresholds: at an intersection over union (IoU) of 0.50 (mAP50) and across a broader range from 0.50 to 0.95 (mAP50-95). mAP50 assesses the model's accuracy in detecting basil crops with a moderate level of precision, while mAP50-95 extends this assessment across a wider spectrum of IoU values, offering a more comprehensive view of the model's performance.

Precision evaluates the model's ability to precisely identify basil crops by measuring the proportion of true positive predictions, while recall assesses its capability to locate all actual basil crops in the images among the total actual positives. The F1 score balances precision and recall, offering a single metric capturing the model's performance in both aspects. Training and validation loss metrics, including box loss and classification loss, reflect disparities between model predictions and actual annotations, with lower values indicating closer alignment and improved effectiveness in basil crop detection. These evaluation parameters collectively offer a detailed understanding of the YOLOv8 model's accuracy and completeness in basil crop detection, showcasing its proficiency across diverse conditions and growth stages in precision agriculture.

## Training the YOLOv8 Model

Following the preprocessing of images and annotations, we embarked on the training of our YOLOv8 model. The Ultralytics package in Python served as our primary tool for model training. To facilitate this process, we compiled a 'Basil.yaml', a configuration file that defines crucial aspects of the training pipeline. This file specified the locations of the train and val images and annotations folders, the number of classes, and the class names, enabling our model to recognize basil crops precisely.

Our training dataset comprised 171 images, and the validation dataset included 38 images. After comprehensive experimentation, the optimal batch size was determined to be 19. This configuration was crucial for achieving an optimal balance between computational efficiency and training effectiveness. The model was trained with these configurations for 100 epochs, encompassing numerous iterations where the model learned to detect basil crops within the images. The model refined its predictive capabilities during each epoch, gradually converging towards accurate detections. This process encompassed both the training dataset, used to teach the model, and the validation dataset, employed to assess its performance.

## Evaluating the YOLOv8 Model

Once the model was successfully trained, we subjected it to rigorous evaluation using the validation dataset. The evaluation process involved running the model on the validation dataset and assessing its performance against the ground truth annotations (Li et al., 2020). The results were meticulously calculated and presented, offering insights into the model's precision, recall, F1 score, and other metrics that gauge its proficiency in basil crop detection. The concise Table 2 located below summarizes the major validation metrics, highlighting the model's precision, recall, F1 Score, mAP50, and mAP50-95 results. These metrics collectively attest to the YOLOv8 model's exceptional performance in basil crop detection, underpinning the core findings of our research.

**Table 2. Validation results on evaluation metrics.**

| Metric | Precision | Recall | F1 Score | mAP50 | mAP50-95 |
| Result | 0.960 | 0.987 | 0.969 | 0.983 | 0.895 |

Table 3 succinctly summarizes the training and validation losses, which are vital indicators of our YOLOv8 model's performance. These results provide insights into the model's efficiency in making predictions that closely align with the ground truth annotations.

**Table 3. Validation results on bounding boxes.**

| Metric | Train | Validation |
| Box Loss | 0.428 | 0.435 |
| Classification Loss | 0.377 | 0.435 |
| DFL Loss | 0.891 | 0.778 |

In our study of basil crop detection with YOLOv8, we meticulously track box losses, classification losses, and deformable losses during training and validation. These loss metrics quantify various aspects of the model's performance: box losses assess its ability to localize basil crops accurately, classification losses evaluate its capacity to distinguish basil crops from background elements, and deformable losses add spatial adaptability for diverse basil crop orientations. Monitoring these losses provides nuanced insights into the model's precision and resilience, highlighting its suitability for precision agriculture. They are fundamental pillars in optimizing the YOLOv8 model for basil crop detection, refinement, and enhancing practical viability in real-world scenarios.

The evaluation of our YOLOv8 model in basil crop detection includes a visual summary of true and predicted images with corresponding bounding box annotations (Uddin et al., 2023). The visual representation enhances the empirical evidence of our findings and contributes to the transparency and interpretability of the research. Figure 5 shows loss evaluation over epochs, and Fig. 6 shows evaluation metrics over epochs. Figure 7 shows True and Predicted images that prove the model's performance. This addition ensures a thorough understanding of its practical implications in precision agriculture, making the research accessible and valuable to the scientific community and agricultural practitioners.

![](img/ab77471ec8cd54d29506255d715b867e_83_0.png)

**Fig. 5.** Losses evaluation over epochs.

![](img/ab77471ec8cd54d29506255d715b867e_84_0.png)

**Fig. 6.** Evaluation metrics over epochs.

![](img/ab77471ec8cd54d29506255d715b867e_85_0.png)

**Fig. 7.** True and predicted images.

## Scope and Limitations of the Proposed Model

Our research aims to advance precision agriculture, focusing on basil crop detection using the YOLOv8 deep learning model. It includes developing and evaluating an accurate model adaptable to diverse growth stages and environmental conditions. We emphasize the model's configuration, training methodology, and dataset curation, highlighting its transformative potential in agriculture. Future enhancements could extend to other crops and applications like real-time monitoring and decision support systems. Acknowledging limitations, our dataset size is relatively small, and model generalization may not cover all variations. Real-world conditions like unpredictable environments may affect model performance (Gupta, 2016). GPU resources are needed for training, potentially limiting practicality, and broader societal implications should be extensively explored.

## Conclusion

This research combines deep learning technology, advanced agricultural practices, and machine vision systems to revolutionize precision agriculture, focusing on basil crop monitoring. The meticulously designed methodology, relying on curated datasets, rigorous model training, and validation, yielded promising results with the YOLOv8 model. The model demonstrated its adaptability and efficiency in basil crop detection by achieving impressive precision, recall, F1 score, and mean average precision metrics. Beyond empirical findings, the research highlights broader implications for enhancing crop management and sustainability practices. It serves as a foundation for future research and innovation in precision agriculture, emphasizing the potential of technology to optimize farming practices. Opportunities for future enhancements in deep learning capabilities and agricultural needs are recognized, signaling continued progress in this field.

## References

Abbasi, R., Martinez, P. and Ahmad, R. 2023. Crop diagnostic system: A robust disease detection and management system for leafy green crops grown in an aquaponics facility. Artificial Intelligence in Agriculture, 10: 1–12, doi: 10.1016/J.AIIA.2023.09.001.

Anand, R., Mishra, R.K. and Khan, R. 2022. Plant diseases detection using artificial intelligence. Application of Machine Learning in Agriculture, pp. 173–190, doi: 10.1016/B978-0-323-90550-3.00007-2.

Badgujar, C.M., Poulose, A. and Gan, H. 2024. Agricultural Object Detection with You Only Look Once (YOLO) Algorithm: A Bibliometric and Systematic Literature Review, Accessed: May 01, 2024. [Online]. Available: http://arxiv.org/abs/2401.10379.

Bouguettaya, A., Zarzour, H., Kechida, A. Amine and Taberkit, M. 2022. A survey on deep learning-based identification of plant and crop diseases from UAV-based aerial images. Cluster Computing, 26(2): 1297–1317, doi: 10.1007/S10586-022-03627-X.

Chen, Z., Gao, T., Sheng, B., Li, P., Chen, C.L.P. and Li, P. 2020. Outdoor shadow estimating using multiclass geometric decomposition based on BLS. IEEE Transactions on Cybernetics, 50(5): 2020, doi: 10.1109/TCYB.2018.2875983.

Chen, Z., Qiu, G., Li, P., Zhu, L., Yang, X. and Sheng, B. 2023. MGNAS: Distilling adaptive combination of multiple searched networks for one-shot neural architecture search. IEEE Transactions on Pattern Analysis and Machine Intelligence, Accessed: May 10, 2024. [Online]. Available: https://ieeexplore.ieee.org/abstract/document/10179167/.

Chodey, M.D. and Noorullah Shariff, C. 2022. Hybrid deep learning model for in-field pest detection on real-time field monitoring. Journal of Plant Diseases and Protection, 129(3): 635–650, doi: 10.1007/S41348-022-00584-W/METRICS.

Chouhan, S.S., Kaul, A. and Singh, U.P. 2019a. Plants leaf segmentation using bacterial foraging optimization algorithm. 2019 International Conference on Communication and Electronics Systems (ICCES), pp. 1500–1505, doi: 10.1109/ICCES45898.2019.9002039.

Chouhan, S.S., Kaul, A. and Singh, U.P. 2019b. Radial basis function neural network for the segmentation of plant leaf disease. 2019 4th International Conference on Information Systems and Computer Networks (ISCON), pp. 713–716, doi: 10.1109/ISCON47742.2019.9036299.

Dai, L. et al. 2024a. A deep learning system for predicting time to progression of diabetic retinopathy. Nat. Med., 30(2): 584–594, doi: 10.1038/S41591-023-02702-Z.

Dai, L. et al. 2024b. A deep learning system for detecting diabetic retinopathy across the disease spectrum. Nature Communications, Accessed: May 10, 2024. [Online]. Available: https://www.nature.com/articles/s41467-021-23458-5.

Dhingra, G., Kumar, V. and Joshi, H.D. 2019. Basil leaves disease classification and identification by incorporating survival of fittest approach. Chemometrics and Intelligent Laboratory Systems, 186: 1–11, doi: 10.1016/J.CHEMOLAB.2019.01.006.

Farooqui, N.A., Mishra, A.K. and Mehra, R. 2023. Concatenated deep features with modified LSTM for enhanced crop disease classification. Int. J. Intell. Robot. Appl., 7(3): 510–534, doi: 10.1007/S41315-022-00258-8/METRICS.
