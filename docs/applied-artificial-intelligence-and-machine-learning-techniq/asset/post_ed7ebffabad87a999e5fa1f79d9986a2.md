
[6] R. Adam, K. Dell'Aquila, L. Hodges, T. Maldjian, and T. Q. Duong, “Deep learning applications to breast cancer detection by magnetic resonance imaging: A literature review,” Breast Cancer Research, vol. 25, no. 1, p. 87, 2023.

[7] S. Patel, Z. Hassan, S. Iniyan, and U. Desai, “Multi cancer prediction using deep learning and cnn algorithm,” in 2024 second international conference on inventive computing and informatics (ICICI), pp. 214–221, IEEE, 2024.

[8] L. Meng, T. Zheng, Y. Wang, Z. Li, Q. Xiao, J. He, and J. Tan, “Development of a prediction model based on lasso regression to evaluate the risk of non-sentinel lymph node metastasis in chinese breast cancer patients with 1–2 positive sentinel lymph nodes,” Scientific Reports, vol. 11, no. 1, p. 19972, 2021.

[9] F. Pespane, A. Rotili, G. M. Agazzi, F. Botta, S. Raimondi, S. Penco, V. Dominelli, M. Cremonesi, B. A. Jereczek-Fossa, G. Carrafiello, et al., “Recent radiomics advancements in breast cancer: Lessons and pitfalls for the next future,” Current Oncology, vol. 28, no. 4, pp. 2351–2372, 2021.

[10] Y. Yu, Y. Tan, C. Xie, Q. Hu, J. Ouyang, Y. Chen, Y. Gu, A. Li, N. Lu, Z. He, et al., “Development and validation of a preoperative magnetic resonance imaging radiomics-based signature to predict axillary lymph node metastasis and disease-free survival in patients with early-stage breast cancer,” JAMA Network Open, vol. 3, no. 12, pp. e2028086, 2020.

[11] X. Zheng, Z. Yao, Y. Huang, Y. Yu, Y. Wang, Y. Liu, R. Mao, F. Li, Y. Xiao, Y. Hu, et al., “Deep learning radiomics can predict axillary lymph node status in early-stage breast cancer,” Nature Communications, vol. 11, p. 1234, 2020.

[12] S. S. Chakravarthy and H. Rajaguru, “Automatic detection and classification of mammograms using improved extreme learning machine with deep learning,” IRBM, vol. 43, no. 1, pp. 49–61, 2022.

[13] X. Guo, Z. Liu, C. Sun, L. Zhang, Y. Wang, Z. Li, J. Shi, T. Wu, H. Cui, J. Zhang, et al., “Deep learning radiomics of ultrasonography: Identifying the risk of axillary non-sentinel lymph node involvement in primary breast cancer,” EBioMedicine, vol. 60, 2020.

[14] X. Gong, Q. Li, L. Gu, C. Chen, X. Liu, X. Zhang, B. Wang, C. Sun, D. Yang, L. Li, et al., “Conventional ultrasound and contrast-enhanced ultrasound radiomics in breast cancer and molecular subtype diagnosis,” Frontiers in Oncology, vol. 13, p. 1158736, 2023.

[15] T. C. I. Archive, “Qin breast DCE-MRI dataset,” https://www.cancerimagingarchive.net/collection/qin-breast/, 2023. Accessed: 2024-04-24.

[16] T. C. I. Archive, “Home,” https://www.cancerimagingarchive.net. Accessed: 2024-04-24.

[17] P. Rajasree, A. Jatti, D. Santosh, U. Desai, and V. D. Krishnappa, “Breast masses detection and segmentation in full-field digital mammograms using unified convolutional neural network,” in 2022 44th annual international conference of the IEEE engineering in medicine & biology society (EMBC), pp. 1002–1007, IEEE, 2022.

## 6 Enhancing Deep Learning-Based Colon Cancer Detection Using Attention Module

Sk Mahmudul Hassan, Kumar Sekhar Roy, K Susheel Kumar, Arnab Kumar Maji, Keshab Nath, and Ruhul Amin Hazarika

### 6.1 INTRODUCTION

Colorectal cancer stands as one of the leading causes of cancer-related deaths worldwide, with its incidence steadily rising over recent decades. Timely detection and accurate diagnosis play pivotal roles in improving patient outcomes, yet existing screening methods often suffer from limitations in sensitivity, specificity, and accessibility. In this context, the integration of deep learning techniques into the realm of medical imaging offers promising avenues for enhancing colon cancer detection and diagnosis.

