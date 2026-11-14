
## 4 Experimental Results

The ChestX-ray14 dataset with 112,120 frontal-view X-ray images from 30,805 different patients labeled with one or more of 14 thoracic pathologies was utilized in experimental evaluation of the proposed MSAG-DFE framework. For enabling high-throughput deep model training and inference, the whole pipeline was developed in Python 3.10 using PyTorch 2.0 and supported by an NVIDIA RTX A6000 GPU (48 GB VRAM). Patient-level data splitting into training (70%), validation (10%), and test (20%) subsets was required to provide balanced assessment and reproducibility. This was done to avoid data leakage and any patient record overlap among sets.

A variety of evaluation metrics aimed at compensating for the dataset class imbalance were utilized to measure performance. These included F1-score, accuracy, precision, and recall, but most significantly, the area under the receiver operating characteristic curve (AUC), which is considered the gold standard for medical imaging’s imbalanced multi-label classification problems. In order to offer the best possible generalization, training was done employing early stopping and learning rate scheduling on validation AUC. In view of the multi-label classification scenario, sigmoid activation was used along with binary cross-entropy loss for all classes. We employed DenseNet-121 and ResNet-50, two state-of-the-art CNN architectures that have shown outstanding performance on medical image classification tasks and serve as standard baselines, to comprehensively benchmark MSAG-DFE.

From Figure 4, the efficiency and performance comparison of the proposed MSAG-DFE model, ResNet-50, and DenseNet-121 delivers significant new insights. The MSAG-DFE model outperforms the other two in regards to classification performance for each of the five key measures. Notably, its mean AUC of approximately 91.6% is 2.2% higher than DenseNet-121’s (89.4%) and 4.4% greater than ResNet-50’s (87.2%). Its precision is about 90.1%, an increase of 4.4% and 2.5% over ResNet-50 and DenseNet-121, respectively. MSAG-DFE provides recall increases of up to 4.9% over ResNet-50 and 3.6% over DenseNet-121, with higher precision (88.0%), recall (86.3%), and F1-score (87.1%). In medical environments where false negatives would be particularly important, these recall and F1-score improvements are particularly valuable.

In addition to its accuracy improvements, Figure 5 shows the MSAG-DFE model also has a comparable model size of about 10.5 million parameters, much lower than the 23 million parameters of ResNet-50 and slightly above DenseNet-121’s 8 million. Such a trade-off between high accuracy and medium model complexity renders MSAG-DFE a pragmatic and cost-effective solution for real-time or limited-resource scenarios. The MSAG-DFE model provides balanced strength with enhanced prediction accuracy compared to both ResNet-50 and DenseNet-121, superior computational efficiency compared to the former, rendering it extremely well-suited for use in mission-critical applications like medical diagnosis.

## Performance Metrics Comparison

![](img/106ef0dba620d314f9842503e8ef40c8_308_0.png)

## Model Parameters Comparison

![](img/106ef0dba620d314f9842503e8ef40c8_309_0.png)

Figure 5: Comparison of model parameters.

## 5 Conclusion

The MSAG-DFE model proposed and the well-known deep learning models, ResNet-50 and DenseNet-121, were deeply compared in this study to measure classification performance as well as computational efficacy. It can be seen from the data that the MSAG-DFE model outperforms the baseline models in all significant evaluation measures like mean AUC, accuracy, precision, recall, and F1-score. Significantly, the proposed model enhances recall and F1-score, which are essential for reducing false negatives in sensitive applications such as healthcare diagnosis, and reaches a better mean AUC of 91.6%, implying greater discriminatory capacity. Moreover, MSAG-DFE achieves an optimal balance between performance and resource consumption by having a lower model complexity compared to ResNet-50, with roughly 10.5 million parameters. Based on these findings, the proposed MSAG-DFE model is a highly effective and efficient framework that is perfectly suited for real-time application in high-stakes scenarios when efficiency and precision are paramount.

## References

