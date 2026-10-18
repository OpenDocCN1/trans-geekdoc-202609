
The trained deep learning models were evaluated using accuracy, precision, recall, and F1-score. `VGG19` emerged as the most accurate, achieving 98.78% top-1 accuracy. The error was, therefore, minimal, meaning its 19-layer architecture effectively captured fine patterns, ensuring precise breast cancer stage classification. `VGG16`, with its 16-layer architecture, achieved 93.23% accuracy. Though slightly less accurate than `VGG19` model, it remains a strong model, balancing computational efficiency with reliable predictive performance.

This model achieved 90.23% accuracy, leveraging inception modules for multi-scale feature extraction to handle the complex histopathological images. Residual learning mitigated vanishing gradients, enabling it to reach 88.98% accuracy. Though slightly less precise than others, it remains valuable for deep networks.

[Figure 7](#ch5.xhtml#fig5_7) presents the evaluation metrics—precision, recall, and F1-score—for deep learning models used in breast cancer stage classification. `VGG19` outperformed others, achieving 97.80% precision, 98.50% recall, and a 98.15% F1 score. These results highlight its accuracy in identifying true positives while minimizing false positives, a crucial factor in medical image classification. The F1-score further reinforces `VGG19`’s balanced performance, making it the most reliable model in this study.

![Figure 7: Performance score of each model.](images/fig5_7_C.jpg)

Figure 7: Performance score of each model.

![Figure 6: Accuracy of each model.](images/fig5_6_B.jpg)

Figure 6: Accuracy of each model.

`VGG16` achieved 92.50% accuracy, of 92.50%, 93.10% recall, and an F1-score of 92.80%, performing slightly below `VGG19` but remaining a strong model for breast cancer classification. `Inception V3` recorded 89.40% precision, 90.10% recall, and an F1-score of 89.75%, demonstrating solid performance despite lower precision than `VGG` models. `ResNet50`, the least efficient, attained 87.20% precision, equal to 87.20%, 88.00% recall, and an F1-score of 87.60%, still providing reasonable accuracy in distinguishing cancer stages.

The confusion matrices in [Figure 8](#ch5.xhtml#fig5_8) illustrate the classification performance of `VGG19`, `VGG16`, `Inception V3`, and `ResNet50` in breast cancer staging. `VGG19` excelled with 490 true positives and only 10 false negatives, demonstrating strong accuracy in identifying positive cases. It also recorded 8 false positives and 492 true negatives minimizing classification errors and confirming its status as the best-performing model in this study.

![Figure 8: Confusion matrices of each model.](images/fig5_8_B.jpg)

Figure 8: Confusion matrices of each model.

`VGG16` showed strong cancer detection with 461 true positives but missed more cases than `VGG19`, recording 39 false negatives and 25 false positives. `Inception V3` had 445 true positives but struggled with 55 false negatives and 32 false positives, showing moderate classification efficiency. `ResNet50` performed the weakest, with 432 true positives, 68 false negatives, and 37 false positives, highlighting its limitations in cancer stage classification. Confusion matrices reveal varying model effectiveness, with `VGG19` leading in accuracy. The `AUC-ROC` scores in [Figure 9](#ch5.xhtml#fig5_9) highlight each model’s ability to distinguish cancerous from non-cancerous cases. `VGG19` achieved the highest score of 0.995, demonstrating strong reliability for clinical use. `VGG16` followed with 0.930, showing solid discrimination but slightly lower than `VGG19`. `Inception V3` recorded 0.905, indicating respectable classification ability, though less effective than the `VGG` models. `ResNet50` requires further optimization to improve its differentiation between cancer stages.

![Figure 9: AUC-ROC performance of each model.](images/fig5_9_B.jpg)

Figure 9: AUC-ROC performance of each model.

[Figure 10](#ch5.xhtml#fig5_10) summarizes the performance of `VGG19`, `VGG16`, `Inception V3`, and `ResNet50` over 360 epochs, highlighting their accuracy and data loss trends. All models showed a steady decline in loss values as training progressed. `VGG19` demonstrated the strongest performance, reducing loss from 1.500 at epoch 0 to 0.030 at epoch 360, achieving 99.50% accuracy. `VGG16` followed with a final loss of 0.150 and 95.00% accuracy, while `Inception V3` and `ResNet50` ended with losses of 0.150 and 0.300, respectively. The results confirm `VGG19` as the most effective model for breast cancer classification.

![Figure 10: Accuracy and data loss of each model.](images/fig5_10_C.jpg)

Figure 10: Accuracy and data loss of each model.

The models demonstrated steady accuracy improvements across epochs, confirming their learning capabilities. `VGG16` progressed from 45.00% to 95.00%, showing strong classification performance. `Inception V3` improved from 40.00% to 91.00%, while `ResNet50`, the least accurate initially at 38.00%, reached 86.00% by epoch 360. The consistent accuracy gains highlight deep learning’s effectiveness in classifying complex histopathological images, with `VGG19` emerging as the most reliable model due to its low data loss and high accuracy.

This research confirms the efficiency of deep learning models, particularly `VGG19`, in breast cancer stage classification using histopathological images. `VGG19`’s high accuracy (99.50%) and low data loss highlight its ability to learn complex patterns, making it a reliable tool for clinical applications. Its consistent performance underscores its potential as a diagnostic aid for pathologists in treatment planning.

Advancements in deep learning enable real-time integration of models like `VGG19` into medical workflows, facilitating automated histopathological slide analysis. This enhances diagnostic speed, reduces human error, and improves patient outcomes by enabling rapid cancer stage identification and timely interventions.

Deep learning models can extend beyond breast cancer, enhancing diagnostics for various oncological diseases. Training on diverse datasets improves generalizability, enabling accurate classification across cancer types. As data quality and model optimization advance, these systems may aid in both staging and identifying optimal treatment strategies.

Real-time integration enhances telemedicine, enabling remote collaboration among pathologists and oncologists, especially in understaffed regions. User-friendly interfaces ensure healthcare professionals can leverage advanced technology without extensive technical expertise.

## 7\. Conclusion

This research confirms the effectiveness of deep learning models, particularly `VGG19`, in breast cancer stage classification using histopathological images. `VGG19` achieved 99.50% accuracy with minimal data loss (0.030) after 360 epochs, outperforming `VGG16` (95.00%), `Inception V3` (91.00%), and `ResNet50` (86.00%). The results highlight `VGG19`’s superior ability to learn complex patterns, making it a reliable tool for clinical diagnosis. The study reinforces the potential of AI-driven diagnostics to enhance accuracy, efficiency, and patient outcomes, emphasizing the need for integrating machine learning into medical imaging for improved oncology applications.

## References

*   [Bhosale, Y. H. and Patnaik, K. S.](#ch5.xhtml#R_ref8_1) (2023). Bio-medical imaging (X-ray, CT, ultrasound, ECG), genome sequences applications of deep neural network and machine learning in diagnosis, detection, classification, and segmentation of COVID-19: A meta-analysis & systematic review. Multimedia Tools and Applications, 82(25): 39157–39210.

*   [Bilal, K. and Sajid, M.](#ch5.xhtml#R_ref8_2) (2022). Blockchain technology: Opportunities & challenges. In 2022 International Conference on Data Analytics for Business and Industry (ICDABI) (pp. 519–524). IEEE.
