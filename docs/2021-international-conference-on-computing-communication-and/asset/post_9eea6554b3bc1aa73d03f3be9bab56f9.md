
## Machine Learning Approach for Detection of Diabetic Retinopathy with Improved Pre-Processing

Ayushi Sharma*
Department of Information Technology,
Ramrao Adik Institute of Technology, Nerul
sharma.ayushinks@gmail.com

Swapnil Shinde
Department of Information Technology,
Ramrao Adik Institute of Technology, Nerul
swapnil.shinde@rait.ac.in

Imran Ismail Shaikh
Department of Information Technology,
Ramrao Adik Institute of Technology, Nerul
ishaikh422.is@gmail.com

Madhav Vyas
Department of Information Technology,
Ramrao Adik Institute of Technology, Nerul
madhav.vyas@rait.ac.in

Soumya Rani
Department of Information Technology,
Ramrao Adik Institute of Technology, Nerul
soumyarani4021998@gmail.com

### Abstract

Diabetic Retinopathy has been one of the common reason why diabetic patients lose sight. It is caused by the damaging of the blood vessel of the light sensitive tissue at the back of the eye or the retina. The traditional methods for the detection of the disease requires lots of time and efforts hence the proposed system aims to detect diabetic retinopathy using Image Processing and Machine Learning. The input provided to the proposed system are the retinal images from the standard databases DIARETDB0 and DIARETDB1. The system aims to automate the process of detection using a combination of basic image processing steps with more focus on pre-processing to obtain clear image for feature extraction, further Machine Learning algorithms are applied for classification. The statistical features such as area and perimeter are obtained from blood vessels and exudates after pre-processing stage, different pre-processing techniques such as grayscale conversion, binarization, canny edge detection and some morphological operations including image dilation and erosion are applied to obtain clear image. The Machine Learning algorithms are used for result analysis are Weighted KNN, Cubic SVM and Simple Tree which provides an accuracy of 85.8%, 87.2% and 88.6% respectively. The sensitivity and specificity parameters are also obtained, Simple tree yields better results for all the three result parameters.

### Keywords

Blood Vessels; Diabetic Retinopathy; Exudates; Machine Learning; Weighted KNN

## I. INTRODUCTION

### A. Diabetic Retinopathy

Diabetic Retinopathy (DR) is a medical condition in which a patient suffering from diabetes have some complexities in the retina, and due to these complexities, the patient’s eyes are affected. Diabetic Retinopathy is caused by the damage to the blood vessels present in the retina due to diabetes. The blood vessels in the retina either swell up or contract which leads to formation of lumps of fluid or blood which are called as

exudates, hemorrhage and micro aneurysm. These are the early symptoms that can be seen in the retinal images of a diabetic patient. It can also result in permanent loss of vision [2]. It is predicted that the number of diabetic retinopathy patients would increase from 7.7 million to 11 million by 2030 and to 14.5 million by 2050. A survey conducted by Rajendra Prasad Centre for Ophthalmic Sciences and AIIMS, New Delhi in 2019 shows that one out of 46 diabetic patients suffers from diabetic retinopathy. The retinal image of normal eye and DR affected eye is shown in Fig. 1.

![](img/dbca737b9377865a14c4b5d64041ef89_0_0.png)

**Fig. 1. Normal V/s DR affected Retina [2]**

The treatment for mild cases could be done by managing sugar level of the blood and in advance cases the help of surgery or laser treatment is taken [3]. The techniques used in existing system includes Binarization, Thresholding, Opening, Adaptive Histogram Equalization, and Median Filter.

### B. Problem Definition

Diabetic Retinopathy is a growing issue and the leading cause of blindness in the working age adults that is people whose age ranges between 20 and 74. Currently that statistics show that nearly 7.7 million people have suffered from diabetic retinopathy and it is predicted that the number would increase to 11 million by the year 2030 (nearly double in the next ten years) and 14.5 million by 2050. In India, the severity of diabetic retinopathy is so much that around 18% of the Indian citizen are currently suffering from diabetic retinopathy.[4] There are important differences over the past few decades in diagnosis, medical care, socioeconomic factors and other risk factors that influence the prevalence and geographic distribution of diabetes and retinopathy as well.