According to cancer registry reports, India is witnessing a rising trend in cancer cases. According to a study, there will be a rise in cancer cases between 2010 and 2020. India's total cancer burden was predicted to increase by 31.4% between 2015 and 2025 [1]. According to a National Cancer Institute (NIH) estimate, 1,806,950 new cases of cancer will be identified in the United States in 2020, accounting for about 606,520 deaths [2]. With an annual incidence of 1.2 million cases and a 50% fatality rate, colorectal cancer, also known as cancer of the large intestine, is the third most common cancer worldwide and the fourth major cause of cancer-related deaths [3]. Therefore, cancer is considered a major challenge for doctors and researchers.

Researchers and scientists have studied and proposed methods for early diagnosis of cancer. Medical imaging is a useful tool that helps in identifying cancer early on and is important in this process. Several computer-aided diagnosis methods (CADs) were put out to automatically diagnose colon cancer symptoms [4]. Machine learning (ML), which is a subfield of artificial intelligence widely used in medical fields such as brain tumor segmentation, Alzheimer's detection, cancer detection and classification, etc. In the early days, traditional machine learning techniques were used, which were predominantly based on extraction of features. Hand-craft feature extraction is a complex process and has lot of weaknesses as the performance heavily depends on the features. In order to address these shortcomings, deep learning (DL), a type of representation learning was used, which has the ability to learn the features automatically and also increases the performance.

In recent times, DL has gained much attention due to the combination of automatic feature learning, scalability, end-to-end learning, and the availability of frameworks and hardware [5]. Because deep learning algorithms can extract high-level features straight from raw images, they are effective in tumor segmentation and cancer detection and diagnosis. In this research, a convolutional block attention module (CBAM) based CNN model is proposed for effective identification of lung and colon cancer. Fusion of CBAM and CNN models enhances the feature extraction by focusing on the relevant features and hence increases the performance of the model.

The remaining chapter is organized as follows: Section 6.2 discusses the related work on the identification of lung and colon cancers using DL approaches. The proposed methodology is discussed in Section 6.3. Section 6.4 contains the results and discussion along with the dataset and the hyperparameter used in this chapter. Finally, the paper concludes with Section 6.5.

### 6.2 LITERATURE SURVEY

Numerous work has been carried out by researchers in classification of cancer using ML/DL, such as a hybrid feature space based colon classification (HFS-CC) technique used by Saima Rathore et al. [5] to identify colon cancer. Conventional features such as morphological, texture, scale-invariant feature transform (SIFT), and elliptic Fourier descriptors (EFDs) are used to extract the features, and a kernel SVM classifier was used for classification and achieved an accuracy rate of 98.07%. Mehedi Masud et al. [6] used 2D Fourier and 2D discrete wavelet features to identify colon and lung cancers. After extraction of features, the author used CNN model for classification and achieved an accuracy rate of 96.33%. Jianpeng Zhang et al. [7] classify medical images along with colorectal cancer images. In this paper, the author proposed a CDHVF algorithm that combines three pre-trained DL model and two hand-crafted based feature extraction techniques. A. Karthikeyan et al. [3] designed one CNN architecture consisting of eighteen CNN layers to identify the stages in colon cancer. The author fused CNN and LSTM in this work and achieved an accuracy rate of 91%.

Ben Hamida et al. [8] reviewed several DL architectures such as AlexNet, VGG16, InceptionV3, ResNet, and DenseNet architectures to identify colon cancer and proposed UNet and SegNet architecture. They also used patch level image classification, and using SegNet they achieved an accuracy rate of 98.66%.

Md. Alamin Talukder et al. [9] proposed a hybrid ensemble feature extraction based model to identify lung and colon cancers. In this paper, the authors extracted the features using transfer learning on five different DL architectures namely VGG16, VGG19, MobileNet, DenseNet169, and DenseNet201. After extraction of features some well-known ML classifiers such as SVM, RF, XGB, etc. are used for classification.

Indu Chhillar et al. [10] proposed one feature engineering based ML approach to identify lung and colon cancers. In this paper, they extracted 52 Haralick-based texture features and color-based features. With a combine feature set
