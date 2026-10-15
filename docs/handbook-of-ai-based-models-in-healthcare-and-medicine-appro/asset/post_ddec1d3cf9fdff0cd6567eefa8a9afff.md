
## 7 A Survey of Machine Learning- and Deep Learning-Based Techniques for Diabetic Retinopathy Screening

Nitika Sambyal, Poonam Saini, and Rupali Syal

### 7.1 INTRODUCTION

Diabetic retinopathy (DR) is an ophthalmic condition associated with diabetes, which is also identified as a primary cause of visual impairment worldwide [1]. The World Health Organization (WHO) predicts that the total percentage of patients with DR is estimated to increase to 4.4% by 2030 [2]. According to a recent study, DR is also identified as the fifth-most common cause of moderately severe visual impairment (MSVI) [3]. Diabetic retinopathy (DR) is identified as progressive damage to the retina, which may cause blurred vision or even irreversible blindness in extreme cases [4]. The main risk factors for DR are high levels of glucose in the blood, the presence of high blood pressure, dependence on insulin, nutritional and genetic factors, etc.

### 7.1.1 Retina

The retina is a thin (0.5 millimetre) tissue lining present at the back of the eye on the eye’s interior. Any damage to the retina obstructs the receiving and processing of light, which further prevents the brain from receiving visual information, ultimately leading to blindness. Figure 7.1 shows a brief overview of the retina when viewed through an ophthalmoscope.

The main components of the retina are optic disc (nerve), blood vessels, fovea, and macula [5]. The optic disc (optic nerve head) is a circular or white area present in the centre of the retina and is used to transmit visual information from the retina to the brain. Blood vessels are the extensive vascular structure network that maintains the functionality of the retina. The central retinal artery (CRA) enters the eye at the optic disc, from where it divides into two major branches. These branches further sub-divide into arterioles; namely the superior nasal, inferior temporal, superior temporal, and inferior nasal arterioles. The macula is the central part of the retina and measures five millimetres in diameter. The fovea is a blood vessel-free reddish spot present at the centre of the macula which provides sharp central vision.

![](img/a2fc2296b12812e9151e817bff1de16d_131_0.png)

FIGURE 7.1 An overview of the retina. IT: Inferior temporal, ST: Superior temporal, IN: Inferior nasal, SN: Superior nasal

### 7.1.2 DIABETIC RETINOPATHY

The severity and duration of hyperglycemia, genetic predisposition, and metabolic control are the prime factors leading to DR [6]. Traditionally, ophthalmologists have examined the fundus photographs of patients to determine the presence of cues associated with DR. The common DR-associated retinal lesions are hemorrhages, microaneurysms, soft exudates, and hard exudates [7, 8], as illustrated in Figure 7.2. Hemorrhages, also known as red lesions, are dot, blot and flame-shaped and may occur in deeper or more superficial layers of the retina [2]. Microaneurysms are circular in shape and have an approximate size of 100–120 micrometres [9]. Cotton wool spots are small, white, puffy patches with smooth edges [10]. Hard exudates are identified as bright yellow spots caused by the leakage of fats and proteins on the retina [11]. Based on the magnitude of DR severity, the fundus images can be classified into various stages, from healthy to mild to severe to most severe [12].

The fundus photography captures the rear of the eye, known as the fundus, using a specialized fundus camera with a microscope attached to it. The fundus images enable easy immediate review, image magnification, enhancement, and manipulation. This allows effortless monitoring and control of the progression of DR. The manual inspection of fundus images by ophthalmologists using a fundus camera is tedious, time-consuming, and subject to human error [13]. To overcome these limitations and to allow accurate mass screening, the need for diabetic retinopathy computer-aided diagnosis (DR-CAD) system has become indispensable [14]. Such automated systems can aid in early diagnosis, which in turn can control vision deterioration, thereby reducing and possibly preventing the risk of blindness among diabetic patients [15]. The CAD system developed using machine learning (ML) and deep learning (DL) algorithms can enable the speedy interpretation of medical image findings without the need of a skilled professional [16, 17]. The ML algorithms – namely artificial neural networks (ANN), decision trees, k-nearest neighbour (KNN), random forest, and support vector machines (SVM) – are based on expert knowledge and require manual feature extraction and a lot of time for tuning features. On the contrary, deep learning algorithms like convolutional neural networks (CNN), generative adversarial networks (GANs), recurrent neural networks (RNN), etc. are faster and more accurate, as they automatically extract desirable features from the image by learning through multiple levels of abstraction [18–20].

This chapter provides a critical review of various DR-CAD systems consisting of DR classification and retinal lesion detection models that have been proposed to date.

This chapter is organized into seven sections. Section 7.2 focuses on the basic structure and components of a DR-CAD system. Section 7.3 provides an outline of the research papers reviewed. Section 7.4 presents an overview of the literature corresponding to the binary and multistage classification of DR. Section 7.5 presents a review of various models used in the detection and segmentation of retinal abnormalities in fundus images. In Section 7.6, a methodology has been proposed for automatic detection of DR. Section 7.7 presents the findings of the review along with a future scope.

![](img/a2fc2296b12812e9151e817bff1de16d_132_0.png)

Fundus image

FIGURE 7.2 Retinal abnormalities associated with diabetic retinopathy

### 7.2 DR-CAD SYSTEM

A complete DR-CAD system helps in the identification of DR, along with the detection and segmentation of retinal lesions, for better severity analysis. However, there may be some systems that focus on either the classification of DR or retinal lesion detection in fundus images. Figure 7.3 presents a complete structure of basic DR-CAD systems consisting of five main components: preprocessing, segmentation of region of interest (ROI), feature extraction and selection, classification, and retinal lesion detection.

![](img/a2fc2296b12812e9151e817bff1de16d_133_0.png)

FIGURE 7.3 A DR-CAD system

A DR-CAD system consists of five main phases:
- 1. **Preprocessing:** This phase focuses on the improvement of image quality by suppressing distortions or noise, image brightness normalization, and enhancement of significant features for better processing. In DR-CAD systems, it helps in the suppression of anatomical regions like blood vessels and optic disc to clearly visualize the retinal abnormalities.
- 2. **Segmentation:** In this phase, the anatomical structures are segmented so that the region of interest can be obtained for further processing. Segmentation of other anatomical structures like blood vessels and the optic discs is done from fundus images, to better visualize the candidate lesion regions.
- 3. **Feature extraction and selection:** This phase helps in the extraction of significant features from the segmented image. Initially, the pixel- or region-level features are extracted from the candidate retinal lesions. The best-performing features are selected to form a feature vector.
- 4. **Classification:** The features extracted in the above step are then used to categorize the retinal images into various classes. Based on the features extracted from the preprocessed, segmented fundus image, it is classified as either healthy or unhealthy. For multistage classification, the unhealthy fundus image can be further classified, depending on the severity of the disease.
- 5. **Detection and segmentation of retinal lesions:** To allow for better severity screening of DR, the retinal lesions from the unhealthy fundus images can also be detected and segmented. This helps in determining the number of lesions, their size, and their location, which can further allow physicians to better assess the disease severity.