In statistics of the year 2002 it was witnessed that nearly 5 million people suffered from eye diseases, reason being Diabetic retinopathy which rounds up to almost 5% of world blindness. The cases of Diabetic retinopathy are gradually increasing, and hence there is a chance that probably more individual will suffer from complications in the eye, and if these complications are not properly managed, they may lead to permanent loss of vision.

The project aims to automate the process of identifying diabetic retinopathy so that preventive measures can be taken in time, and the effect of diabetic retinopathy can be minimized. Because of the automation of the process, identifying diabetic retinopathy in the early stages becomes easier and as a result, proper treatment can be provided at the proper time by the doctors.

### C. Scope of the project

There are many approaches being pursued to learn more about the development and progression of diabetes-related sight loss and to identify improvements in diagnostics and treatments. Across the world, clinical trials are actively testing new options and evaluating new practices to improve the way by which diabetes-related sight loss is detected and treated. Some examples of these studies are included below.

Researchers are aware of the importance of early detection of the complications of diabetes to limit significant damage to the eye and loss of sight. As such, research teams are actively seeking improvements in the ways by which diabetes-related sight loss is identified and when it is detected. One such clinical trial is aiming to develop and test a new predictive technology that could improve the way in which Diabetic Retinopathy is identified. Researchers aim to analyze details about the individual's background, medical history and laboratory test results to develop an improved means of identifying and managing the condition.

Another study also seeks to test artificial intelligence to detect diabetic retinopathy. Research also underway seeks to find new molecules circulating in the blood stream which could highlight the prognosis of people living with diabetic retinopathy; namely identifying those people for whom the condition may be mild, moderate or more severe overtime.

The aim of the project is to identify the severity based on automated way for extraction of different features (including

Blood Vessels and Exudates) of the retinal images of a diabetic retinopathy patient so that preventive measures can be taken in the earlier stage of the diabetic retinopathy.

### D. Objective and Aim

- To automate the process of diagnosis of Diabetic Retinopathy
- To diagnose if the person suffers from diabetic retinopathy or not.
- To increase the efficiency of the system.

The main motive of the proposed system is to automate the whole process of detecting diabetic retinopathy. The input to the system will be the retinal images. The system will apply filtering techniques to those images. Image pre-processing steps are applied to get accurate result. Customized algorithms for the extraction of blood vessel and exudates are applied on the images. Finally the system will detect diabetic retinopathy i.e. whether the patient is suffering from diabetic retinopathy or not.

## II. LITERATURE SURVEY

The diabetic retinopathy concerns not only the technical aspects such as image processing and machine learning algorithms, but also the non-technical aspects such as what features to extract, and so on.

Hemanth D. et al. [6], have proposed a hybrid method which combines image processing and deep learning on DR fundus images for improved detection. The authors have performed Histogram equalization and CLAHE on the DR images and passed it to CNN for classification. CNN provides higher accuracy but involves computation time so the authors suggest to use some pre-processing methods in image processing to reduce the same.

R. Ravindraiiah et al [8] used fuzzy based clustering method, which are less complex and more robust in their system, it groups pixels with common features and accumulates data into distinct datasets. The processing steps involved in their paper included fixing the number of clusters 'C' and randomly initializing the cluster centers Ci, updating the membership matrix Mij, updating the cluster centers Ci, updating the membership matrix Mij, updating the Objective Function JMKSFCM, If the absolute value of (J, t-J, t-1) is less than epsilon then stop the iteration process otherwise repeating the steps 2 to 4 Where e = 0.0001.

Another paper by Shailesh Kumar et al [7] proposed a system that extracts the micro aneurysm i.e. the tiny red spots on the retina for the early detection of diabetic retinopathy. The process included basic steps such as the green channel technique, adaptive histogram equalization, segmentation and SVM for classification.

The system proposed by Karkhanis Apurva Anant, Tushar Ghorpade, Vimla Jethani [9] used the methods to classify DR
