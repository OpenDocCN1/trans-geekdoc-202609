
Yang, T., Wu, R., Tao, R., Wen, S., Ma, N., Zhao, Y., Yu, X., Li, H., 2020. ‘Multi-scale long short-term memory network with multi-lag structure for blood glucose prediction’, in: KDH@ECAI’20, Santiago de Compostela, Spain Virtually, pp. 136–140.

Zhu, T., Kuang, L., Daniels, J., Herrero, P., Li, K., Georgiou, P., 2022. ‘IoMT-enabled real-time blood glucose prediction with deep learning and edge computing’. IEEE Internet of Things Journal 10, 1–1.

Zhu, T., Kuang, L., Li, K., Zeng, J., Herrero, P., Georgiou, P., 2021. ‘Blood glucose prediction in type 1 diabetes using deep learning on the edge’, in: IEEE ISCAS’21, Daegu, South Korea, pp. 1–5.

Zhu, T., Yao, X., Li, K., Herrero, P., Georgiou, P., 2020. ‘Blood glucose prediction for type 1 diabetes using generative adversarial networks’, in: KDH@ECAI’20, Santiago de Compostela, Spain Virtually, pp. 90–94.

## Automated Early Detection of Diabetes Mellitus from Retinal Fundus Images Using Residual U-Net Approach

K. Sujatha, R.S. Ponmagal, N. Janaki, N.P.G. Bhavani, and SuQun Cao

### 4.1 INTRODUCTION

Diabetes mellitus (DM) is considered to be the deadliest disease prevailing across the world. Early diagnosis of DM plays a paramount role in increasing the patient’s survival rate. Recent development in the medical and technological fields offers directions to improvise the methodology of detecting and segmenting the retinal images to confine the location in helping the medical practitioners to focus on the problem and treat the patient with accurate procedures. To predict and segment the retinal images, many approaches have been proposed recently. Since deep learning methods play prominent roles in DM detection and segmentation, these two approaches are considered [1–11]. Also, as IoT is leading the technological advancement in connecting devices across the globe, integrated IoT-based routing is used with the above methods to fine-tune and locate the precise location of cancerous cells in the bone. The main challenges faced by bone cancer segmentation and IoT routing techniques are explained here [12,13]. In Ref. [14], the classification of the images is a major challenge using fully convolution networks (FCNs) architecture. The devised AGResU-Net in Ref. [10] failed to consider a clinical segmentation model to improve the segmentation accuracy.

In Ref. [15], segmentation using textural features and sparse kernel coding was developed for segmenting the bone cancers, but the major challenge lies in extending the single-dimensional data source to a multi-dimensional data source, thereby segmenting the non-normal retinal region tissues from the normal portion. Thus, the proposed project develops a method that resolves the identified issues and provides accuracy, sensitivity, specificity, and region of curve parameters along with emphasizing the performance measures such as fitness measures [16–24]. An embedded-based software product helps medical professionals, doctors, specialists, researchers, and other experts in the medical field to diagnose DM at an early stage and start the treatment accordingly (Figure 4.1).

The chapter is organized in such a way that Section 4.1 gives an introduction to diabetic retinopathy (DR). A literature survey is carried out to identify the methods discussed by the researchers in Section 4.2. The existing challenges that are prevailing are identified from the literature survey and discussed in Section 4.3 which comprises the gaps existing in the research field. The research gaps are identified and the objectives are carefully formulated after a thorough analysis of the literature articles. The deep learning model is discussed in Section 4.4 along with the results and discussion in Section 4.5. Concluding remarks for this chapter are presented in Section 4.6 followed by the references which are cited in the text.

### DIABETIC RETINOPATHY

![](img/7df621e14c1a5d96077d3e56e3977008_68_0.png)

FIGURE 4.1 Normal retina vs. retinal images with diabetic retinopathy. (Credits: ShutterStock Images.)

### 4.2 LITERATURE SURVEY

The deficit secretion of insulin by the pancreas causes DM. As the blood sugar level increases, DM progresses; DM affects the flow of blood in the circulatory system, including the retina, and causes damage to the vascular structure in the human body, which in turn decreases vision for the patient, leading to DR.

To detect DR at its early stages [25], researchers have used support vector machine (SVM), sequential minimal optimization (SMO), random forest, and naive Bayesian (NB) for classification. Nearly, 90% of accurate results for diagnosis are achieved using the above methods.

In this work [26], the conditions of DM are categorized as normal and abnormal using wavelet features with an accuracy level of 92.5%. The optic disc is detected using Karhunen–Loeve Transform (KLT) to identify DM from the images of the retina [8], by segmenting the major blood vessels. The accuracy achieved is about 91.5% with reduced computation time for histograms. The main disadvantage is that the effective output is not achieved and also the contrast of the image is very low. DR [9] may lead to vision loss if left untreated. Researchers have used discrete cosine transform (DCT) and k-nearest neighbor (k-NN) to classify DR [27].

A robust method for feature extraction followed by k-means clustering is used by the researchers for DR identification from the retinal images [10] with an accuracy of 95%. Artifacts cause some information to be lost if this method is used. The shape of the optical disc varies with severity [28–37]. The presence of blood vessels increases the complexity of diagnosis. So, the optical disc is divided into small regions of interest for area calculation and to exert the relevant features [11], facilitating the early detection carried out using an adaptive mask with variable configurations and fuzzy logic for classification. Thus, the methods proposed by the researchers depend on analysis of the retinal images. From these images, features are extracted and categorized as per the severity of the existing conditions [38–46].

### 4.3 RESEARCH GAP

Based on the survey analysis, novel methods for noise removal, feature extraction, reduction, and classification for early diagnosis of DR with robustness are an added highlight for this work. Sensitivity and specificity are used for evaluation of the performance.

### 4.4 OBJECTIVES AND RESEARCH HIGHLIGHTS

### 4.4.1 Objectives

As per the analysis of the literature, existing methods based on retinal segmentation are not efficient for image-based classification which is a main challenge for improving the segmentation accuracy and extending the single-modal data source to multi-modal data source. The research outcome of this work is develop a software product. To transform the research outcomes of this work into a software product, detect DR and perform segmentation, thus helping in the treatment of the patient and rescuing the life. The objective is to invent methods to resolve the identified issues and devise a method that helps in the early diagnosis of DR. Thus, the main aim is to design a robust and efficient DR detection scheme based on segmentation of retinal images from fundus camera using the deep learning neural network (DLNN) model embedded in IoT by emphasizing on accuracy, sensitivity, and specificity. The proposed outcome is to design a robust and efficient algorithm for deep learning neural networks for the segmentation of fundus retinal images with the simulation of DLNN models for segmentation, RoI extraction, and routing in IoT, focusing on performance metrics such as appropriateness measures. If a software product is developed using embedded technology, focusing on feasibility and utilization, it can help the medical experts to diagnose DM at an early stage from the retinal images and to start the treatment accordingly.

### 4.4.2 Research Highlights

The research highlights include:

- Identification of NL, NPDR, and PDR from the retinal fundus images
- To implement healthcare IoT (HIoT)
- RA-UNet for segmentation
- Adaptive threshold (AT) for RoI extraction
- Diagnosis using deep learning neural models with and without optimization techniques like SSOA and CAViaR