- [1] Sinha, A. & Dolz, J. (2020). Multi-scale self-guided attention for medical image segmentation. IEEE journal of biomedical and health informatics, 25(1), 121–130.
- [2] Xu, Z., Tian, B., Liu, S., Wang, X., Yuan, D., Gu, J. & Leung, V. C. (2023). Collaborative attention guided multi-scale feature fusion network for medical image segmentation. IEEE Transactions on Network Science and Engineering, 11(2), 1857–1871.
- [3] Li, Y., Wu, Y., Huang, M., Zhang, Y. & Bai, Z. (2023). Attention-guided multi-scale learning network for automatic prostate and tumor segmentation on MRI. Computers in Biology and Medicine, 165, 107374.
- [4] Poudel, S. & Lee, S. W. (2021). Deep multi-scale attentional features for medical image segmentation. Applied Soft Computing, 109, 107445.
- [5] Yan, Q., Wang, B., Zhang, W., Luo, C., Xu, W., Xu, Z. & You, Z. (2020). Attention-guided deep neural network with multi-scale feature fusion for liver vessel segmentation. IEEE Journal of Biomedical and Health Informatics, 25(7), 2629–2642.
- [6] Xu, C., Lou, M., Qi, Y., Wang, Y., Pi, J. & Ma, Y. (2021). Multi-scale attention-guided network for mammograms classification. Biomedical Signal Processing and Control, 68, 102730.
- [7] Li, Y., Huang, M., Zhang, Y. & Bai, Z. (2024). Attention Guided Multi Scale Feature Fusion Network for Automatic Prostate Segmentation. Computers, Materials & Continua, 78(2).
- [8] Ahmed, M. R., Ashrafi, A. F., Ahmed, R. U., Shatabda, S., Islam, A. M. & Islam, S. (2023). DoubleU-NetPlus: a novel attention and context-guided dual U-Net with multi-scale residual feature fusion network for semantic segmentation of medical images. Neural Computing and Applications, 35(19), 14379–14401.
- [9] Chen, B., Liu, Y., Zhang, Z., Lu, G. & Kong, A. W. K. (2023). Transattunet: Multi-level attention-guided u-net with transformer for medical image segmentation. IEEE Transactions on Emerging Topics in Computational Intelligence, 8(1), 55–68.
- [10] Zhang, J., Luan, Z., Ni, L., Qi, L. & Gong, X. (2024). MSDANet: A multi-scale dilation attention network for medical image segmentation. Biomedical Signal Processing and Control, 90, 105889.
- [11] Smith, J. (2024). Advanced Medical Image Segmentation with Multi-Scale Feature Fusion and Attention Mechanisms. Journal of Computer Science and Software Applications, 4(4), 18–25.
- [12] Ji, Q., Wang, J., Ding, C., Wang, Y., Zhou, W., Liu, Z. & Yang, C. (2023). DMAGNet: Dual-path multi-scale attention guided network for medical image segmentation. IET Image Processing, 17(13), 3631–3644.
- [13] Wang, Z., Zou, Y., Chen, H., Liu, P. X. & Chen, J. (2024). Multi-scale features and attention guided for brain tumor segmentation. Journal of Visual Communication and Image Representation, 100, 104141.
- [14] Khan, M., Fu, S. & Ullah, I. (2025). Attention-Guided Asymmetric Multiscale Polyp Segmentation Network. IEEE Transactions on Instrumentation and Measurement.
- [15] Fiaz, M., Noman, M., Cholakkal, H., Anwer, R. M., Hanna, J. & Khan, F. S. (2024). Guided-attention and gated-aggregation network for medical image segmentation. Pattern Recognition, 156, 110812.
- [16] Ahmed, B. S., Arya, M. S., Sangeetha, S. K. B. & Auxilia Ovsin, N. V. (2022). Diabetes mellitus disease prediction and type classification involving predictive modeling using machine learning techniques and classifiers. Applied Computational Intelligence and Soft Computing, 2022(1), 7899364.
- [17] Liu, Y., Yun, H., Xia, Y., Luan, J. & Li, M. (2024). MSGAT: Multi-scale gated axial reverse attention transformer network for medical image segmentation. Biomedical Signal Processing and Control, 95, 106341.
- [18] Xu, M., Ma, Q., Zhang, H., Kong, D. & Zeng, T. (2024). MEF-UNet: An end-to-end ultrasound image segmentation algorithm based on multi-scale feature extraction and fusion. Computerized Medical Imaging and Graphics, 114, 102370.
- [19] Alam, M. S., Wang, D., Liao, Q. & Sowmya, A. (2022). A multi-scale context aware attention model for medical image segmentation. IEEE Journal of Biomedical and Health Informatics, 27(8), 3731–3739.
