Our hypothesis is, in the future, to incorporate the experience of pathologists when constructing our model. By analyzing deep neural network decisions, we will try to identify regions in an input breast cancer image that indicate a particular type of cancer. By evaluating the diagnostic experience as a priori, we can determine the differences in the support areas when the choice is made between pathologists and algorithms. Additionally, we can construct an attention-based network model that will help to improve the model’s accuracy in the future.

# 3.6 CONCLUSIONS

An adversarial network-based approach provides unique advantages in medical image processing. In this study, we developed a semi-supervised GAN capable of learning both labeled and unlabeled images. Our research has experimentally evaluated this proposed model for multi-classification by using semi-supervised GAN on the BreaKHis dataset over four magnification factors (40×, 100×, 200×, and 400×). For the magnification factor 100× and 400×, the best accuracy of 88% was obtained. Also, the AUC of 0.95 was accomplished in the magnification factor 400×. Furthermore, this study showed that SSGAN performed better with a smaller number of labeled images than CNN. In the future, we will explore multi-class classification using various architectures and data-balancing techniques. The proposed scheme achieved promising results for the task of categorizing breast cancer images. This method can reduce pathologists’ workload and improve diagnosis quality when used in breast cancer diagnostic scenarios.

# KEYWORDS

+   - histopathology
+   - generative adversarial networks
+   - semi-supervised generative adversarial networks (SSGAN)
+   - convolution neural network
+   - breast cancer