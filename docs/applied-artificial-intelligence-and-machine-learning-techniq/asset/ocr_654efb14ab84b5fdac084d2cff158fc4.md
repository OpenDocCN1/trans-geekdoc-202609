# TABLE 6.4 Performance Comparison

| Model Name | Parameter | Depth | Accuracy (%) |
|---|---|---|---|
| VGG16 [16] | 138.4M | 16 | 96.23 |
| VGG19 [16] | 143.7M | 19 | 96.51 |
| InceptionV3 [17] | 23.9M | 189 | 97.20 |
| ResNet50 [18] | 25.6M | 107 | 97.43 |
| DenseNet121 [19] | 8.1M | 242 | 96.07 |
| MobileNetV2 [20] | 3.5M | 105 | 94.50 |
| Proposed | 0.0565M | 13 | 98.34 |

model in terms of the ROC-AUC curve. Figure 6.6 shows the ROC-AUC curve of the proposed model, and the figure shows that the proposed model classifies the images with high-performance accuracy.

To better demonstrate the feature extraction capability in the proposed model, some state-of-the-art DL models are implemented for comparison. Different variants of DL such as VGG16, VGG19, InceptionV3, ResNet50, DenseNet, EfficientNetB0, and MobileNetV2 are considered for comparison. The performance comparison is shown in Table 6.4. From Table 6.4, it is seen the proposed model gives higher performance accuracy as compared to the state-of-the-art DL architectures with fewer parameters.

# 6.5 CONCLUSION

This study demonstrates the effectiveness of incorporating attention modules into deep learning-based models for enhancing colon cancer detection from medical imaging data. The integration of attention modules allows the model to dynamically adapt its focus based on the saliency of features within the image, enabling it to prioritize areas with potentially malignant lesions while suppressing irrelevant background noise. In this chapter, we have proposed one lightweight DL model with CBAM in the identification of lung and colon cancers. The performance of the proposed CNN with CBAM model is compared with CNN architecture without self-attention model and several state-of-the-art DL architectures. The result shows that CNN with attention has the better ability to identify the images and achieves an accuracy rate of 98.34%. Further, the proposed model is compared with several DL models in terms of parameters, and it is seen that the proposed model used a few parameter and less model depth.

# REFERENCES

+   [1] Shafi, L., Iqbal, P., Khaliq, R.: Cancer burden in india: A statistical analysis on incidence rates. Indian Journal of Public Health **67**(4), 582–587 (2023)
+   [2] Pacal, I., Karaboga, D., Basturk, A., Akay, B., Nalbantoglu, U.: A comprehensive review of deep learning in colon cancer. Computers in Biology and Medicine **126**, 104003 (2020)